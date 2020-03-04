# What did I learn?

1. JUnit 5  
  Aby zmigrować trzeba zmienić pakiet dla adnotacji @Test i dla asercji
  Nowa asercja asertAll pozwala (jak Softly) wykonać wszystkie wskazane sprawdzenia
  Lepsze parametyzowalne testy
  https://www.baeldung.com/parameterized-tests-junit-5
  Nie trzeba się ograniczać - zamiast pojedynczego RunWith plus wiele @Rule, teraz można wiele @ExtendWith  

2. nvmw pomaga ogarnąć wiele wersji node'a  

3. Lombok - biblioteka i plugin do intellij  
  generates code in ".class" file instead of in the source code file
  daje wiele adnotacji, które pozwalają nie pisać getterów, setterów, constructors, pole logger, klasy builder, toString
  ale są z nim problemy: https://github.com/jhipster/generator-jhipster/issues/398
  
4. Builder  
    jak pisać lepsze Buildery, rozwiązanie problemu wymaganych pól: https://blog.tratif.com/2017/11/17/builder-pattern-revisited/   
    1. FluentBuilder pattern - metody zwracają interface wymuszający zawołanie jeszcze konkretnego withXYZ przed build()
    1. Builder robi validate() w metodzie build(), gdzie sprawdza, czy wymagane pola ustawione
    1. Zamiast wartości podawane w metodzie withXYZ ustawiać w polu xyz buildera, lub co gorsza tworzonego obiektu, zbieraj listę operations List<Consumer<BudowanaKlasa>> operations, np.: operations.add(user -> user.login = inLogin);
    1. Builder as an inner class in builded class

5. Conventional commits
   
   One commit per PR  

   Types of commit:  

   - feat: Add a new feature (equivalent to a MINOR in Semantic Versioning).
   - fix: Fix a bug (equivalent to a PATCH in Semantic Versioning).
   - docs: Documentation changes.
   - style: Code style change (semicolon, indentation...).
   - refactor: Refactor code without changing public API.
   - perf: Update code performances.
   - test: Add test to an existing feature.
   - chore: Update something without impacting the user (ex: bump a dependency in package.json).

https://www.conventionalcommits.org/en/v1.0.0/
