FROM ruby:3.2

# Install essential build tools and dependencies
RUN apt-get update -qq && \
    apt-get install -y build-essential libpq-dev nodejs libyaml-dev

# Set working directory
WORKDIR /app

# Copy Gemfile and install gems
COPY Gemfile Gemfile.lock ./
RUN bundle install

# Copy the full app
COPY . .

# Precompile bootsnap (optional performance boost)
RUN bundle exec bootsnap precompile --gemfile

# Expose port
EXPOSE 3000

# Start the server
CMD ["rails", "server", "-b", "0.0.0.0"]

