---
title: 4210 — SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 2493014e80e79ac2935c1bcc685147a74e48fb47
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774260"
---
# <a name="4210---sqlexceptioncaught"></a>4210 — SqlExceptionCaught
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|4210|  
|słowa kluczowe|WFInstanceStore|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że został zgłoszony wyjątek SQL.  
  
## <a name="message"></a>Komunikat  
 Przechwycono wyjątek SQL o numerze %1 komunikat %2.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs:String|Numer błędu SQL.|  
|ExceptionMessage|xs:String|Komunikat z wyjątku SQL.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
