---
title: 4205 — FoundProcessingError
ms.date: 03/30/2017
ms.assetid: f2235a15-dd87-439e-8cb9-8b1b89a3dacf
ms.openlocfilehash: 732632ddc9a7712169ace984c1d6d0098a7ae608
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774338"
---
# <a name="4205---foundprocessingerror"></a>4205 — FoundProcessingError
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|4205|  
|słowa kluczowe|WFInstanceStore|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że polecenie dostawcy SQL nie powiodło się.  
  
## <a name="message"></a>Komunikat  
 Polecenie nie powiodło się: %1  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|ExceptionMessage|xs:String|Komunikat z wyjątku SQL.|  
|Wyjątek|xs:String|Szczegóły wyjątku, dla wyjątku|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
