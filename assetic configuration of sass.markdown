gem update --system<br>
gem install sass<br>
gem install compass<br>

if you only install compass then it also include sass installation

<b>Configure Assetic in app/config/config.yml</b> 

<pre>assetic:
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
</pre>          

<b> in html.php file </b>
<pre>
    <?php $view['slots']->output('base_css','') ?>
<?php  foreach($view['assetic']->stylesheets(
   array('@AppPlayerBundle/Resources/public/assets/scss/file1.scss',           
           '@AppPlayerBundle/Resources/public/assets/scss/file2.scss'),
        array('cssrewrite'), array('output' => 'css/main.css', 'package' => 'assetic')) as $url): ?>
        <link rel="stylesheet" href="<?php echo $url ?>" />
    <?php endforeach; ?>
</pre>   
   
<b> Do assets:install & assetic:dump </b>  
<pre>
php app/console assets:install
php app/console assetic:dump
</pre>

          
