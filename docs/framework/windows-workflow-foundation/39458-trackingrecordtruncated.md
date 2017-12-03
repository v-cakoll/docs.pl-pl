---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|39458|  
|Słowa kluczowe|WFTracking|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że został obcięty rekord śledzenia. Zmienne/adnotacje/dane użytkownika zostały usunięte.  
  
## <a name="message"></a>Komunikat  
 Obcięty rekord śledzenia %1 został zapisany w sesji usługi ETW za pomocą dostawcy %2. Zmienne/adnotacje/dane użytkownika zostały usunięte  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:String|Liczba rekordów śledzenia.|  
|Identyfikator dostawcy|xs:String|Identyfikator dostawcy ETW.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
