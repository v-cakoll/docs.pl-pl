---
title: Schemat ustawień sieci
description: Informacje o schemacie dla ustawień sieci, które określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem i obsługuje identyfikatory URI.
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
ms.openlocfilehash: 6a22d7f1608db2e8909d0ead11e9110ec8a8a2c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504579"
---
# <a name="network-settings-schema"></a>Schemat ustawień sieci
Ustawienia sieci określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem.

\<system.net>Ustawienia określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią. W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [ \<system.Net> elementu (Ustawienia sieci)](system-net-element-network-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<authenticationModules>— Element (Ustawienia sieci)](authenticationmodules-element-network-settings.md)|Określa moduły używane do uwierzytelniania żądań internetowych.|  
|[\<connectionManagement>— Element (Ustawienia sieci)](connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostami internetowymi.|  
|[\<defaultProxy>— Element (Ustawienia sieci)](defaultproxy-element-network-settings.md)|Określa serwer proxy używany przez żądania HTTP do Internetu.|  
|[\<mailSettings>— Element (Ustawienia sieci)](mailsettings-element-network-settings.md)|Zawiera ustawienia dla opcji wysyłania poczty.|  
|[\<requestCaching>— Element (Ustawienia sieci)](requestcaching-element-network-settings.md)|Kontroluje mechanizm buforowania dla żądań sieci.|  
|[\<webRequestModules>— Element (Ustawienia sieci)](webrequestmodules-element-network-settings.md)|Określa moduły używane do żądania informacji z hostów internetowych.|  
  
\<uri>Ustawienia określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI). W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [ \<uri> elementu (ustawienia identyfikatora URI)](uri-element-uri-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<idn>— Element (ustawienia identyfikatora URI)](idn-element-uri-settings.md)|Określa, czy do nazw domen są stosowane analizowanie międzynarodowych nazw domen (IDN).|  
|[\<iriParsing>— Element (ustawienia identyfikatora URI)](iriparsing-element-uri-settings.md)|Określa, czy do <xref:System.Uri> i czy należy zastosować analizę IRI (International Resource Identifier).|  
|[\<schemeSettings>— Element (ustawienia identyfikatora URI)](schemesettings-element-uri-settings.md)|Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.|  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie aplikacji internetowych](../../../network-programming/configuring-internet-applications.md)
- [Schemat pliku konfiguracji](../index.md)
