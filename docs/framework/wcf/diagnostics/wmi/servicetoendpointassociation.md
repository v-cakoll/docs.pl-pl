---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452712"
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
 Typ danych: usługi  
  
 Dostęp do typu: tylko do odczytu  
Kwalifikatory: klucz  
  
 Usługa skojarzonej z punktem końcowym.  
  
### <a name="ref"></a>ref  
 Typ danych: punkt końcowy  
  
 Dostęp do typu: tylko do odczytu  
Kwalifikatory: klucz  
  
 Punkt końcowy skojarzony z usługą.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|
