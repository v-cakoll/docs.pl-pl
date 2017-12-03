---
title: 1010 - ActivityCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d26aa2c30defd2eb794d013155e05ccd496eebe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1010---activitycompleted"></a>1010 - ActivityCompleted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1010|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie zakończy działanie.  
  
## <a name="message"></a>Komunikat  
 Działanie "%1", nazwa wyświetlana: %2, identyfikator wystąpienia: '%3' została ukończona w stan "%4".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|Identyfikator wystąpienia|xs:String|Identyfikator wystąpienia działania.|  
|Stan|xs:String|Stan działania.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
