---
title: "Schemat ustawień sieci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d8f13b75d0558c002fd29938ce98d85f358acc9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="network-settings-schema"></a>Schemat ustawień sieci
Ustawienia sieci określają, jak programu .NET Framework łączy się z Internetem. W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w obszarze [ \<system.Net > (ustawienia sieciowe) elementu](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<authenticationModules — > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Określa moduły używane do uwierzytelniania żądań Internet.|  
|[\<connectionmanagement — > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostami w Internecie.|  
|[\<defaultProxy — > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Określa serwer proxy do żądań HTTP w Internecie.|  
|[\<mailSettings > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Zawiera ustawienia Opcje wysyłania poczty.|  
|[\<requestCaching — > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Określa moduły używane do żądania informacji z Internetu hostów.|  
|[\<requestCaching — > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw.|  
|[\<webRequestModules — > elementu (ustawienia sieciowe)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Określa moduły używane do żądania informacji z Internetu hostów.|  
  
 Identyfikator URI ustawienia określają, jak programu .NET Framework obsługuje adresy URL wyrazić przy użyciu uniform resource identifier (URI). W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w obszarze [ \<Uri > elementu (ustawienia identyfikatorów Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<IDN > elementu (ustawienia identyfikatorów Uri)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Określa, czy międzynarodowych nazw domen (IDN) podczas analizowania została zastosowana do nazw domen.|  
|[\<iriParsing > elementu (ustawienia identyfikatorów Uri)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Określa identyfikator zasobu międzynarodowych (IRI) podczas analizowania odnosi się do <xref:System.Uri> i określa, czy powinny być stosowane IRI podczas analizowania reguły.|  
|[\<schemeSettings > elementu (ustawienia identyfikatorów Uri)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie aplikacji internetowych](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
