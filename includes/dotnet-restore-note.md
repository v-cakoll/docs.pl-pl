---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102748"
---
Nie trzeba uruchamiać programu [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) , ponieważ jest on uruchamiany niejawnie przez wszystkie polecenia, które wymagają wykonania przywracania, takie jak,,,, `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` i `dotnet pack` . Aby wyłączyć Przywracanie niejawne, użyj `--no-restore` opcji.

`dotnet restore`Polecenie jest nadal przydatne w niektórych scenariuszach, w których jawne jest przywracanie, takie jak [kompilacje ciągłej integracji w Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować po wystąpieniu przywracania.

Informacje o sposobach zarządzania źródłami danych NuGet znajdują się w [ `dotnet restore` dokumentacji](../docs/core/tools/dotnet-restore.md).
