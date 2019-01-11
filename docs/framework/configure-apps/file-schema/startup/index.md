---
title: Schemat ustawień uruchamiania
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0a03438968f487f574606f415fb9d43223030038
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222158"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="8c1e6-102">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="8c1e6-102">Startup settings schema</span></span>

<span data-ttu-id="8c1e6-103">Ustawienia uruchamiania określić wersję środowiska uruchomieniowego języka wspólnego, należy uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8c1e6-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="8c1e6-104">Element</span><span class="sxs-lookup"><span data-stu-id="8c1e6-104">Element</span></span>|<span data-ttu-id="8c1e6-105">Opis</span><span class="sxs-lookup"><span data-stu-id="8c1e6-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c1e6-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="8c1e6-106">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="8c1e6-107">Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="8c1e6-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="8c1e6-108">Skorzystaj z aplikacji utworzonych za pomocą środowiska uruchomieniowego wersji 1.1  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="8c1e6-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="8c1e6-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="8c1e6-109">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="8c1e6-110">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="8c1e6-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="8c1e6-111">\<Uruchamianie ></span><span class="sxs-lookup"><span data-stu-id="8c1e6-111">\<startup></span></span>](startup-element.md)|<span data-ttu-id="8c1e6-112">Zawiera  **\<requiredRuntime >** i  **\<supportedRuntime >** elementów.</span><span class="sxs-lookup"><span data-stu-id="8c1e6-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c1e6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c1e6-113">See also</span></span>

- [<span data-ttu-id="8c1e6-114">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8c1e6-114">Configuration File Schema</span></span>](../index.md)  
- [<span data-ttu-id="8c1e6-115">Instrukcje: Konfigurowanie aplikacji do obsługi w programie .NET Framework 4 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="8c1e6-115">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)