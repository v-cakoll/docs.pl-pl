---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102748"
---
<span data-ttu-id="fcf95-101">Nie trzeba uruchamiać programu [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , ponieważ jest on uruchamiany niejawnie przez wszystkie polecenia, które wymagają wykonania przywracania, takie jak,,,, `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` i `dotnet pack` .</span><span class="sxs-lookup"><span data-stu-id="fcf95-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="fcf95-102">Aby wyłączyć Przywracanie niejawne, użyj `--no-restore` opcji.</span><span class="sxs-lookup"><span data-stu-id="fcf95-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="fcf95-103">`dotnet restore`Polecenie jest nadal przydatne w niektórych scenariuszach, w których jawne jest przywracanie, takie jak [kompilacje ciągłej integracji w Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować po wystąpieniu przywracania.</span><span class="sxs-lookup"><span data-stu-id="fcf95-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="fcf95-104">Informacje o sposobach zarządzania źródłami danych NuGet znajdują się w [ `dotnet restore` dokumentacji](../docs/core/tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="fcf95-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
