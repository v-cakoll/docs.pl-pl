---
title: 4205 - FoundProcessingError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2235a15-dd87-439e-8cb9-8b1b89a3dacf
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 376e90de00759a88c6c938f2125653161d8e5201
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="4205---foundprocessingerror"></a>4205 - FoundProcessingError
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|4205|  
|Słowa kluczowe|WFInstanceStore|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że polecenia dostawcy SQL nie powiodło się.  
  
## <a name="message"></a>Komunikat  
 Polecenie nie powiodło się: %1  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|ExceptionMessage|xs:String|Komunikat wyjątku SQL.|  
|Wyjątek|xs:String|Szczegóły wyjątku dla wyjątku|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
