---
title: 1025 — BookmarkScopeInitialized
ms.date: 03/30/2017
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
ms.openlocfilehash: ddc9b48120b9d31f71bfc99fff19ef252b08e295
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924647"
---
# <a name="1025---bookmarkscopeinitialized"></a>1025 — BookmarkScopeInitialized
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1025|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że BookmarkScope został zainicjowany.  
  
## <a name="message"></a>Komunikat  
 BookmarkScope, który miał TemporaryId: "%1" została zainicjowana o identyfikatorze: "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TemporaryId|xs:String|Tymczasowy identyfikator zakładki.|  
|InitializedId|xs:String|Zainicjowana klasa identyfikator zakładki.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
