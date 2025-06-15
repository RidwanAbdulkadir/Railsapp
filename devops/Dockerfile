FROM ruby:3.2

# Set working directory
WORKDIR /app

# Install dependencies
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client yarn

# Install bundler
RUN gem install bundler

# Copy app files
COPY . .

# Install gems
RUN bundle install

# Precompile assets (optional, if using frontend)
# RUN bundle exec rake assets:precompile

EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]

