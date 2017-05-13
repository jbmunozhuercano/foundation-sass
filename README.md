# Foundation-sass

## Light version of the Zurb Foundation framework

### Foundation version 6.3.1

You can use the compiler you want, Koala, Scout, Grunt, whatever...

Add your own styles to the app.scss file in the scss folder.

### Example of Gruntfile:

After installing with npm locally in the folder of the project grunt-contrib-sass and grunt-contrib-watch, use the next Gruntfile:

''' javascript
module.exports = function(grunt) {

    grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),        
        /*
        * Sass
        */
        sass: {
            dev: {
                options: {
                    style: 'expanded',
                    sourcemap: 'none', /* inline */
                },
                files: {
                    'css/app-human.css': 'scss/app.scss'
                }
            },
	dist: {
                options: {
                    style: 'compressed',
                    sourcemap: 'none'
                },
                files: {
                    'css/app.css': 'sass/app.scss'
                }
            }
        },
        /*
        * Watch
        */
        watch: {
            css: {
                files: '**/*.scss',
                tasks: 'sass'                
            }
        }
        
    });
    grunt.loadNpmTasks('grunt-contrib-sass');
    grunt.loadNpmTasks('grunt-contrib-watch');
    grunt.registerTask('default', ['watch']);
}
''' 
