FROM ruby:3.2

# Set working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update -qq && apt-get install -y \
  nodejs \
  postgresql-client \
  yarn \
  build-essential \
  libpq-dev \
  curl

# Install bundler
RUN gem install bundler

# Copy Gemfile and Gemfile.lock for better caching
COPY Gemfile* ./

# Install gems
RUN bundle install

# Copy the rest of the app
COPY . .

# Set environment variables (optional defaults)
ENV RAILS_ENV=development
ENV RACK_ENV=development

# Precompile assets if needed (only for production apps)
# RUN bundle exec rake assets:precompile

# Expose the Rails port
EXPOSE 3000

# Default command to run Rails server
CMD ["bundle", "exec", "rails", "server", "-b", "0.0.0.0"]
