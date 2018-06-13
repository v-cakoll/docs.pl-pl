---
title: Schemat ustawień sieci Web
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 93d0d2ea5cf3b0329d9b1a03a233cff2d8133072
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767482"
---
# <a name="web-settings-schema"></a>Schemat ustawień sieci Web
Ustawienia sieci Web Określ procesora CPU i poziom wykonywania ustawień programu ASP.NET, które są stosowane do całego procesu zachowanie zarządzane przez program ASP.NET hosting warstwy. Te ustawienia różnią się od ustawienia Typ domeny aplikacji, które są określone w pliku Web.config aplikacji ASP.NET.  
  
 Ustawienia sieci Web znajdują się w plikach konfigurację Aspnet.config, które znajdują się w folderach instalacji wersji programu .NET Framework. Na przykład plik konfigurację Aspnet.config dla [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] znajduje się w następującym folderze:  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Ustawienia sieci Web nie są używane w innych plikach konfiguracji przykład pliku machine.config, główny plik Web.config lub plików Web.config w poziomie aplikacji.  
  
 [\<Konfiguracja > — Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<System.Web > elementu (ustawienia sieci Web)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [\<applicationPool > elementu (ustawienia sieci Web)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Zawiera informacje, które korzysta z warstwy hostingu ASP.NET.|  
|[\<ApplicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Określa procesora CPU i poziom wykonywania ustawień programu ASP.NET, które są stosowane do całego procesu zachowanie zarządzane przez program ASP.NET hosting warstwy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
