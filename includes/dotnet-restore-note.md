---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632113"
---
> [!NOTE]
> Począwszy od .NET Core 2.0 SDK, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) nie trzeba uruchamiać, ponieważ jest uruchamiany niejawnie przez `dotnet new` `dotnet build` wszystkie `dotnet run`polecenia, które wymagają przywrócenia występuje, takich jak , i .
> Jest to nadal prawidłowe polecenie w niektórych scenariuszach, w których wykonywanie jawnego przywracania ma sens, takich jak [kompilacje ciągłej integracji w usłudze Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które muszą jawnie kontrolować czas, w którym występuje przywracanie.
