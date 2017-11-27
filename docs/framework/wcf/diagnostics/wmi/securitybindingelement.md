---
title: SecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b567c173c5a04421bce57585d96b8b45144c5625
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 Klasa obiektu SecurityBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa obiektu SecurityBindingElement ma następujące właściwości:  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Określa algorytmy używane z powiązaniem.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy każdy komunikat zawiera sygnaturę czasową.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Źródło entropii używane do tworzenia kluczy.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Typ danych: LocalServiceSecuritySettings  
  
 Dostęp typu: tylko do odczytu  
  
 Powiązania właściwości zabezpieczeń lokalnej usługi.  
  
### <a name="messagesecurityversion"></a>Właściwości MessageSecurityVersion  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wersja używana do zabezpieczenia komunikatów.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Kolejność elementów nagłówka zabezpieczeń dla tego powiązania.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
