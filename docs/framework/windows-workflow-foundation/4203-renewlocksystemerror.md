---
title: 4203 - RenewLockSystemError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06d4695eb125475f41a94c7f2266df6d2c3f400d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="4203---renewlocksystemerror"></a>4203 - RenewLockSystemError
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|4203|  
|Słowa kluczowe|WFInstanceStore|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje dostawcy SQL można przedłużyć okresu ważności blokady z powodu albo okresu ważności blokady już minęła lub właściciel blokady został usunięty. Obiekt SqlWorkflowInstanceStore zostanie przerwane.  
  
## <a name="message"></a>Komunikat  
 Nie można przedłużyć okresu ważności blokady, blokada już wygasła lub właściciel blokady został usunięty. Trwa przerywanie SqlWorkflowInstanceStore.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
