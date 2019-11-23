---
title: Projektowanie warstwy trwałości infrastruktury
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z wzorcem repozytorium w projekcie warstwy trwałości infrastruktury.
ms.date: 10/08/2018
ms.openlocfilehash: f1c5df1cc5672760374610a416ae22b45cd76c25
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737948"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Zaprojektowanie warstwy trwałości infrastruktury

Składniki trwałości danych zapewniają dostęp do danych znajdujących się w granicach mikrousługi (czyli bazy danych mikrousług). Zawierają one rzeczywistą implementację składników, takich jak repozytoria i klasy [jednostek pracy](https://martinfowler.com/eaaCatalog/unitOfWork.html) , takie jak niestandardowe Entity Framework (EF) <xref:Microsoft.EntityFrameworkCore.DbContext> obiekty. EF DbContext implementuje oba elementy, repozytorium i jednostki pracy.

## <a name="the-repository-pattern"></a>Wzorzec repozytorium

Repozytoria to klasy lub składniki, które hermetyzują logikę wymaganą do uzyskiwania dostępu do źródeł danych. Umożliwiają one scentralizowanie funkcji dostępu do danych, co zapewnia lepszą łatwość utrzymania i rozdzielenie infrastruktury lub technologii używanej do uzyskiwania dostępu do baz danych z warstwy modelu domeny. Jeśli używasz mapowania obiektowo-relacyjnego (ORM), takiego jak Entity Framework, kod, który musi być zaimplementowany, jest uproszczony, dzięki czemu LINQ i silne pisanie. Pozwala to skupić się na logice trwałości danych, a nie na instalacji wodociągowej.

Wzorzec repozytorium jest dobrze udokumentowanym sposobem pracy ze źródłem danych. W [wzorcach księgi architektury aplikacji przedsiębiorstwa](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowlera opisuje repozytorium w następujący sposób:

> Repozytorium wykonuje zadania pośredniego między warstwami modelu domeny i mapowaniem danych, działając w podobny sposób jak w przypadku zestawu obiektów domeny w pamięci. Obiekty klienta deklaratywnie kompilują zapytania i wysyłają je do repozytoriów na potrzeby odpowiedzi. Koncepcyjnie repozytorium jest hermetyzowane z zestawem obiektów przechowywanych w bazie danych i operacjach, które mogą być wykonywane na nich, zapewniając sposób zbliżony do warstwy trwałości. Repozytoria, również obsługa celu oddzielenia, jasno i w jednym kierunku, zależności między domeną służbową i alokacją danych lub mapowaniem.

### <a name="define-one-repository-per-aggregate"></a>Zdefiniuj jedno repozytorium na zagregowane

Dla każdego elementu zagregowanego agregacji lub agregacji należy utworzyć jedną klasę repozytorium. W mikrousłudze na podstawie wzorców projektowania opartego na domenach (DDD) jedynym kanałem, którego należy użyć do zaktualizowania bazy danych, powinny być repozytoria. Wynika to z faktu, że mają one relację jeden do jednego z zagregowanym elementem głównym, który kontroluje niezagregowaną i transakcyjną spójność agregacji. Nie można wysyłać zapytań do bazy danych za pomocą innych kanałów (jak w przypadku podejścia CQRS), ponieważ zapytania nie zmieniają stanu bazy danych. Jednak obszar transakcyjny (czyli aktualizacje) musi być zawsze kontrolowany przez repozytoria i zagregowane elementy główne.

W zasadzie repozytorium umożliwia wypełnienie danych w pamięci pochodzącej z bazy danych w postaci jednostek domeny. Gdy jednostki znajdują się w pamięci, można je zmienić, a następnie utrwalić z powrotem do bazy danych za pomocą transakcji.

Jak wspomniano wcześniej, jeśli używasz wzorca architektury CQS/CQRS, początkowe zapytania są wykonywane przez zapytania boczne z modelu domeny, wykonywane przez proste instrukcje SQL przy użyciu Dapper. Takie podejście jest znacznie bardziej elastyczne niż repozytoria, ponieważ można wykonywać zapytania i dołączać do dowolnych tabel, które nie są ograniczone przez reguły z agregacji. Te dane przechodzą do warstwy prezentacji lub aplikacji klienckiej.

Jeśli użytkownik wprowadza zmiany, dane, które mają zostać zaktualizowane, pochodzą z aplikacji klienckiej lub z warstwy prezentacji do warstwy aplikacji (takiej jak usługa interfejsu API sieci Web). Po otrzymaniu polecenia w programie obsługi poleceń, należy użyć repozytoriów, aby pobrać dane, które mają zostać zaktualizowane z bazy danych. Aktualizujesz ją w pamięci za pomocą danych przesłanych z poleceniami, a następnie dodasz lub zaktualizujesz dane (jednostki domeny) w bazie danych za pomocą transakcji.

Ważne jest, aby ponownie wyróżnić tylko jedno repozytorium dla każdego zagregowanego elementu głównego, jak pokazano na rysunku 7-17. Aby osiągnąć cel zagregowanego elementu głównego, aby zachować spójność transakcyjną między wszystkimi obiektami w ramach agregacji, nigdy nie należy tworzyć repozytorium dla każdej tabeli w bazie danych.

![Diagram przedstawiający relacje między domeną a inną infrastrukturą.](./media/infrastructure-persistence-layer-design/repository-aggregate-database-table-relationships.png)

**Rysunek 7-17**. Relacja między repozytoriami, agregacjami i tabelami baz danych

Na powyższym diagramie przedstawiono relacje między warstwami domeny i infrastruktury: agregacja kupująca zależy od IBuyerRepository, a agregacja kolejności zależy od interfejsów IOrderRepository, te interfejsy są zaimplementowane w warstwie infrastruktury przez odpowiednie repozytoria, które zależą od UnitOfWork, również zaimplementowane, które uzyskują dostęp do tabel w warstwie danych.

### <a name="enforce-one-aggregate-root-per-repository"></a>Wymuszaj jeden zagregowany element główny na repozytorium

Może być cenny do zaimplementowania projektu repozytorium w taki sposób, że wymusza regułę, że tylko agregowane elementy główne powinny mieć repozytoria. Można utworzyć typ repozytorium generycznego lub podstawowego, który ogranicza typ jednostek, z którymi współpracuje, aby upewnić się, że mają interfejs znacznika `IAggregateRoot`.

W ten sposób każda klasa repozytorium zaimplementowana w warstwie infrastruktury implementuje swój własny kontrakt lub interfejs, jak pokazano w poniższym kodzie:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Każdy interfejs określonego repozytorium implementuje ogólny interfejs IRepository:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Jednak lepszym sposobem zapewnienia, że kod wymusza Konwencję, że każde repozytorium jest powiązane z pojedynczą agregacją, ma na celu implementację ogólnego typu repozytorium. Dzięki temu jest to jawne, że używasz repozytorium, aby określić wartość zagregowaną. Można to łatwo zrobić przez implementację ogólnego `IRepository` interfejsu podstawowego, jak w poniższym kodzie:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Wzorzec repozytorium ułatwia testowanie logiki aplikacji

Wzorzec repozytorium umożliwia łatwe testowanie aplikacji za pomocą testów jednostkowych. Należy pamiętać, że testy jednostkowe tylko testują kod, a nie infrastruktury, więc abstrakcje repozytorium ułatwiają osiągnięcie tego celu.

Zgodnie z wcześniejszą sekcją zaleca się zdefiniowanie i umieszczenie interfejsów repozytorium w warstwie modelu domeny, tak aby warstwa aplikacji, taka jak mikrousługa internetowego interfejsu API, nie zależała bezpośrednio od warstwy infrastruktury, w której zostały zaimplementowane. rzeczywiste klasy repozytorium. Wykonując te czynności i korzystając z iniekcji zależności na kontrolerach internetowego interfejsu API, można zaimplementować repozytoria, które zwracają fałszywe dane zamiast danych z bazy danych. To rozdzielone podejście umożliwia tworzenie i uruchamianie testów jednostkowych, które koncentrują się na logice aplikacji, bez konieczności łączności z bazą danych.

Połączenia z bazami danych mogą zakończyć się niepowodzeniem i, co ważniejsze, uruchamianie setek testów względem bazy danych jest nieprawidłowe z dwóch powodów. Po pierwsze może zająć dużo czasu z powodu dużej liczby testów. Następnie rekordy bazy danych mogą ulec zmianie i mieć wpływ na wyniki testów, dzięki czemu mogą być niespójne. Testowanie bazy danych nie jest testem jednostkowym, ale testem integracji. Należy szybko uruchamiać wiele testów jednostkowych, ale mniej testów integracji z bazami danych.

W odniesieniu do separacji problemów testów jednostkowych, logika działa na jednostkach domeny w pamięci. Przyjęto założenie, że Klasa repozytorium dostarczyła te. Gdy logika modyfikuje jednostki domeny, zakłada, że Klasa repozytorium będzie je poprawnie przechowywać. Ważnym punktem jest utworzenie testów jednostkowych względem modelu domeny i jego logiki domeny. Zagregowane elementy główne są głównymi granicami spójności w DDD.

Repozytoria zaimplementowane w eShopOnContainers polegają EF Core na implementacji DbContext dla wzorców repozytorium i jednostki pracy przy użyciu modułu śledzącego zmiany, dzięki czemu nie duplikują tej funkcji.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Różnica między wzorcem repozytorium a wzorcem starszej klasy dostępu do danych (Klasa DAL)

Obiekt dostępu do danych bezpośrednio wykonuje operacje dostępu do danych i trwałości w odniesieniu do magazynu. Repozytorium oznacza dane z operacjami, które mają być wykonywane w pamięci jednostki obiektu pracy (jak w EF w przypadku używania klasy <xref:Microsoft.EntityFrameworkCore.DbContext>), ale te aktualizacje nie są natychmiast wykonywane do bazy danych.

Jednostka pracy jest określana jako pojedyncza transakcja, która obejmuje wiele operacji wstawiania, aktualizowania lub usuwania. W prostym przypadku oznacza to, że dla konkretnej akcji użytkownika, takiej jak rejestracja w witrynie sieci Web, wszystkie operacje wstawiania, aktualizowania i usuwania są obsługiwane w jednej transakcji. Jest to bardziej wydajne niż obsługa wielu transakcji bazy danych w chattier sposób.

Te wiele operacji trwałości są wykonywane później w ramach jednej akcji, gdy kod z warstwy aplikacji. Decyzja o stosowaniu zmian w pamięci do rzeczywistego magazynu bazy danych jest zwykle oparta na [wzorcu jednostki pracy](https://martinfowler.com/eaaCatalog/unitOfWork.html). W EF, wzorzec jednostki pracy jest implementowany jako <xref:Microsoft.EntityFrameworkCore.DbContext>.

W wielu przypadkach ten wzorzec lub sposób stosowania operacji do magazynu może zwiększyć wydajność aplikacji i ograniczyć możliwość niespójności. Powoduje także zmniejszenie blokowania transakcji w tabelach bazy danych, ponieważ wszystkie zamierzone operacje są zatwierdzane jako część jednej transakcji. Jest to bardziej wydajne w porównaniu do wykonywania wielu operacji izolowanych względem bazy danych. W związku z tym wybrany ORM może zoptymalizować wykonywanie względem bazy danych przez zgrupowanie kilku akcji aktualizacji w ramach tej samej transakcji, w przeciwieństwie do wielu małych i oddzielnych wykonań transakcji.

### <a name="repositories-shouldnt-be-mandatory"></a>Repozytoria nie powinny być obowiązkowe

Niestandardowe repozytoria są przydatne z przyczyn pożądanych wcześniej, a to podejście do mikrousługi porządkowania w eShopOnContainers. Nie jest to jednak zasadniczy wzór do zaimplementowania w projekcie DDD, a nawet w ogólnym opracowaniu platformy .NET.

Na przykład Jimmy Bogard, podczas przekazywania bezpośredniej opinii dla tego przewodnika, w następujący sposób:

> Prawdopodobnie to największa opinia. Nie jestem wentylatorem dla repozytoriów, głównie ponieważ ukrywają one ważne informacje o podstawowym mechanizmie trwałości. To dlatego, że jest to tylko MediatR dla poleceń. Mogę użyć pełnej mocy warstwy trwałości i wypchnąć wszystkie takie zachowanie domeny do moich zagregowanych elementów głównych. Zazwyczaj nie chcę zasymulować moich repozytoriów — nadal muszę mieć test integracji z rzeczywistym użyciem. Dzięki temu CQRS się, że nie mamy jeszcze potrzeby dla repozytoriów.

Repozytoria mogą być przydatne, ale nie są krytyczne dla Twojego projektu DDD, w sposób, w jaki wzorzec agregacji i bogaty model domeny są. W związku z tym użyj wzorca repozytorium lub nie, tak jak jest to możliwe. Mimo to będziesz używać wzorca repozytorium za każdym razem, gdy używasz EF Core, chociaż w tym przypadku repozytorium obejmuje całą mikrousługę lub ograniczony kontekst.

## <a name="additional-resources"></a>Dodatkowe zasoby

### <a name="repository-pattern"></a>Wzorzec repozytorium

- **Wzorzec repozytorium** \
  <https://deviq.com/repository-pattern/>

- **Edward Hieatt i Rob Me. Wzorzec repozytorium.** \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **Wzorzec repozytorium** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans. Projektowanie oparte na domenie: zapełnianie złożoności w oprogramowaniu.** (Książka; zawiera omówienie wzorca repozytorium) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Wzorzec jednostki pracy

- **Fowlera Martin. Wzorzec jednostki pracy.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **Implementowanie wzorców repozytorium i jednostki pracy w aplikacji ASP.NET MVC** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Poprzedni](domain-events-design-implementation.md)
>[Następny](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
