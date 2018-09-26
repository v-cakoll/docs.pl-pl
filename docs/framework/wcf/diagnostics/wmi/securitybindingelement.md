---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
ms.openlocfilehash: 19c65b3028ad63b8a78205d00f44cc32322648d5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47069977"
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
### <a name="defaultalgorithmsuite"></a>defaultAlgorithmSuite  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa algorytmów do użycia dla tego wiązania.  
  
### <a name="includetimestamp"></a>includeTimestamp  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy każdy komunikat zawiera sygnaturę czasową.  
  
### <a name="keyentropymode"></a>keyEntropyMode  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Źródło entropia używana do tworzenia kluczy.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Typ danych: LocalServiceSecuritySettings  
  
 Dostęp do typu: tylko do odczytu  
  
 Właściwości zabezpieczeń powiązania dla lokalnej usługi.  
  
### <a name="messagesecurityversion"></a>właściwości messageSecurityVersion  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wersja używana do zabezpieczenia komunikatów.  
  
### <a name="securityheaderlayout"></a>securityHeaderLayout  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Kolejność elementów w nagłówku zabezpieczeń dla tego powiązania.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
