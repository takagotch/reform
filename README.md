### reform
---

https://github.com/trailblazer/reform


```
= form_for @form do |f|
  = f.input :title
  
= text_field :title @form.title
= text_field "artist[name]", @form.artist.name

= form_for @from do |f|
  = f.text_field :title
  = f.fields_for :artist do |a|
    = a.text_field :name
    
```

```ruby
class AlbumForm < Reform::Form
  property :title
  validates :title, presence: true
end

class AlbumsController
  def new
    @form = AlbumForm.new(Album.new)
  end
end

def edit
  @form = AlbumForm.new(Album.find(1))
end

class SongsController
  def create
    @form = SongFrom.new(Song.new)
    if @form.validate(params[:song])
    end
  end
end

if @form.validate(params[:song])
  @form.save
else
  #
end

class AlbumFrom < Reform::Form
  property :price_in_cents, default: 9_95
end

@form.save do |hash|
  hash
  Album.create(hash)
end

@form.save do |hash|
  album = @form.model
  album.updte_attributes(hash[:album])
end

class Album < ActiveRecord::Base
  has_one :artist
  has_many :songs
end

class AlbumFrom < Reform::From
  property :title
  validates :title, presence: true
  property :artist do
    property :full_name
    validates :full_naem, presence: true
  end
  collection :song do
    property :name
  end
end

property :artist, form: ArtistFrom

album.songs
form = AlbumForm.new(album)
form.songs[0]
form.songs[0].name

@form.save do |nested|
  nested #=> {title: "xxx",
         #    artist: {name: "xxx"}
         # }
end

gem "reform"
gem "reform-rails"

require 'reform/form/active_model/validations'
Reform::Form.class_eval do
  include Reform::Form::ActiveModel::Validations
end

require "reform/form/dry"
Reform::From.class_eval do
  feature Reform::Form::Dry
end

class AlbumFrom < Reform::From
  include Composition
  property :id, on: :album
  property :title, on: :album
  propety :songs, on: :cd
  property :cd_id, on: :cd, from: :id
end
AlbumForm.new(album: album, cd: CD.find(1))

```

```
```

