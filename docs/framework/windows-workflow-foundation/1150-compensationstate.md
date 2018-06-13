---
title: 1150 - CompensationState
ms.date: 03/30/2017
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
ms.openlocfilehash: 61613a27c4d4d8fb0b206246fef25ae87def47a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510685"
---
# <a name="1150---compensationstate"></a>1150 - CompensationState
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1150|  
|Słowa kluczowe|WFActivities|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Oznacza zmianę stanu w działanie CompensableActivity.  
  
## <a name="message"></a>Komunikat  
 Działanie CompensableActivity "%1" jest w stanie "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|Stan|xs:String|Stan kompensacji.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
