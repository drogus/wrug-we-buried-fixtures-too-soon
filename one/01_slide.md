!SLIDE
# We buried fixtures too soon #
## Piotr Sarnacki ##

!SLIDE

# @drogus #

!SLIDE bullets incremental

# Historia #

* Rails
* Test/Unit
* Fixtures

!SLIDE center

# Wtem... #

!SLIDE center

![](troll-factories.png)

!SLIDE

## I od tej pory każdy pieprzony projekt w Railsach używa fabryk... ##

!SLIDE center

![](troll-problem.png)

!SLIDE

# Czy fixtures to naprawdę zło wcielone? #

!SLIDE bullets incremental

# Fixtures - zalety #

* gotowy zestaw do *większości* testów
* szybkość (raz wczytane do bazy, później w użyciu są transakcje)
* można użyć podczas developmentu jako zestaw podstawowych danych

!SLIDE bullets incremental

# Fixtures - wady #

* ciężko jest ogarnąć stan bazy danych w dużym projekcie
* w plikach yml zachowane są wartości wrzucane bezpośrednio do bazy danych
* kiepskie przy jakichkolwiek edge cases

!SLIDE center

## Po co nam o tym mówisz? Przecież wszyscy używają fabryk i wiedzą, że są lepsze! ##

!SLIDE center

![](pedo-sad-panda.png)

!SLIDE center

![](sadpanda.gif)

!SLIDE center

![](righttool.png)

!SLIDE center

# RIGHT TOOL FOR THE JOB #

!SLIDE bullets incremental

# Gdzie się sprawdzają fixtures? #

* projekty ze skomplikowanymi zależnościami
* rzadko zmieniające się dane (kategorie, województwa)
* projekty, w których większość testów potrzebuje podobnego setupu

!SLIDE center

## Ale przecież fixtures mają tyle wad! :( ##

!SLIDE center

![](go_cry_emo_kid.jpg)

!SLIDE bullets

# Fixtures - wady #

* ciężko jest ogarnąć stan bazy danych w dużym projekcie
* w plikach yml zachowane są wartości wrzucane bezpośrednio do bazy danych
* kiepskie przy jakichkolwiek edge cases

!SLIDE bullets incremental

## ciężko jest ogarnąć stan bazy danych w dużym projekcie ##

* niestety, raczej nie do obejścia

!SLIDE bullets incremental

## kiepskie przy jakichkolwiek edge cases ##

* wystarczy do takich przypadków dorzucić fabryki

!SLIDE

    @@@ruby
    user = users(:johnny)
    edge_case_user =
        Factory.create(:login => "bob")


!SLIDE bullets incremental

## w plikach yml zachowane są wartości wrzucane bezpośrednio do bazy danych ##

* fixtures wcale nie muszą być generowane z plików YML

!SLIDE center

## Wait a minute... ! ##

!SLIDE center

## Jak w takim razie generować fixtures? ##

!SLIDE

# Fixtories! #

    @@@ruby
    Fixtories.define(:user) do |f|
      f.create :johnny,
               :email => "johnny@example.com",
               :password => "secret"

      f.create :bob,
               :bob => "bob@example.com",
               :password => "secret",
    end

!SLIDE bullets incremental

# Fixtories #

* gem do wczytywania fixtures używając fabryk
* dzięki użyciu fabryk uruchamiane są normalnie callbacki i walidacje

!SLIDE

# Coming soon #

!SLIDE

# Dziękuję za uwagę #

!SLIDE

# Pytania? #
