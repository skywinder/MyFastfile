notify = "YES"
fabric_group = "main"


desc "Update build number"
lane :bump_build_number do
    increment_build_number
    commit_version_bump
end

desc "Bump major"
lane :bump_major do
    increment_build_number
    increment_version_number(bump_type:"major")
    commit_version_bump
end

desc "Bump patch"
lane :bump_patch do
    increment_build_number
    increment_version_number(bump_type:"patch")
    commit_version_bump
end

desc "Bump minor"
lane :bump_minor do
    increment_build_number
    increment_version_number(bump_type:"minor")
    commit_version_bump
end


lane :commit_version_bump do
    commit_version_bump(message: "test message")
end

lane :upload do
    #deliver
    deliver(force: true,
            skip_metadata: true,
            skip_screenshots: true,)        
end

lane :tag do
    fetched_tag = sh("cd .. && agvtool what-marketing-version -terse1 | tr -d '\n'")
    build_number = sh("cd .. && agvtool what-version -terse | tr -d '\n'")
    add_git_tag(tag: "#{fetched_tag}(#{build_number})")
end

