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
manager: markl
ms.openlocfilehash: 68f37e3efca784b94be90d5779c9bc402f144448
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530337"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="8345a-102">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="8345a-102">Startup Settings Schema</span></span>
<span data-ttu-id="8345a-103">Ustawienia uruchamiania określić wersję środowiska uruchomieniowego języka wspólnego, należy uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8345a-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="8345a-104">Element</span><span class="sxs-lookup"><span data-stu-id="8345a-104">Element</span></span>|<span data-ttu-id="8345a-105">Opis</span><span class="sxs-lookup"><span data-stu-id="8345a-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8345a-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="8345a-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="8345a-107">Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="8345a-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="8345a-108">Skorzystaj z aplikacji utworzonych za pomocą środowiska uruchomieniowego wersji 1.1  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="8345a-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="8345a-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="8345a-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="8345a-110">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="8345a-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="8345a-111">\<Uruchamianie ></span><span class="sxs-lookup"><span data-stu-id="8345a-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="8345a-112">Zawiera  **\<requiredRuntime >** i  **\<supportedRuntime >** elementów.</span><span class="sxs-lookup"><span data-stu-id="8345a-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8345a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8345a-113">See Also</span></span>  
 [<span data-ttu-id="8345a-114">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8345a-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="8345a-115">\<PaveOver > Określanie wersji środowiska uruchomieniowego, które ma być używana</span><span class="sxs-lookup"><span data-stu-id="8345a-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
