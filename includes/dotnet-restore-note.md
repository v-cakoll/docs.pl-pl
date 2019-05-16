---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632113"
---
> [!NOTE]
> Począwszy od programu .NET Core 2.0 SDK, nie trzeba uruchamiać [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) , ponieważ jest uruchamiane domyślnie przez wszystkie polecenia, które wymagają Przywracanie wystąpienia, takie jak `dotnet new`, `dotnet build` i `dotnet run`.
> Nadal jest prawidłowe polecenie, w niektórych scenariuszach, gdzie wykonując jawne przywracanie ma sens, takich jak [kompilacje ciągłej integracji w usługach Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które wymagają, aby jawnie kontrolować czas, w którym występuje, przywracania.
