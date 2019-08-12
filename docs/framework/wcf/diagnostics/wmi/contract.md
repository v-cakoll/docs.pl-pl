---
title: Kontrakt
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868434"
---
# <a name="contract"></a>Kontrakt
Kontrakt  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa kontraktu nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa kontraktu ma następujące właściwości:  
  
### <a name="appdomainid"></a>AppDomainId  
 Typ danych: sint32  
  
 Typ dostępu: Tylko do odczytu  
  
 Identyfikator domeny aplikacji, która hostuje kontrakt.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: Tablica zachowań  
  
 Typ dostępu: Tylko do odczytu  
  
 Zachowania skojarzone z tym kontraktem.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Typ dostępu: Tylko do odczytu  
  
 Nazwa kontraktu w języku WSDL.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Typ dostępu: Tylko do odczytu  
  
 Przestrzeń nazw `portType` elementu w języku WSDL.  
  
### <a name="operations"></a>Składowa  
 Typ danych: Tablica operacji  
  
 Typ dostępu: Tylko do odczytu  
  
 Operacje na tym kontrakcie.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Typ dostępu: Tylko do odczytu  
  
 Identyfikator procesu, który hostuje kontrakt.  
  
### <a name="ref"></a>ref  
 Typ danych: Kontrakt  
  
 Typ dostępu: Tylko do odczytu  
  
 Typ wywołania zwrotnego, gdy kontrakt jest kontraktem dwukierunkowym.  
  
### <a name="sessionmode"></a>SessionMode  
 Typ danych: ciąg  
  
 Typ dostępu: Tylko do odczytu  
  
 Wskazuje, czy kontrakt wymaga powiązania skojarzonego z tym kontraktem, aby można było używać sesji kanału.  
  
### <a name="type"></a>Typ  
 Typ danych: ciąg  
  
 Typ dostępu: Tylko do odczytu  
  
 Typ kontraktu.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK|Zadeklarowany w ServiceModel. mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ContractDescription>
