---
title: "403 — SuspendSignpostEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 10e745ded72caa493119d7e27a5c777b2185b96e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="403---suspendsignpostevent"></a>403 — SuspendSignpostEvent
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|403|  
|Słowa kluczowe|Rozwiązywanie problemów|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie oznacza zawieszania działania na trasie. Zawiera nazwę działania.  
  
## <a name="message"></a>Komunikat  
 Granica aktywności.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Dane rozszerzone|`xs:string`|Nazwa działania.|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
