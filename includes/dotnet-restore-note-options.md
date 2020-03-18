---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179985"
---
> [!NOTE]
> Począwszy od .NET Core 2.0, nie [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) trzeba uruchamiać, ponieważ jest uruchamiany niejawnie przez `dotnet build` wszystkie `dotnet run`polecenia, które wymagają przywrócenia występuje, takich jak i . Jest to nadal prawidłowe polecenie w niektórych scenariuszach, w których wykonywanie jawnego przywracania ma sens, takich jak [kompilacje ciągłej integracji w usłudze Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować czas, w którym występuje przywracanie.
>
> To polecenie obsługuje `dotnet restore` również opcje po przekazaniu w `--source`długiej formie (na przykład). Opcje krótkiej formy, takie jak `-s`, nie są obsługiwane.
