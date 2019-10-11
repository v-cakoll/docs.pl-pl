---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179985"
---
> [!NOTE]
> <span data-ttu-id="25692-101">Począwszy od platformy .NET Core 2,0, nie trzeba uruchamiać [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , ponieważ jest ona uruchamiana niejawnie przez wszystkie polecenia, które wymagają wykonania przywracania, takie jak `dotnet build` i `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="25692-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="25692-102">Nadal jest to prawidłowe polecenie w niektórych scenariuszach, w których wykonywanie jawnego przywracania ma sens, na przykład [w przypadku kompilacji ciągłej integracji w Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować czas, w którym następuje przywracanie.</span><span class="sxs-lookup"><span data-stu-id="25692-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="25692-103">To polecenie obsługuje również opcje `dotnet restore`, gdy są przesyłane w postaci długiej (na przykład `--source`).</span><span class="sxs-lookup"><span data-stu-id="25692-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="25692-104">Opcje krótkiej formy, takie jak `-s`, nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="25692-104">Short form options, such as `-s`, are not supported.</span></span>
