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
# <a name="web-settings-schema"></a><span data-ttu-id="b7657-102">Schemat ustawień sieci Web</span><span class="sxs-lookup"><span data-stu-id="b7657-102">Web Settings Schema</span></span>
<span data-ttu-id="b7657-103">Ustawienia sieci Web określają ustawienia ASP.NET procesora i wykonania, które mają zastosowanie do zachowania całego procesu zarządzanego przez warstwę hostingu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7657-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="b7657-104">Te ustawienia różnią się od ustawień typu domeny aplikacji, które są określone w pliku Web. config aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7657-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
<span data-ttu-id="b7657-105">Ustawienia sieci Web są zawarte w plikach ASPNET. config, które znajdują się w folderach instalacyjnych dla wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7657-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="b7657-106">Na przykład plik ASPNET. config dla .NET Framework 2,0 znajduje się w następującym folderze:</span><span class="sxs-lookup"><span data-stu-id="b7657-106">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
<span data-ttu-id="b7657-107">Ustawienia sieci Web nie są używane w innych plikach konfiguracyjnych, takich jak plik Machine. config, główny Web. config lub plik Web. config na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b7657-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  

<span data-ttu-id="b7657-108">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b7657-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b7657-109">&nbsp;&nbsp;[ **\<system. web >** ](system-web-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b7657-109">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span></span>\
<span data-ttu-id="b7657-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<applicationPool >** ](applicationpool-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b7657-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)</span></span>

|<span data-ttu-id="b7657-111">Element</span><span class="sxs-lookup"><span data-stu-id="b7657-111">Element</span></span>|<span data-ttu-id="b7657-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b7657-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7657-113">\<> System. Web</span><span class="sxs-lookup"><span data-stu-id="b7657-113">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="b7657-114">Zawiera informacje, które są używane przez warstwę hostingu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7657-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="b7657-115">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="b7657-115">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="b7657-116">Określa ustawienia ASP.NET na poziomie procesora i wykonania, które mają zastosowanie do zachowania całego procesu zarządzanego przez warstwę hostingu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7657-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7657-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7657-117">See also</span></span>

- [<span data-ttu-id="b7657-118">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b7657-118">Configuration File Schema</span></span>](../index.md)
