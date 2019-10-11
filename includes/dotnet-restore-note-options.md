---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179985"
---
> [!NOTE]
> Począwszy od platformy .NET Core 2,0, nie trzeba uruchamiać [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , ponieważ jest ona uruchamiana niejawnie przez wszystkie polecenia, które wymagają wykonania przywracania, takie jak `dotnet build` i `dotnet run`. Nadal jest to prawidłowe polecenie w niektórych scenariuszach, w których wykonywanie jawnego przywracania ma sens, na przykład [w przypadku kompilacji ciągłej integracji w Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować czas, w którym następuje przywracanie.
>
> To polecenie obsługuje również opcje `dotnet restore`, gdy są przesyłane w postaci długiej (na przykład `--source`). Opcje krótkiej formy, takie jak `-s`, nie są obsługiwane.
