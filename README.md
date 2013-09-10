Magento-Customer-Attributes
===========================

Add new magento customer attributes

added new attribute: customer_referral
```php
<?php
$customer_referral = array();
$attribute = Mage::getModel('eav/config')->getAttribute('customer', 'customer_referral');
foreach ( $attribute->getSource()->getAllOptions(true, true) as $option){
    $customer_referral[$option['value']] = $option['label'];
}
?>
```
app/design/frontend/base/default/template/customer/form/edit.phtml
```php
<li>
	<label for="customer_referral"><?php echo $this->__('Where did you hear about us?') ?></label><br/>
	<div class="input-box">
		<select name="customer_referral" id="customer_referral" title="<?php echo $this->__('Where did you hear about us?') ?>">
			<?php $selected = $this->htmlEscape($this->getCustomer()->getData('customer_referral')) ?>
			<?php foreach($customer_referral as $id => $label): ?>
			  <option value="<?php echo $id ?>"<?php if($id == $selected): ?> selected="selected"<?php endif; ?>><?php echo $this->htmlEscape($label) ?></option>
			<?php endforeach; ?>
		</select>
	</div>
</li>

```
