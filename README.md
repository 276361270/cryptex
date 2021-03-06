Cryptex
=======

An [Elixir][] library for encrypting/decrypting, signing/verifying data.

[Elixir]: http://elixir-lang.org

## Usage

```elixir
secret_key_base = "072d1e0157c008193fe48a670cce031faa4e..."
encrypted_cookie_salt = "encrypted cookie"
encrypted_signed_cookie_salt = "signed encrypted cookie"

secret = KeyGenerator.generate(secret_key_base, encrypted_cookie_salt)
sign_secret = KeyGenerator.generate(secret_key_base, encrypted_signed_cookie_salt)
encryptor = MessageEncryptor.new(secret, sign_secret)

data = %{current_user: %{name: "José"}}
encrypted = MessageEncryptor.encrypt_and_sign(encryptor, data)
decrypted = MessageEncryptor.decrypt_and_verify(encryptor, encrypted)
decrypted.current_user.name # => "José"
```

## License

The MIT License (MIT)

Copyright (c) 2014 Sonny Scroggin

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
