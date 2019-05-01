---
ms.openlocfilehash: 95fd83d517096eecb69e57f15c8c70f497a290b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646952"
---
> [!NOTE]
> <span data-ttu-id="03228-101">Począwszy od programu .NET Core 2.0 SDK, nie trzeba uruchamiać [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) , ponieważ jest uruchamiane domyślnie przez wszystkie polecenia, które wymagają Przywracanie wystąpienia, takie jak `dotnet new`, `dotnet build` i `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="03228-101">Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`.</span></span>
> <span data-ttu-id="03228-102">Nadal jest prawidłowe polecenie, w niektórych scenariuszach, gdzie wykonując jawne przywracanie ma sens, takich jak [kompilacje ciągłej integracji w usługach Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które wymagają, aby jawnie kontrolować czas, w którym występuje, przywracania.</span><span class="sxs-lookup"><span data-stu-id="03228-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>