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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5783e63d81c8951afb6b1646b595fc619d51549c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193583"
---
# <a name="network-settings-schema"></a>Schemat ustawień sieci
Ustawienia sieci Określ, jak .NET Framework łączy się z Internetem. W poniższej tabeli opisano funkcję każdego elementu podrzędnego konfiguracji, w obszarze [ \<przestrzeni nazw system.Net >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<authenticationModules >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Określa moduły używane do uwierzytelniania żądań internetowych.|  
|[\<connectionManagement >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń na hostach w Internecie.|  
|[\<defaultProxy — >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Określa serwer proxy dla żądań HTTP w Internecie.|  
|[\<mailSettings — >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Zawiera ustawienia dla opcje wysyłania poczty.|  
|[\<requestCaching — >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Określa mechanizm buforowania żądań sieci.|  
|[\<webRequestModules >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Określa moduły używane do żądania informacji z hostów w Internecie.|  
  
 Ustawienia identyfikatorów URI Określ, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI). W poniższej tabeli opisano funkcję każdego elementu podrzędnego konfiguracji, w obszarze [ \<Uri >, Element (ustawienia identyfikatora Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<IDN >, Element (ustawienia identyfikatora Uri)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Określa, jeśli analizy Zinternacjonalizowanych nazw domen (IDN) są stosowane do nazw domen.|  
|[\<iriParsing >, Element (ustawienia identyfikatora Uri)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Określa, jeśli analizy międzynarodowego identyfikatora zasobów (IRI) są stosowane do <xref:System.Uri> , czy powinna być stosowana IRI podczas analizowania reguły.|  
|[\<schemeSettings >, Element (ustawienia identyfikatora Uri)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie aplikacji internetowych](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
