require "roda"

class App < Roda
  plugin :render
  plugin :public
  plugin :assets, css: 'bulma.min.css'

  route do |r|
    r.assets
    r.public
    r.root do
      render('home')
    end
    r.get 'acceis' do
      @base_url = 'https://www.acceis.fr/'
      if r.params['redirect_url'].nil?
        r.redirect '/'
      elsif /\A#{Regexp.escape(@base_url)}/.\Z/.match?(r.params['redirect_url'])
        r.redirect r.params['redirect_url']
      elsif /\A#{@base_url}/.\Z/.match?(r.params['redirect_url'])
        response.write ENV['FLAG_1']
        r.redirect r.params['redirect_url']
      elsif /^#{Regexp.escape(@base_url)}/.$/.match?(r.params['redirect_url'])
        response.write ENV['FLAG_2']
        r.redirect r.params['redirect_url']
      elsif /\A#{Regexp.escape(@base_url)}/.\Z/i.match?(r.params['redirect_url'])
        response.write ENV['FLAG_3']
        r.redirect r.params['redirect_url']
      else
        r.redirect 'https://www.acceis.fr/rejoignez-nous/'
      end
    end
  end
end
