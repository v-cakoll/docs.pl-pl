---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509975"
---
# <a name="1009---activityscheduled"></a>1009 - ActivityScheduled
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1009|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie jest zaplanowane co do wykonania.  
  
## <a name="message"></a>Komunikat  
 Działanie "%1", nazwa wyświetlana nadrzędne: "%2", identyfikator wystąpienia: '%3' zaplanowało działanie podrzędne %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie nadrzędne|xs:String|Nazwa typu działania nadrzędnego.|  
|ParentDisplayName|xs:String|Nazwa wyświetlana działania nadrzędnego.|  
|ParentInstanceId|xs:String|Identyfikator wystąpienia działania nadrzędnego.|  
|ChildActivity|xs:String|Nazwa typu działania podrzędnego zaplanowane.|  
|ChildDisplayName|xs:String|Nazwa wyświetlana działania podrzędnego zaplanowane.|  
|ChildInstanceId|xs:String|Identyfikator wystąpienia działania podrzędnego zaplanowane.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
