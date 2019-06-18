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
ms.openlocfilehash: 0fbc28bb7b871cc245d0fe477ea8e15c147549bb
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170021"
---
# <a name="web-settings-schema"></a>Schemat ustawień sieci Web
Ustawienia sieci Web Określ procesora CPU i poziom wykonywania ustawień platformy ASP.NET, które są stosowane do całego procesu zachowanie zarządzanych przez platformę ASP.NET, hostowanie warstwy. Ustawienia te różnią się od ustawienia Typ domeny aplikacji, które są określone w pliku Web.config aplikacji ASP.NET.  
  
 Ustawienia sieci Web są zawarte w plikach Aspnet.config, które znajdują się w folderach instalacji wersji programu .NET Framework. Na przykład plik Aspnet.config dla .NET Framework 2.0, znajduje się w następującym folderze:  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Ustawienia sieci Web nie są używane w innych plikach konfiguracji takich jak plik machine.config, główny plik Web.config lub plików Web.config w poziomie aplikacji.  
  
 [\<Konfiguracja > Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<System.Web >, Element (ustawienia sieci Web)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [\<applicationPool >, Element (ustawienia sieci Web)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Zawiera informacje, które korzysta z warstwy hostingu platformy ASP.NET.|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Określa procesor CPU i poziom wykonywania ustawień platformy ASP.NET, które są stosowane do całego procesu zachowanie zarządzanych przez platformę ASP.NET, hostowanie warstwy.|  
  
## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
