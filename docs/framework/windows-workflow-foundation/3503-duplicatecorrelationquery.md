---
title: 3503 — DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755600"
---
# <a name="3503---duplicatecorrelationquery"></a>3503 — DuplicateCorrelationQuery
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|3503|  
|słowa kluczowe|WFServices|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Wskazuje, że znaleziono zduplikowane CorrelationQuery. Zduplikowane zapytania nie będą używane, podczas obliczania korelacji.  
  
## <a name="message"></a>Komunikat  
 Znaleziono zduplikowane CorrelationQuery, w której = "%1". To zapytanie zduplikowane nie będzie używane, podczas obliczania korelacji.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Gdzie|xs:String|Gdzie części zapytania korelacji.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
