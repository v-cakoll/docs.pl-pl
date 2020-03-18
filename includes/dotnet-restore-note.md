---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632113"
---
> [!NOTE]
> <span data-ttu-id="6057d-101">Począwszy od .NET Core 2.0 SDK, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) nie trzeba uruchamiać, ponieważ jest uruchamiany niejawnie przez `dotnet new` `dotnet build` wszystkie `dotnet run`polecenia, które wymagają przywrócenia występuje, takich jak , i .</span><span class="sxs-lookup"><span data-stu-id="6057d-101">Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`.</span></span>
> <span data-ttu-id="6057d-102">Jest to nadal prawidłowe polecenie w niektórych scenariuszach, w których wykonywanie jawnego przywracania ma sens, takich jak [kompilacje ciągłej integracji w usłudze Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować czas, w którym występuje przywracanie.</span><span class="sxs-lookup"><span data-stu-id="6057d-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
