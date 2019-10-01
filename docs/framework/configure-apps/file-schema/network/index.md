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
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698151"
---
# <a name="network-settings-schema"></a>Schemat ustawień sieci
Ustawienia sieci określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem.

Ustawienia @no__t -0system. net > określają, jak .NET Framework łączy się z siecią. W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [elementu \<System .net > (Ustawienia sieci)](system-net-element-network-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<authenticationModules >, element (Ustawienia sieci)](authenticationmodules-element-network-settings.md)|Określa moduły używane do uwierzytelniania żądań internetowych.|  
|[\<connectionManagement >, element (Ustawienia sieci)](connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostami internetowymi.|  
|[\<defaultProxy >, element (Ustawienia sieci)](defaultproxy-element-network-settings.md)|Określa serwer proxy używany przez żądania HTTP do Internetu.|  
|[\<mailSettings >, element (Ustawienia sieci)](mailsettings-element-network-settings.md)|Zawiera ustawienia dla opcji wysyłania poczty.|  
|[\<requestCaching >, element (Ustawienia sieci)](requestcaching-element-network-settings.md)|Kontroluje mechanizm buforowania dla żądań sieci.|  
|[\<webRequestModules >, element (Ustawienia sieci)](webrequestmodules-element-network-settings.md)|Określa moduły używane do żądania informacji z hostów internetowych.|  
  
Ustawienia > \<uri określają, jak .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI). W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [elementu \<uri > (ustawienia identyfikatora URI)](uri-element-uri-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<idn >, element (ustawienia identyfikatora URI)](idn-element-uri-settings.md)|Określa, czy do nazw domen są stosowane analizowanie międzynarodowych nazw domen (IDN).|  
|[\<iriParsing >, element (ustawienia identyfikatora URI)](iriparsing-element-uri-settings.md)|Określa, czy do <xref:System.Uri> ma być stosowana analiza międzynarodowego identyfikatora zasobów (IRI) i czy mają być stosowane reguły analizy IRI.|  
|[\<schemeSettings >, element (ustawienia identyfikatora URI)](schemesettings-element-uri-settings.md)|Określa sposób, w jaki <xref:System.Uri> będzie analizowana dla określonych schematów.|  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie aplikacji internetowych](../../../network-programming/configuring-internet-applications.md)
- [Schemat pliku konfiguracji](../index.md)
