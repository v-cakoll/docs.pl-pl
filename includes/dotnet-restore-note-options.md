---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179985"
---
> [!NOTE]
> <span data-ttu-id="50d32-101">Począwszy od .NET Core 2.0, nie [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) trzeba uruchamiać, ponieważ jest uruchamiany niejawnie przez `dotnet build` wszystkie `dotnet run`polecenia, które wymagają przywrócenia występuje, takich jak i .</span><span class="sxs-lookup"><span data-stu-id="50d32-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="50d32-102">Jest to nadal prawidłowe polecenie w niektórych scenariuszach, w których wykonywanie jawnego przywracania ma sens, takich jak [kompilacje ciągłej integracji w usłudze Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować czas, w którym występuje przywracanie.</span><span class="sxs-lookup"><span data-stu-id="50d32-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="50d32-103">To polecenie obsługuje `dotnet restore` również opcje po przekazaniu w `--source`długiej formie (na przykład).</span><span class="sxs-lookup"><span data-stu-id="50d32-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="50d32-104">Opcje krótkiej formy, takie jak `-s`, nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="50d32-104">Short form options, such as `-s`, are not supported.</span></span>
