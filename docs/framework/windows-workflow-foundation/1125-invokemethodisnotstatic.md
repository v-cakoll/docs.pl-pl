---
title: 1125 — InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: 692c5e56dac0a69ab5705acd284f048391145641
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924268"
---
# <a name="1125---invokemethodisnotstatic"></a>1125 — InvokeMethodIsNotStatic
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1125|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Podczas wykonywania kroku użyciu metody CacheMetadata działania InvokeMethod wskazuje, że wywoływanej metody nie jest statyczne.  
  
## <a name="message"></a>Komunikat  
 InvokeMethod "%1" - metoda nie jest statyczne.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:String|Nazwa wyświetlana działania InvokeMethod.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
