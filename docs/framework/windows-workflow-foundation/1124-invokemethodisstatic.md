---
title: 1124 — InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: 49a9dec73392681fd4150c611f78399a1e15dd48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924062"
---
# <a name="1124---invokemethodisstatic"></a>1124 — InvokeMethodIsStatic
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1124|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Podczas wykonywania kroku użyciu metody CacheMetadata działania InvokeMethod wskazuje, że metoda do wywołania jest statyczna.  
  
## <a name="message"></a>Komunikat  
 InvokeMethod "%1" - metoda jest statyczna.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:String|Nazwa wyświetlana działania InvokeMethod.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
