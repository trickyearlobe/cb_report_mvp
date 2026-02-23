task :default do
    puts `rake --tasks`
end

desc "All tasks"
task :all => [
    'fetch:all',
    'run:all',
    'analyse:all',
    # 'upload_to_elasticsearch',
    # 'clean'
]

desc "Tasks for fetching data"
namespace :fetch do
    desc "Fetch all data"
    task :all => [ :nodes, :cookbooks ]

    desc "Fetch nodes from the Chef server"
    task :nodes do
        puts "Fetching nodes"
        `./scripts/fetch_nodes`
    end

    desc "Fetch cookbooks from the Chef server"
    task :cookbooks do
        puts "Fetching cookbooks"
        `./scripts/fetch_cookbooks`
    end
end

desc "Tasks for running linting and testing"
namespace :run do
    desc "Run all linting and testing"
    task :all => [ :cookstyle, :kitchen ]

    desc "Run linting using cookstyle against all cookbooks"
    task :cookstyle do
        puts "Running cookstyle on all cookbooks"
        puts `./scripts/run_cookstyle`
    end

    desc "Run converge and functional tests against all cookbooks"
    task :kitchen do
        puts "Running kitchen converge and functional tests on all cookbooks"
        puts`./scripts/run_kitchen`
    end
end

desc "Tasks for analysing data"
namespace :analyse do
    desc "Analyse all data"
    task :all => [ :cookbook_usage, :cookstyle, :kitchen ]

    desc "Analyse cookbook usage from node data"
        task :cookbook_usage do
            puts "Analysing cookbook usage from node data"
        puts `./scripts/analyse_cookbook_usage`
    end

    desc "Analyse cookstyle results and merge it to the cookbook reports"
    task :cookstyle do
        puts "Analysing cookstyle results on downloaded cookbooks"
        puts `./scripts/analyse_cookbook_style`
    end

    desc "Analyse test kitchen results and merge it to the cookbook reports"
    task :kitchen do
        puts "Analysing test kitchen results on all cookbooks"
        puts `./scripts/analyse_test_kitchen`
    end
end

desc "Upload results to Elasticsearch"
task :upload_to_elasticsearch do
    puts "Uploading results to Elasticsearch"
    `./scripts/upload_to_elasticsearch`
end

desc "Clean up local data"
task :clean do
    puts "Cleaning up"
    `./scripts/clean`
end