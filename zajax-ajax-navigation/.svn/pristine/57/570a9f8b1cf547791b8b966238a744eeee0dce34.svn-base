<?php
/*
Plugin Name: Zajax
Plugin URI: http://www.wordpress.org/wordpress-plugins/zajax
Description: Ajax navigation for Wordpress
Author: onigetoc
Version: 0.4
Author URI: http://www.scriptsmashup.com
*/

function zajax_enqueue_script() {

	wp_enqueue_style(
		'zajax-css', plugin_dir_url( __FILE__ ) . 'css/zajax.css', 
		array('dashicons') 
	);

	wp_enqueue_script(
		'fastclick', plugin_dir_url( __FILE__ ) . 'js/fastclick.js', 
		array() 
	);

	wp_enqueue_script(
		'zajax-js', plugin_dir_url( __FILE__ ) . 'js/zajax.js', 
		array('jquery'), null, true // add in footer    
	);
	wp_enqueue_script(
		'zajax-send-complete', plugin_dir_url( __FILE__ ) . 'js/send_complete.js', 
		array('jquery') // add in footer    
	);

	$zajax_options_get = unserialize( get_option('zajax_options') ); // Get main Content Class ID	
				
	$zajax_main = $zajax_options_get['zajax_main'];
	$zajax_main_mobile = $zajax_options_get['zajax_main_mobile'];
	$zajax_ClassID = $zajax_options_get['zajax_ClassID'];
	$zajax_search = $zajax_options_get['zajax_search'];
	$zajax_ignore = $zajax_options_get['zajax_ignore'];
	$zajax_dolist = $zajax_options_get['zajax_dolist'];
	$zajax_masonry = $zajax_options_get['zajax_masonry'];
	$zajax_body = $zajax_options_get['zajax_body'];
	$zajax_back = $zajax_options_get['zajax_back'];
	$zajax_preload = $zajax_options_get['zajax_preload'];
	

	$zajax_data = array(
		//'siteUrl' 		=> site_url() . '/',
		//'ids' 			=> $ids,
		'zajax_main' 	=> $zajax_main,
		'zajax_main_mobile' => $zajax_main_mobile,
		'zajax_ClassID' => $zajax_ClassID,
		'zajax_search' 	=> $zajax_search,
		'zajax_ignore' 	=> $zajax_ignore,
		'zajax_dolist' 	=> $zajax_dolist, // reload js file in header
		'zajax_masonry' => $zajax_masonry,
		'zajax_body'   	=> $zajax_body,
		'zajax_back'   	=> $zajax_back,
		'zajax_preload' => $zajax_preload

	);
	
	wp_localize_script('zajax-js', 'zajax_data', $zajax_data);
	
	
}
add_action( 'wp_enqueue_scripts', 'zajax_enqueue_script');
/*************************/


/* Insert anythings to web site header */ 
function zajax_insert_header() { 

	$zajax_options_get = unserialize( get_option('zajax_options') );
	
	if($zajax_options_get){			
		
		$zajax_loading = $zajax_options_get['zajax_loading'];
		
		if(!$zajax_loading) $zajax_loading = '2299dd';
	}

?>
<style>

#nprogress .spinner-icon {
  border-top-color: #<?php echo $zajax_loading ?>;
  border-left-color: #<?php echo $zajax_loading ?>;
}
#nprogress .bar {background: #<?php echo $zajax_loading ?>;}
#nprogress .peg {box-shadow: 0 0 10px #<?php echo $zajax_loading ?>, 0 0 5px #<?php echo $zajax_loading ?>;}

</style>

<?php }
add_action( 'wp_head', 'zajax_insert_header' );

/*****************************************/

add_action( 'admin_enqueue_scripts', 'zajax_scripts' );
function zajax_scripts() { 
	
	wp_enqueue_style( 'colorpick-css', plugins_url('admin/css/colpick.css', __FILE__) );
	wp_enqueue_script( 'colorpick-js', plugin_dir_url( __FILE__ ) . 'admin/js/colpick.min.js' );
	
}

