---
ms.openlocfilehash: 6c04437c2a211b244e6c5eda0893b267c59668e9
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102775"
---
Nie trzeba uruchamiać, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) ponieważ jest uruchamiany niejawnie przez wszystkie polecenia, które `dotnet new` `dotnet build`wymagają `dotnet run` `dotnet test`przywrócenia, takie jak , , , , `dotnet publish`i `dotnet pack`. Aby wyłączyć niejawne `--no-restore` przywracanie, użyj tej opcji.

Polecenie `dotnet restore` jest nadal przydatne w niektórych scenariuszach, w których jawnie przywracanie ma sens, takie jak [kompilacje ciągłej integracji w usługach Azure DevOps](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować, gdy nastąpi przywracanie.

Aby uzyskać informacje dotyczące zarządzania źródłami danych NuGet, zobacz [ `dotnet restore` dokumentację](../docs/core/tools/dotnet-restore.md).

To polecenie `dotnet restore` obsługuje opcje przekazywane w postaci długiej (na przykład `--source`). Krótkie opcje formularza, `-s`takie jak , nie są obsługiwane.
