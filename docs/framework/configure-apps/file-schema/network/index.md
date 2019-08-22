---
title: Schemat ustawień sieci
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 0f5d762a2b688bebcb7c027be6c639b6d64c069d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664107"
---
# <a name="network-settings-schema"></a>Schemat ustawień sieci
Ustawienia sieci określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem. W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [ \<elementu System .net > (ustawienia sieciowe)](system-net-element-network-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<authenticationModules >, element (Ustawienia sieci)](authenticationmodules-element-network-settings.md)|Określa moduły używane do uwierzytelniania żądań internetowych.|  
|[\<connectionManagement >, element (Ustawienia sieci)](connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostami internetowymi.|  
|[\<defaultProxy >, element (Ustawienia sieci)](defaultproxy-element-network-settings.md)|Określa serwer proxy używany przez żądania HTTP do Internetu.|  
|[\<mailSettings >, element (Ustawienia sieci)](mailsettings-element-network-settings.md)|Zawiera ustawienia dla opcji wysyłania poczty.|  
|[\<requestCaching >, element (Ustawienia sieci)](requestcaching-element-network-settings.md)|Kontroluje mechanizm buforowania dla żądań sieci.|  
|[\<webRequestModules >, element (Ustawienia sieci)](webrequestmodules-element-network-settings.md)|Określa moduły używane do żądania informacji z hostów internetowych.|  
  
 Ustawienia identyfikatora URI określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI). W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [ \<identyfikatora URI > element (ustawienia identyfikatora URI)](uri-element-uri-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> IDN — element (ustawienia identyfikatora URI)](idn-element-uri-settings.md)|Określa, czy do nazw domen są stosowane analizowanie międzynarodowych nazw domen (IDN).|  
|[\<iriParsing >, element (ustawienia identyfikatora URI)](iriparsing-element-uri-settings.md)|Określa <xref:System.Uri> , czy do i czy należy zastosować analizę IRI (International Resource Identifier).|  
|[\<schemeSettings >, element (ustawienia identyfikatora URI)](schemesettings-element-uri-settings.md)|Określa, w <xref:System.Uri> jaki sposób będzie analizowana dla określonych schematów.|  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie aplikacji internetowych](../../../network-programming/configuring-internet-applications.md)
- [Schemat pliku konfiguracji](../index.md)
