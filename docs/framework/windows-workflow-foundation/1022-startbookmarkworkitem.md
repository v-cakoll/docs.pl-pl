---
title: 1022 - StartBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aaabbdca455d31d22b232ae2b08edef0687ac30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1022---startbookmarkworkitem"></a>1022 - StartBookmarkWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1022|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że element roboczy BookmarkWorkItem jest rozpoczęcie wykonywania.  
  
## <a name="message"></a>Komunikat  
 Rozpoczęcie wykonywania elementu roboczego BookmarkWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.  Nazwa zakładki: %4, zakres zakładek: %5.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|Identyfikator wystąpienia|xs:String|Identyfikator wystąpienia działania.|  
|Nazwa zakładki|xs:String|Nazwa zakładki.|  
|Zakres zakładek|xs:String|Zakres zakładki.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
