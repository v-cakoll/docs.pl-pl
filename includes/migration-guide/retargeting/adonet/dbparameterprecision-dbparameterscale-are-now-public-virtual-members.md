---
ms.openlocfilehash: 1721d32f8cdc9b6ea4b4732e38afa56a8a532600
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091697"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>Właściwości DbParameter.Precision i DbParameter.Scale są teraz publicznymi wirtualnymi elementami członkowskimi

|   |   |
|---|---|
|Szczegóły|<xref:System.Data.Common.DbParameter.Precision> i <xref:System.Data.Common.DbParameter.Scale> są implementowane jako publiczne właściwości wirtualne. Zastępują one odpowiednie implementacje interfejsu jawnego <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> i <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.|
|Sugestia|Podczas ponownego kompilowania dostawcy bazy danych programu ADO.NET te różnice będą wymagać zastosowania słowa kluczowego „override” do właściwości Precision i Scale. Jest to potrzebne tylko w przypadku ponownego kompilowania składników; istniejące pliki binarne będą nadal działać.|
|Zakres|Mały|
|Wersja|4.5.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|
