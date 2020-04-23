---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102748"
---
<span data-ttu-id="4972d-101">Nie trzeba uruchamiać, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) ponieważ jest uruchamiany niejawnie przez wszystkie polecenia, które `dotnet new` `dotnet build`wymagają `dotnet run` `dotnet test`przywrócenia, takie jak , , , , `dotnet publish`i `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="4972d-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="4972d-102">Aby wyłączyć niejawne `--no-restore` przywracanie, użyj tej opcji.</span><span class="sxs-lookup"><span data-stu-id="4972d-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="4972d-103">Polecenie `dotnet restore` jest nadal przydatne w niektórych scenariuszach, w których jawnie przywracanie ma sens, takie jak [kompilacje ciągłej integracji w usługach Azure DevOps](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować, gdy nastąpi przywracanie.</span><span class="sxs-lookup"><span data-stu-id="4972d-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="4972d-104">Aby uzyskać informacje dotyczące zarządzania źródłami danych NuGet, zobacz [ `dotnet restore` dokumentację](../docs/core/tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="4972d-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
