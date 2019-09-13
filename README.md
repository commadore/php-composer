# PHP  Composer
PHP composer docker container that allows ssh on windows
Uses hirak/prestissimo under the hood for that parallel goodness

## Windows File permissions

As discussed [Volume Mounting SSH Keys into a Docker Container](https://nickjanetakis.com/blog/docker-tip-56-volume-mounting-ssh-keys-into-a-docker-container)

Windows disgregards the file permissions so you can't just map your ssh folder as a volume an expect it to work.

## Usage
(With ConEmu bash you need the / before $(pwd))

`docker run --rm -v /$(pwd):/app -v C:/Users/your_user/.ssh:/tmp/.ssh commadore/composer`

I'd also recommend making a volume for cache too

`docker run --rm --volume C:/composer_cache:/root/composer/ -v /$(pwd):/app -v C:/Users/your_user/.ssh:/tmp/.ssh commadore/composer`

I also alias mine in my .bashrc

`alias composer='docker run --rm --volume C:/composer_cache:/root/composer/ -v /$(pwd):/app -v C:/Users/your_user/.ssh:/tmp/.ssh commadore/composer '`

Then I can just use

`composer update`

YMMV
