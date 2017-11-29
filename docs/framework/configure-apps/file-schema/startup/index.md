---
title: "Schemat ustawień uruchamiania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 61ea6d0c974683e73e835720cff48ff84169217e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="startup-settings-schema"></a><span data-ttu-id="e0f46-102">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="e0f46-102">Startup Settings Schema</span></span>
<span data-ttu-id="e0f46-103">Ustawienia uruchamiania Określ wersję środowiska CLR, które należy uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="e0f46-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="e0f46-104">Element</span><span class="sxs-lookup"><span data-stu-id="e0f46-104">Element</span></span>|<span data-ttu-id="e0f46-105">Opis</span><span class="sxs-lookup"><span data-stu-id="e0f46-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0f46-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="e0f46-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="e0f46-107">Określa, czy aplikacja obsługuje tylko wersję 1.0 środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e0f46-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="e0f46-108">Należy użyć aplikacji skompilowanej za pomocą środowiska wykonawczego w wersji 1.1  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="e0f46-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="e0f46-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="e0f46-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="e0f46-110">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="e0f46-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="e0f46-111">\<Uruchamianie ></span><span class="sxs-lookup"><span data-stu-id="e0f46-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="e0f46-112">Zawiera  **\<requiredRuntime >** i  **\<supportedRuntime >** elementów.</span><span class="sxs-lookup"><span data-stu-id="e0f46-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0f46-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0f46-113">See Also</span></span>  
 [<span data-ttu-id="e0f46-114">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e0f46-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e0f46-115">\<PaveOver > Określanie wersji środowiska uruchomieniowego do użycia</span><span class="sxs-lookup"><span data-stu-id="e0f46-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
