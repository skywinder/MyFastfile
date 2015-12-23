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
lane :bump do
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

lane :fabric do |options|
    configuration = "Debug"
    if options[:bump]
        bump_build_number
    end

    sh("cd .. && ipa distribute:crashlytics -c ./Crashlytics.framework -f ./#{scheme}.ipa -g #{fabric_group} -n #{notify}")
end
