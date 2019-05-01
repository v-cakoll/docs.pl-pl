---
title: 401— StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: 1776252c362feb3c3ebc04651603944040ceee7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999755"
---
# <a name="401--stopsignpostevent"></a>401— StopSignPostEvent
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|401|  
|słowa kluczowe|Rozwiązywanie problemów|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie oznacza koniec działania end-to-end. Zawiera on nazwę działania.  
  
## <a name="message"></a>Komunikat  
 Hranice aktivity  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Dane rozszerzone|`xs:string`|Nazwa działania.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
