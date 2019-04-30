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
ms.openlocfilehash: 1f0241b65c915dd5703ceea97dd5b07f88832003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698492"
---
# <a name="web-settings-schema"></a><span data-ttu-id="8d9d3-102">Schemat ustawień sieci Web</span><span class="sxs-lookup"><span data-stu-id="8d9d3-102">Web Settings Schema</span></span>
<span data-ttu-id="8d9d3-103">Ustawienia sieci Web Określ procesora CPU i poziom wykonywania ustawień platformy ASP.NET, które są stosowane do całego procesu zachowanie zarządzanych przez platformę ASP.NET, hostowanie warstwy.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="8d9d3-104">Ustawienia te różnią się od ustawienia Typ domeny aplikacji, które są określone w pliku Web.config aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="8d9d3-105">Ustawienia sieci Web są zawarte w plikach Aspnet.config, które znajdują się w folderach instalacji wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="8d9d3-106">Na przykład plik Aspnet.config dla [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] znajduje się w następującym folderze:</span><span class="sxs-lookup"><span data-stu-id="8d9d3-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="8d9d3-107">Ustawienia sieci Web nie są używane w innych plikach konfiguracji takich jak plik machine.config, główny plik Web.config lub plików Web.config w poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="8d9d3-108">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="8d9d3-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="8d9d3-109">\<System.Web >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="8d9d3-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="8d9d3-110">\<applicationPool >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="8d9d3-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="8d9d3-111">Element</span><span class="sxs-lookup"><span data-stu-id="8d9d3-111">Element</span></span>|<span data-ttu-id="8d9d3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8d9d3-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d9d3-113">\<system.web></span><span class="sxs-lookup"><span data-stu-id="8d9d3-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="8d9d3-114">Zawiera informacje, które korzysta z warstwy hostingu platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="8d9d3-115">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="8d9d3-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="8d9d3-116">Określa procesor CPU i poziom wykonywania ustawień platformy ASP.NET, które są stosowane do całego procesu zachowanie zarządzanych przez platformę ASP.NET, hostowanie warstwy.</span><span class="sxs-lookup"><span data-stu-id="8d9d3-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d9d3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d9d3-117">See also</span></span>

- [<span data-ttu-id="8d9d3-118">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8d9d3-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
