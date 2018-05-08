---
title: Projektowanie infrastruktury warstwę trwałości
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie infrastruktury warstwę trwałości
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/08/2017
ms.openlocfilehash: 2b15fcaeaa8934caceaeab963123650354abf291
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="designing-the-infrastructure-persistence-layer"></a>Projektowanie infrastruktury warstwę trwałości

Składniki trwałości danych zapewniają dostęp do danych hostowanej w granicach mikrousługi (to znaczy, że baza danych mikrousługi). Zawierają one rzeczywistego wykonania składniki, takie jak repozytoria i [jednostki pracy](https://martinfowler.com/eaaCatalog/unitOfWork.html) klas, takich jak niestandardowe DBContexts EF.

## <a name="the-repository-pattern"></a>Wzorzec repozytorium

Repozytoria są klasy lub składniki, które hermetyzują logiki wymagany dostęp do źródeł danych. One scentralizowane typowych funkcji dostępu danych, zapewniając lepsze utrzymanie i oddzielenie infrastruktury lub technologii, które umożliwiają dostęp do bazy danych z warstwy modelu domeny. Jeśli używasz ORM, takich jak Entity Framework, kod, który musi być implementowana jest uproszczone dzięki użyciu LINQ i silne wpisywanie. To umożliwia użytkownikowi skupienie się na logice trwałości danych, a nie dane dostępu instalację.

Wzorzec repozytorium jest to dobrze udokumentowane sposób pracy ze źródłem danych. W książce [wzorce Enterprise architektura](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), pole Fowler opisuje repozytorium w następujący sposób:

Repozytorium jest wykonywane pośrednika między warstwy modelu domeny i mapowanie danych działa w sposób podobny do zestawu obiektów domeny w pamięci. Obiekty klienta deklaratywnie tworzyć kwerendy i wyślij je do przechowywania dla odpowiedzi. Koncepcyjnie repozytorium hermetyzuje zestaw obiektów przechowywanych w bazie danych i operacje, które można wykonywać na nich, dzięki czemu zbliżonej do warstwę trwałości. Repozytoriów obsługuje również celem oddzielanie wyraźnie i w jednym kierunku zależności między domeną pracy i alokacji danych lub mapowania.

### <a name="define-one-repository-per-aggregate"></a>Zdefiniuj jednego repozytorium na agregacji

Dla każdego agregacji lub zbiorczej katalogu głównego należy utworzyć jedną klasę repozytorium. Mikrousługi, w oparciu o wzorce projektowe opartych na domenie tylko kanału, które powinny być używane do aktualizowania bazy danych powinien być repozytoriów. Jest tak, ponieważ mają one relacje jeden do jednego z głównym agregacji, który kontroluje invariants i spójności transakcyjnej wartości zagregowanej. Można w bazie danych za pośrednictwem innych kanałów (jak następujące podejście CQRS), ponieważ zapytania nie zmieniaj stanu bazy danych. Jednak obszaru transakcyjne — aktualizacje — zawsze muszą być kontrolowane przez przechowywania i agregacji katalogów głównych.

Zasadniczo repozytorium służy do wypełniania danych w pamięci, która pochodzi z bazy danych w formularzu jednostek domeny. Po zatwierdzeniu jednostek w pamięci, można je zmienić i następnie utrwalone w bazie danych za pomocą transakcji.

Jak wspomniano wcześniej, jeśli używasz wzorzec architektury CQS/CQRS, początkowej kwerendy będą wykonywane przez zapytania po stronie poza modelu domeny, z zastosowaniem prostych instrukcji SQL przy użyciu Dapper. Takie podejście jest bardziej elastyczne niż repozytoriów, ponieważ może zapytania i Dołącz do żadnych tabel należy, i tych zapytań nie są ograniczone przez zasady z agregacji. Te dane będą przejdź do aplikacji klienta lub warstwy prezentacji.

Jeśli użytkownik wprowadzi zmiany, mają być aktualizowane dane będą pobierane z warstwy aplikacji lub prezentacji klienta do warstwy aplikacji (na przykład usługi interfejsu API sieci Web). Po otrzymaniu programem obsługi polecenia (z danymi) umożliwia repozytoria pobrać dane, które chcesz zaktualizować z bazy danych. Należy zaktualizować w pamięci z informacjami o przekazany za pomocą poleceń, a następnie dodać lub zaktualizować danych (jednostki domeny) w bazie danych za pomocą transakcji.

Należy pamiętać, że tego repozytorium tylko jeden powinien być zdefiniowany dla każdego katalogu głównego agregacji, jak pokazano na rysunku 9-17. Aby osiągnąć głównego agregacji do zapewniania spójności transakcyjnej między wszystkich obiektów w agregacji, nigdy nie należy tworzyć repozytorium dla każdej tabeli w bazie danych.

![](./media/image18.png)

**Rysunek 9-17**. Relacja między repozytoriów, agreguje i tabel bazy danych

### <a name="enforcing-one-aggregate-root-per-repository"></a>Wymuszanie jeden główny agregacji na repozytorium

Może być przydatna do zaimplementowania projektu repozytorium w taki sposób, że wymusza reguły, że tylko agregacji elementy główne powinny mieć repozytoriów. Można utworzyć typu ogólnego lub podstawowym repozytorium, który ogranicza typ jednostek działa z do upewnij się, że mają one IAggregateRoot interfejsu znacznika.

W związku z tym każda klasa repozytorium zaimplementowana w warstwie infrastruktury implementuje własne umowy lub interfejsu, jak pokazano w poniższym kodzie:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

Każdy interfejs określonych repozytorium implementuje interfejs ogólny IRepository:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Jednak lepszym sposobem kod wymusić Konwencji czy każdego repozytorium musi być powiązana do pojedynczego agregacji byłoby do zaimplementowania typu ogólnego repozytorium, tak aby zawierała jawne, że używasz repozytorium pod kątem określonej agregacji. Który można łatwo to zrobić wykonania tego ogólny interfejs podstawowy IRepository, zgodnie z poniższym kodem:

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Wzorzec repozytorium ułatwia testowanie aplikacji logiki

Wzorca repozytorium umożliwia łatwe testowanie aplikacji przy użyciu testów jednostkowych. Należy pamiętać, że testy jednostkowe tylko testowe z kodu, nie infrastruktury tak abstrakcje repozytorium ułatwiają osiągnąć ten cel.

Zgodnie z opisem w sekcji wcześniej, zalecane jest definiowanie i umieszczony interfejsy repozytorium warstwy modelu domeny warstwy aplikacji (na przykład mikrousługi z interfejsu API sieci Web) nie zależy od bezpośrednio na warstwie infrastrukturze gdzie masz zaimplementowano klasy rzeczywiste repozytorium. W ten sposób i użyciem iniekcji zależności w kontrolerów interfejsu API sieci Web, można zaimplementować zasymulować repozytoriów, które zwracają fałszywych danych zamiast danych z bazy danych. Czy rozdzielonymi podejście pozwala na tworzenie i testów jednostkowych wykonywania, który można przetestować tylko logiki aplikacji bez połączenia z bazą danych.

Połączenia z bazami danych może zakończyć się niepowodzeniem i co ważniejsze, działania setki testy w bazie danych jest zła dwóch powodów. Po pierwsze może zająć dużo czasu z powodu dużej liczby testów. Po drugie rekordów bazy danych może i wpływu wyniki testów, dzięki czemu nie są zgodne. Testowanie bazy danych nie jest testów jednostkowych, ale Testowanie integracji. Powinien mieć wiele testów jednostkowych szybkiego uruchamiania, ale mniej integracji testów względem bazy danych.

Pod względem separacji dla testów jednostkowych logika działa na jednostkach domeny w pamięci. Zakłada się, że klasa repozytorium wydał te. Po logiki modyfikuje jednostek domeny, przyjęto założenie, że klasa repozytorium zapisze je poprawnie. Należy koniecznie zwrócić uwagę jest tworzenia testów jednostkowych przed modelu domeny i jego logika domeny. Łączny certyfikaty główne są granice głównego spójności w DDD.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Różnica między wzorca repozytorium i starszych wzorzec klasą (DAL) dostęp do danych

Obiekt dostępu do danych bezpośrednio wykonuje operacje dostępu i trwałości danych z magazynu. Znaczniki repozytorium danych przy użyciu operacje, które należy wykonać w pamięci jednostkę pracy obiektu (jak EF przy użyciu kontekstu DbContext), ale te aktualizacje nie są wykonywane bezpośrednio.

Jednostka pracy jest określana jako jedna transakcja, która obejmuje wiele wstawiania, aktualizowania lub usuwania operacji. Proste warunków oznacza to, że działania określonego użytkownika (na przykład, rejestracja w witrynie sieci Web), insert, update i delete transakcji są obsługiwane w ramach jednej transakcji. Jest to bardziej efektywne niż Obsługa wielu transakcji bazy danych w sposób chattier.

Te wiele operacji trwałości są wykonywane później w ramach jednej akcji, gdy polecenia kodu z warstwy aplikacji. Decyzja o wprowadzanie zmian w pamięci do magazynu rzeczywistej bazy danych jest zwykle oparta na [wzorzec jednostki pracy](https://martinfowler.com/eaaCatalog/unitOfWork.html). W EF wzorzec jednostki pracy jest implementowany jako DBContext.

W wielu przypadkach ten wzorzec lub sposób stosowania operacje magazynu mogą zwiększyć wydajność aplikacji i zmniejszyć ryzyko wystąpienia niespójności. Ponadto zmniejsza transakcji blokowania w tabelach bazy danych, ponieważ wszystkie operacje przeznaczone są zatwierdzone w ramach jednej transakcji. Jest to bardziej skuteczne, w odróżnieniu od wykonywania wielu izolowanego operacji w bazie danych. W związku z tym wybranego ORM jest w stanie zoptymalizować wykonywania w bazie danych przez grupowanie kilka akcji aktualizacji w ramach tej samej transakcji, w przeciwieństwie do wielu wykonaniami małych i oddzielne transakcji.

### <a name="repositories-should-not-be-mandatory"></a>Repozytoria nie będą już wymagane

Niestandardowe repozytoria przydają się z powodów wymienionych wcześniej, a to podejście do porządkowania mikrousługi w eShopOnContainers. Jednak nie jest istotne wzorzec do wdrożenia w projekcie DDD lub nawet ogólnie Programowanie w .NET.

Na przykład Jimmy Bogard, podczas tworzenia pobrania tego przewodnika powiedział następujące czynności:

Prawdopodobnie będzie największych opinii. Naprawdę nie mam wentylator repozytoriów głównie, ponieważ ukrywają szczegóły ważne podstawowego mechanizmu stanu trwałego. Jego Dlaczego można przejść do MediatR poleceń, zbyt. I Użyj pełnych możliwości warstwę trwałości i wypchnąć tego zachowania domeny do mojego agregacji katalogów głównych. Zazwyczaj nie powinny się mock Moje repozytoria — muszę mieć tej integracji testu z czegoś. Przechodzenie CQRS oznaczało, że firma Microsoft nie naprawdę potrzebują repozytoria więcej.

Znaleźliśmy repozytoria użyteczne, ale możemy potwierdzić, że nie są istotne dla Twojej DDD w taki sposób, łączny wzorca i model domeny sformatowanego. W związku z tym Użyj wzorca repozytorium, lub nie, jak widać dopasowania.

## <a name="the-specification-pattern"></a>Wzorzec specyfikacji

Wzorzec specyfikacji (pełną nazwę byłoby wzorzec specyfikacji zapytania) jest zaprojektowany jako miejsce, w którym można umieścić definicji zapytania opcjonalne, sortowanie i stronicowanie logiki wzorca projektowego Domain-Driven.

Wzorzec specyfikacja definiuje kwerendę w obiekcie. Na przykład aby hermetyzować stronicowane zapytanie, które wyszukuje niektórych produktów, można utworzyć specyfikację PagedProduct, która pobiera niezbędne parametry wejściowe (pageNumber pageSize, filtr, itp.). Następnie w dowolnej metody repozytorium (zazwyczaj przeciążenia List()) będzie akceptować ISpecification i uruchomić zapytanie oczekiwanych na podstawie tej specyfikacji.

Istnieje kilka zalety tego podejścia:

* Specyfikacja ma nazwę (w przeciwieństwie do grupy wyrażenia LINQ) można omawiać temat.

* Specyfikacja można jednostki testowane w izolacji upewnij się, że jest ona odpowiednia. Można również łatwo ponownie, jeśli potrzebujesz podobne zachowania. Na przykład, w widoku MVC akcji i interfejsu API sieci Web, a także w różnych usług.

* Specyfikacja mogą służyć do opisywania kształt danych ma zostać zwrócona, tak, aby zapytania mogą zwracać tylko te dane są wymagane. Eliminuje to potrzebę opóźnionego ładowania w aplikacji sieci web (która zazwyczaj nie jest dobrym pomysłem) i pomaga zapewnić implementacje repozytorium z staje się przeładowanie Dysponując tymi szczegółowymi informacjami.

Przykładowy ogólny interfejs specyfikacji jest następujący kod z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb ).

```csharp
// https://github.com/dotnet-architecture/eShopOnWeb 
public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

W kolejnych sekcjach jest wyjaśniono sposób implementacji wzorca specyfikacji Entity Framework Core 2.0 i jak z niego korzystać z dowolnej klasy repozytorium.

**Ważna Uwaga:** wzorzec specyfikacji jest starego wzorzec, który można zaimplementować wiele różnych sposobów, jak w następujących zasobach dodatkowych. Wzorzec/pomysł warto wiedzieć, niemniej jednak starszej implementacji, które są nie wykorzystaniu nowoczesny język funkcji, takich jak Linq i wyrażenia są starsze metod.

## <a name="additional-resources"></a>Dodatkowe zasoby

### <a name="the-repository-pattern"></a>Wzorzec repozytorium

-   **Edward Hieatt i Tomasz mnie. Wzorzec repozytorium.**
    [*https://martinfowler.com/eaaCatalog/repository.html*](https://martinfowler.com/eaaCatalog/repository.html)

-   **Wzorzec repozytorium**
    [*https://msdn.microsoft.com/library/ff649690.aspx*](https://msdn.microsoft.com/library/ff649690.aspx)

-   **Wzorzec repozytorium: Danych abstrakcję funkcji trwałości**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)

-   **Evans marek. Projektowanie oparte na domenie: Czoła złożoności serca oprogramowania.** (Książki; zawiera omówienie wzorca repozytorium) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="unit-of-work-pattern"></a>Jednostka pracy wzorca

-   **Pole Fowler. Jednostka pracy wzorca.**
    [*https://martinfowler.com/eaaCatalog/unitOfWork.html*](https://martinfowler.com/eaaCatalog/unitOfWork.html)

<!-- -->

-   **Implementowanie repozytorium i jednostki pracy w aplikacji platformy ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

### <a name="the-specification-pattern"></a>Wzorzec specyfikacji

-   **Wzorzec specyfikacji.**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)

-   **Evans, marek (2004). Domena zmiennych projektu. Addison-Wesley. str. 224.**

-   **Wymagania. Pole Fowler**
    [*https://www.martinfowler.com/apsupp/spec.pdf/*](https://www.martinfowler.com/apsupp/spec.pdf)

>[!div class="step-by-step"]
[Previous] (domain-events-design-implementation.md) [Next] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)
