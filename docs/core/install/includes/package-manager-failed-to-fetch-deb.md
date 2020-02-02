---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920656"
---

Podczas instalowania pakietu .NET Core może zostać wyświetlony komunikat o błędzie podobny do `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`. Ogólnie mówiąc, ten błąd oznacza, że źródło danych pakietu dla platformy .NET Core jest uaktualniane z nowszymi wersjami pakietów i należy spróbować ponownie później. Podczas uaktualniania kanał informacyjny pakietu nie powinien być dostępny przez ponad 30 minut. Jeśli ten błąd będzie ciągle wyświetlany przez ponad 30 minut, należy rozwiązać problem w <https://github.com/dotnet/core/issues>.
