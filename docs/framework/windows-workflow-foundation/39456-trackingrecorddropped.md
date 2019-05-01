---
title: 39456 — TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774429"
---
# <a name="39456---trackingrecorddropped"></a>39456 — TrackingRecordDropped
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|39456|  
|słowa kluczowe|WFTracking|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że rekord śledzenia został porzucony, ponieważ jego rozmiar przekracza maksymalną dozwoloną przez dostawcę sesji funkcji ETW.  
  
## <a name="message"></a>Komunikat  
 Rozmiar śledzenia rekord %1 przekracza maksymalną dozwoloną przez sesję funkcji ETW dla dostawcy %2  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Wyjątek|xs:String|Szczegóły wyjątku, dla wyjątku|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
