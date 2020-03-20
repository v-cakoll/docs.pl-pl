---
title: 'Instrukcje: Określanie parametrów połączenia'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150574"
---
# <a name="how-to-define-the-connection-string"></a>Instrukcje: Określanie parametrów połączenia

W tym temacie pokazano, jak zdefiniować ciąg połączenia, który jest używany podczas łączenia się z modelem koncepcyjnym. Ten temat jest oparty na modelu koncepcyjnym [AdventureWorks Sales.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) Model sprzedaży AdventureWorks jest używany we wszystkich tematach związanych z zadaniami w dokumentacji entity framework. W tym temacie przyjęto założenie, że już skonfigurowano platformę encji i zdefiniowano model sprzedaży AdventureWorks. Aby uzyskać więcej informacji, zobacz [Jak: Ręczne definiowanie plików modelu i mapowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Procedury opisane w tym temacie znajdują się również w temacie [Jak: Ręczne konfigurowanie projektu struktury encji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Jeśli używasz Kreatora modelu danych jednostki w projekcie programu Visual Studio, automatycznie generuje plik .edmx i konfiguruje projekt do korzystania z entity framework. Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

## <a name="to-define-the-entity-framework-connection-string"></a>Aby zdefiniować parametry połączenia programu Entity Framework

- Otwórz plik konfiguracji aplikacji projektu (app.config) i dodaj następujący parametry połączenia:

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Jeśli projekt nie ma pliku konfiguracji aplikacji, można go dodać, wybierając **polecenie Dodaj nowy element** z menu **Projekt,** wybierając kategorię **Ogólne,** wybierając pozycję **Plik konfiguracji aplikacji,** a następnie klikając przycisk **Dodaj**.

## <a name="see-also"></a>Zobacz też

- [Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Jak: Tworzenie nowego pliku .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [Narzędzia ADO.NET modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
