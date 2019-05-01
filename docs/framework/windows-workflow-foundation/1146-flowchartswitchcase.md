---
title: 1146 — FlowchartSwitchCase
ms.date: 03/30/2017
ms.assetid: 274e9209-1720-4512-a615-e742f00895f4
ms.openlocfilehash: 9f4e3af664ed30634e4b56f16cd6caf2366c3674
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923906"
---
# <a name="1146---flowchartswitchcase"></a>1146 — FlowchartSwitchCase
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1146|  
|słowa kluczowe|WFActivities|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, w którym to przypadku została wybrana w przełączniku schematu blokowego.  
  
## <a name="message"></a>Komunikat  
 Schemat blokowy "%1'/FlowSwitch — przypadek"%2"został wybrany.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|FlowChart|xs:String|Wyświetlana nazwa schematu blokowego.|  
|przypadek|xs:String|Przełącznik zamierzone, Zapisz wybrany.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
