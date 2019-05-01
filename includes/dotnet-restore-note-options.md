---
ms.openlocfilehash: 319aca3c5edea7e7bb64fe9081d9f23d3012ff9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648632"
---
> [!NOTE]
> Począwszy od programu .NET Core 2.0, nie trzeba uruchamiać [ `dotnet restore` ](~/docs/core/tools/dotnet-restore.md) , ponieważ jest ona uruchamiana niejawnie przez wszystkie polecenia, takie jak `dotnet build` i `dotnet run`, przywracanie wystąpienia, które wymagają. Nadal jest prawidłowe polecenie, w niektórych scenariuszach, gdzie wykonując jawne przywracanie ma sens, takich jak [kompilacje ciągłej integracji w usługach Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) lub w systemach kompilacji, które wymagają, aby jawnie kontrolować czas, w którym występuje, przywracania.
>
> To polecenie obsługuje również `dotnet restore` opcji, gdy dane są przekazywane w długich fragmentów (na przykład `--source`). Krótkie Opcje formularza, takie jak `-s`, nie są obsługiwane.