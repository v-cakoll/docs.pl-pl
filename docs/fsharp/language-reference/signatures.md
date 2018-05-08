---
title: Podpisy (F#)
description: 'Dowiedz się, jak używać plik sygnatury języka F # do przechowywania informacji o publiczne podpisów zestawu F # program elementów, takich jak typy, obszary nazw i modułów.'
ms.date: 05/16/2016
ms.openlocfilehash: 04539a871dda9eedd1495e0e5b1f3f5026bae037
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="signatures"></a>Podpisy

Plik sygnatury zawiera informacje o publiczne podpisów zestawu F # program elementów, takich jak typy, obszary nazw i modułów. Może służyć do określenia dostępność tych elementów programu.


## <a name="remarks"></a>Uwagi
Dla każdego języka F # pliku kod, mogą mieć *plik sygnatury*, czyli plik, który ma taką samą nazwę jak plik kodu, ale .fsi rozszerzenia zamiast języka. Pliki sygnatur można również dodać do kompilacji wiersza polecenia, korzystając z wiersza polecenia bezpośrednio. Aby odróżnić pliki kodu i pliki podpisów, pliki kodu są czasami określane jako *plików implementacji*. W projekcie plik podpisu należy poprzedzać pliku skojarzonego kodu.

Plik sygnatury opisuje obszary nazw, modułów, typy i elementy członkowskie w odpowiedniego pliku implementacji. Możesz skorzystać z informacji w pliku podpisu do określenia części kodu w odpowiedniej implementacji plików są dostępne z kodu poza pliku implementacji, i jakie elementy są wewnętrzne pliku implementacji. Przestrzenie nazw, moduły i typy, które zostaną uwzględnione w pliku podpis musi być podzbiór przestrzeni nazw, moduły i typy, które znajdują się w pliku implementacji. Z pewnymi wyjątkami zauważyć w dalszej części tego tematu te elementy języka, które nie są wymienione w pliku podpisu są uznawane za prywatne do pliku implementacji. Jeśli plik podpisu nie zostanie znaleziony w projekcie lub wiersza polecenia, dostępność domyślny jest używany.

Aby uzyskać więcej informacji o ułatwieniach dostępu domyślnego, zobacz [kontroli dostępu](access-control.md).

W pliku podpisu nie powtarzaj definicji typów i implementacje każdej metody lub funkcji. W zamian użyj podpis dla każdej metody i funkcji, która działa jako pełną specyfikację funkcji, które jest implementowany przez fragment modułu lub przestrzeni nazw. Składnia podpis typu jest taka sama, jak używać w deklaracjach metoda abstrakcyjna w abstrakcyjnej klasy i interfejsy i jest również wyświetlany za pomocą funkcji IntelliSense i fsi.exe interpreter języka F # wyświetlanych poprawnie skompilowanych danych wejściowych.

Jeśli nie ma wystarczającej ilości informacji w podpisie typu, aby wskazać, czy typ jest zapieczętowany lub czy jest to typ interfejsu, należy dodać atrybut wskazujący rodzaj typu w kompilatorze. W poniższej tabeli opisano atrybuty, które używają do tego celu.



|Atrybut|Opis|
|---------|-----------|
|`[<Sealed>]`|Dla typu, który nie ma abstrakcyjnych elementów członkowskich lub który nie ma zastosowania.|
|`[<Interface>]`|Dla typu, który jest interfejsem.|
Kompilator generuje błąd, jeśli atrybuty nie są spójne podpisu i deklaracji w pliku implementacji.

Użyj słowa kluczowego `val` do tworzenia podpisu wartość lub wartość funkcji. Słowo kluczowe `type` wprowadza podpis typu.

Plik sygnatury można wygenerować za pomocą `--sig` — opcja kompilatora. Ogólnie rzecz biorąc możesz nie zapisuj .fsi pliki ręcznie. Zamiast tego należy wygenerować .fsi plików przy użyciu kompilatora, dodaj je do projektu, jeśli istnieje i edytować je przez usunięcie metod i funkcje, które nie mają być dostępne.

Istnieje kilka reguł sygnatur typu:


- Skróty typów w pliku z implementacją nie musi odpowiadać typu bez skrót w pliku podpisu.


- Rekordów i rozłączne musi ujawniać wszystkie lub żadne swoich pól i konstruktory i kolejności w sygnaturze musi odpowiadać kolejności w pliku implementacji. Klasy może ujawnić niektóre, wszystkie lub żadne swoich pól i metod w podpisie.


- Klasy i struktury, które mają konstruktorów musi ujawniać deklaracji ich klas podstawowych ( `inherits` deklaracji). Ponadto klas i struktur, które mają konstruktorów musi ujawniać wszystkie metody abstrakcyjne i deklaracjami interfejs.


- Typy interfejsów muszą ujawnić, wszystkie metody i interfejsów.


Zasady na wartość podpisy są następujące:


- Modyfikatory dostępu (`public`, `internal`i tak dalej) i `inline` i `mutable` Modyfikatory w sygnaturze musi odpowiadają implementacji.


- Musi być zgodna z liczbą parametrów typu ogólnego, (lub niejawnie wywnioskować jawnie deklarować) i typy i ograniczenia parametrów typu ogólnego typu muszą być zgodne.


- Jeśli `Literal` atrybut jest używany, musi znajdować się w sygnaturze i implementacji i dla obu należy użyć tej samej wartości literału.


- Wzorzec parametrów (znanej także jako *argumentów*) sygnatury i implementacji muszą być zgodne.


W poniższym przykładzie kodu przedstawiono przykład pliku podpisu z przestrzeni nazw, modułu wartość funkcji i podpisy typu wraz z odpowiednich atrybutów. Przedstawia on również odpowiedniego pliku implementacji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

Poniższy kod przedstawia plik implementacji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Kontrola dostępu](access-control.md)

[Opcje kompilatora](compiler-options.md)
