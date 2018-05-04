---
title: SqlClient Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: 159cada00c523a1b417f5c6f4d0fac43a80f5db9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="sqlclient-for-the-entity-framework"></a>SqlClient Entity Framework
W tej sekcji opisano dostawcy danych programu .NET Framework dla programu SQL Server (SqlClient), dzięki czemu Entity Framework do pracy za pośrednictwem programu Microsoft SQL Server.  
  
## <a name="provider-schema-attribute"></a>Atrybut schematu dostawcy  
 `Provider` atrybut `Schema` elementu w języku definicji schematu magazynu (SSDL).  
  
 Użyj SqlClient, należy przypisać do ciągu "System.Data.SqlClient" `Provider` atrybutu `Schema` elementu.  
  
## <a name="providermanifesttoken-schema-attribute"></a>Atrybut schematu ProviderManifestToken  
 `ProviderManifestToken` Wymagany atrybut `Schema` elementu w pliku SSDL. Token ten jest używany załadować manifestu dostawcy dla scenariuszy w trybie offline. Aby uzyskać więcej informacji na temat `ProviderManifestToken` atrybutów, zobacz [elementu schematu (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222).  
  
 Klient SQL może służyć jako dostawca danych dla różnych wersji programu SQL Server. Te wersje są dostępne różne możliwości. Na przykład [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] nie obsługuje `varchar(max)` i `nvarchar(max)` typy, które zostały wprowadzone w programie [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].  
  
 SqlClient tworzy i przyjmuje następujące dostawcy tokenów manifestu dla różnych wersji programu SQL Server.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
>  Począwszy od programu Visual Studio 2010, [narzędzi modelu danych jednostki ADO.NET](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) nie obsługują programu SQL Server 2000.  
  
## <a name="provider-namespace-name"></a>Nazwa dostawcy Namespace  
 Wszystkich dostawców musi określać przestrzeń nazw. Ta właściwość określa, że Entity Framework, które prefiks jest używany przez dostawcę dla określonych elementów składowych, takich jak typy i funkcje. Przestrzeń nazw dla manifestów dostawca SqlClient jest `SqlServer`. Aby uzyskać więcej informacji na temat obszarów nazw, zobacz [przestrzeni nazw](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Types  
 Dostawca SqlClient Entity Framework udostępnia informacje dotyczące mapowania między typami w modelu koncepcyjnym i typów programu SQL Server. Aby uzyskać więcej informacji, zobacz [SqlClient dla jednostki FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>Funkcje  
 Dostawca SqlClient Entity Framework definiuje listę funkcje obsługiwane przez dostawcę. Aby uzyskać listę obsługiwanych funkcji, zobacz [SqlClient Entity Framework funkcji](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Klient SQL dla funkcji programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Klient SQL dla typów programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Znane problemy klienta SQL dla programu Entity Framework](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Jednostki języka SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Dokumentacja języka](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [Znane problemy w programie dostawca SqlClient Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
