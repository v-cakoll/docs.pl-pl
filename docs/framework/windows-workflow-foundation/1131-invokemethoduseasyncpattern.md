---
title: 1131 — InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009958"
---
# <a name="1131---invokemethoduseasyncpattern"></a>1131 — InvokeMethodUseAsyncPattern
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1131|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Podczas wykonywania kroku użyciu metody CacheMetadata działania InvokeMethod wskazuje, że korzysta on wzorca asynchronicznego podczas wywoływania metody.  
  
## <a name="message"></a>Komunikat  
 InvokeMethod "%1" - metoda używa wzorca asynchronicznego "%2" i "%3".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:String|Nazwa wyświetlana działania InvokeMethod.|  
|BeginMethod|xs:String|Nazwa metody begin.|  
|EndMethod|xs:String|Nazwa metody end.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
