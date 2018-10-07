---
title: Zestawy wieloplikowe
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f319ef94a5a0f1a5239a2f506386dbc15f0505ef
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846425"
---
# <a name="multifile-assemblies"></a>Zestawy wieloplikowe

Można utworzyć zestawy wieloplikowe, za pomocą kompilatorów wiersza polecenia lub programu Visual Studio z programem Visual C++. Jeden plik w zestawie musi zawierać manifest zestawu. Zestaw, który uruchamia aplikację musi również zawierać punkt wejścia, takich jak metoda Main lub WinMain.

Na przykład załóżmy, że gdy masz już aplikację, która zawiera dwa moduły kodu Client.cs i Stringer.cs. Tworzy Stringer.cs `myStringer` przestrzeni nazw, która odwołuje się kod w Client.cs. Zawiera Client.cs `Main` metoda, która jest punkt wejścia aplikacji. W tym przykładzie skompilować modułów kodu dwa, a następnie utwórz trzeci plik, który zawiera manifest zestawu, który uruchamia aplikację. Manifest zestawu odwołuje się do zarówno `Client` i `Stringer` modułów.

> [!NOTE]
> Zestawy wieloplikowe może mieć tylko jeden wpis punktu, nawet jeśli zestaw ma wiele modułów kodu.

Istnieje kilka powodów, warto utworzyć zestaw wieloplikowy:

-   Aby połączyć modułów napisanych w różnych językach. Jest to najbardziej typowe przyczyny tworzenia zestawu wieloplikowego.

-   Aby zoptymalizować, pobierania aplikacji poprzez umieszczenie rzadko używanych typów w module, który jest pobierany tylko wtedy, gdy jest to wymagane.

    > [!NOTE]
    > Jeśli tworzysz aplikacje, które będą pobierane przy użyciu `<object>` tagu za pomocą programu Microsoft Internet Explorer jest ważne, aby utworzyć zestawy wieloplikowe. W tym scenariuszu utworzysz plik oddzielnie od moduły kodu, które zawiera jedynie manifestu zestawu. Program Internet Explorer pliki do pobrania manifestu zestawu, a następnie tworzy wątków do pobierania dodatkowych modułów ani zestawów wymaganych. Podczas pobierania pliku zawierającego manifest zestawu Internet Explorer będzie odpowiadać na dane wejściowe użytkownika. Mniejszy plik zawierający manifest zestawu, tym krótszy czas programu Internet Explorer będzie odpowiadać.

-   Aby połączyć modułów kodu, napisanych przez wielu deweloperów. Mimo że każdy deweloper może skompilować poszczególnych modułów kodu do zestawu, to wymuszenie pewnych typów publicznie narażonych, które nie są widoczne, jeśli wszystkie moduły są umieszczane w zestawu wieloplikowego.

Po utworzeniu zestawu, możesz utworzyć plik, który zawiera manifest zestawu (i tym samym zestawie), lub możesz nadać silnej nazwy pliku (i zestawu) i umieścić go w globalnej pamięci podręcznej.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: kompilacja zestawów wieloplikowych](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)