---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3fcd93dbc30b20f7822a54babde8277e32d8335
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1035|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie ustawił transakcja czasu wykonywania.  
  
## <a name="message"></a>Komunikat  
 Transakcja czasu wykonywania została ustawiona przez działanie %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.  Wykonanie izolowane, ograniczone do działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|Identyfikator wystąpienia|xs:String|Identyfikator wystąpienia działania.|  
|IsolatedActivity|xs:String|Nazwa typu transakcji jest izolowane, ograniczone do działania.|  
|IsolatedActivityDisplayName|xs:String|Nazwa wyświetlana transakcji jest izolowane, ograniczone do działania.|  
|IsolatedActivityInstanceId|xs:String|Identyfikator wystąpienia transakcji jest izolowane, ograniczone do działania.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
