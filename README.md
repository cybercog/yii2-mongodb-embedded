Yii2 behaviors implement handling of mongodb embedded documents
===============================================================

* Add attribute with name starting with underscore to model.
* Add "safe" validation rule for attribute without underscore in name..
* Use attribute without underscore in name in forms or views
~~~
'address' => [
    'class' => EmbedsOneBehavior::className(),
    'attribute' => '_address',
    'embeddedClass' => Address::className()
],
'phones' => [
    'class' => EmbedsManyBehavior::className(),
    'attribute' => '_phones',
    'initEmptyScenarios' => ['create', 'update'],
    'embeddedClass' => Phone::className()
],
~~~
* Use attribute without underscore in form or view
~~~
echo $form->field($company->address, 'detail');
echo $form->field($company->address, 'id')->hiddenInput();

foreach($company->phones as $key => $phone) {
    echo $form->field($phone, 'number');
    echo $form->field($phone, 'type');
}
~~~