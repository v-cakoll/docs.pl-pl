---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920741"
---

Podczas instalowania pakietu .NET Core może zostać wyświetlony komunikat o błędzie podobny do `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`. Ogólnie mówiąc, ten błąd oznacza, że źródło danych pakietu dla platformy .NET Core jest uaktualniane z nowszymi wersjami pakietów i należy spróbować ponownie później. Podczas uaktualniania kanał informacyjny pakietu nie powinien być dostępny przez więcej niż 2 godziny. Jeśli ten błąd będzie ciągle wyświetlany przez ponad 2 godziny, należy rozwiązać problem w <https://github.com/dotnet/core/issues>.
