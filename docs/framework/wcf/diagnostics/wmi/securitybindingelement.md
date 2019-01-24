---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: f7c4e30b72af36de1d3088e4ca8cd98ced734104
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692327"
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa elementu SecurityBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa elementu SecurityBindingElement ma następujące właściwości:  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Określa algorytmów do użycia dla tego wiązania.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość logiczna określająca, czy każdy komunikat zawiera sygnaturę czasową.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Źródło entropia używana do tworzenia kluczy.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Typ danych: LocalServiceSecuritySettings  
  
 Typ dostępu: tylko do odczytu  
  
 Właściwości zabezpieczeń powiązania dla lokalnej usługi.  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Wersja używana do zabezpieczenia komunikatów.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Kolejność elementów w nagłówku zabezpieczeń dla tego powiązania.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
