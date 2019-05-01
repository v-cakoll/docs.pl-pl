---
title: 1035 — RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924855"
---
# <a name="1035---runtimetransactionset"></a>1035 — RuntimeTransactionSet
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1035|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie ustawił transakcji środowiska uruchomieniowego.  
  
## <a name="message"></a>Komunikat  
 Transakcja środowiska uruchomieniowego została ustawiona przez działanie "%1", DisplayName: "%2", InstanceId: "%3".  Wykonanie wyizolowane do działania "%4", DisplayName: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|InstanceId|xs:String|Identyfikator wystąpienia działania.|  
|IsolatedActivity|xs:String|Nazwa typu transakcji jest izolowane do działania.|  
|IsolatedActivityDisplayName|xs:String|Nazwa wyświetlana transakcji jest izolowane do działania.|  
|IsolatedActivityInstanceId|xs:String|Identyfikator wystąpienia transakcji jest izolowane do działania.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
