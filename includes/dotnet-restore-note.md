---
ms.openlocfilehash: 95fd83d517096eecb69e57f15c8c70f497a290b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646952"
---
> [!NOTE]
> Począwszy od programu .NET Core 2.0 SDK, nie trzeba uruchamiać [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) , ponieważ jest uruchamiane domyślnie przez wszystkie polecenia, które wymagają Przywracanie wystąpienia, takie jak `dotnet new`, `dotnet build` i `dotnet run`.
> Nadal jest prawidłowe polecenie, w niektórych scenariuszach, gdzie wykonując jawne przywracanie ma sens, takich jak [kompilacje ciągłej integracji w usługach Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które wymagają, aby jawnie kontrolować czas, w którym występuje, przywracania.