function zajax_settings()
{
	// this is where we'll display our admin options
	if ($_POST['action'] == 'update')
	{		
		$message = '<div id="message" class="updated fade"><p><strong>Options Saved</strong></p></div>';
	}


	// zajax options
	if ($_POST['zajax']) {
		$zajax_options = serialize($_POST['zajax']);  
		update_option('zajax_options', $zajax_options);
		update_option('zajax_send', $_POST['zajax_send']);
		update_option('zajax_complete', $_POST['zajax_complete']);	
	}
	
	$zajax_options_get = unserialize( get_option('zajax_options') ); // Get main Content Class ID
	
	if($zajax_options_get){			
		$zajax_main = $zajax_options_get['zajax_main'];
		$zajax_main_mobile = $zajax_options_get['zajax_main_mobile'];
		$zajax_ClassID = $zajax_options_get['zajax_ClassID'];
		$zajax_search = $zajax_options_get['zajax_search'];
		$zajax_ignore = $zajax_options_get['zajax_ignore'];
		$zajax_dolist = $zajax_options_get['zajax_dolist'];
		$zajax_loading = $zajax_options_get['zajax_loading'];
		$zajax_masonry = $zajax_options_get['zajax_masonry'];
		$zajax_body = $zajax_options_get['zajax_body'];
		$zajax_back = $zajax_options_get['zajax_back'];
		$zajax_preload = $zajax_options_get['zajax_preload'];
		$zajax_send = stripslashes(get_option('zajax_send'));
		$zajax_complete = stripslashes(get_option('zajax_complete'));

		//checked( get_option('zajax_body'), 1, true );
	}else{
		$zajax_main = '#content';
		$zajax_search = '#searchform';
		$zajax_loading = '2299dd';
		$zajax_preload = 0;
		$zajax_back = 1;
		//$zajax_ClassID = '.menu';			
	}
	
	if(!$zajax_loading) $zajax_loading = '2299dd';
	
	// send complete jQuery codes
	$zajax_codes = "//This file is generated from the zajax admin panel - dont edit here! \n
var $ = jQuery; \n 
function zajax_send() { ".$zajax_send." };
function zajax_complete() { ".$zajax_complete." };";
	
	$file = fopen(plugin_dir_path(__FILE__) . 'js/send_complete.js', 'w');
	fwrite($file, $zajax_codes);
	fclose($file);
	
// images

//get_bloginfo('url');
$uniqid2 = uniqid();

$Preview_path = plugin_dir_url( __FILE__ ).'img/';

function zajax_activate() {

}
register_activation_hook( __FILE__, 'zajax_activate' );

	
$plugin_dir = plugins_url(); 
$plugin_url = plugins_url( '' , __FILE__ ).'/';

$plugin_data = get_plugin_data( __FILE__ );
$plugin_version = $plugin_data['Version'];
$plugin_name = $plugin_data['Name'];
?>

<div class="wrap">
<h2><span class="dashicons dashicons-update" style="line-height: inherit;"></span> <?php echo $plugin_name ?> Settings</h2><?php 
    echo $message ;
    
    if ($plugin_name != 'Zajax-Pro') { ?>
        <table class="wp-list-table widefat fixed bookmarks" style="margin-bottom: 20px;">
            <thead>
                <tr>
                    <th><strong>Get Zajax Pro</strong></th>
                </tr>
            </thead>
            <tbody>
            <tr>
                <td><a style="float: left;margin-right: 50px;" href="http://www.scriptsmashup.com/product/zajax-ajax-navigation-plugin-for-wordpress" target="_blank"><img src="http://www.scriptsmashup.com/wp-content/uploads/2015/12/square-banner-zajax-100px.png"></a>
                    <a href="http://www.scriptsmashup.com/product/zajax-ajax-navigation-plugin-for-wordpress" target="_blank"><h3 style="color: #167CFF;margin-top: 0;">Get Zajax Pro</h3></a>
                    <ol>
                    	<li>Preload page on mouse hover to load faster when user click on the link.</li>
                    	<li>Reload multiple sections outside the main section by ID or Class. (Menu, footer, sidebar, Ads, Google Ads). by just providing the ID/CLASS with #/. as prefix.</li>
                        <li>Work with Google Analytics</li>
                    </ol>
                </td>
             </tr>
          </tbody>
        </table><?php } ?>
    
<form method="post" action="">
<input type="hidden" name="action" value="update" />
 <table class="wp-list-table widefat fixed bookmarks">
            <thead>
                <tr>
                    <th><?php echo $plugin_name ?> (version: <?php echo $plugin_version ?> )
                    <?php add_thickbox(); // http://codex.wordpress.org/ThickBox ?>
                    <a href="<?php echo plugins_url( 'rd.html', __FILE__ ) ; ?>?TB_iframe=true&width=600&height=550" class="thickbox"><span class="dashicons dashicons-megaphone"></span> Help </a>
                    
                    
<div id="zajax_help" style="display:none;">

     <p>
          This is my hidden content! It will appear in ThickBox when the link is clicked.
     </p>
</div>
                    
                    </th>
                </tr>
            </thead>
            <tbody>
            <tr>
                <td>

            <table class="form-table">
            <tbody>
            <!-- main content Id or class -->
            <tr valign="top">
            <th scope="row">Main container ID or Class</th>
            <td>
            <span class="description"> Enter the main content you want to ajax load. Just one is allowed, usually the Wordpress main content is" <strong>#content</strong> Sometime it may be <strong>#container</strong> or <strong>#main</strong> or <strong>#primary</strong></span><br />
            <input type="text" name="zajax[zajax_main]" class="none" id="none" value="<?php echo $zajax_main ?>"></input>    
            </td>
            </tr>
            <!-- main content Id or class MOBILE -->
            <tr valign="top">
            <th scope="row">Main container ID or Class for Mobile</th>
            <td>
            <span class="description"> Enter the main content for <strong>mobile</strong> you want to ajax load. Just one is allowed, usually the Wordpress main content is" <strong>#content</strong> Sometime it may be <strong>#container</strong> or <strong>#main</strong> or <strong>#primary</strong> (Leave empty if it's the same as desktop main content)</span><br />
            <input type="text" name="zajax[zajax_main_mobile]" class="none" id="none" value="<?php echo $zajax_main_mobile ?>"></input>    
            </td>
            </tr>
 			<!-- Others content Id or class -->
            <th scope="row">other content ID or Class</th>
            <td>
            <span class="description wtf"> Enter one or many others elements to add who are external to the main content area that who want to reload EX: <strong>.menu,header,.widget-area</strong>. They should be outside the main container (you can mix with desktop and mobile version)</span><br class="wtf">
                <a href="http://www.scriptsmashup.com/product/zajax-ajax-navigation-plugin-for-wordpress" target="_blank"><strong class="wth" style="color: #167CFF;">Pro Version Only</strong></a>
                <input class="wtf" type="text" name="zajax[zajax_ClassID]" style="width:80%;" class="none" id="none" value="<?php echo $zajax_ClassID ?>"></input>
    
            </td>
            </tr>
 			<!-- Search ID Class -->
            <tr valign="top">
            <th scope="row">Search form ID or Class</th>
            <td>
            <span class="description"> Enter one or many search form id or and class EX: <strong>#searchform,.searchform</strong></span><br />
            <input type="text" name="zajax[zajax_search]" style="width:80%;" class="none" id="none" value="<?php echo $zajax_search ?>"></input>
            </td>
            </tr>

 			<!-- Javascript ignore list -->
            <tr valign="top">
            <th scope="row">Javascript ignore list</th>
            <td>
            <span class="description"> Enter list of javascript file(s) to ignore and not reload in the body separate by comma EX: <strong>filename1.js,filename2.js</strong></span><br />
            <input type="text" name="zajax[zajax_ignore]" style="width:80%;" class="none" id="none" value="<?php echo $zajax_ignore ?>"></input>
            </td>
            </tr>
            
 			<!-- Javascript do list js file in the header -->
            <tr valign="top">
            <th scope="row">Javascript reload list</th>
            <td>
            <span class="description"> Enter list of javascript file(s) to reload in the header separate by comma EX: <strong>mycustom.js,myslider.js (Tips: do not reload jquery plugins but reload the file(s) who call the functions to make these plugin work)</strong></span><br />
            <input type="text" name="zajax[zajax_dolist]" style="width:80%;" class="none" id="none" value="<?php echo $zajax_dolist ?>"></input>
            </td>
            </tr>

			<!-- Preload -->
            <tr valign="top">
            <th scope="row">Preload page on Mouse Hover</th>
            <td>
            <span class="description wtf">Page will preload when user Mouse Hover a link more than 100 miliseconds ( Uncheck if this function add too much burden on your server but page will load slower )</span>
                <span class="wtf"><br><br>Preload page on Mouse Hover: <input type="checkbox" name="zajax[zajax_preload]" value="1" <?php if ($zajax_preload == 1) { echo ' CHECKED="CHECKED" ';} ?> /></span>
                <a href="http://www.scriptsmashup.com/product/zajax-ajax-navigation-plugin-for-wordpress" target="_blank"><strong class="wth" style="color: #167CFF;">Pro Version Only</strong></a>
            </td>
            </tr>
            
 			<!-- Reload Masonry -->
            <tr valign="top">
            <th scope="row">Reload Masonry</th>
            <td>
            <span class="description"> If your theme use the <strong><a href="http://masonry.desandro.com/" target="_blank">Masonry</a></strong> plugin we need to reload it. Find out the masonry container ID or Class and add it here. EX: </strong>#masonry-grid</strong></span><br />
            <input type="text" name="zajax[zajax_masonry]" style="width:80%;" class="none" id="none" value="<?php echo $zajax_masonry ?>"></input>
            </td>
            </tr>

			<!-- Show back button -->
            <tr valign="top">
            <th scope="row">Show back button</th>
            <td>
            <span class="description">Show back button arrow. (Great for mobile navigation) fixed bottom left</span><br /><br />
                Show back button: <input type="checkbox" name="zajax[zajax_back]" value="1" <?php if ($zajax_back == 1) { echo ' CHECKED="CHECKED" ';} ?> />
            </td>
            </tr>

			<!-- load body -->
            <tr valign="top">
            <th scope="row">Load all body</th>
            <td>
            <span class="description">Ok, nothing worked, check this to reload all body, you can still leave the main content ID / Class there, users you'll be bluffed</span><br /><br />
                Load all body: <input type="checkbox" name="zajax[zajax_body]" value="1" <?php if ($zajax_body == 1) { echo ' CHECKED="CHECKED" ';} ?> />
            </td>
            </tr>

			<!-- zajax_send -->
            <tr valign="top">
            <th scope="row">Javascript/jQuery on ajax send</th>
            <td>
            <span class="description">Insert javascript or jQuery code here on ajax send. It trigger just before ajax page loading ( you can use the jQuery sign $ ) EX: $('#loading').show()</span><br /> 
            <textarea name="zajax_send" rows="10" style="width:100%"><?php echo $zajax_send ?></textarea>
            </td>
            </tr>

			<!-- zajax_complete -->
            <tr valign="top">
            <th scope="row">Javascript/jQuery on ajax complete</th>
            <td>
            <span class="description">Insert javascript or jQuery code here on ajax complete. It trigger at the end of ajax page loading ( you can use the jQuery sign $ )  EX: $('#loading').hide()</span><br />
            <textarea name="zajax_complete" rows="10" style="width:100%"><?php echo $zajax_complete ?></textarea>
            </td>
            </tr>

			<!-- Progress bar color -->
            <tr valign="top">
            <th scope="row">Set progress bar and loading color</th>
            <td>
                # <input type="text" name="zajax[zajax_loading]" class="zajax_picker" id="picker" value="<?php echo $zajax_loading ?>" style="border-color: #<?php echo $zajax_loading ?>;"></input>
            </td>
            </tr>

            <tr valign="top">
            <th scope="row">&nbsp;</th>
            <td>
                <input type="submit" class="button-primary" value="Save Changes">
            </td>
            </tr>
    
            </tbody>
            </table> 
          
     </tbody>
</table> 


</form>

 
</div><!--Wrap end -->
<!--End basic Table -->
<script type="text/javascript">

jQuery(document).ready(function($){

	setTimeout(function(){
		//jQuery('div#message').css('display','none');		
		jQuery('div#message').fadeOut("slow");
	}, 1000);


	jQuery('#picker').colpick({
		layout:'hex',
		submit:0,
		color:'<?php echo $zajax_loading ?>',
		colorScheme:'dark', //light
		onChange:function(hsb,hex,rgb,el,bySetColor) {
		jQuery(el).css('border-color','#'+hex);

		if(!bySetColor) jQuery(el).val(hex);
		}
	}).keyup(function(){
		jQuery(this).colpickSetColor(this.value);
	});
	

}); // Ready end

</script>
<style>
/* plugin admin */
.zajax_picker{
	width: 90px;
	border-right: 30px solid;
}

#picker {
	border-right: 30px solid;
}

