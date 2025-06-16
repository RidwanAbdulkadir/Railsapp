FROM ruby:3.2

# Set working directory
WORKDIR /app

# Install dependencies
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client yarn

# Install bundler
RUN gem install bundler

# Copy Gemfiles first (for layer caching)
COPY Gemfile* ./

# Install gems
RUN bundle install

# Copy the rest of the app, including Rakefile
COPY . .

# Expose port for the Rails server
EXPOSE 3000

# Start app using Rake task
CMD ["bundle", "exec", "rake", "start"]
