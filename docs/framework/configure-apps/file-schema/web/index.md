---
title: "Schemat ustawień sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: efdfba94bd2d2a64b3434c97f30a035f210fda9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
|[\<System.Web >](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Zawiera informacje, które korzysta z warstwy hostingu ASP.NET.|  
|[\<applicationPool >](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|Określa procesora CPU i poziom wykonywania ustawień programu ASP.NET, które są stosowane do całego procesu zachowanie zarządzane przez program ASP.NET hosting warstwy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
