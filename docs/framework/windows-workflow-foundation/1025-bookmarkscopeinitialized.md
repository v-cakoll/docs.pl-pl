---
title: 1025 - BookmarkScopeInitialized
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aec874ea3c93878e519eb691a99f415a4810709
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1025---bookmarkscopeinitialized"></a>1025 - BookmarkScopeInitialized
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1025|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że zakres zakładek został zainicjowany.  
  
## <a name="message"></a>Komunikat  
 Zakres zakładek o identyfikatorze temporaryid: '%1' został zainicjowany o identyfikatorze: "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TemporaryId|xs:String|Tymczasowy identyfikator zakładki.|  
|InitializedId|xs:String|Identyfikator zainicjowane zakładki.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
