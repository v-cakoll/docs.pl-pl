---
title: 1016 — CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925089"
---
# <a name="1016---completecompletionworkitem"></a>1016 — CompleteCompletionWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1016|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że CompletionWorkItem zostało zakończone.  
  
## <a name="message"></a>Komunikat  
 CompletionWorkItem zostało ukończone dla nadrzędnej działania "%1", DisplayName: "%2", InstanceId: "%3". Ukończono %4, DisplayName: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie nadrzędne|xs:String|Nazwa typu działania nadrzędnego.|  
|ParentDisplayName|xs:String|Nazwa wyświetlana działania nadrzędnego.|  
|ParentInstanceId|xs:String|Identyfikator wystąpienia działanie nadrzędne.|  
|CompletedActivity|xs:String|Nazwa typu zakończonego działania.|  
|CompletedActivityDisplayName|xs:String|Nazwa wyświetlana zakończonego działania.|  
|CompletedActivityInstanceId|xs:String|Identyfikator wystąpienia zakończonego działania.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
