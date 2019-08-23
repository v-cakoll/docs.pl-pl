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
ms.openlocfilehash: d53d3a105203addfacb1c982e0960bd12996f571
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941423"
---
# <a name="web-settings-schema"></a>Schemat ustawień sieci Web
Ustawienia sieci Web określają ustawienia ASP.NET procesora i wykonania, które mają zastosowanie do zachowania całego procesu zarządzanego przez warstwę hostingu ASP.NET. Te ustawienia różnią się od ustawień typu domeny aplikacji, które są określone w pliku Web. config aplikacji ASP.NET.  
  
 Ustawienia sieci Web są zawarte w plikach ASPNET. config, które znajdują się w folderach instalacyjnych dla wersji .NET Framework. Na przykład plik ASPNET. config dla .NET Framework 2,0 znajduje się w następującym folderze:  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Ustawienia sieci Web nie są używane w innych plikach konfiguracyjnych, takich jak plik Machine. config, główny Web. config lub plik Web. config na poziomie aplikacji.  
  
 [\<> elementu konfiguracji](../configuration-element.md)  
  
 [\<System. Web >, element (Ustawienia sieci Web)](system-web-element-web-settings.md)  
  
 [\<applicationPool >, element (Ustawienia sieci Web)](applicationpool-element-web-settings.md)  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|Zawiera informacje, które są używane przez warstwę hostingu ASP.NET.|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|Określa ustawienia ASP.NET na poziomie procesora i wykonania, które mają zastosowanie do zachowania całego procesu zarządzanego przez warstwę hostingu ASP.NET.|  
  
## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
