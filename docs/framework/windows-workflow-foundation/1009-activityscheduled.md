---
title: 1009 - ActivityScheduled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdaa8ca4efeffb3895e0056303721b13cdc1ae27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1009---activityscheduled"></a>1009 - ActivityScheduled
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1009|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie jest zaplanowane co do wykonania.  
  
## <a name="message"></a>Komunikat  
 Działanie "%1", nazwa wyświetlana nadrzędne: "%2", identyfikator wystąpienia: '%3' zaplanowało działanie podrzędne %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie nadrzędne|xs:String|Nazwa typu działania nadrzędnego.|  
|ParentDisplayName|xs:String|Nazwa wyświetlana działania nadrzędnego.|  
|ParentInstanceId|xs:String|Identyfikator wystąpienia działania nadrzędnego.|  
|ChildActivity|xs:String|Nazwa typu działania podrzędnego zaplanowane.|  
|ChildDisplayName|xs:String|Nazwa wyświetlana działania podrzędnego zaplanowane.|  
|ChildInstanceId|xs:String|Identyfikator wystąpienia działania podrzędnego zaplanowane.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
