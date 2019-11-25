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
ms.openlocfilehash: 030841330ff37cddb0c9e3e466a55a4be098e784
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088790"
---
# <a name="web-settings-schema"></a>Schemat ustawień sieci Web
Ustawienia sieci Web określają ustawienia ASP.NET procesora i wykonania, które mają zastosowanie do zachowania całego procesu zarządzanego przez warstwę hostingu ASP.NET. Te ustawienia różnią się od ustawień typu domeny aplikacji, które są określone w pliku Web. config aplikacji ASP.NET.  
  
Ustawienia sieci Web są zawarte w plikach ASPNET. config, które znajdują się w folderach instalacyjnych dla wersji .NET Framework. Na przykład plik ASPNET. config dla .NET Framework 2,0 znajduje się w następującym folderze:  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
Ustawienia sieci Web nie są używane w innych plikach konfiguracyjnych, takich jak plik Machine. config, główny Web. config lub plik Web. config na poziomie aplikacji.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<system. web >** ](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<applicationPool >** ](applicationpool-element-web-settings.md)

|Element|Opis|  
|-------------|-----------------|  
|[\<> System. Web](system-web-element-web-settings.md)|Zawiera informacje, które są używane przez warstwę hostingu ASP.NET.|  
|[\<applicationPool >](applicationpool-element-web-settings.md)|Określa ustawienia ASP.NET na poziomie procesora i wykonania, które mają zastosowanie do zachowania całego procesu zarządzanego przez warstwę hostingu ASP.NET.|  
  
## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
