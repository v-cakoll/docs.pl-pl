---
title: 'Instrukcje: Określanie parametrów połączenia'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: a78158c7553c0b479b935e3b94931313df912c2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854658"
---
# <a name="how-to-define-the-connection-string"></a>Instrukcje: Określanie parametrów połączenia

W tym temacie przedstawiono sposób definiowania parametrów połączenia, które są używane podczas nawiązywania połączenia z modelem koncepcyjnym. Ten temat jest oparty na modelu koncepcyjnym [sprzedaży AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) . Model sprzedaży AdventureWorks jest używany w całym temacie tematy związane z zadaniami w dokumentacji Entity Framework. W tym temacie założono, że skonfigurowano już Entity Framework i zdefiniowano model sprzedaży AdventureWorks. Aby uzyskać więcej informacji, zobacz [jak: Ręcznie zdefiniuj model i pliki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))mapowania. Procedury opisane w tym temacie są również dołączone [do: Ręcznie skonfiguruj projekt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))Entity Framework.

> [!NOTE]
> W przypadku używania Kreatora Entity Data Model w projekcie programu Visual Studio program automatycznie generuje plik. edmx i konfiguruje projekt do korzystania z Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z Kreatora Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

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
- [Instrukcje: Utwórz nowy plik. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
