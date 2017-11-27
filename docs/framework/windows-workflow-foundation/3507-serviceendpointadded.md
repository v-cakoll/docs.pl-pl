---
title: 3507 - ServiceEndpointAdded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 463482bbcc659c6dba15b854ff06f41754f63ccc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="3507---serviceendpointadded"></a>3507 - ServiceEndpointAdded
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3507|  
|Słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 Wskazuje, że dodano punkt końcowy usługi.  
  
## <a name="message"></a>Komunikat  
 Punkt końcowy usługi został dodany dla adresu "%1", powiązania "%2" i kontraktu "%3".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Adres|xs:String|Adres punktu końcowego.|  
|Powiązanie|xs:String|Powiązanie punktu końcowego.|  
|Kontrakt|xs:String|Kontrakt punktu końcowego.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
