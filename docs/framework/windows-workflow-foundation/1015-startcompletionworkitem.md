---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7457b65f81e9e26b9de6055df474a83ce4264846
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1015---startcompletionworkitem"></a>1015 - StartCompletionWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1015|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że element roboczy CompletionWorkItem jest rozpoczęcie wykonywania.  
  
## <a name="message"></a>Komunikat  
 Rozpoczęcie wykonywania elementu roboczego CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'. Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie nadrzędne|xs:String|Nazwa typu działania nadrzędnego.|  
|ParentDisplayName|xs:String|Nazwa wyświetlana działania nadrzędnego.|  
|ParentInstanceId|xs:String|Identyfikator wystąpienia działania nadrzędnego.|  
|CompletedActivity|xs:String|Nazwa typu działania ukończone.|  
|CompletedActivityDisplayName|xs:String|Nazwa wyświetlana ukończonego działania.|  
|CompletedActivityInstanceId|xs:String|Identyfikator wystąpienia działania ukończone.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
