---
title: "402 — StartSignpostEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0cd786f78336be50ad2ef5447f74b92b2abbdc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="402---startsignpostevent"></a>402 — StartSignpostEvent
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|402|  
|Słowa kluczowe|Rozwiązywanie problemów|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie oznacza początek działania na trasie. Zawiera nazwę działania.  
  
## <a name="message"></a>Komunikat  
 Granica aktywności.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Dane rozszerzone|`xs:string`|Nazwa działania.|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
