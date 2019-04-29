---
title: 'Instrukcje: Określanie parametrów połączenia'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 7fb722acbb13b3502d004978581701cc70118ff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606113"
---
# <a name="how-to-define-the-connection-string"></a>Instrukcje: Określanie parametrów połączenia

W tym temacie pokazano, jak zdefiniować parametry połączenia, który jest używany podczas nawiązywania połączenia z modelu koncepcyjnego. Ten temat opiera się na [sprzedaży AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) modelu koncepcyjnego. W całym tematy związane z zadaniem używany jest Model sprzedaż AdventureWorks [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentacji. W tym temacie założono, że użytkownik skonfigurował już [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i zdefiniowane AdventureWorks Sales Model. Aby uzyskać więcej informacji, zobacz [jak: Ręcznie zdefiniować modelu i mapowania plików](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Procedury przedstawione w tym temacie znajdują się również w [jak: Ręczne konfigurowanie projektu programu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Jeśli używasz [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] kreatora w projekcie programu Visual Studio automatycznie generuje plik edmx i konfiguruje projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreator modelu Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

## <a name="to-define-the-entity-framework-connection-string"></a>Aby zdefiniować parametry połączenia programu Entity Framework

- Otwórz plik konfiguracji aplikacji projektu (app.config) i dodaj następujące parametry połączenia:

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Jeśli projekt nie ma pliku konfiguracji aplikacji, możesz dodać kategorię, wybierając **Dodaj nowy element** z **projektu** menu, wybierając **ogólne** kategorii Wybieranie **pliku konfiguracji aplikacji**, a następnie klikając polecenie **Dodaj**.

## <a name="see-also"></a>Zobacz także

- [Szybki start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Instrukcje: Utwórz nowy plik edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [Narzędzia do modelu danych jednostki ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
