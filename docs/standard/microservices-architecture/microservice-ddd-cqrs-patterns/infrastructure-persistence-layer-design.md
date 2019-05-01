---
title: Projektowanie warstwy trwałości infrastruktury
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Zapoznaj się z wzorca repozytorium w projekcie warstwy trwałości infrastruktury.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 3e9c2ce0a332351f136dcd4dcb6d3da4f794a1eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019779"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Projektowanie warstwy trwałości infrastruktury

Składniki trwałości danych zapewniają dostęp do danych hostowanej w granicach mikrousługi (czyli mikrousług database). Zawierają one rzeczywiste wdrożenie składników, takich jak repozytoria i [jednostki pracy](https://martinfowler.com/eaaCatalog/unitOfWork.html) klasy, takie jak niestandardowe Entity Framework (EF) <xref:Microsoft.EntityFrameworkCore.DbContext> obiektów. Kontekst DbContext EF implementuje, repozytorium i wzorce jednostki pracy.

## <a name="the-repository-pattern"></a>Wzorzec repozytorium

Repozytoria są klasy lub składniki, które hermetyzują logikę wymaganą dostęp do źródeł danych. One scentralizować typowych funkcji dostępu do danych, zapewniając lepsze łatwość konserwacji i oddzielenie infrastruktury lub technologii dostępu do baz danych w warstwie modelu domeny. Jeśli używasz obiektowo-relacyjny mapowania (ORM) takich jak Entity Framework, kod, który musi zostać wdrożone zostało uproszczone dzięki LINQ i silne wpisywanie. To umożliwia użytkownikowi skupienie się na logice trwałość danych, a nie dane dostępu nadmiar.

Wzorzec repozytorium jest dobrze udokumentowana sposób pracy ze źródłem danych. W książce [wzorców Enterprise Architektura aplikacji](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martina Fowlera opisuje repozytorium w następujący sposób:

> Repozytorium wykonuje zadania pośrednik między warstwami modelu domeny i mapowanie danych działające w sposób podobny do zestawu obiektów domeny w pamięci. Obiekty klienta deklaratywne tworzenie zapytań i wysyłać je do repozytoriów dla odpowiedzi. Model repozytorium hermetyzuje zestaw obiektów przechowywanych w bazie danych i operacje, które można wykonywać na nich dzięki czemu zbliżonej do warstwy trwałości. Repozytoriów, obsługuje również celem oddzielenie wyraźnie, jak i w jednym kierunku zależności między domeną pracy i przydział danych lub mapowania.

### <a name="define-one-repository-per-aggregate"></a>Zdefiniuj jedno repozytorium na agregacji

Dla każdego głównego agregacji lub agregacji należy utworzyć jedną klasę repozytorium. W oparciu o wzorce projektowania driven wyznaczenie mikrousłudze oraz tylko kanału, który należy używać do aktualizacji bazy danych powinna być repozytoriów. Jest tak, ponieważ mają one relację jeden do jednego z głównego agregacji, określający invariants agregacji i poziomu spójności transakcyjnej. Można wykonywać zapytania bazy danych za pośrednictwem innych kanałów (jak następujące podejście CQRS), ponieważ zapytania nie zmienia stanu bazy danych. Jednak obszar transakcyjna (aktualizacje) zawsze muszą być kontrolowane przez repozytoriów i agregacji katalogów głównych.

Repozytorium można po prostu wprowadź dane w pamięci, który pochodzi z bazy danych w postaci jednostki domeny. Gdy jednostki są w pamięci, można je zmienić i następnie utrwalone w bazie danych za pomocą transakcji.

Jak wspomniano wcześniej, jeśli używasz to wzorzec architektoniczny CQS/CQRS, początkowego zapytania są wykonywane przez zapytania po stronie poza model domeny, wykonywane przez proste instrukcje SQL, używając z programem Dapper. To podejście jest znacznie większą elastycznością niż repozytoriów, ponieważ można wykonywać zapytania i Dołącz do żadnych tabel należy, a te zapytania nie są ograniczone przez zasady z wartości zagregowanych. Tych danych jest przesyłany do aplikacji klienta lub warstwy prezentacji.

Jeśli użytkownik wprowadzi zmiany, zaktualizowanie danych pochodzi z warstwy prezentacji lub aplikacji klienta do warstwy aplikacji (na przykład usługi interfejsu API sieci Web). Po wyświetleniu polecenia programu obsługi poleceń użyjesz repozytoriów można pobrać dane, które chcesz zaktualizować z bazy danych. Należy je zaktualizować w pamięci z danymi przekazaną za pomocą polecenia, a następnie dodania lub zaktualizowania danych (jednostki domeny), która znajduje się w bazie danych za pomocą transakcji.

Należy ponownie podkreślić, należy zdefiniować tylko jedno repozytorium dla każdego katalogu głównego agregacji, jak pokazano na rysunku 7-17. Aby osiągnąć głównego agregacji do zapewniania spójności transakcyjnej między wszystkie obiekty w agregacji, nigdy nie należy utworzyć repozytorium dla każdej tabeli w bazie danych.

![Relacje między warstwami domeny i infrastruktury: Kupujący agregacji jest zależna od IBuyerRepository i kolejności agregacji jest zależna od interfejsów IOrderRepository, te interfejsy są implementowane w warstwie infrastruktury przez odpowiednie repozytoria, które są zależne od UnitOfWork, również implementowany które uzyskuje dostęp do tabel w warstwie danych.](./media/image18.png)

**Rysunek 7-17**. Relacja między repozytoriami, agregacje i tabel bazy danych

### <a name="enforce-one-aggregate-root-per-repository"></a>Wymuszanie jeden główny agregacji na repozytorium

Może być przydatne do zaimplementowania projektu repozytorium w taki sposób, że wymusza reguły, że tylko katalogi główne agregacji powinny mieć repozytoriów. Można utworzyć typu ogólnego lub podstawowego repozytorium, który ogranicza typu jednostek współpracuje z, aby zapewnić `IAggregateRoot` interfejs znacznika.

W związku z tym każda klasa repozytorium zaimplementowane w warstwie infrastruktury implementuje własne umowy lub interfejsu, jak pokazano w poniższym kodzie:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Każdy interfejs danego repozytorium implementuje interfejs ogólny IRepository:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

Jednak lepszy sposób kod wymuszanie Konwencji każdego repozytorium dotyczy jednej wartości zagregowanej jest zaimplementowanie typu ogólnego repozytorium. W ten sposób jest jawne, że używasz repozytorium pod kątem określonych agregacji. Można to łatwo zrobić poprzez implementację ogólnego `IRepository` interfejs podstawowy, jak w poniższym kodzie:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>Wzorzec repozytorium ułatwia testowanie logika aplikacji

Wzorca repozytorium umożliwia łatwe testowanie aplikacji przy użyciu testów jednostkowych. Należy pamiętać, testy jednostkowe tylko przetestować Twojego kodu, nie infrastruktury, więc abstrakcje repozytorium ułatwiają osiągnięcia tego celu.

Jak wspomniano w sekcji wcześniej, zalecane jest definiowanie i umieścić interfejsów repozytorium w warstwie modelu domeny dzięki warstwy aplikacji, takich jak usługi mikrousług interfejsu API sieci Web nie są zależne bezpośrednio na warstwie infrastruktury gdzie zastało zaimplementowane klasy rzeczywiste repozytorium. W ten sposób i z użyciem iniekcji zależności kontrolery interfejsu API sieci Web, można zaimplementować makiety repozytoria, które zwracają dane fikcyjne zamiast danych z bazy danych. To podejście rozdzielony umożliwia tworzenie i Uruchamianie testów jednostkowych, które koncentrują się logiki aplikacji bez konieczności łączność z bazą danych.

Połączenia z bazami danych może zakończyć się niepowodzeniem, a co ważniejsze, uruchomienie setek testy względem bazy danych jest zła dwóch powodów. Po pierwsze może potrwać dłuższy czas z powodu dużej liczby testów. Po drugie rekordów bazy danych może zmienić i wpłynąć na wyniki testów, tak aby nie są zgodne. Testowanie w bazie danych nie jest test jednostkowy, ale wiąże się test integracji. Powinny mieć wiele testów jednostkowych szybkiego uruchamiania, ale integracja mniejszą liczbę testów względem bazy danych.

Pod względem separacji dla testów jednostkowych logika działa na jednostkach domeny w pamięci. Założono, że klasa repozytorium dostarczał te. Gdy logika modyfikuje jednostki domeny, przyjęto założenie, że klasa repozytorium zapisze je poprawnie. Istotną kwestią jest tworzenie testów jednostkowych dla modelu domeny i jej logiki domeny. Katalogi główne agregacji są granice spójności głównego w DDD.

Repozytoria zaimplementowane w ramach aplikacji eShopOnContainers zależy od programu EF Core DbContext implementacji wzorców repozytorium i jednostki pracy przy użyciu jego śledzenie zmian, więc one nie Duplikuj tę funkcję.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>Różnica między wzorca repozytorium i starszych wzorzec dostępu do danych w klasą (DAL)

Obiekt dostępu do danych bezpośrednio wykonuje operacje dostępu i trwałość magazynu danych. Repozytorium oznacza dane za pomocą operacji do wykonania w pamięci jednostkę, obiektu pracy (jak EF, korzystając z <xref:Microsoft.EntityFrameworkCore.DbContext> klasy), ale te aktualizacje nie są wykonywane bezpośrednio w bazie danych.

Jednostka pracy jest określany jako jedna transakcja, która obejmuje wiele wstawiania, aktualizowania lub usuwania operacji. Mówiąc najprościej oznacza to, że dla określonego użytkownika akcji, takich jak rejestracja w witrynie sieci Web, insert, update i operacje usuwania są obsługiwane w ramach jednej transakcji. Jest to bardziej wydajne niż Obsługa wielu transakcji bazy danych w sposób chattier.

Te wiele operacji trwałości są wykonywane później w ramach jednej akcji podczas polecenia kodu z warstwy aplikacji. Decyzja o zastosowanie zmian w pamięci do przechowywania bazy danych zazwyczaj opiera się na [wzorzec jednostki pracy](https://martinfowler.com/eaaCatalog/unitOfWork.html). W programie EF, wzorzec jednostki pracy jest implementowany jako <xref:Microsoft.EntityFrameworkCore.DbContext>.

W wielu przypadkach ten wzorzec lub sposób stosowania operacji wykonywanych przy użyciu magazynu, można zwiększyć wydajność aplikacji i zmniejszyć ryzyko wystąpienia niespójności. Zmniejsza to także transakcji blokowania w tabelach bazy danych, ponieważ wszystkie operacje zamierzony są zatwierdzone w ramach jednej transakcji. Jest to bardziej wydajne w porównaniu do wykonywania wielu izolowanym operacji w bazie danych. W związku z tym wybranych ORM można zoptymalizować wykonywania w bazie danych za pomocą grupowania kilka akcji aktualizacji w ramach tej samej transakcji, w przeciwieństwie do wielu małych, jak i oddzielnych transakcji wykonań.

### <a name="repositories-shouldnt-be-mandatory"></a>Repozytoria nie powinien być obowiązkowe

Niestandardowe repozytoria są przydatne z powodów wymienionych wcześniej, a to podejście do szeregowania mikrousługi w ramach aplikacji eShopOnContainers. Jednak nie jest istotne wzorzec można zaimplementować w projektowania DDD, a nawet ogólnie rzecz biorąc programowanie na platformie .NET.

Na przykład Jimmy Bogard, podczas dostarczania informacji zwrotnych w tym przewodniku powiedział następujące czynności:

> Będzie to prawdopodobnie największy opinii. Tak naprawdę nie mam wentylator repozytoriów, przede wszystkim, ponieważ ukrywają ważnych szczegółów podstawowego mechanizmu stanu trwałego. Jego Dlaczego mam szukać MediatR poleceń, zbyt. Czy mogę używać pełnych możliwości warstwy trwałości i wypychanie tego zachowania domeny do mojego agregacji katalogów głównych. Zazwyczaj nie powinny się testowanie moich repozytoriów — muszę mieć integrację testu za pomocą czegoś. Przechodząc CQRS przeznaczone nie naprawdę się na potrzeby repozytoriów więcej.

Repozytoria mogą być przydatne, ale nie są one krytyczny dla projektu DDD w taki sposób, że wzorzec agregacji i model domeny zaawansowane są. W związku z tym Użyj wzorca repozytorium, czy nie, wedle uznania. Mimo to będzie można za pomocą wzorca repozytorium zawsze, gdy używasz programu EF Core, chociaż w tym przypadku repozytorium obejmuje cały mikrousług lub ograniczony kontekst.

## <a name="additional-resources"></a>Dodatkowe zasoby

### <a name="repository-pattern"></a>Wzorzec repozytorium

- **Wzorzec repozytorium** \
  <https://deviq.com/repository-pattern/>

- **Edward Hieatt i Rob mnie. Wzorzec repozytorium.** \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **Wzorzec repozytorium** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans. Projektowania opartego na domenie: Co dzień do czynienia złożoności serce oprogramowania.** (Zarezerwuj; zawiera omówienie wzorca repozytorium) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Jednostka wzorzec pracy

- **Martin Fowler. Jednostka wzorzec pracy.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **Wdrażanie z repozytorium i jednostki pracy w aplikacji ASP.NET MVC** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Poprzednie](domain-events-design-implementation.md)
>[dalej](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
