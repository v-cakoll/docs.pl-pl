---
title: "Implementowanie odczyty/kwerendy w mikrousługi CQRS"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie odczyty/kwerendy w mikrousługi CQRS"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e017aaaa701d8033110be8d6244d3e1120fc4fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>Implementowanie odczyty/kwerendy w mikrousługi CQRS

Odczyty/zapytań porządkowania mikrousługi z aplikacji odwołanie eShopOnContainers implementuje zapytania niezależnie od DDD modelu i obszar transakcyjnych. Wykonano głównie, ponieważ znacząco różnią wymagań dla zapytań i transakcji. Zapisy wykonania transakcji, które muszą być zgodne z logiką domeny. Z drugiej strony, zapytania, są idempotentności i być rozdzielone od zasad domeny.

Podejście jest proste, jak pokazano na rysunku 9-3. Interfejs API zaimplementowano przez kontrolery interfejsu API sieci Web przy użyciu dowolnej infrastruktury (na przykład micro ORM, takich jak Dapper) i zwracanie dynamiczne ViewModels w zależności od potrzeb aplikacji interfejsu użytkownika.

![](./media/image3.png)

**Rysunek 9-3**. Najprostsza metoda zapytań w mikrousługi CQRS

Jest to najprostsza metoda możliwe w dla zapytań. Definicje kwerendy w bazie danych i zwracać dynamiczne ViewModel, oparty na bieżąco dla każdego zapytania. Ponieważ zapytania są idempotentności, nie zmieni ich danych niezależnie od tego, ile razy wykonywania zapytania. W związku z tym nie trzeba być ograniczone przez dowolnego wzorzec DDD używany po stronie transakcyjnych, takie jak wartości zagregowanych i innych wzorcach i dlatego zapytania są oddzielone od obszaru transakcyjnych. Po prostu zapytania do bazy danych, która wymaga interfejsu użytkownika i zwracać ViewModel dynamiczne, które muszą być statycznie zdefiniowany dowolnego miejsca (nie klasy dla ViewModels) z wyjątkiem w instrukcji SQL, samodzielnie.

Ponieważ jest to prosty podejście, kod wymagany dla strony zapytania (takich jak kodu za pomocą micro, takich jak ORM [Dapper](https://github.com/StackExchange/Dapper)) może być zaimplementowany [w tym samym projekcie interfejsu API sieci Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Na rysunku 9-4 przedstawiono to. Zapytania są definiowane w **Ordering.API** mikrousługi projektu w ramach rozwiązania eShopOnContainers.

![](./media/image4.png)

**Rysunek 9-4**. Zapytania w mikrousługi porządkowanie w eShopOnContainers

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Przy użyciu ViewModels celowo dla aplikacji klienta, niezależnie od ograniczeń modelu domeny

Ponieważ zapytania są wykonywane do uzyskiwania danych wymaganych przez aplikacje klienckie, zwrócony typ można w szczególności wprowadzone dla klientów, na podstawie danych zwróconych przez zapytania. Te modele lub obiekty Transfer danych (DTOs), są nazywane ViewModels.

Zwrócone dane (ViewModel) może być wynikiem sprzężenia danych z wielu obiektów lub tabele w bazie danych, lub nawet Agreguje wiele zdefiniowanych w modelu domeny dla transakcyjnego obszaru. W takim przypadku ponieważ tworzenia kwerend niezależnie od modelu domeny, agregacje granic i ograniczenia całkowicie są ignorowane, a wolnych do badania żadnych tabel i kolumn, który może być konieczne. Ta metoda zapewnia dużą elastyczność i wydajność dla deweloperów, tworzenie lub aktualizowanie zapytań.

ViewModels może być statyczne typy zdefiniowane w klasach. Lub też można tworzyć dynamicznie na podstawie kwerend wykonywana (jak jest implementowane w porządkowania mikrousługi), który jest bardzo elastyczne dla deweloperów.

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>Przy użyciu Dapper jako micro ORM do wykonywania zapytań 

Podczas wykonywania zapytań, można użyć dowolnego micro ORM, Entity Framework Core lub nawet zwykły ADO.NET. W przykładowej aplikacji do porządkowania mikrousługi w eShopOnContainers jako przykład popularnych ORM micro wybrano Dapper. Można go uruchomić zwykły kwerend SQL o bardzo dużej wydajności, ponieważ jest bardzo małe framework. Dapper można napisać zapytanie SQL, które mogą uzyskać dostęp i dołączyć wiele tabel.

Dapper jest projekt typu open source (utworzony przez Sam szafran oryginału) i jest częścią bloki konstrukcyjne, używane w [przepełnienie stosu](https://stackoverflow.com/). Aby użyć Dapper, wystarczy zainstalować go za pomocą [pakietu Dapper NuGet](https://www.nuget.org/packages/Dapper), jak pokazano na poniższej ilustracji.

![](./media/image5.png)

Należy również dodać za pomocą instrukcji tak kod ma dostęp do metody Dapper rozszerzenia.

Użycie Dapper w kodzie, możesz bezpośrednio użyć dostępne w przestrzeni nazw System.Data.SqlClient klasy SqlClient. Za pomocą metody QueryAsync i innych metod rozszerzenia, które rozszerza klasy SqlClient można po prostu uruchamianie zapytań w sposób prosty i wydajność.

## <a name="dynamic-and-static-viewmodels"></a>ViewModels dynamiczną i statyczną

Jak pokazano w poniższym kodzie z porządkowania mikrousługi, większość ViewModels zwrócony przez zapytania są zaimplementowane jako *dynamiczne*. Oznacza to, że podzbiór atrybutów, które mają być zwracane jest oparty na samą kwerendę. Po dodaniu nowej kolumny do zapytania, lub Dołącz do tych danych jest dynamicznie dodawane do zwrócony ViewModel. Takie podejście zmniejsza potrzebę modyfikowania zapytań w odpowiedzi na aktualizacje odpowiedni model danych, co ta podejście do projektowania, elastyczne i bardziej odporne na przyszłe zmiany.

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
@"SELECT o.[Id] as ordernumber,
o.[OrderDate] as [date],os.[Name] as [status],
SUM(oi.units*oi.unitprice) as total
FROM [ordering].[Orders] o
LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
  }
}
```

Istotne jest, czy przy użyciu typu dynamicznego, zwracane zbierania danych będzie można dynamicznie złożonego jako ViewModel.

Dla większości zapytań nie trzeba wstępnie DTO lub ViewModel klasy, co sprawia, że ich kodowania proste i produktywności. Można jednak wstępnie ViewModels (na przykład wstępnie zdefiniowanych DTOs), jeśli chcesz mieć ViewModels z bardziej ograniczony w definicji jako umów.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman. Punkty danych - Dapper, Entity Framework i aplikacji hybrydowych (artykuł MSDN Mag.)**

    *https://msdn.microsoft.com/en-us/Magazine/mt703432.aspx*


>[!div class="step-by-step"]
[Poprzednie] (eshoponcontainers-cqrs-ddd-microservice.md) [dalej] (ddd ukierunkowane microservice.md)
