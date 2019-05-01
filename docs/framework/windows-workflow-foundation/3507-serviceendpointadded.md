---
title: 3507 — ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: c787a1a5af752a3d08e2049cfa0b600b7739e56c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009841"
---
# <a name="3507---serviceendpointadded"></a>3507 — ServiceEndpointAdded
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|3507|  
|słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Wskazuje, że punkt końcowy usługi został dodany.  
  
## <a name="message"></a>Komunikat  
 Punkt końcowy usługi został dodany dla adresu "%1", powiązania "%2" i kontraktu "%3".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Adres|xs:String|Adres punktu końcowego.|  
|Wiązanie|xs:String|Powiązanie punktu końcowego.|  
|Kontrakt|xs:String|Kontrakt punktu końcowego.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
