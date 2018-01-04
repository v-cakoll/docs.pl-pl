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
ms.workload: dotnet
ms.openlocfilehash: a4ece61330fe8e41d9afb894791f9f9e36db35f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="web-settings-schema"></a><span data-ttu-id="c12a6-102">Schemat ustawień sieci Web</span><span class="sxs-lookup"><span data-stu-id="c12a6-102">Web Settings Schema</span></span>
<span data-ttu-id="c12a6-103">Ustawienia sieci Web Określ procesora CPU i poziom wykonywania ustawień programu ASP.NET, które są stosowane do całego procesu zachowanie zarządzane przez program ASP.NET hosting warstwy.</span><span class="sxs-lookup"><span data-stu-id="c12a6-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="c12a6-104">Te ustawienia różnią się od ustawienia Typ domeny aplikacji, które są określone w pliku Web.config aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c12a6-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="c12a6-105">Ustawienia sieci Web znajdują się w plikach konfigurację Aspnet.config, które znajdują się w folderach instalacji wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c12a6-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="c12a6-106">Na przykład plik konfigurację Aspnet.config dla [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] znajduje się w następującym folderze:</span><span class="sxs-lookup"><span data-stu-id="c12a6-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="c12a6-107">Ustawienia sieci Web nie są używane w innych plikach konfiguracji przykład pliku machine.config, główny plik Web.config lub plików Web.config w poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c12a6-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="c12a6-108">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="c12a6-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="c12a6-109">\<System.Web > elementu (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="c12a6-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="c12a6-110">\<applicationPool > elementu (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="c12a6-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="c12a6-111">Element</span><span class="sxs-lookup"><span data-stu-id="c12a6-111">Element</span></span>|<span data-ttu-id="c12a6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c12a6-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c12a6-113">\<System.Web ></span><span class="sxs-lookup"><span data-stu-id="c12a6-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="c12a6-114">Zawiera informacje, które korzysta z warstwy hostingu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c12a6-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="c12a6-115">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="c12a6-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="c12a6-116">Określa procesora CPU i poziom wykonywania ustawień programu ASP.NET, które są stosowane do całego procesu zachowanie zarządzane przez program ASP.NET hosting warstwy.</span><span class="sxs-lookup"><span data-stu-id="c12a6-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c12a6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c12a6-117">See Also</span></span>  
 [<span data-ttu-id="c12a6-118">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c12a6-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
