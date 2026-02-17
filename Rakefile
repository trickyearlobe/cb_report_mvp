task :default do
    tasks = Rake.application.tasks
    tasks.each do |task|
        puts task unless task.name == 'default'
    end
end

task :analyse_in_use_cookbooks do
    `./analyse_in_use_cookbooks`
end
