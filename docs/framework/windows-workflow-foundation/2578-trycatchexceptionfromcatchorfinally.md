---
title: 2578 — TryCatchExceptionFromCatchOrFinally
ms.date: 03/30/2017
ms.assetid: 4803fee6-b8d8-4937-9907-d5c5fd5299db
ms.openlocfilehash: 46fb52e665d49ed7a0336dbeeb6ed07f0d479fb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755613"
---
# <a name="2578---trycatchexceptionfromcatchorfinally"></a>2578 — TryCatchExceptionFromCatchOrFinally
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|2578|  
|słowa kluczowe|WFActivities|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje bloku Catch lub Finally działanie został zgłoszony wyjątek.  
  
## <a name="message"></a>Komunikat  
 Catch lub Finally działania, który jest skojarzony z działania TryCatch "%1" został zgłoszony wyjątek.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
