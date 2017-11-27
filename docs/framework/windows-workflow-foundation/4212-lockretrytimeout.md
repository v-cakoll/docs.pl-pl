---
title: 4212 - LockRetryTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 897e6ef8b739654a61058106966c870c47f8129a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="4212---lockretrytimeout"></a>4212 - LockRetryTimeout
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|4212|  
|Słowa kluczowe|WFInstanceStore|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Dostawca SQL został przekroczony limit czasu próby uzyskania blokady wystąpienia.  
  
## <a name="message"></a>Komunikat  
 Limit czasu próby uzyskania blokady wystąpienia.  Operacja nie została ukończona w ciągu przydzielonego limitu czasu równego %1. Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Opóźnienie|xs:String|Opóźnienie między kolejnymi próbami.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
