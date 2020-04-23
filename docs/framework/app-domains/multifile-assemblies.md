---
title: Zestawy wieloplikowe
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: 2a70e45d50763cf99c55cf08600c3c816b4043b7
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644208"
---
# <a name="multifile-assemblies"></a>Zestawy wieloplikowe

Można tworzyć zestawy wieloplikowe przeznaczone dla .NET Framework przy użyciu kompilatorów wiersza polecenia lub programu Visual Studio z Visual C++. Jeden plik w zestawie musi zawierać manifest zestawu. Zestaw, który uruchamia aplikację, musi również zawierać punkt wejścia, taki jak `Main` lub. `WinMain`

Załóżmy na przykład, że masz aplikację, która zawiera dwa moduły kodu, *Client.cs* i *Stringer.cs*. *Stringer.cs* tworzy `myStringer` przestrzeń nazw, do której odwołuje się kod w *Client.cs*. *Client.cs* zawiera `Main` metodę, która jest punktem wejścia aplikacji. W tym przykładzie kompilujesz dwa moduły kodu, a następnie utworzysz trzeci plik, który zawiera manifest zestawu, który uruchamia aplikację. Manifest zestawu odwołuje się zarówno do modułów *klienta* , jak i *Stringer* .

> [!NOTE]
> Zestawy wieloplikowe mogą mieć tylko jeden punkt wejścia, nawet jeśli zestaw ma wiele modułów kodu.

Istnieje kilka powodów, dla których warto utworzyć zestaw wieloplikowy:

- Do łączenia modułów pisanych w różnych językach. Jest to najbardziej typowy powód tworzenia zestawu wieloplikowego.

- Aby zoptymalizować pobieranie aplikacji przez umieszczenie rzadko używanych typów w module, który jest pobierany tylko wtedy, gdy jest to konieczne.

    > [!NOTE]
    > Jeśli tworzysz aplikacje, które zostaną pobrane przy użyciu `<object>` znacznika programu Microsoft Internet Explorer, ważne jest, aby utworzyć zestawy wieloplikowe. W tym scenariuszu utworzysz plik oddzielony od modułów kodu, który zawiera tylko manifest zestawu. Program Internet Explorer najpierw pobierze manifest zestawu, a następnie utworzy wątki robocze do pobrania wymaganych modułów lub zestawów. Podczas pobierania pliku zawierającego manifest zestawu program Internet Explorer nie będzie odpowiadać na dane wejściowe użytkownika. Im mniejszy plik zawierający manifest zestawu, tym mniej czasu program Internet Explorer nie odpowiada.

- Do łączenia modułów kodu pisanych przez kilku deweloperów. Chociaż każdy deweloper może kompilować każdy moduł kodu do zestawu, może to spowodować, że niektóre typy mają być ujawnione publicznie, które nie są ujawniane, jeśli wszystkie moduły są umieszczane w zestawie wieloplikowym.

Po utworzeniu zestawu można podpisać plik, który zawiera manifest zestawu, a tym samym zestaw lub można nadać plikowi i zestawowi silną nazwę i umieścić go w globalnej pamięci podręcznej zestawów.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: kompilowanie zestawu wieloplikowego](build-multifile-assembly.md)
- [Programowanie przy użyciu zestawów](../../standard/assembly/index.md)
