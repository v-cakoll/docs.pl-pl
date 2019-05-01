---
title: 1023 — CompleteBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
ms.openlocfilehash: 8677f25057486247e64879298755fe972bd373d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008853"
---
# <a name="1023---completebookmarkworkitem"></a>1023 — CompleteBookmarkWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1023|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że BookmarkWorkItem zostało zakończone.  
  
## <a name="message"></a>Komunikat  
 BookmarkWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3". Nazwa_zakładki: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|InstanceId|xs:String|Identyfikator wystąpienia działania.|  
|BookmarkName|xs:String|Nazwa zakładki.|  
|BookmarkScope|xs:String|Zakres zakładki.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
