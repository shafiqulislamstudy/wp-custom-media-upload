# wp-custom-media-upload
custom media upload in custom wordpress plugin

HTML Part:

<?php wp_enqueue_media(); ?>
<div class="container">
	<div class="row justify-content-center">
		<div class="col-lg-8">
			<form class="mt-5">
        
				<div class="row mb-3">
					<label for="photo" class="col-sm-2 col-form-label">Photo</label>
					<div class="col-sm-10">
						<input type="button" value="Upload Image" id="btnUpload" class="btn btn-success">
						<span id="previewImg"></span>
						<input type="hidden" name="photo" id="getImg">
					</div>
				</div>
			
				<button type="submit" class="btn btn-primary">Submit</button>
			</form>
		</div>
	</div>
</div>


JS Part:

jQuery(document).ready(function(){

jQuery('#btnUpload').on("click",function(){
	var image = wp.media({
		title:'Custom image',
		multiple: false
	}).open().on('select',function(){
		var attachment = image.state().get('selection').first().toJSON().url;

		console.log(attachment);

		jQuery('#previewImg').html("<img src='"+attachment+"' style='height:100px;width:100px;'>");
		jQuery('#getImg').val(attachment)
	});
});

});
