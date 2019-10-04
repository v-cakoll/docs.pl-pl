---
title: 'Instrukcje: Definiowanie parametrów połączenia'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9ce0b427cac17fc338877c5f85d3648d15d5ee14
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833952"
---
# <a name="how-to-define-the-connection-string"></a>Instrukcje: Definiowanie parametrów połączenia

W tym temacie przedstawiono sposób definiowania parametrów połączenia, które są używane podczas nawiązywania połączenia z modelem koncepcyjnym. Ten temat jest oparty na modelu koncepcyjnym [sprzedaży AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) . Model sprzedaży AdventureWorks jest używany w całym temacie tematy związane z zadaniami w dokumentacji Entity Framework. W tym temacie założono, że skonfigurowano już Entity Framework i zdefiniowano model sprzedaży AdventureWorks. Aby uzyskać więcej informacji, zobacz [jak: ręcznie zdefiniować model i pliki mapowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Procedury opisane w tym temacie są również dołączone [do: ręczne Konfigurowanie projektu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> W przypadku używania Kreatora Entity Data Model w projekcie programu Visual Studio program automatycznie generuje plik. edmx i konfiguruje projekt do korzystania z Entity Framework. Aby uzyskać więcej informacji, zobacz [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

## <a name="to-define-the-entity-framework-connection-string"></a>Aby zdefiniować Entity Framework parametry połączenia

- Otwórz plik konfiguracji aplikacji projektu (App. config) i Dodaj następujące parametry połączenia:

```xml
<connectionStrings>
    <add name="AdventureWorksEntities" 
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Jeśli projekt nie ma pliku konfiguracji aplikacji, można go dodać, wybierając pozycję **Dodaj nowy element** z menu **projekt** , wybierając kategorię **Ogólne** , wybierając **plik konfiguracji aplikacji**, a następnie klikając polecenie **Dodaj**.

## <a name="see-also"></a>Zobacz także

- [Szybki start](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Instrukcje: Tworzenie nowego pliku. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
