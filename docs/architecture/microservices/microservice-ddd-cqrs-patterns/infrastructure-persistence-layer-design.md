---
title: Projektowanie warstwy trwałości infrastruktury
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Eksploruj wzorzec repozytorium w projektowaniu warstwy trwałości infrastruktury.
ms.date: 10/08/2018
ms.openlocfilehash: e10c8c1569089d5c8274df655ad7a12f2ebb7c22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846812"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Projektowanie warstwy trwałości infrastruktury

Składniki trwałości danych zapewniają dostęp do danych hostowanych w granicach mikrousługi (czyli bazy danych mikrousługi). Zawierają one rzeczywistą implementację składników, takich jak repozytoria i klasy <xref:Microsoft.EntityFrameworkCore.DbContext> Jednostki [Pracy,](https://martinfowler.com/eaaCatalog/unitOfWork.html) takie jak niestandardowe obiekty entity framework (EF). EF DbContext implementuje zarówno repozytorium, jak i wzorce Jednostki Pracy.

## <a name="the-repository-pattern"></a>Wzór repozytorium

Repozytoria są klasy lub składniki, które hermetyzują logikę wymaganą do uzyskania dostępu do źródeł danych. Centralizują one wspólne funkcje dostępu do danych, zapewniając lepszą łatwość konserwacji i oddzielenie infrastruktury lub technologii używanych do uzyskiwania dostępu do baz danych z warstwy modelu domeny. Jeśli używasz object-relacyjne mapper (ORM) jak entity framework, kod, który musi zostać zaimplementowany jest uproszczony, dzięki LINQ i silne goczyć. Dzięki temu można skupić się na logiki trwałości danych, a nie na dostęp do danych instalacji wodociągowej.

Wzorzec repozytorium jest dobrze udokumentowanym sposobem pracy ze źródłem danych. W książce [Patterns of Enterprise Application Architecture](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/)Martin Fowler opisuje repozytorium w następujący sposób:

> Repozytorium wykonuje zadania pośrednika między warstwami modelu domeny a mapowaniem danych, działając w podobny sposób jak zestaw obiektów domeny w pamięci. Client obiektów deklaratywnie kompilacji zapytań i wysłać je do repozytoriów w celu uzyskania odpowiedzi. Koncepcyjnie repozytorium hermetyzuje zestaw obiektów przechowywanych w bazie danych i operacje, które mogą być wykonywane na nich, zapewniając sposób, który jest bliżej warstwy trwałości. Repozytoria, również, obsługuje cel oddzielenia, wyraźnie i w jednym kierunku, zależność między domeną pracy i alokacji danych lub mapowania.

### <a name="define-one-repository-per-aggregate"></a>Definiowanie jednego repozytorium na wartość zagregowaną

Dla każdego katalogu głównego agregacji należy utworzyć jedną klasę repozytorium. W mikrousługach opartych na wzorcach projektu opartego na domenie (DDD) jedynym kanałem, którego należy użyć do aktualizacji bazy danych, powinny być repozytoria. Dzieje się tak, ponieważ mają one relacji jeden-do-jednego z katalogu głównego agregacji, który kontroluje agregacji invariants i spójności transakcyjnej. Jest w porządku, aby zapytanie bazy danych za pośrednictwem innych kanałów (jak można zrobić zgodnie z podejściem CQRS), ponieważ kwerendy nie zmieniają stanu bazy danych. Jednak obszar transakcyjny (czyli aktualizacje) zawsze musi być kontrolowany przez repozytoria i zagregowane katalogi główne.

Zasadniczo repozytorium umożliwia wypełnianie danych w pamięci pochodzącej z bazy danych w postaci jednostek domeny. Gdy jednostki są w pamięci, można je zmienić, a następnie utrwalić z powrotem do bazy danych za pośrednictwem transakcji.

Jak wspomniano wcześniej, jeśli używasz wzorca architektonicznego CQS/CQRS, początkowe zapytania są wykonywane przez zapytania poboczne z modelu domeny, wykonywane przez proste instrukcje SQL przy użyciu Dapper. Takie podejście jest znacznie bardziej elastyczne niż repozytoria, ponieważ można wysyłać zapytania i łączyć wszystkie potrzebne tabele, a te kwerendy nie są ograniczone przez reguły z agregatów. Te dane trafiają do warstwy prezentacji lub aplikacji klienckiej.

Jeśli użytkownik wnosi zmiany, dane, które mają zostać zaktualizowane, pochodzą z aplikacji klienckiej lub warstwy prezentacji do warstwy aplikacji (takiej jak usługa interfejsu API sieci Web). Po otrzymaniu polecenia w programie obsługi poleceń, używasz repozytoriów, aby uzyskać dane, które chcesz zaktualizować z bazy danych. Zaktualizuj go w pamięci za pomocą danych przekazywanych za pomocą poleceń, a następnie dodać lub zaktualizować dane (jednostki domeny) w bazie danych za pośrednictwem transakcji.

Należy ponownie podkreślić, że należy zdefiniować tylko jedno repozytorium dla każdego katalogu głównego agregacji, jak pokazano na rysunku 7-17. Aby osiągnąć cel zagregowanego katalogu głównego w celu zachowania spójności transakcyjnej między wszystkimi obiektami w agregacji, nigdy nie należy tworzyć repozytorium dla każdej tabeli w bazie danych.

![Diagram przedstawiający relacje domeny i innej infrastruktury.](./media/infrastructure-persistence-layer-design/repository-aggregate-database-table-relationships.png)

**Rysunek 7-17**. Relacja między repozytoriami, agregacjami i tabelami baz danych

Powyższy diagram przedstawia relacje między warstwy domeny i infrastruktury: Agregacji nabywcy zależy od IBuyerRepository i zagregowanie zamówienia zależy od interfejsów IOrderRepository, te interfejsy są implementowane w warstwie Infrastruktura przez odpowiednie repozytoria, które zależą od UnitOfWork, również zaimplementowane tam, który uzyskuje dostęp do tabel w warstwie Dane.

### <a name="enforce-one-aggregate-root-per-repository"></a>Wymuszanie jednego agregowanego katalogu głównego dla repozytorium

Może być przydatne do zaimplementowania projektu repozytorium w taki sposób, że wymusza regułę, że tylko zagregowane katalogi główne powinny mieć repozytoria. Można utworzyć ogólny lub podstawowy typ repozytorium, który ogranicza typ jednostek, z którymi `IAggregateRoot` współpracuje, aby upewnić się, że mają interfejs znacznika.

W związku z tym każda klasa repozytorium zaimplementowana w warstwie infrastruktury implementuje swój własny kontrakt lub interfejs, jak pokazano w następującym kodzie:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Każdy interfejs repozytorium implementuje ogólny interfejs irepository:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Jednak lepszym sposobem, aby kod wymusić konwencję, że każde repozytorium jest związane z pojedynczej agregacji jest zaimplementowanie typu ogólnerepozytorium. W ten sposób jest jawne, że używasz repozytorium do kierowania określonej agregacji. Można to łatwo zrobić, `IRepository` implementując ogólny interfejs podstawowy, jak w poniższym kodzie:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Wzorzec repozytorium ułatwia testowanie logiki aplikacji

Wzorzec repozytorium umożliwia łatwe testowanie aplikacji za pomocą testów jednostkowych. Należy pamiętać, że testy jednostkowe tylko przetestować kod, a nie infrastruktury, więc abstrakcje repozytorium ułatwiają osiągnięcie tego celu.

Jak wspomniano we wcześniejszej sekcji, zaleca się zdefiniowanie i umieszczenie interfejsów repozytorium w warstwie modelu domeny, aby warstwa aplikacji, taka jak mikrousługa interfejsu API sieci Web, nie zależała bezpośrednio od warstwy infrastruktury, w której zaimplementowano rzeczywistych klas repozytorium. W ten sposób i przy użyciu iniekcji zależności w kontrolerach interfejsu API sieci Web, można zaimplementować makiety repozytoriów, które zwracają fałszywe dane zamiast danych z bazy danych. To podejście oddzielone od produkcji umożliwia tworzenie i uruchamianie testów jednostkowych, które koncentrują logikę aplikacji bez konieczności łączności z bazą danych.

Połączenia z bazami danych może zakończyć się niepowodzeniem i, co ważniejsze, uruchamianie setek testów w bazie danych jest złe z dwóch powodów. Po pierwsze, może to zająć dużo czasu ze względu na dużą liczbę testów. Po drugie rekordy bazy danych może ulec zmianie i wpłynąć na wyniki testów, dzięki czemu mogą nie być spójne. Testowanie w bazie danych nie jest testem jednostkowym, ale testem integracji. Należy mieć wiele testów jednostkowych działa szybko, ale mniej testów integracji z bazami danych.

Pod względem separacji problemów dla testów jednostkowych logika działa na jednostkach domeny w pamięci. Zakłada, że klasa repozytorium dostarczyła te. Gdy logika modyfikuje jednostki domeny, zakłada, że klasa repozytorium będzie przechowywać je poprawnie. Ważnym punktem jest tworzenie testów jednostkowych względem modelu domeny i jego logiki domeny. Zagregowane katalogi główne są głównymi granicami spójności w DDD.

Repozytoria zaimplementowane w eShopOnContainers polegać na implementacji DBContext EF Core repozytorium i jednostki pracy wzorców przy użyciu jego śledzenia zmian, więc nie powielać tej funkcji.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Różnica między wzorcem repozytorium a wzorcem starszej klasy dostępu do danych (klasa DAL)

Obiekt dostępu do danych bezpośrednio wykonuje operacje dostępu do danych i trwałości względem magazynu. Repozytorium oznacza dane z operacji, które mają być wykonywane w pamięci obiektu jednostki pracy <xref:Microsoft.EntityFrameworkCore.DbContext> (jak w EF podczas korzystania z klasy), ale te aktualizacje nie są wykonywane natychmiast do bazy danych.

Jednostka pracy jest określana jako pojedyncza transakcja, która obejmuje wiele operacji wstawiania, aktualizowania lub usuwania. W prostych słowach oznacza to, że dla określonej akcji użytkownika, takiej jak rejestracja na stronie internetowej, wszystkie operacje wstawiania, aktualizowania i usuwania są obsługiwane w ramach jednej transakcji. Jest to bardziej efektywne niż obsługa wielu transakcji bazy danych w sposób chattier.

Te wiele operacji trwałości są wykonywane później w jednej akcji, gdy kod z warstwy aplikacji poleceń go. Decyzja o zastosowaniu zmian w pamięci do rzeczywistego magazynu bazy danych jest zazwyczaj oparta na [wzorzec Jednostki pracy](https://martinfowler.com/eaaCatalog/unitOfWork.html). W EF wzorzec jednostki pracy <xref:Microsoft.EntityFrameworkCore.DbContext>jest implementowany jako .

W wielu przypadkach ten wzorzec lub sposób stosowania operacji względem magazynu może zwiększyć wydajność aplikacji i zmniejszyć możliwość niespójności. Zmniejsza również blokowanie transakcji w tabelach bazy danych, ponieważ wszystkie zamierzone operacje są zatwierdzane w ramach jednej transakcji. Jest to bardziej efektywne w porównaniu do wykonywania wielu izolowanych operacji względem bazy danych. W związku z tym wybrany ORM można zoptymalizować wykonanie względem bazy danych przez grupowanie kilka akcji aktualizacji w ramach tej samej transakcji, w przeciwieństwie do wielu małych i oddzielnych wykonań transakcji.

### <a name="repositories-shouldnt-be-mandatory"></a>Repozytoria nie powinny być obowiązkowe

Niestandardowe repozytoria są przydatne z powodów cytowanych wcześniej i to jest podejście do mikrousługi zamawiania w eShopOnContainers. Jednak nie jest to istotny wzorzec do zaimplementowania w projekcie DDD lub nawet w ogóle rozwoju .NET.

Na przykład, Jimmy Bogard, zapewniając bezpośrednie informacje zwrotne dla tego przewodnika, powiedział, co następuje:

> To będzie prawdopodobnie moje największe opinie. Naprawdę nie jestem fanem repozytoriów, głównie dlatego, że ukrywają ważne szczegóły podstawowego mechanizmu trwałości. Dlatego idę do MediatR dla poleceń, zbyt. Mogę użyć pełnej mocy warstwy trwałości i wcisnąć wszystkie te zachowania domeny do moich zagregowanych korzeni. Zwykle nie chcę wyśmiewać moich repozytoriów - nadal muszę mieć ten test integracji z prawdziwymi. Going CQRS oznaczało, że tak naprawdę nie mamy potrzeby repozytoriów więcej.

Repozytoria mogą być przydatne, ale nie są krytyczne dla projektu DDD, w taki sposób, że wzorca agregacji i model domeny sformatowanej są. W związku z tym należy użyć wzorca repozytorium, czy nie, zgodnie z potrzebami. W każdym razie będziesz używać wzorca repozytorium za każdym razem, gdy używasz EF Core, chociaż w tym przypadku repozytorium obejmuje całą mikrousługę lub ograniczony kontekst.

## <a name="additional-resources"></a>Zasoby dodatkowe

### <a name="repository-pattern"></a>Wzorzec repozytorium

- **Edward Hieatt i Rob mnie. Wzór repozytorium.** \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **Wzór repozytorium** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans. Projektowanie oparte na domenie: radzenie sobie ze złożonością w sercu oprogramowania.** (Książka; zawiera omówienie wzorca repozytorium) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Wzór jednostki roboczej

- **Martin Fowler. Wzór jednostki pracy.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **Implementowanie repozytorium i jednostki wzorców pracy w ASP.NET aplikacji MVC** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Poprzedni](domain-events-design-implementation.md)
>[następny](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
