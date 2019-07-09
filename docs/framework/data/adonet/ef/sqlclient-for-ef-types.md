---
title: Klient SQL dla typów programu Entity Framework
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: 7e3abe86128670656bfb2607b8531c9ceb0e4134
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662120"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Klient SQL dla typów programu Entity Framework
Dostawca danych .NET Framework, dla pliku manifestu dostawcy programu SQL Server (SqlClient) zawiera listę dostawcy typów pierwotnych, aspektami dla każdego typu mapowania między koncepcyjnej i typów pierwotnych modelu magazynu i promocji i konwersji reguły między typów pierwotnych modelu koncepcyjnego i magazynu.  
  
 W poniższej tabeli opisano typy dla baz danych programu SQL Server 2008, SQL Server 2005 i SQL Server 2000 i sposób mapowania tych typów typy modelu koncepcyjnego. Niektóre nowe typy zostały wprowadzone w nowszych wersjach programu SQL Server nie są obsługiwane w starszych wersjach programu SQL Server. Te typy są podane w poniższej tabeli.  
  
|Typ dostawcy<br /><br /> nazwa|Typ dostawcy<br /><br /> atrybuty|`EDMSimpleType`<br /><br /> nazwa|Aspektami|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|n/d|`Edm.Boolean`|n/d|  
|`tinyint`|n/d|`Edm.Byte`|n/d|  
|`smallint`|n/d|`Edm.Int16`|n/d|  
|`int`|n/d|`Edm.Int32`|n/d|  
|`bigint`|n/d|`Edm.Int64`|n/d|  
|`float`|n/d|`Edm.Double`|n/d|  
|`real`|n/d|`Edm.Double`|n/d|  
|`decimal`|n/d|`Edm.Decimal`|Dokładność:<br /><br /> -Minimalne: 1<br /><br /> – Maksymalna liczba: 38<br /><br /> — Wartość domyślna: 18<br /><br /> -Stałe: False<br /><br /> Skala:<br /><br /> -Minimalne: 0<br /><br /> – Maksymalna liczba: 38<br /><br /> — Wartość domyślna: 0<br /><br /> -Stałe: False|  
|`numeric`|n/d|`Edm.Decimal`|Dokładność:<br /><br /> -Minimalne: 1<br /><br /> – Maksymalna liczba: 38<br /><br /> — Wartość domyślna: 18<br /><br /> -Stałe: False<br /><br /> Skala:<br /><br /> -Minimalne: 0<br /><br /> – Maksymalna liczba: 38<br /><br /> — Wartość domyślna: 0<br /><br /> -Stałe: False|  
|`smallmoney`|n/d|`Edm.Decimal`|Dokładność:<br /><br /> — Wartość domyślna: 10<br /><br /> -Stałe: Prawda<br /><br /> Skala:<br /><br /> — Wartość domyślna: 4<br /><br /> -Stałe: Prawda|  
|`money`|n/d|`Edm.Decimal`|Dokładność:<br /><br /> — Wartość domyślna: 19<br /><br /> -Stałe: Prawda<br /><br /> Skala:<br /><br /> — Wartość domyślna: 4<br /><br /> -Stałe: Prawda|  
|`binary`|n/d|`Edm.Binary`|MaxLength:<br /><br /> -Minimalne: 1<br /><br /> – Maksymalna liczba: 8000<br /><br /> — Wartość domyślna: 8000<br /><br /> -Stałe: False<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: Prawda<br /><br /> -Stałe: Prawda|  
|`varbinary`|n/d|`Edm.Binary`|MaxLength:<br /><br /> -Minimalne: 1<br /><br /> – Maksymalna liczba: 8000<br /><br /> — Wartość domyślna: 8000<br /><br /> -Stałe: False<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
|`varbinary(max)`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2000.|n/d|`Edm.Binary`|MaxLength:<br /><br /> — Wartość domyślna: 214748364780<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
|`image`|n/d|`Edm.Binary`|MaxLength:<br /><br /> — Wartość domyślna: 2147483647<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
|`timestamp`|n/d|`Edm.Binary`|MaxLength:<br /><br /> — Wartość domyślna: 8<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: Prawda<br /><br /> -Stałe: Prawda|  
|`rowversion`|n/d|`Edm.Binary`|MaxLength:<br /><br /> — Wartość domyślna: 8<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: Prawda<br /><br /> -Stałe: Prawda|  
|`smalldatetime`|n/d|`Edm.DateTime`|Dokładność:<br /><br /> — Wartość domyślna: 0<br /><br /> -Stałe: Prawda|  
|`datetime`|n/d|`Edm.DateTime`|Dokładność:<br /><br /> — Wartość domyślna: 3<br /><br /> -Stałe: Prawda|  
|`date`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTime`|Dokładność:<br /><br /> — Wartość domyślna: 0<br /><br /> -Stałe: False|  
|`time`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2005 i SQL Server 2000.|n/d|`Edm.Time`|Dokładność:<br /><br /> — Wartość domyślna: 7<br /><br /> -Stałe: False|  
|`datetime2`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTime`|Dokładność:<br /><br /> — Wartość domyślna: 7<br /><br /> -Stałe: False|  
|`datetimeoffset`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTimeOffset`|Dokładność:<br /><br /> — Wartość domyślna: 7<br /><br /> -Stałe: False|  
|`nvarchar`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2000.|n/d|`Edm.String`|MaxLength:<br /><br /> -Minimalne: 1<br /><br /> – Maksymalna liczba: 4000<br /><br /> — Wartość domyślna: 4000<br /><br /> -Stałe: False<br /><br /> Unicode:<br /><br /> — Wartość domyślna: Prawda<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
|`varchar`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w programie SQL Server 2000.|n/d|`Edm.String`|MaxLength:<br /><br /> -Minimalne: 1<br /><br /> – Maksymalna liczba: 8000<br /><br /> — Wartość domyślna: 8000<br /><br /> -Stałe: False<br /><br /> Unicode:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
|`char`|n/d|`Edm.String`|MaxLength:<br /><br /> -Minimalne: 1<br /><br /> – Maksymalna liczba: 8000<br /><br /> — Wartość domyślna: 8000<br /><br /> -Stałe: False<br /><br /> Unicode:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: Prawda<br /><br /> -Stałe: Prawda|  
|`nchar`|n/d|`Edm.String`|MaxLength:<br /><br /> -Minimalne: 1<br /><br /> – Maksymalna liczba: 4000<br /><br /> — Wartość domyślna: 4000<br /><br /> -Stałe: False<br /><br /> Unicode:<br /><br /> — Wartość domyślna: Prawda<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: Prawda<br /><br /> -Stałe: Prawda|  
|`varchar`(`max`)|n/d|`Edm.String`|MaxLength:<br /><br /> — Wartość domyślna: 2147483647<br /><br /> -Stałe: Prawda<br /><br /> Unicode:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
|`nvarchar`(`max`)|n/d|`Edm.String`|MaxLength:<br /><br /> — Wartość domyślna: 1073741823<br /><br /> -Stałe: Prawda<br /><br /> Unicode:<br /><br /> — Wartość domyślna: Prawda<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
|`ntext`|Porównywanie równości: False<br /><br /> Porównywanie kolejności: False|`Edm.String`|MaxLength:<br /><br /> — Wartość domyślna: 1073741823<br /><br /> -Stałe: Prawda<br /><br /> Unicode:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
|`text`|Porównywanie równości: False<br /><br /> Porównywanie kolejności: False|`Edm.String`|MaxLength:<br /><br /> — Wartość domyślna: 2147483647<br /><br /> -Stałe: Prawda<br /><br /> Unicode:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
|`Unique`<br /><br /> `identifier`|Porównywanie równości: Prawda<br /><br /> Porównywanie kolejności: Prawda|`Edm.Guid`|n/d|  
|`xml`|Porównywanie równości: False<br /><br /> Porównywanie kolejności: False|`Edm.String`|MaxLength:<br /><br /> — Wartość domyślna: 1073741823<br /><br /> -Stałe: Prawda<br /><br /> Unicode:<br /><br /> — Wartość domyślna: Prawda<br /><br /> -Stałe: Prawda<br /><br /> FixedLength:<br /><br /> — Wartość domyślna: False<br /><br /> -Stałe: Prawda|  
  
## <a name="see-also"></a>Zobacz także

- [Specyfikacje CSDL, SSDL i MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
