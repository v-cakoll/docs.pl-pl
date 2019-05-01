---
title: 1015 — StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032269"
---
# <a name="1015---startcompletionworkitem"></a>1015 — StartCompletionWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1015|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że CompletionWorkItem Trwa uruchamianie wykonywania.  
  
## <a name="message"></a>Komunikat  
 Rozpoczynanie wykonywania CompletionWorkItem dla nadrzędnego działania "%1", DisplayName: "%2", InstanceId: "%3". Ukończono %4, DisplayName: '%5', InstanceId: '%6'.  
  
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
