---
title: 1132 — InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924218"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a>1132 — InvokeMethodDoesNotUseAsyncPattern
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1132|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Podczas wykonywania kroku użyciu metody CacheMetadata działania InvokeMethod wskazuje, że nie używa wzorca asynchronicznego podczas wywoływania metody.  
  
## <a name="message"></a>Komunikat  
 InvokeMethod "%1" - metoda nie korzysta z wzorca asynchronicznego.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:String|Nazwa wyświetlana działania InvokeMethod.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
