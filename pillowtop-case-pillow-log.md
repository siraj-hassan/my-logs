
2023-11-21 18:26:07,303 ERROR [notify] Notify Exception: case-pillow Error in processing changes chunk: cc404ae1-366e-4d4f-9006-51a3a255b188
Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 175, in maybe_not_found
    yield
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/factory.py", line 580, in do_action
    response = action(self, *args, **kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/action.py", line 88, in __call__
    response = getattr(parent.meta.client, operation_name)(*args, **params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 514, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 938, in _make_api_call
    raise error_class(parsed_response, operation_name)
botocore.errorfactory.NoSuchKey: An error occurred (NoSuchKey) when calling the GetObject operation: The specified key does not exist.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 696, in get_xml
    return self.get_attachment('form.xml')
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/attachment.py", line 259, in get_attachment
    with attachment.open() as content:
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/models.py", line 107, in open
    return db.get(meta=self)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/dimagi/utils/retry.py", line 31, in retry
    return func(*args, **kw)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/usr/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 181, in maybe_not_found
    raise throw
corehq.blobs.exceptions.NotFound: 7996095027ca4224a843b94df20c4036

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 221, in _batch_process_with_error_handling
    retry_changes, change_exceptions = processor.process_changes_chunk(changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 433, in process_changes_chunk
    failed, exceptions = self._process_chunk_for_domain(domain, changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 458, in _process_chunk_for_domain
    if adapter.config.filter(doc, eval_context):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/models.py", line 378, in filter
    return filter_fn(document, eval_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in __call__
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in <genexpr>
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 94, in __call__
    self.expression(item, evaluation_context), self.reference_expression(item, evaluation_context))
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 658, in __call__
    argument = self._argument_expression(item, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 195, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 285, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 69, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 853, in __call__
    return self._get_forms(case_id, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in _get_forms
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in <listcomp>
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 881, in _get_form_json
    form_json = form.to_json()
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 666, in to_json
    data = dict(serializer.data)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 555, in data
    ret = super().data
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 253, in data
    self._data = self.to_representation(self.instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 509, in to_representation
    attribute = field.get_attribute(instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 457, in get_attribute
    return get_attribute(instance, self.source_attrs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 97, in get_attribute
    instance = getattr(instance, attr)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 614, in form_data
    xml = self.get_xml()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 698, in get_xml
    raise MissingFormXml(self.form_id)
corehq.form_processor.exceptions.MissingFormXml: cc404ae1-366e-4d4f-9006-51a3a255b188
2023-11-21 18:26:08,194 ERROR interface [case-pillow] Error on change: e178729d-7424-42e9-b9ec-1d68a19fba5c, cc404ae1-366e-4d4f-9006-51a3a255b188
Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 175, in maybe_not_found
    yield
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/factory.py", line 580, in do_action
    response = action(self, *args, **kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/action.py", line 88, in __call__
    response = getattr(parent.meta.client, operation_name)(*args, **params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 514, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 938, in _make_api_call
    raise error_class(parsed_response, operation_name)
botocore.errorfactory.NoSuchKey: An error occurred (NoSuchKey) when calling the GetObject operation: The specified key does not exist.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 696, in get_xml
    return self.get_attachment('form.xml')
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/attachment.py", line 259, in get_attachment
    with attachment.open() as content:
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/models.py", line 107, in open
    return db.get(meta=self)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/dimagi/utils/retry.py", line 31, in retry
    return func(*args, **kw)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/usr/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 181, in maybe_not_found
    raise throw
corehq.blobs.exceptions.NotFound: 7996095027ca4224a843b94df20c4036

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 221, in _batch_process_with_error_handling
    retry_changes, change_exceptions = processor.process_changes_chunk(changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 433, in process_changes_chunk
    failed, exceptions = self._process_chunk_for_domain(domain, changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 458, in _process_chunk_for_domain
    if adapter.config.filter(doc, eval_context):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/models.py", line 378, in filter
    return filter_fn(document, eval_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in __call__
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in <genexpr>
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 94, in __call__
    self.expression(item, evaluation_context), self.reference_expression(item, evaluation_context))
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 658, in __call__
    argument = self._argument_expression(item, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 195, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 285, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 69, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 853, in __call__
    return self._get_forms(case_id, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in _get_forms
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in <listcomp>
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 881, in _get_form_json
    form_json = form.to_json()
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 666, in to_json
    data = dict(serializer.data)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 555, in data
    ret = super().data
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 253, in data
    self._data = self.to_representation(self.instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 509, in to_representation
    attribute = field.get_attribute(instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 457, in get_attribute
    return get_attribute(instance, self.source_attrs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 97, in get_attribute
    instance = getattr(instance, attr)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 614, in form_data
    xml = self.get_xml()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 698, in get_xml
    raise MissingFormXml(self.form_id)
corehq.form_processor.exceptions.MissingFormXml: cc404ae1-366e-4d4f-9006-51a3a255b188

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 175, in maybe_not_found
    yield
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/factory.py", line 580, in do_action
    response = action(self, *args, **kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/action.py", line 88, in __call__
    response = getattr(parent.meta.client, operation_name)(*args, **params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 514, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 938, in _make_api_call
    raise error_class(parsed_response, operation_name)
botocore.errorfactory.NoSuchKey: An error occurred (NoSuchKey) when calling the GetObject operation: The specified key does not exist.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 696, in get_xml
    return self.get_attachment('form.xml')
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/attachment.py", line 259, in get_attachment
    with attachment.open() as content:
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/models.py", line 107, in open
    return db.get(meta=self)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/dimagi/utils/retry.py", line 31, in retry
    return func(*args, **kw)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/usr/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 181, in maybe_not_found
    raise throw
corehq.blobs.exceptions.NotFound: 7996095027ca4224a843b94df20c4036

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 254, in process_with_error_handling
    processor.process_change(change)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 556, in process_change
    if table.config.filter(doc, eval_context):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/models.py", line 378, in filter
    return filter_fn(document, eval_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in __call__
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in <genexpr>
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 94, in __call__
    self.expression(item, evaluation_context), self.reference_expression(item, evaluation_context))
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 658, in __call__
    argument = self._argument_expression(item, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 195, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 285, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 69, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 853, in __call__
    return self._get_forms(case_id, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in _get_forms
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in <listcomp>
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 881, in _get_form_json
    form_json = form.to_json()
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 666, in to_json
    data = dict(serializer.data)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 555, in data
    ret = super().data
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 253, in data
    self._data = self.to_representation(self.instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 509, in to_representation
    attribute = field.get_attribute(instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 457, in get_attribute
    return get_attribute(instance, self.source_attrs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 97, in get_attribute
    instance = getattr(instance, attr)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 614, in form_data
    xml = self.get_xml()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 698, in get_xml
    raise MissingFormXml(self.form_id)
corehq.form_processor.exceptions.MissingFormXml: cc404ae1-366e-4d4f-9006-51a3a255b188
2023-11-21 18:26:08,195 ERROR [notify] Notify Exception: Unexpected error in pillow
Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 175, in maybe_not_found
    yield
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/factory.py", line 580, in do_action
    response = action(self, *args, **kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/action.py", line 88, in __call__
    response = getattr(parent.meta.client, operation_name)(*args, **params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 514, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 938, in _make_api_call
    raise error_class(parsed_response, operation_name)
botocore.errorfactory.NoSuchKey: An error occurred (NoSuchKey) when calling the GetObject operation: The specified key does not exist.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 696, in get_xml
    return self.get_attachment('form.xml')
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/attachment.py", line 259, in get_attachment
    with attachment.open() as content:
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/models.py", line 107, in open
    return db.get(meta=self)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/dimagi/utils/retry.py", line 31, in retry
    return func(*args, **kw)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/usr/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 181, in maybe_not_found
    raise throw
corehq.blobs.exceptions.NotFound: 7996095027ca4224a843b94df20c4036

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 221, in _batch_process_with_error_handling
    retry_changes, change_exceptions = processor.process_changes_chunk(changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 433, in process_changes_chunk
    failed, exceptions = self._process_chunk_for_domain(domain, changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 458, in _process_chunk_for_domain
    if adapter.config.filter(doc, eval_context):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/models.py", line 378, in filter
    return filter_fn(document, eval_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in __call__
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in <genexpr>
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 94, in __call__
    self.expression(item, evaluation_context), self.reference_expression(item, evaluation_context))
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 658, in __call__
    argument = self._argument_expression(item, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 195, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 285, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 69, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 853, in __call__
    return self._get_forms(case_id, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in _get_forms
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in <listcomp>
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 881, in _get_form_json
    form_json = form.to_json()
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 666, in to_json
    data = dict(serializer.data)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 555, in data
    ret = super().data
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 253, in data
    self._data = self.to_representation(self.instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 509, in to_representation
    attribute = field.get_attribute(instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 457, in get_attribute
    return get_attribute(instance, self.source_attrs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 97, in get_attribute
    instance = getattr(instance, attr)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 614, in form_data
    xml = self.get_xml()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 698, in get_xml
    raise MissingFormXml(self.form_id)
corehq.form_processor.exceptions.MissingFormXml: cc404ae1-366e-4d4f-9006-51a3a255b188

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 175, in maybe_not_found
    yield
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/factory.py", line 580, in do_action
    response = action(self, *args, **kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/action.py", line 88, in __call__
    response = getattr(parent.meta.client, operation_name)(*args, **params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 514, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 938, in _make_api_call
    raise error_class(parsed_response, operation_name)
botocore.errorfactory.NoSuchKey: An error occurred (NoSuchKey) when calling the GetObject operation: The specified key does not exist.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 696, in get_xml
    return self.get_attachment('form.xml')
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/attachment.py", line 259, in get_attachment
    with attachment.open() as content:
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/models.py", line 107, in open
    return db.get(meta=self)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/dimagi/utils/retry.py", line 31, in retry
    return func(*args, **kw)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/usr/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 181, in maybe_not_found
    raise throw
corehq.blobs.exceptions.NotFound: 7996095027ca4224a843b94df20c4036

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 254, in process_with_error_handling
    processor.process_change(change)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 556, in process_change
    if table.config.filter(doc, eval_context):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/models.py", line 378, in filter
    return filter_fn(document, eval_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in __call__
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in <genexpr>
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 94, in __call__
    self.expression(item, evaluation_context), self.reference_expression(item, evaluation_context))
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 658, in __call__
    argument = self._argument_expression(item, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 195, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 285, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 69, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 853, in __call__
    return self._get_forms(case_id, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in _get_forms
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in <listcomp>
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 881, in _get_form_json
    form_json = form.to_json()
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 666, in to_json
    data = dict(serializer.data)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 555, in data
    ret = super().data
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 253, in data
    self._data = self.to_representation(self.instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 509, in to_representation
    attribute = field.get_attribute(instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 457, in get_attribute
    return get_attribute(instance, self.source_attrs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 97, in get_attribute
    instance = getattr(instance, attr)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 614, in form_data
    xml = self.get_xml()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 698, in get_xml
    raise MissingFormXml(self.form_id)
corehq.form_processor.exceptions.MissingFormXml: cc404ae1-366e-4d4f-9006-51a3a255b188
2023-11-21 18:26:08,366 ERROR [notify] Notify Exception: processor error in pillow case-pillow invalid page in block 24080225 of relation base/16400/20068
Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 175, in maybe_not_found
    yield
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/factory.py", line 580, in do_action
    response = action(self, *args, **kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/action.py", line 88, in __call__
    response = getattr(parent.meta.client, operation_name)(*args, **params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 514, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 938, in _make_api_call
    raise error_class(parsed_response, operation_name)
botocore.errorfactory.NoSuchKey: An error occurred (NoSuchKey) when calling the GetObject operation: The specified key does not exist.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 696, in get_xml
    return self.get_attachment('form.xml')
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/attachment.py", line 259, in get_attachment
    with attachment.open() as content:
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/models.py", line 107, in open
    return db.get(meta=self)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/dimagi/utils/retry.py", line 31, in retry
    return func(*args, **kw)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/usr/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 181, in maybe_not_found
    raise throw
corehq.blobs.exceptions.NotFound: 7996095027ca4224a843b94df20c4036

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 221, in _batch_process_with_error_handling
    retry_changes, change_exceptions = processor.process_changes_chunk(changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 433, in process_changes_chunk
    failed, exceptions = self._process_chunk_for_domain(domain, changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 458, in _process_chunk_for_domain
    if adapter.config.filter(doc, eval_context):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/models.py", line 378, in filter
    return filter_fn(document, eval_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in __call__
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in <genexpr>
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 94, in __call__
    self.expression(item, evaluation_context), self.reference_expression(item, evaluation_context))
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 658, in __call__
    argument = self._argument_expression(item, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 195, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 285, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 69, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 853, in __call__
    return self._get_forms(case_id, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in _get_forms
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in <listcomp>
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 881, in _get_form_json
    form_json = form.to_json()
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 666, in to_json
    data = dict(serializer.data)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 555, in data
    ret = super().data
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 253, in data
    self._data = self.to_representation(self.instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 509, in to_representation
    attribute = field.get_attribute(instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 457, in get_attribute
    return get_attribute(instance, self.source_attrs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 97, in get_attribute
    instance = getattr(instance, attr)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 614, in form_data
    xml = self.get_xml()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 698, in get_xml
    raise MissingFormXml(self.form_id)
corehq.form_processor.exceptions.MissingFormXml: cc404ae1-366e-4d4f-9006-51a3a255b188

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 175, in maybe_not_found
    yield
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/factory.py", line 580, in do_action
    response = action(self, *args, **kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/action.py", line 88, in __call__
    response = getattr(parent.meta.client, operation_name)(*args, **params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 514, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 938, in _make_api_call
    raise error_class(parsed_response, operation_name)
botocore.errorfactory.NoSuchKey: An error occurred (NoSuchKey) when calling the GetObject operation: The specified key does not exist.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 696, in get_xml
    return self.get_attachment('form.xml')
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/attachment.py", line 259, in get_attachment
    with attachment.open() as content:
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/models.py", line 107, in open
    return db.get(meta=self)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/dimagi/utils/retry.py", line 31, in retry
    return func(*args, **kw)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/usr/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 181, in maybe_not_found
    raise throw
corehq.blobs.exceptions.NotFound: 7996095027ca4224a843b94df20c4036

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 254, in process_with_error_handling
    processor.process_change(change)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 556, in process_change
    if table.config.filter(doc, eval_context):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/models.py", line 378, in filter
    return filter_fn(document, eval_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in __call__
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in <genexpr>
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 94, in __call__
    self.expression(item, evaluation_context), self.reference_expression(item, evaluation_context))
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 658, in __call__
    argument = self._argument_expression(item, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 195, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 285, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 69, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 853, in __call__
    return self._get_forms(case_id, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in _get_forms
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in <listcomp>
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 881, in _get_form_json
    form_json = form.to_json()
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 666, in to_json
    data = dict(serializer.data)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 555, in data
    ret = super().data
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 253, in data
    self._data = self.to_representation(self.instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 509, in to_representation
    attribute = field.get_attribute(instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 457, in get_attribute
    return get_attribute(instance, self.source_attrs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 97, in get_attribute
    instance = getattr(instance, attr)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 614, in form_data
    xml = self.get_xml()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 698, in get_xml
    raise MissingFormXml(self.form_id)
corehq.form_processor.exceptions.MissingFormXml: cc404ae1-366e-4d4f-9006-51a3a255b188

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 84, in _execute
    return self.cursor.execute(sql, params)
psycopg2.errors.DataCorrupted: invalid page in block 24080225 of relation base/16400/20068


The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 261, in process_with_error_handling
    handle_pillow_error(self, change, ex)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 511, in handle_pillow_error
    error.save()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/base.py", line 739, in save
    self.save_base(using=using, force_insert=force_insert,
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/base.py", line 776, in save_base
    updated = self._save_table(
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/base.py", line 858, in _save_table
    updated = self._do_update(base_qs, using, pk_val, values, update_fields,
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/base.py", line 912, in _do_update
    return filtered._update(values) > 0
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/query.py", line 802, in _update
    return query.get_compiler(self.db).execute_sql(CURSOR)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/sql/compiler.py", line 1559, in execute_sql
    cursor = super().execute_sql(result_type)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/sql/compiler.py", line 1175, in execute_sql
    cursor.execute(sql, params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/sentry_sdk/integrations/django/__init__.py", line 582, in execute
    return real_execute(self, sql, params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 66, in execute
    return self._execute_with_wrappers(sql, params, many=False, executor=self._execute)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 75, in _execute_with_wrappers
    return executor(sql, params, many, context)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 84, in _execute
    return self.cursor.execute(sql, params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/utils.py", line 90, in __exit__
    raise dj_exc_value.with_traceback(traceback) from exc_value
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 84, in _execute
    return self.cursor.execute(sql, params)
django.db.utils.InternalError: invalid page in block 24080225 of relation base/16400/20068

Starting pillow <class 'pillowtop.pillow.interface.ConstructedPillow'>.run()
Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 175, in maybe_not_found
    yield
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/factory.py", line 580, in do_action
    response = action(self, *args, **kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/action.py", line 88, in __call__
    response = getattr(parent.meta.client, operation_name)(*args, **params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 514, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 938, in _make_api_call
    raise error_class(parsed_response, operation_name)
botocore.errorfactory.NoSuchKey: An error occurred (NoSuchKey) when calling the GetObject operation: The specified key does not exist.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 696, in get_xml
    return self.get_attachment('form.xml')
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/attachment.py", line 259, in get_attachment
    with attachment.open() as content:
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/models.py", line 107, in open
    return db.get(meta=self)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/dimagi/utils/retry.py", line 31, in retry
    return func(*args, **kw)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/usr/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 181, in maybe_not_found
    raise throw
corehq.blobs.exceptions.NotFound: 7996095027ca4224a843b94df20c4036

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 221, in _batch_process_with_error_handling
    retry_changes, change_exceptions = processor.process_changes_chunk(changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 433, in process_changes_chunk
    failed, exceptions = self._process_chunk_for_domain(domain, changes_chunk)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 458, in _process_chunk_for_domain
    if adapter.config.filter(doc, eval_context):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/models.py", line 378, in filter
    return filter_fn(document, eval_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in __call__
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in <genexpr>
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 94, in __call__
    self.expression(item, evaluation_context), self.reference_expression(item, evaluation_context))
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 658, in __call__
    argument = self._argument_expression(item, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 195, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 285, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 69, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 853, in __call__
    return self._get_forms(case_id, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in _get_forms
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in <listcomp>
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 881, in _get_form_json
    form_json = form.to_json()
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 666, in to_json
    data = dict(serializer.data)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 555, in data
    ret = super().data
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 253, in data
    self._data = self.to_representation(self.instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 509, in to_representation
    attribute = field.get_attribute(instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 457, in get_attribute
    return get_attribute(instance, self.source_attrs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 97, in get_attribute
    instance = getattr(instance, attr)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 614, in form_data
    xml = self.get_xml()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 698, in get_xml
    raise MissingFormXml(self.form_id)
corehq.form_processor.exceptions.MissingFormXml: cc404ae1-366e-4d4f-9006-51a3a255b188

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 175, in maybe_not_found
    yield
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/factory.py", line 580, in do_action
    response = action(self, *args, **kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/boto3/resources/action.py", line 88, in __call__
    response = getattr(parent.meta.client, operation_name)(*args, **params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 514, in _api_call
    return self._make_api_call(operation_name, kwargs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/botocore/client.py", line 938, in _make_api_call
    raise error_class(parsed_response, operation_name)
botocore.errorfactory.NoSuchKey: An error occurred (NoSuchKey) when calling the GetObject operation: The specified key does not exist.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 696, in get_xml
    return self.get_attachment('form.xml')
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/attachment.py", line 259, in get_attachment
    with attachment.open() as content:
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/models.py", line 107, in open
    return db.get(meta=self)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/dimagi/utils/retry.py", line 31, in retry
    return func(*args, **kw)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 99, in get
    resp = self._s3_bucket().Object(key).get()
  File "/usr/lib/python3.9/contextlib.py", line 137, in __exit__
    self.gen.throw(typ, value, traceback)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/blobs/s3db.py", line 181, in maybe_not_found
    raise throw
corehq.blobs.exceptions.NotFound: 7996095027ca4224a843b94df20c4036

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 254, in process_with_error_handling
    processor.process_change(change)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/pillow.py", line 556, in process_change
    if table.config.filter(doc, eval_context):
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/models.py", line 378, in filter
    return filter_fn(document, eval_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in __call__
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 61, in <genexpr>
    return any(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in __call__
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 44, in <genexpr>
    return all(_filter(item, evaluation_context) for _filter in self.filters)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/filters/__init__.py", line 94, in __call__
    self.expression(item, evaluation_context), self.reference_expression(item, evaluation_context))
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 658, in __call__
    argument = self._argument_expression(item, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 195, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 285, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 69, in __call__
    items = _evaluate_items_expression(self._items_expression, doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/list_specs.py", line 18, in _evaluate_items_expression
    result = itemx_ex(doc, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 853, in __call__
    return self._get_forms(case_id, evaluation_context)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in _get_forms
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 866, in <listcomp>
    xforms = [self._get_form_json(f, evaluation_context) for f in xforms if f.domain == domain]
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/apps/userreports/expressions/specs.py", line 881, in _get_form_json
    form_json = form.to_json()
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 666, in to_json
    data = dict(serializer.data)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 555, in data
    ret = super().data
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 253, in data
    self._data = self.to_representation(self.instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/serializers.py", line 509, in to_representation
    attribute = field.get_attribute(instance)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 457, in get_attribute
    return get_attribute(instance, self.source_attrs)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/rest_framework/fields.py", line 97, in get_attribute
    instance = getattr(instance, attr)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 614, in form_data
    xml = self.get_xml()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/memoized.py", line 20, in _memoized
    cache[key] = value = fn(*args, **kwargs)
  File "/home/cchq/www/echis/releases/2023-11-21_11.15/corehq/form_processor/models/forms.py", line 698, in get_xml
    raise MissingFormXml(self.form_id)
corehq.form_processor.exceptions.MissingFormXml: cc404ae1-366e-4d4f-9006-51a3a255b188

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 84, in _execute
    return self.cursor.execute(sql, params)
psycopg2.errors.DataCorrupted: invalid page in block 24080225 of relation base/16400/20068


The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/home/cchq/www/echis/current/manage.py", line 190, in <module>
    main()
  File "/home/cchq/www/echis/current/manage.py", line 48, in main
    execute_from_command_line(sys.argv)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/core/management/__init__.py", line 419, in execute_from_command_line
    utility.execute()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/core/management/__init__.py", line 413, in execute
    self.fetch_command(subcommand).run_from_argv(self.argv)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/core/management/base.py", line 354, in run_from_argv
    self.execute(*args, **cmd_options)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/core/management/base.py", line 398, in execute
    output = self.handle(*args, **options)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/management/commands/run_ptop.py", line 137, in handle
    start_pillow(pillow)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/run_pillowtop.py", line 39, in start_pillow
    pillow_instance.run()
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 116, in run
    self.process_changes(since=self.get_last_checkpoint_sequence(), forever=True)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 175, in process_changes
    self._batch_process_with_error_handling(changes_chunk)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 234, in _batch_process_with_error_handling
    reprocess_serially(changes_chunk, processor)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 211, in reprocess_serially
    self.process_with_error_handling(change, processor)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 261, in process_with_error_handling
    handle_pillow_error(self, change, ex)
  File "/home/cchq/www/echis/current/corehq/ex-submodules/pillowtop/pillow/interface.py", line 511, in handle_pillow_error
    error.save()
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/base.py", line 739, in save
    self.save_base(using=using, force_insert=force_insert,
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/base.py", line 776, in save_base
    updated = self._save_table(
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/base.py", line 858, in _save_table
    updated = self._do_update(base_qs, using, pk_val, values, update_fields,
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/base.py", line 912, in _do_update
    return filtered._update(values) > 0
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/query.py", line 802, in _update
    return query.get_compiler(self.db).execute_sql(CURSOR)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/sql/compiler.py", line 1559, in execute_sql
    cursor = super().execute_sql(result_type)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/models/sql/compiler.py", line 1175, in execute_sql
    cursor.execute(sql, params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/sentry_sdk/integrations/django/__init__.py", line 582, in execute
    return real_execute(self, sql, params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 66, in execute
    return self._execute_with_wrappers(sql, params, many=False, executor=self._execute)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 75, in _execute_with_wrappers
    return executor(sql, params, many, context)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 84, in _execute
    return self.cursor.execute(sql, params)
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/utils.py", line 90, in __exit__
    raise dj_exc_value.with_traceback(traceback) from exc_value
  File "/home/cchq/www/echis/current/python_env/lib/python3.9/site-packages/django/db/backends/utils.py", line 84, in _execute
    return self.cursor.execute(sql, params)
django.db.utils.InternalError: invalid page in block 24080225 of relation base/16400/20068
