---
title: 1020 — CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 2a382a2f12f4800cd70286a553af253e2af64c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924751"
---
# <a name="1020---createbookmark"></a>1020 — CreateBookmark
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1020|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że utworzono zakładki działania.  
  
## <a name="message"></a>Komunikat  
 Zakładka została utworzona dla działania "%1", DisplayName: "%2", InstanceId: "%3".  Nazwa_zakładki: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|InstanceId|xs:String|Identyfikator wystąpienia działania.|  
|BookmarkName|xs:String|Nazwa zakładki.|  
|BookmarkScope|xs:String|Zakres zakładki.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
