---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ea57cc60f9626763308267a98624c825f8312b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a>3557 - TransactedReceiveScopeEndCommitFailed
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3557|  
|Słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 Wskazuje, że wywołanie metody EndCommit w obiekcie CommittableTransaction zwrócił TransactionException.  
  
## <a name="message"></a>Komunikat  
 Wywołanie metody EndCommit w obiekcie CommittableTransaction o identyfikatorze = '%1' zgłosił TransactionException z następującym komunikatem: "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator transakcji|xs:String|Identyfikator obiekcie CommittableTransaction.|  
|Wyjątek|xs:String|Szczegóły wyjątku dla wyjątku|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
