task :default do
    puts `rake -T`
end

desc "All tasks"
task :all => [ :fetch => :all, :run => :all, :analyse => :all]

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
        `./scripts/run_cookstyle`
    end

    desc "Run converge and functional tests against all cookbooks"
    task :kitchen do
        puts "Running kitchen converge and functional tests on all cookbooks"
        `./scripts/run_kitchen`
    end
end

desc "Tasks for analysing data"
namespace :analyse do
    desc "Analyse all data"
    task :all => [ :cookbook_usage, :cookstyle, :test_kitchen ]

    desc "Analyse cookbook usage from node data"
        task :cookbook_usage do
            puts "Analysing cookbook usage from node data"
        `./scripts/analyse_cookbook_usage`
    end

    desc "Analyse cookstyle results and merge it to the cookbook reports"
    task :cookstyle do
        puts "Analysing cookstyle results on all cookbooks"
        `./scripts/analyse_cookbook_style`
    end

    desc "Analyse test kitchen results and merge it to the cookbook reports"
    task :analyse_test_kitchen do
        puts "Analysing test kitchen results on all cookbooks"
        `./scripts/analyse_test_kitchen`
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