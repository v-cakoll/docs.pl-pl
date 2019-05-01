---
title: 1009 — ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924660"
---
# <a name="1009---activityscheduled"></a>1009 — ActivityScheduled
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1009|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie jest zaplanowane do wykonania.  
  
## <a name="message"></a>Komunikat  
 Nadrzędne działanie "%1", DisplayName: "%2", InstanceId: "%3" podrzędnych zaplanowanego działania "%4" DisplayName: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie nadrzędne|xs:String|Nazwa typu działania nadrzędnego.|  
|ParentDisplayName|xs:String|Nazwa wyświetlana działania nadrzędnego.|  
|ParentInstanceId|xs:String|Identyfikator wystąpienia działanie nadrzędne.|  
|ChildActivity|xs:String|Nazwa typu działania podrzędnego zaplanowane.|  
|ChildDisplayName|xs:String|Nazwa wyświetlana działania podrzędnego zaplanowane.|  
|ChildInstanceId|xs:String|Identyfikator wystąpienia działania podrzędnego zaplanowane.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
