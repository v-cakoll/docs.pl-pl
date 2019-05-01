---
title: 1040 — InArgumentBound
ms.date: 03/30/2017
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
ms.openlocfilehash: 984372c07ccfb11f2f05d5488fa5ffc95075db41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009750"
---
# <a name="1040---inargumentbound"></a>1040 — InArgumentBound
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1040|  
|słowa kluczowe|WFActivities|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że In argument została powiązana.  
  
## <a name="message"></a>Komunikat  
 Argument "%1" w działaniu "%2", DisplayName: "%3", InstanceId: "%4" została powiązana z wartością: %5.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InArgument|xs:String|Nazwa InArgument.|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|InstanceId|xs:String|Identyfikator wystąpienia działania.|  
|Wartość|xs:String|Wartość powiązana InArgument.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
