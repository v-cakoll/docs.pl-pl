---
title: ServiceToEndpointAssociation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da8703b80f2fbcc2f02eb64c94baf0707a1a93bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Mapuje usługi do punktu końcowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ServiceToEndpointAssociation nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ServiceToEndpointAssociation ma następujące właściwości:  
  
### <a name="ref"></a>ref  
 Typ danych: usługi  
  
 Dostęp typu: tylko do odczytu  
Kwalifikatory: klucz  
  
 Usługa skojarzona z punktem końcowym.  
  
### <a name="ref"></a>ref  
 Typ danych: punktu końcowego  
  
 Dostęp typu: tylko do odczytu  
Kwalifikatory: klucz  
  
 Punkt końcowym skojarzony z usługą.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|
