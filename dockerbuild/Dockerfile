FROM wordpress
MAINTAINER koyhoge <t.koyama@rakumo.com>

COPY --from=composer:1.5 /usr/bin/composer /usr/bin/composer

ENV WORDPRESS_PLUGIN_DIR /usr/src/wordpress/wp-content/plugins
ENV PLUGIN_BASE appengine-wordpress-plugin

RUN mkdir $WORDPRESS_PLUGIN_DIR/appengine-plugin
COPY $PLUGIN_BASE/appengine-plugin $WORDPRESS_PLUGIN_DIR/appengine-plugin/

RUN mkdir $WORDPRESS_PLUGIN_DIR/gcs-media-plugin
COPY $PLUGIN_BASE/gcs-media-plugin $WORDPRESS_PLUGIN_DIR/gcs-media-plugin

RUN cd $WORDPRESS_PLUGIN_DIR/gcs-media-plugin && \
	composer install --no-plugins --no-scripts

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["apache2-foreground"]
