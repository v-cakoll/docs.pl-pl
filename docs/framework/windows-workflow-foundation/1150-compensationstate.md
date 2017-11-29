---
title: 1150 - CompensationState
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5debccf664768b84a7b213cd012b484df8fe3ef8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1150---compensationstate"></a>1150 - CompensationState
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1150|  
|Słowa kluczowe|WFActivities|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Oznacza zmianę stanu w działanie CompensableActivity.  
  
## <a name="message"></a>Komunikat  
 Działanie CompensableActivity "%1" jest w stanie "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|Stan|xs:String|Stan kompensacji.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
