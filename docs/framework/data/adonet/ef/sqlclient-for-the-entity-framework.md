---
title: Element SqlClient programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: d81499961e7e47bba3b2594ddddd192c87a4a936
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195465"
---
# <a name="sqlclient-for-the-entity-framework"></a>Element SqlClient programu Entity Framework
W tej sekcji opisano .NET Framework Data Provider for SQL Server (SqlClient), co umożliwia Entity Framework do pracy za pośrednictwem programu Microsoft SQL Server.  
  
## <a name="provider-schema-attribute"></a>Provider Schema Attribute  
 `Provider` jest to atrybut `Schema` element język definicji schematu magazynu (SSDL).  
  
 Użyj SqlClient, należy przypisać do ciągu "System.Data.SqlClient" `Provider` atrybutu `Schema` elementu.  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken Schema Attribute  
 `ProviderManifestToken` Wymagany atrybut `Schema` element SSDL. Ten token służy do ładowania manifestu dostawcy dla scenariuszy w trybie offline. Aby uzyskać więcej informacji na temat `ProviderManifestToken` atrybutów, zobacz [elementu schematu (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).  
  
 Klient SQL może służyć jako dostawca danych dla różnych wersji programu SQL Server. Te wersje mają różne możliwości. Na przykład [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] nie obsługuje `varchar(max)` i `nvarchar(max)` typy, które zostały wprowadzone w programie [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].  
  
 Klient SQL tworzy i akceptuje następujące tokeny manifestu dostawcy dla różnych wersji programu SQL Server.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
>  Począwszy od programu Visual Studio 2010, [narzędzia modelu danych jednostki ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) nie obsługują programu SQL Server 2000.  
  
## <a name="provider-namespace-name"></a>Nazwa Namespace dostawcy  
 Wszyscy dostawcy należy określić przestrzeni nazw. Ta właściwość zawiera informacje dla programu Entity Framework, który prefiks jest używany przez dostawcę dla określonego konstrukcji, takich jak typy i funkcje. Przestrzeń nazw dla manifestów dostawcy SqlClient jest `SqlServer`. Aby uzyskać więcej informacji na temat przestrzenie nazw, zobacz [przestrzenie nazw](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Types  
 Dostawcy SqlClient programu Entity Framework zawiera informacje dotyczące mapowania między typami modelu koncepcyjnego i typów programu SQL Server. Aby uzyskać więcej informacji, zobacz [SqlClient dla typów programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>Funkcje  
 Dostawcy SqlClient programu Entity Framework definiuje listę funkcji obsługiwanych przez dostawcę. Aby uzyskać listę obsługiwanych funkcji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Klient SQL dla funkcji programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Klient SQL dla typów programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Znane problemy klienta SQL dla programu Entity Framework](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Zobacz także

- [Język Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Dokumentacja języka](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [Znane problemy w dostawcy SqlClient programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
