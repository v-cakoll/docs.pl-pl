---
ms.openlocfilehash: 15418d1ac3ade6a0fa35ca61a02134e20af1baea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602979"
---

Podczas instalowania pakietu .NET Core może zostać wyświetlony komunikat o błędzie podobny do `Failed to fetch ... File has unexpected size ... Mirror sync in progress?` . Ten błąd może oznaczać, że kanał informacyjny pakietu dla platformy .NET Core jest uaktualniany z nowszymi wersjami pakietu i należy spróbować ponownie później. Podczas uaktualniania kanał informacyjny pakietu nie powinien być dostępny przez ponad 30 minut. Jeśli ten błąd będzie ciągle wyświetlany przez ponad 30 minut, należy rozwiązać problem o <https://github.com/dotnet/core/issues> .
