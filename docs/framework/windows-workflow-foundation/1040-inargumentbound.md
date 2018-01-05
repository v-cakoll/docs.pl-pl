---
title: 1040 - InArgumentBound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a86eeef0479b33e3c76223fa3ef2f74f4f337aa0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1040---inargumentbound"></a>1040 - InArgumentBound
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1040|  
|Słowa kluczowe|WFActivities|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że In argument został powiązany.  
  
## <a name="message"></a>Komunikat  
 W argumencie "%1" w działaniu '%2', nazwa wyświetlana: %3, identyfikator wystąpienia: "%4" został powiązany z wartością: %5.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InArgument|xs:String|Nazwa InArgument.|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|Identyfikator wystąpienia|xs:String|Identyfikator wystąpienia działania.|  
|Wartość|xs:String|Wartość powiązana InArgument.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
