---
title: Klient SQL dla typów programu Entity Framework
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: d132583bba2520d37693be6c4b085cfa514003e0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737848"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Klient SQL dla typów programu Entity Framework
Plik manifestu dostawcy programu .NET Framework Dostawca danych for SQL Server (SqlClient) zawiera listę typów pierwotnych dostawcy, zestawów reguł dla każdego typu, mapowania między typami pierwotnymi modelu koncepcyjnego i magazynu oraz podwyższenie i konwersję reguły między typami pierwotnymi modelu koncepcyjnego i magazynu.  
  
 Poniższa tabela zawiera opis typów dla SQL Server 2008, SQL Server 2005 i SQL Server 2000 baz danych oraz tego, jak te typy są mapowane na typy modelu koncepcyjnego. Niektóre nowe typy zostały wprowadzone w nowszych wersjach SQL Server nie są obsługiwane we wcześniejszych wersjach SQL Server. Te typy są wymienione w poniższej tabeli.  
  
|Typ dostawcy<br /><br /> nazwa|Typ dostawcy<br /><br /> atrybuty|`EDMSimpleType`<br /><br /> nazwa|Aspektami|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|n/d|`Edm.Boolean`|n/d|  
|`tinyint`|n/d|`Edm.Byte`|n/d|  
|`smallint`|n/d|`Edm.Int16`|n/d|  
|`int`|n/d|`Edm.Int32`|n/d|  
|`bigint`|n/d|`Edm.Int64`|n/d|  
|`float`|n/d|`Edm.Double`|n/d|  
|`real`|n/d|`Edm.Double`|n/d|  
|`decimal`|n/d|`Edm.Decimal`|Dokładne<br /><br /> -Minimum: 1<br /><br /> -Maksimum: 38<br /><br /> -Domyślnie: 18<br /><br /> -Stała: FAŁSZ<br /><br /> Zasięgu<br /><br /> -Minimum: 0<br /><br /> -Maksimum: 38<br /><br /> -Wartość domyślna: 0<br /><br /> -Stała: FAŁSZ|  
|`numeric`|n/d|`Edm.Decimal`|Dokładne<br /><br /> -Minimum: 1<br /><br /> -Maksimum: 38<br /><br /> -Domyślnie: 18<br /><br /> -Stała: FAŁSZ<br /><br /> Zasięgu<br /><br /> -Minimum: 0<br /><br /> -Maksimum: 38<br /><br /> -Wartość domyślna: 0<br /><br /> -Stała: FAŁSZ|  
|`smallmoney`|n/d|`Edm.Decimal`|Dokładne<br /><br /> -Domyślnie: 10<br /><br /> -Stała: prawda<br /><br /> Zasięgu<br /><br /> -Domyślnie: 4<br /><br /> -Stała: prawda|  
|`money`|n/d|`Edm.Decimal`|Dokładne<br /><br /> -Domyślnie: 19<br /><br /> -Stała: prawda<br /><br /> Zasięgu<br /><br /> -Domyślnie: 4<br /><br /> -Stała: prawda|  
|`binary`|n/d|`Edm.Binary`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maksimum: 8000<br /><br /> -Wartość domyślna: 8000<br /><br /> -Stała: FAŁSZ<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: prawda<br /><br /> -Stała: prawda|  
|`varbinary`|n/d|`Edm.Binary`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maksimum: 8000<br /><br /> -Wartość domyślna: 8000<br /><br /> -Stała: FAŁSZ<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
|`varbinary(max)`<br /><br /> Uwaga: ten typ nie jest obsługiwany w SQL Server 2000.|n/d|`Edm.Binary`|MaxLength<br /><br /> -Wartość domyślna: 214748364780<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
|`image`|n/d|`Edm.Binary`|MaxLength<br /><br /> -Wartość domyślna: 2147483647<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
|`timestamp`|n/d|`Edm.Binary`|MaxLength<br /><br /> -Domyślnie: 8<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: prawda<br /><br /> -Stała: prawda|  
|`rowversion`|n/d|`Edm.Binary`|MaxLength<br /><br /> -Domyślnie: 8<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: prawda<br /><br /> -Stała: prawda|  
|`smalldatetime`|n/d|`Edm.DateTime`|Dokładne<br /><br /> -Wartość domyślna: 0<br /><br /> -Stała: prawda|  
|`datetime`|n/d|`Edm.DateTime`|Dokładne<br /><br /> -Wartość domyślna: 3<br /><br /> -Stała: prawda|  
|`date`<br /><br /> Uwaga: ten typ nie jest obsługiwany w SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTime`|Dokładne<br /><br /> -Wartość domyślna: 0<br /><br /> -Stała: FAŁSZ|  
|`time`<br /><br /> Uwaga: ten typ nie jest obsługiwany w SQL Server 2005 i SQL Server 2000.|n/d|`Edm.Time`|Dokładne<br /><br /> -Domyślnie: 7<br /><br /> -Stała: FAŁSZ|  
|`datetime2`<br /><br /> Uwaga: ten typ nie jest obsługiwany w SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTime`|Dokładne<br /><br /> -Domyślnie: 7<br /><br /> -Stała: FAŁSZ|  
|`datetimeoffset`<br /><br /> Uwaga: ten typ nie jest obsługiwany w SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTimeOffset`|Dokładne<br /><br /> -Domyślnie: 7<br /><br /> -Stała: FAŁSZ|  
|`nvarchar`<br /><br /> Uwaga: ten typ nie jest obsługiwany w SQL Server 2000.|n/d|`Edm.String`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maksimum: 4000<br /><br /> -Wartość domyślna: 4000<br /><br /> -Stała: FAŁSZ<br /><br /> Unicode:<br /><br /> -Wartość domyślna: prawda<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
|`varchar`<br /><br /> Uwaga: ten typ nie jest obsługiwany w SQL Server 2000.|n/d|`Edm.String`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maksimum: 8000<br /><br /> -Wartość domyślna: 8000<br /><br /> -Stała: FAŁSZ<br /><br /> Unicode:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
|`char`|n/d|`Edm.String`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maksimum: 8000<br /><br /> -Wartość domyślna: 8000<br /><br /> -Stała: FAŁSZ<br /><br /> Unicode:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: prawda<br /><br /> -Stała: prawda|  
|`nchar`|n/d|`Edm.String`|MaxLength<br /><br /> -Minimum: 1<br /><br /> -Maksimum: 4000<br /><br /> -Wartość domyślna: 4000<br /><br /> -Stała: FAŁSZ<br /><br /> Unicode:<br /><br /> -Wartość domyślna: prawda<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: prawda<br /><br /> -Stała: prawda|  
|`varchar`(`max`)|n/d|`Edm.String`|MaxLength<br /><br /> -Wartość domyślna: 2147483647<br /><br /> -Stała: prawda<br /><br /> Unicode:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
|`nvarchar`(`max`)|n/d|`Edm.String`|MaxLength<br /><br /> -Wartość domyślna: 1073741823<br /><br /> -Stała: prawda<br /><br /> Unicode:<br /><br /> -Wartość domyślna: prawda<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
|`ntext`|Równe porównywalne: FAŁSZ<br /><br /> Zamówienie porównywalne: FAŁSZ|`Edm.String`|MaxLength<br /><br /> -Wartość domyślna: 1073741823<br /><br /> -Stała: prawda<br /><br /> Unicode:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
|`text`|Równe porównywalne: FAŁSZ<br /><br /> Zamówienie porównywalne: FAŁSZ|`Edm.String`|MaxLength<br /><br /> -Wartość domyślna: 2147483647<br /><br /> -Stała: prawda<br /><br /> Unicode:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
|`Unique`<br /><br /> `identifier`|Równe porównywalne: prawda<br /><br /> Zamówienie porównywalne: prawda|`Edm.Guid`|n/d|  
|`xml`|Równe porównywalne: FAŁSZ<br /><br /> Zamówienie porównywalne: FAŁSZ|`Edm.String`|MaxLength<br /><br /> -Wartość domyślna: 1073741823<br /><br /> -Stała: prawda<br /><br /> Unicode:<br /><br /> -Wartość domyślna: prawda<br /><br /> -Stała: prawda<br /><br /> FixedLength:<br /><br /> -Wartość domyślna: false<br /><br /> -Stała: prawda|  
  
## <a name="see-also"></a>Zobacz także

- [Specyfikacje CSDL, SSDL i MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
