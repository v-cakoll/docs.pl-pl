---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: c602ea2b708fced37c5b309596fe2312be21e741
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603567"
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
  
 Typ dostępu: tylko do odczytu  
  
 Identyfikator elementu appdomain umowy.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: Zachowanie tablicy  
  
 Typ dostępu: tylko do odczytu  
  
 Zachowania skojarzonego z nim.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa kontraktu w języku WSDL.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Przestrzeń nazw `portType` elementu w języku WSDL.  
  
### <a name="operations"></a>Operacje  
 Typ danych: Operacja tablicy  
  
 Typ dostępu: tylko do odczytu  
  
 Operace tohoto kontraktu.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Proces identyfikator procesu, który obsługuje kontrakt.  
  
### <a name="ref"></a>ref  
 Typ danych: Kontrakt  
  
 Typ dostępu: tylko do odczytu  
  
 Rodzaj wywołania zwrotnego, gdy kontrakt jest kontraktu dwukierunkowego.  
  
### <a name="sessionmode"></a>SessionMode  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy kontrakt wymaga powiązania skojarzonego z nim do użycia kanału sesji.  
  
### <a name="type"></a>Typ  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Typ kontraktu.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Description.ContractDescription>
