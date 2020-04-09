---
title: Projektowanie warstwy trwałości infrastruktury
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się ze wzorcem repozytorium w projektowaniu warstwy trwałości infrastruktury.
ms.date: 10/08/2018
ms.openlocfilehash: 1b2665e81ade60affa84563121c04bca08537f07
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988482"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Projektowanie warstwy trwałości infrastruktury

Składniki trwałości danych zapewniają dostęp do danych hostowanych w granicach mikrousługi (czyli bazy danych mikrousług). Zawierają one rzeczywistą implementację składników, takich jak repozytoria i [jednostki](https://martinfowler.com/eaaCatalog/unitOfWork.html) <xref:Microsoft.EntityFrameworkCore.DbContext> pracy klas, takich jak niestandardowe entity framework (EF) obiektów. EF DbContext implementuje zarówno repozytorium i jednostki pracy wzorców.

## <a name="the-repository-pattern"></a>Wzorzec repozytorium

Repozytoria to klasy lub składniki, które hermetyzują logikę wymaganą do uzyskania dostępu do źródeł danych. Centralizują one wspólne funkcje dostępu do danych, zapewniając lepszą łatwość konserwacji i oddzielenie infrastruktury lub technologii używanej do uzyskiwania dostępu do baz danych z warstwy modelu domeny. Jeśli używasz mapera obiektowego (ORM), takiego jak Entity Framework, kod, który musi zostać zaimplementowany, jest uproszczony dzięki LINQ i silnemu wpisywanie. Dzięki temu można skupić się na logiki trwałości danych, a nie na dostęp do danych instalacji wodno-kanalizacyjnych.

Wzorzec repozytorium jest dobrze udokumentowany sposób pracy ze źródłem danych. W książce [Patterns of Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/)Martin Fowler opisuje repozytorium w następujący sposób:

> Repozytorium wykonuje zadania pośrednika między warstwami modelu domeny a mapowaniem danych, działając w sposób podobny do zestawu obiektów domeny w pamięci. Obiekty klienta deklaratywnie tworzą zapytania i wysyłają je do repozytoriów w celu uzyskania odpowiedzi. Koncepcyjnie repozytorium hermetyzuje zestaw obiektów przechowywanych w bazie danych i operacji, które mogą być wykonywane na nich, zapewniając sposób, który jest bliżej warstwy trwałości. Repozytoria, również, obsługuje cel oddzielenia, wyraźnie i w jednym kierunku, zależność między domeną pracy i alokacji danych lub mapowania.

### <a name="define-one-repository-per-aggregate"></a>Definiowanie jednego repozytorium na agregację

Dla każdego katalogu głównego agregacji lub agregacji należy utworzyć jedną klasę repozytorium. W mikrousługach opartych na wzorcach projektu opartego na domenie (DDD) jedynym kanałem, którego należy użyć do zaktualizowania bazy danych, powinny być repozytoria. Dzieje się tak, ponieważ mają one relację jeden do jednego z korzenia agregacji, który kontroluje invariants agregacji i spójności transakcyjnej. Jest w porządku, aby zbadać bazę danych za pośrednictwem innych kanałów (jak można zrobić po cqrs podejście), ponieważ kwerendy nie zmieniają stan bazy danych. Jednak obszar transakcyjny (czyli aktualizacje) musi być zawsze kontrolowany przez repozytoria i zagregowane katalogi główne.

Zasadniczo repozytorium pozwala na wypełnianie danych w pamięci, które pochodzą z bazy danych w postaci jednostek domeny. Gdy jednostki są w pamięci, można je zmienić, a następnie utrwalić z powrotem do bazy danych za pośrednictwem transakcji.

Jak wspomniano wcześniej, jeśli używasz wzorca architektury CQS/CQRS, początkowe zapytania są wykonywane przez zapytania boczne z modelu domeny, wykonywane przez proste instrukcje SQL przy użyciu Dapper. Takie podejście jest znacznie bardziej elastyczne niż repozytoria, ponieważ można wysyłać zapytania i dołączać do dowolnych tabel, których potrzebujesz, a te zapytania nie są ograniczone przez reguły z agregatów. Te dane trafiają do warstwy prezentacji lub aplikacji klienckiej.

Jeśli użytkownik wprowadza zmiany, dane, które mają zostać zaktualizowane, pochodzą z warstwy aplikacji lub prezentacji klienckiej do warstwy aplikacji (takiej jak usługa interfejsu API sieci Web). Po otrzymaniu polecenia w programie obsługi poleceń, należy użyć repozytoriów, aby uzyskać dane, które chcesz zaktualizować z bazy danych. Zaktualizować go w pamięci z danymi przekazanymi za pomocą poleceń, a następnie dodać lub zaktualizować dane (jednostki domeny) w bazie danych za pośrednictwem transakcji.

Należy ponownie podkreślić, że należy zdefiniować tylko jedno repozytorium dla każdego katalogu głównego agregacji, jak pokazano na rysunku 7-17. Aby osiągnąć cel agregacji katalogu głównego, aby zachować spójność transakcyjną między wszystkimi obiektami w ramach agregacji, nigdy nie należy tworzyć repozytorium dla każdej tabeli w bazie danych.

![Diagram przedstawiający relacje domeny i innej infrastruktury.](./media/infrastructure-persistence-layer-design/repository-aggregate-database-table-relationships.png)

**Rysunek 7-17**. Relacja między repozytoriami, agregacjami i tabelami bazy danych

Powyższy diagram przedstawia relacje między warstwami Domeny i infrastruktury: Agregacja kupującego zależy od IBuyerRepository i Agregacji zamówień zależy od interfejsów IOrderRepository, interfejsy te są implementowane w warstwie Infrastruktura przez odpowiednie repozytoria, które zależą od UnitOfWork, również tam zaimplementowane, który uzyskuje dostęp do tabel w warstwie Danych.

### <a name="enforce-one-aggregate-root-per-repository"></a>Wymuszanie jednego katalogu głównego agregacji na repozytorium

Zaimplementowanie projektu repozytorium w taki sposób może być przydatne do zaimplementowania projektu repozytorium w taki sposób, że wymusza regułę, że tylko agregowane katalogi główne powinny mieć repozytoria. Można utworzyć typ ogólnego lub podstawowego repozytorium, który ogranicza typ jednostek, `IAggregateRoot` z którymi współpracuje, aby upewnić się, że mają interfejs znacznika.

W związku z tym każda klasa repozytorium zaimplementowana w warstwie infrastruktury implementuje własną umowę lub interfejs, jak pokazano w poniższym kodzie:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Każdy określony interfejs repozytorium implementuje ogólny interfejs IRepository:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Jednak lepszym sposobem, aby kod wymusić konwencję, że każde repozytorium jest związane z pojedynczego agregacji jest zaimplementowanie typu repozytorium ogólnego. W ten sposób jest jawne, że używasz repozytorium do kierowania określonego agregacji. Można to łatwo zrobić, implementując ogólny `IRepository` interfejs podstawowy, jak w poniższym kodzie:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Wzorzec repozytorium ułatwia testowanie logiki aplikacji

Wzorzec repozytorium umożliwia łatwe testowanie aplikacji za pomocą testów jednostkowych. Należy pamiętać, że testy jednostkowe tylko przetestować kod, a nie infrastruktury, więc abstrakcje repozytorium ułatwiają osiągnięcie tego celu.

Jak wspomniano we wcześniejszej sekcji, zaleca się zdefiniowanie i umieszczenie interfejsów repozytorium w warstwie modelu domeny, aby warstwa aplikacji, taka jak mikrousługa interfejsu API sieci Web, nie była zależna bezpośrednio od warstwy infrastruktury, w której zaimplementowano rzeczywiste klasy repozytorium. W ten sposób i przy użyciu iniekcji zależności w kontrolerach interfejsu API sieci Web, można zaimplementować makiety repozytoriów, które zwracają fałszywe dane zamiast danych z bazy danych. To podejście niezwiązane z wielkością produkcji umożliwia tworzenie i uruchamianie testów jednostkowych, które koncentrują się na logice aplikacji bez konieczności łączności z bazą danych.

Połączenia z bazami danych może zakończyć się niepowodzeniem i, co ważniejsze, uruchamianie setki testów w bazie danych jest złe z dwóch powodów. Po pierwsze, może to zająć dużo czasu ze względu na dużą liczbę testów. Po drugie rekordy bazy danych może zmienić i mieć wpływ na wyniki testów, tak aby nie były spójne. Testowanie bazy danych nie jest testem jednostkowym, ale testem integracji. Powinno być wiele testów jednostkowych uruchomionych szybko, ale mniej testów integracji z bazami danych.

Pod względem rozdzielenia problemów dla testów jednostkowych logika działa na jednostki domeny w pamięci. Przyjęto założenie, że klasa repozytorium dostarczyła te. Gdy logika modyfikuje jednostki domeny, zakłada, że klasa repozytorium będzie przechowywać je poprawnie. Ważnym punktem w tym miejscu jest utworzenie testów jednostkowych dla modelu domeny i jego logiki domeny. Zagregowane katalogi główne są głównymi granicami spójności w DDD.

Repozytoria zaimplementowane w eShopOnContainers opierają się na implementacji DbContext ef core repozytorium i jednostki pracy przy użyciu jego śledzenia zmian, więc nie powielają tej funkcji.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Różnica między wzorcem repozytorium a wzorcem starszej klasy dostępu do danych (klasa DAL)

Obiekt dostępu do danych bezpośrednio wykonuje operacje dostępu do danych i trwałości względem magazynu. Repozytorium oznacza dane z operacji, które mają być wykonywane w pamięci jednostki obiektu <xref:Microsoft.EntityFrameworkCore.DbContext> pracy (jak w EF podczas korzystania z klasy), ale te aktualizacje nie są wykonywane natychmiast do bazy danych.

Jednostka pracy jest określana jako pojedyncza transakcja, która obejmuje wiele operacji wstawania, aktualizowania lub usuwania. W prostych słowach oznacza to, że dla określonej akcji użytkownika, takich jak rejestracja w witrynie sieci Web, wszystkie operacje wstawiania, aktualizacji i usuwania są obsługiwane w jednej transakcji. Jest to bardziej wydajne niż obsługa wielu transakcji bazy danych w sposób chattier.

Te wiele operacji trwałości są wykonywane później w jednej akcji, gdy kod z warstwy aplikacji polecenia go. Decyzja o zastosowaniu zmian w pamięci do rzeczywistego magazynu bazy danych jest zazwyczaj oparta na [wzorcu Jednostka pracy](https://martinfowler.com/eaaCatalog/unitOfWork.html). W EF wzorzec jednostki pracy <xref:Microsoft.EntityFrameworkCore.DbContext>jest implementowany jako .

W wielu przypadkach ten wzorzec lub sposób stosowania operacji względem magazynu może zwiększyć wydajność aplikacji i zmniejszyć możliwość niespójności. Zmniejsza również blokowanie transakcji w tabelach bazy danych, ponieważ wszystkie zamierzone operacje są zatwierdzane jako część jednej transakcji. Jest to bardziej wydajne w porównaniu do wykonywania wielu operacji izolowanych w bazie danych. W związku z tym wybrany ORM można zoptymalizować wykonanie w bazie danych, grupując kilka akcji aktualizacji w ramach tej samej transakcji, w przeciwieństwie do wielu małych i oddzielnych wykonań transakcji.

### <a name="repositories-shouldnt-be-mandatory"></a>Repozytoria nie powinny być obowiązkowe

Niestandardowe repozytoria są przydatne z powodów wymienionych wcześniej i jest to podejście do zamawiania mikrousług w eShopOnContainers. Jednak nie jest niezbędnym wzorcem do zaimplementowania w projekcie DDD lub nawet w ogóle rozwoju .NET.

Na przykład Jimmy Bogard, udzielając bezpośredniej informacji zwrotnej na temat tego przewodnika, powiedział, co następuje:

> To będzie prawdopodobnie moja największa opinia. Naprawdę nie jestem fanem repozytoriów, głównie dlatego, że ukrywają ważne szczegóły leżącego u podstaw mechanizmu trwałości. Dlatego idę do MediatR dla poleceń, zbyt. Mogę użyć pełnej mocy warstwy trwałości i wypchnąć wszystkie te zachowania domeny do moich zagregowanych korzeni. Zwykle nie chcę drwić z moich repozytoriów - nadal muszę mieć ten test integracji z prawdziwymi. Going CQRS oznaczało, że tak naprawdę nie mamy potrzeby repozytoriów więcej.

Repozytoria mogą być przydatne, ale nie są krytyczne dla projektu DDD, w taki sposób, że agreguj wzorzec i model domeny rozszerzonej są. W związku z tym należy użyć wzorca repozytorium lub nie, jak widzisz stosowne. W każdym razie będziesz używać wzorca repozytorium za każdym razem, gdy używasz EF Core chociaż w tym przypadku repozytorium obejmuje całej mikrousługi lub ograniczonego kontekstu.

## <a name="additional-resources"></a>Zasoby dodatkowe

### <a name="repository-pattern"></a>Wzorzec repozytorium

- **Edward Hieatt i Rob mnie. Wzorzec repozytorium.** \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **Wzorzec repozytorium** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans. Projektowanie oparte na domenie: radzenie sobie ze złożonością w sercu oprogramowania.** (Książka; zawiera omówienie wzorca repozytorium) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Wzór jednostki pracy

- **Martin Fowler. Wzór jednostki pracy.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **Implementowanie repozytorium i jednostki wzorców pracy w ASP.NET aplikacji MVC** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Poprzedni](domain-events-design-implementation.md)
>[następny](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
