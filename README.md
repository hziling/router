Router  
=====

A simple router for WSGI application.

Example:
------------
Firstly, register a URL with a function and methods.

    def hello(name):
        return 'Hello {0}!'.format(name)

    router = Router()
    router.register('/hello/<name>', hello, ['GET'])


The URL also can be a pattern like:

`"/author/<username>"` which will match `"/author/Jone"` or `"/author/Bob"`,

`"/post/<int:id>"` which will match `"/post/1"` or `"/post/20"`.

Then we can get the function with the registered path:

    print router.get('/hello/world')
    Out: (<function hello at 0x0000000007BE9128>, {'name': 'world'})

or get the path with the registered function:

    print router.url_for(hello, name='world')
    Out: /hello/world

Tests:
--------
    ..............
    ----------------------------------------------------------------------
    Ran 14 tests in 0.002s

    OK