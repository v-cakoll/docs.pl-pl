---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048234"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Mapy usługi do punktu końcowego.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
 Typ danych: Usługa  
  
 Typ dostępu: tylko do odczytu  
Kwalifikatory: Key  
  
 Usługa skojarzonej z punktem końcowym.  
  
### <a name="ref"></a>ref  
 Typ danych: Punkt końcowy  
  
 Typ dostępu: tylko do odczytu  
Kwalifikatory: Key  
  
 Punkt końcowy skojarzony z usługą.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|
