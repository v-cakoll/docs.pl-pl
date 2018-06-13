---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512164"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a>3557 - TransactedReceiveScopeEndCommitFailed
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3557|  
|Słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
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
