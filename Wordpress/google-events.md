# Dynamic Google Analytics Events with Contact Form 7

'event_category': '<?php echo $th_category_str; ?>',    --> Parent Category
'event_action': 'Form Submission',                      --> Form Submission
'event_label': '<?php echo $th_title_str; ?> Form'});   --> Page Title

<!--
TH - START || EVENTS FOR FORMS SUBMISSIONS
-->

<?php  

$th_title = get_the_title();
if($post->post_parent) {
	$th_category = get_the_title($post->post_parent);
} else {
	$th_category = get_the_title();
} 

// Replace encoded version of "&"
$th_symbol_to_replace = "&#038;";
$th_replace_with = "και";

$th_category_str = str_replace($th_symbol_to_replace, $th_replace_with, $th_category);
$th_title_str = str_replace($th_symbol_to_replace, $th_replace_with, $th_title);

?>

<script>

	document.addEventListener( 'wpcf7mailsent', function( event ) {
		gtag('event', 'send', {
			'event_category': '<?php echo $th_category_str; ?>',
			'event_action': 'Form Submission',
			'event_label': '<?php echo $th_title_str; ?> Form'});
			
		console.log(event.detail)	
		}, false );

</script>

<!--
TH - END || EVENTS FOR FORMS SUBMISSIONS
-->
