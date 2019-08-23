---
title: Element SqlClient programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: ec67637c416f2560c1f5d0a9fd0e856703820a84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954970"
---
# <a name="sqlclient-for-the-entity-framework"></a>Element SqlClient programu Entity Framework
W tej sekcji opisano Dostawca danych .NET Framework dla SQL Server (SqlClient), co umożliwia Entity Framework pracy nad Microsoft SQL Server.  
  
## <a name="provider-schema-attribute"></a>Atrybut schematu dostawcy  
 `Provider`jest atrybutem `Schema` elementu w języku definicji schematu magazynu (SSDL).  
  
 Aby użyć programu SqlClient, przypisz ciąg "System. Data. SqlClient" do `Provider` atrybutu `Schema` elementu.  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken — atrybut schematu  
 `ProviderManifestToken`jest wymaganym atrybutem `Schema` elementu w SSDL. Ten token służy do ładowania manifestu dostawcy dla scenariuszy w trybie offline. Aby uzyskać więcej informacji `ProviderManifestToken` o atrybutach, zobacz [Schema element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).  
  
 Klient SQL może być używany jako dostawca danych dla różnych wersji SQL Server. Wersje te mają różne możliwości. Na przykład SQL Server 2000 nie obsługuje `varchar(max)` i `nvarchar(max)` typów, które zostały wprowadzone w SQL Server 2005.  
  
 Klient SqlClient tworzy i akceptuje następujące tokeny manifestu dostawcy dla różnych wersji SQL Server.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
> Począwszy od programu Visual Studio 2010 [narzędzia ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) nie obsługują SQL Server 2000.  
  
## <a name="provider-namespace-name"></a>Nazwa przestrzeni nazw dostawcy  
 Wszyscy dostawcy muszą określać przestrzeń nazw. Ta właściwość informuje Entity Framework którego prefiks jest używany przez dostawcę dla określonych konstrukcji, takich jak typy i funkcje. Przestrzeń nazw manifestów dostawcy SqlClient ma wartość `SqlServer`. Aby uzyskać więcej informacji na temat przestrzeni nazw, zobacz [przestrzenie nazw](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Types  
 Dostawca SqlClient dla Entity Framework zawiera informacje dotyczące mapowania między typami modeli koncepcyjnych a typami SQL Server. Aby uzyskać więcej informacji, zobacz [SqlClient for Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>Funkcje  
 Dostawca SqlClient dla Entity Framework definiuje listę funkcji obsługiwanych przez dostawcę. Listę obsługiwanych funkcji można znaleźć [w temacie SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Klient SQL dla funkcji programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Klient SQL dla typów programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Znane problemy klienta SQL dla programu Entity Framework](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Zobacz także

- [Jednostki języka SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Dokumentacja języka](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [Znane problemy w dostawcy SqlClient dla Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