#dynamic_input input, #dynamic_input2 input {
	margin-bottom: 8px;
}
#dynamic_input, #dynamic_input2 {
	margin-top: 8px;
}
#dynamic_input .dashicons-yes, #dynamic_input2 .dashicons-yes {
	font-size: 30px;
	margin-right: 5px;
	color: green;
}
#dynamic_input .dashicons-admin-tools, #dynamic_input2 .dashicons-admin-tools {
	color: #828382;
	margin-left: 5px;
	line-height: 30px;
}
/*
.wth{
    display: none;
}
*/
</style>
<?php } // End Setting function 

// Admin plugin setting
function zajax_admin_menu()
{
	// this is where we add our plugin to the admin menu
	add_options_page('Zajax options', 'Zajax', 9, basename(__FILE__), 'zajax_settings');
}

add_action('admin_menu', 'zajax_admin_menu');

add_action('plugin_action_links_' . plugin_basename(__FILE__), 'zajax_adminbar');
function zajax_adminbar($links){

	$new_links = array();

	$adminlink = get_bloginfo('wpurl').'/wp-admin/';

	$podz_link = 'http://zajax.com';

	$new_links[] = '<a href="'.$adminlink.'options-general.php?page=zajax.php">Settings</a>';

	return array_merge($links,$new_links );

}
?>