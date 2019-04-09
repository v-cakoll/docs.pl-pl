---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 1d367d0c5d14e6e75539dd2b20cdffcf2b34963d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153858"
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
