---
title: Schemat ustawień uruchamiania
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701518"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="d3545-102">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="d3545-102">Startup settings schema</span></span>

<span data-ttu-id="d3545-103">Ustawienia uruchamiania określają wersję środowiska uruchomieniowego języka wspólnego, która powinna uruchamiać aplikację.</span><span class="sxs-lookup"><span data-stu-id="d3545-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="d3545-104">Element</span><span class="sxs-lookup"><span data-stu-id="d3545-104">Element</span></span>|<span data-ttu-id="d3545-105">Opis</span><span class="sxs-lookup"><span data-stu-id="d3545-105">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="d3545-106">Określa, że aplikacja obsługuje tylko wersję 1,0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="d3545-106">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="d3545-107">Aplikacje skompilowane przy użyciu środowiska uruchomieniowego w wersji 1,1 powinny używać **\<supportedRuntime>** elementu.</span><span class="sxs-lookup"><span data-stu-id="d3545-107">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="d3545-108">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="d3545-108">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="d3545-109">Zawiera **\<requiredRuntime>** elementy i **\<supportedRuntime>** .</span><span class="sxs-lookup"><span data-stu-id="d3545-109">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3545-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3545-110">See also</span></span>

- [<span data-ttu-id="d3545-111">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d3545-111">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d3545-112">Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji</span><span class="sxs-lookup"><span data-stu-id="d3545-112">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
