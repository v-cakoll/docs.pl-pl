---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616109"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>Właściwości DbParameter.Precision i DbParameter.Scale są teraz publicznymi wirtualnymi elementami członkowskimi

#### <a name="details"></a>Szczegóły

<xref:System.Data.Common.DbParameter.Precision> i <xref:System.Data.Common.DbParameter.Scale> są implementowane jako publiczne właściwości wirtualne. Zastępują one odpowiednie implementacje interfejsu jawnego <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> i <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.

#### <a name="suggestion"></a>Sugestia

Podczas ponownego kompilowania dostawcy bazy danych programu ADO.NET te różnice będą wymagać zastosowania słowa kluczowego „override” do właściwości Precision i Scale. Jest to potrzebne tylko w przypadku ponownego kompilowania składników; istniejące pliki binarne będą nadal działać.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.5.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
