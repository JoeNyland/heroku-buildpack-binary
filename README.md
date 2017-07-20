# heroku-buildpack-binary

Deploy binary packages to Heroku!

## Usage

* Add the buildpack
  * To use this buildpack at app creation:
    ```
    heroku apps:create --buildpack https://github.com/JoeNyland/heroku-buildpack-binary.git
    ```
  * To add this buildpack to an existing app: 
    ```
    heroku buildpacks:add https://github.com/JoeNyland/heroku-buildpack-binary.git
    ```
* Copy your binaries to `bin/` inside your app repo. If your binaries aren't placed in `/bin`, this buildpack will
fail to detect that this is a binary app.
* Create a `Procfile`
  ```
  cat >> Procfile <<EOF
  ## Web server
  ## Note: You must bind the web server to \$PORT which is provided by Heroku!
  # web: bin/binary-name --add --additional --parameters -vv --port $PORT

  ## Normal worker
  # worker: bin/binary-name --add --additional --parameters -vv
  EOF
  ```
* Deploy!
  ```
  git add bin/ Procfile
  git commit -m 'Import binaries and add Heroku Profile'
  git push heroku HEAD
  ```

## Issues
Please report any issues on the GitHub Issues page [here](https://github.com/JoeNyland/heroku-buildpack-binary/issues).

## Contributing
Bug reports and pull requests are welcome on GitHub at https://github.com/JoeNyland/heroku-buildpack-binary. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

