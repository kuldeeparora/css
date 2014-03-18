gem update --system
gem install sass
gem install compass

## if you only install compass then it also include sass

## Configure Assetic in app/config/config.yml 

assetic:
    debug:          %kernel.debug%
    write_to:       %kernel.root_dir%/../web/build
    use_controller: false
    filters:
        cssrewrite: ~
        sass:
          bin: %sass_bin_path%
        compass:
          bin: %compass_bin_path%
          apply_to: "\.scss$"
          

sass_bin_path: /usr/local/bin/sass
compass_bin_path: /usr/local/bin/compass

          