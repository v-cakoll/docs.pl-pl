---
title: 3557 — TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774455"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a>3557 — TransactedReceiveScopeEndCommitFailed
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|3557|  
|słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Wskazuje, że wywołanie EndCommit na CommittableTransaction zgłosił TransactionException —.  
  
## <a name="message"></a>Komunikat  
 Wywołanie EndCommit na Commitabletransakction o identyfikatorze = '%1' zgłosił TransactionException — z następującym komunikatem: "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TransactionId|xs:String|Identyfikator Commitabletransakction.|  
|Wyjątek|xs:String|Szczegóły wyjątku, dla wyjątku|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
