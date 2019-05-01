---
title: 1014 — ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982270"
---
# <a name="1014---schedulecompletionworkitem"></a>1014 — ScheduleCompletionWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1014|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że CompletionWorkItem została zaplanowana.  
  
## <a name="message"></a>Komunikat  
 CompletionWorkItem zaplanowano nadrzędnego działania "%1", DisplayName: "%2", InstanceId: "%3".  Ukończono %4, DisplayName: '%5', InstanceId: '%6'.  
  
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
