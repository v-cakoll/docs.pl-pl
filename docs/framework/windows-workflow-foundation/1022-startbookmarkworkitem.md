---
title: 1022 — StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 93d906b32b51effaa709da6763f535708cd6f821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924725"
---
# <a name="1022---startbookmarkworkitem"></a>1022 — StartBookmarkWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1022|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że BookmarkWorkItem Trwa uruchamianie wykonywania.  
  
## <a name="message"></a>Komunikat  
 Rozpoczynanie wykonywania BookmarkWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".  Nazwa_zakładki: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|InstanceId|xs:String|Identyfikator wystąpienia działania.|  
|BookmarkName|xs:String|Nazwa zakładki.|  
|BookmarkScope|xs:String|Zakres zakładki.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
