---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 12e9cbf5232ebbad33ccc4fdca33233997d27357
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194673"
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
 Klasy kontraktu nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa kontraktu ma następujące właściwości:  
  
### <a name="appdomainid"></a>AppDomainId  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Identyfikator elementu appdomain umowy.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: zachowanie tablicy  
  
 Dostęp do typu: tylko do odczytu  
  
 Zachowania skojarzonego z nim.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Nazwa kontraktu w języku WSDL.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Przestrzeń nazw `portType` elementu w języku WSDL.  
  
### <a name="operations"></a>Operacje  
 Typ danych: operacja tablicy  
  
 Dostęp do typu: tylko do odczytu  
  
 Operace tohoto kontraktu.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Proces identyfikator procesu, który obsługuje kontrakt.  
  
### <a name="ref"></a>ref  
 Typ danych: kontraktu  
  
 Dostęp do typu: tylko do odczytu  
  
 Rodzaj wywołania zwrotnego, gdy kontrakt jest kontraktu dwukierunkowego.  
  
### <a name="sessionmode"></a>SessionMode  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wskazuje, czy kontrakt wymaga powiązania skojarzonego z nim do użycia kanału sesji.  
  
### <a name="type"></a>Typ  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Typ kontraktu.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ContractDescription>
