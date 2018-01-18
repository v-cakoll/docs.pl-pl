---
title: Klient SQL dla FrameworkTypes jednostki
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 50898395dcba9e33544cae63208b352c7a6fb6f4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Klient SQL dla FrameworkTypes jednostki
Dostawcy danych programu .NET Framework dla pliku manifestu dostawcy programu SQL Server (SqlClient) zawiera listę dostawcy typów pierwotnych aspektów dla każdego typu mapowania między koncepcyjnej i typów pierwotnych modelu magazynu, a podwyższenia poziomu i konwersji reguły między typów pierwotnych modelu koncepcyjnego i magazynu.  
  
 W poniższej tabeli opisano typy programu SQL Server 2008 [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], i [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] baz danych i sposób mapowania koncepcyjnego do tych typów wzór typów. Niektóre nowe typy zostały wprowadzone w nowszych wersjach programu SQL Server nie są obsługiwane we wcześniejszych wersjach programu SQL Server. Te typy są wymienione w poniższej tabeli.  
  
|Typ dostawcy<br /><br /> nazwa|Typ dostawcy<br /><br /> atrybuty|`EDMSimpleType`<br /><br /> nazwa|Aspektami|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|n/d|`Edm.Boolean`|n/d|  
|`tinyint`|n/d|`Edm.Byte`|n/d|  
|`smallint`|n/d|`Edm.Int16`|n/d|  
|`int`|n/d|`Edm.Int32`|n/d|  
|`bigint`|n/d|`Edm.Int64`|n/d|  
|`float`|n/d|`Edm.Double`|n/d|  
|`real`|n/d|`Edm.Double`|n/d|  
|`decimal`|n/d|`Edm.Decimal`|Dokładność:<br /><br /> — Wartość pola minimalna: 1<br /><br /> -Maksymalna: 38<br /><br /> -Domyślne: 18<br /><br /> -Stałej: False<br /><br /> Skala:<br /><br /> — Wartość pola minimalna: 0<br /><br /> -Maksymalna: 38<br /><br /> -Domyślna: 0<br /><br /> -Stałej: False|  
|`numeric`|n/d|`Edm.Decimal`|Dokładność:<br /><br /> — Wartość pola minimalna: 1<br /><br /> -Maksymalna: 38<br /><br /> -Domyślne: 18<br /><br /> -Stałej: False<br /><br /> Skala:<br /><br /> — Wartość pola minimalna: 0<br /><br /> -Maksymalna: 38<br /><br /> -Domyślna: 0<br /><br /> -Stałej: False|  
|`smallmoney`|n/d|`Edm.Decimal`|Dokładność:<br /><br /> -Domyślny: 10<br /><br /> -Stałej: True<br /><br /> Skala:<br /><br /> -Domyślna: 4<br /><br /> -Stałej: True|  
|`money`|n/d|`Edm.Decimal`|Dokładność:<br /><br /> -Domyślne: 19<br /><br /> -Stałej: True<br /><br /> Skala:<br /><br /> -Domyślna: 4<br /><br /> -Stałej: True|  
|`binary`|n/d|`Edm.Binary`|Element MaxLength:<br /><br /> — Wartość pola minimalna: 1<br /><br /> -Maksymalna: 8000<br /><br /> -Domyślne: 8000<br /><br /> -Stałej: False<br /><br /> FixedLength:<br /><br /> -Domyślnie: True<br /><br /> -Stałej: True|  
|`varbinary`|n/d|`Edm.Binary`|Element MaxLength:<br /><br /> — Wartość pola minimalna: 1<br /><br /> -Maksymalna: 8000<br /><br /> -Domyślne: 8000<br /><br /> -Stałej: False<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
|`varbinary(max)`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|n/d|`Edm.Binary`|Element MaxLength:<br /><br /> -Domyślne: 214748364780<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
|`image`|n/d|`Edm.Binary`|Element MaxLength:<br /><br /> -Domyślne: 2147483647<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
|`timestamp`|n/d|`Edm.Binary`|Element MaxLength:<br /><br /> -Domyślne: 8<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: True<br /><br /> -Stałej: True|  
|`rowversion`|n/d|`Edm.Binary`|Element MaxLength:<br /><br /> -Domyślne: 8<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: True<br /><br /> -Stałej: True|  
|`smalldatetime`|n/d|`Edm.DateTime`|Dokładność:<br /><br /> -Domyślna: 0<br /><br /> -Stałej: True|  
|`datetime`|n/d|`Edm.DateTime`|Dokładność:<br /><br /> -Domyślne: 3<br /><br /> -Stałej: True|  
|`date`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTime`|Dokładność:<br /><br /> -Domyślna: 0<br /><br /> -Stałej: False|  
|`time`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2005 i SQL Server 2000.|n/d|`Edm.Time`|Dokładność:<br /><br /> -Domyślne: 7<br /><br /> -Stałej: False|  
|`datetime2`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTime`|Dokładność:<br /><br /> -Domyślne: 7<br /><br /> -Stałej: False|  
|`datetimeoffset`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTimeOffset`|Dokładność:<br /><br /> -Domyślne: 7<br /><br /> -Stałej: False|  
|`nvarchar`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|n/d|`Edm.String`|Element MaxLength:<br /><br /> — Wartość pola minimalna: 1<br /><br /> -Maksymalna: 4000<br /><br /> -Domyślne: 4000<br /><br /> -Stałej: False<br /><br /> Unicode:<br /><br /> -Domyślnie: True<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
|`varchar`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|n/d|`Edm.String`|Element MaxLength:<br /><br /> — Wartość pola minimalna: 1<br /><br /> -Maksymalna: 8000<br /><br /> -Domyślne: 8000<br /><br /> -Stałej: False<br /><br /> Unicode:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
|`char`|n/d|`Edm.String`|Element MaxLength:<br /><br /> — Wartość pola minimalna: 1<br /><br /> -Maksymalna: 8000<br /><br /> -Domyślne: 8000<br /><br /> -Stałej: False<br /><br /> Unicode:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: True<br /><br /> -Stałej: True|  
|`nchar`|n/d|`Edm.String`|Element MaxLength:<br /><br /> — Wartość pola minimalna: 1<br /><br /> -Maksymalna: 4000<br /><br /> -Domyślne: 4000<br /><br /> -Stałej: False<br /><br /> Unicode:<br /><br /> -Domyślnie: True<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: True<br /><br /> -Stałej: True|  
|`varchar`(`max`)|n/d|`Edm.String`|Element MaxLength:<br /><br /> -Domyślne: 2147483647<br /><br /> -Stałej: True<br /><br /> Unicode:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
|`nvarchar`(`max`)|n/d|`Edm.String`|Element MaxLength:<br /><br /> - Default: 1073741823<br /><br /> -Stałej: True<br /><br /> Unicode:<br /><br /> -Domyślnie: True<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
|`ntext`|Porównywanie równości: False<br /><br /> Umożliwia porównywanie kolejności: False|`Edm.String`|Element MaxLength:<br /><br /> - Default: 1073741823<br /><br /> -Stałej: True<br /><br /> Unicode:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
|`text`|Porównywanie równości: False<br /><br /> Umożliwia porównywanie kolejności: False|`Edm.String`|Element MaxLength:<br /><br /> -Domyślne: 2147483647<br /><br /> -Stałej: True<br /><br /> Unicode:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
|`Unique`<br /><br /> `identifier`|Porównywanie równości: True<br /><br /> Umożliwia porównywanie kolejności: True|`Edm.Guid`|n/d|  
|`xml`|Porównywanie równości: False<br /><br /> Umożliwia porównywanie kolejności: False|`Edm.String`|Element MaxLength:<br /><br /> - Default: 1073741823<br /><br /> -Stałej: True<br /><br /> Unicode:<br /><br /> -Domyślnie: True<br /><br /> -Stałej: True<br /><br /> FixedLength:<br /><br /> -Domyślnie: False<br /><br /> -Stałej: True|  
  
## <a name="see-also"></a>Zobacz też  
 [Specyfikacje CSDL, SSDL i MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
