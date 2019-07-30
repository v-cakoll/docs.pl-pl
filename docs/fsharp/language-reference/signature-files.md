---
title: Pliki sygnatur
description: Dowiedz się, F# jak używać plików sygnatur do przechowywania informacji o podpisach publicznych zestawu elementów F# programu, takich jak typy, przestrzenie nazw i moduły.
ms.date: 06/15/2018
ms.openlocfilehash: c04ac8bf4ee360a2caa15be8f2bbea41105bd160
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627157"
---
# <a name="signatures"></a>Podpisy

Plik podpisu zawiera informacje o podpisach publicznych zestawu elementów F# programu, takich jak typy, przestrzenie nazw i moduły. Może służyć do określania dostępności tych elementów programu.

## <a name="remarks"></a>Uwagi

Dla każdego F# pliku kodu można mieć *plik podpisu*, który jest plikiem o takiej samej nazwie jak plik kodu, ale z rozszerzeniem. FSI zamiast. FS. Pliki sygnatur można również dodać do wiersza polecenia kompilacji, jeśli używasz wiersza polecenia bezpośrednio. W celu rozróżnienia plików kodu i plików sygnatur pliki kodu są czasami określane jako *pliki implementacji*. W projekcie plik podpisu powinien poprzedzać skojarzony plik kodu.

Plik podpisu zawiera opis przestrzeni nazw, modułów, typów i elementów członkowskich w odpowiednim pliku implementacji. Informacje w pliku podpisu służą do określania, które części kodu w odpowiednim pliku implementacji są dostępne z kodu poza plikiem implementacji i jakie części są wewnętrzne dla pliku implementacji. Przestrzenie nazw, moduły i typy, które są zawarte w pliku sygnatury, muszą być podzbiorem przestrzeni nazw, modułów i typów, które są zawarte w pliku implementacji. W przypadku niektórych wyjątków zanotowanych w dalszej części tego tematu te elementy języka, które nie są wymienione w pliku podpisu, są uznawane za prywatne z plikiem implementacji. Jeśli plik podpisu nie zostanie znaleziony w projekcie lub wierszu polecenia, zostanie użyta domyślna dostępność.

Aby uzyskać więcej informacji na temat domyślnego ułatwienia dostępu, zobacz [Access Control](access-control.md).

W pliku podpisu nie powtarza się definicji typów i implementacji każdej metody lub funkcji. Zamiast tego należy użyć podpisu dla każdej metody i funkcji, która działa jako kompletna Specyfikacja funkcji implementowanych przez fragment modułu lub przestrzeni nazw. Składnia sygnatury typu jest taka sama jak ta, która jest używana w deklaracjach metod abstrakcyjnych w interfejsach i klasach abstrakcyjnych, a także jest F# wyświetlana przez funkcję IntelliSense i interpreter FSI. exe, gdy wyświetla prawidłowo skompilowane dane wejściowe.

Jeśli w sygnaturze typu nie ma wystarczającej ilości informacji wskazujących, czy typ jest zapieczętowany, czy też jest typem interfejsu, należy dodać atrybut, który wskazuje charakter typu kompilatora. Atrybuty, które są używane w tym celu, są opisane w poniższej tabeli.

|Atrybut|Opis|
|---------|-----------|
|`[<Sealed>]`|Dla typu, który nie ma abstrakcyjnych elementów członkowskich lub nie należy go rozszerzać.|
|`[<Interface>]`|Dla typu, który jest interfejsem.|

Kompilator generuje błąd, jeśli atrybuty nie są spójne między sygnaturą i deklaracją w pliku implementacji.

Użyj słowa kluczowego `val` , aby utworzyć podpis dla wartości wartości lub funkcji. Słowo kluczowe `type` wprowadza sygnaturę typu.

Plik podpisu można wygenerować przy użyciu `--sig` opcji kompilatora. Ogólnie rzecz biorąc, pliki. FSI nie są zapisywane ręcznie. Zamiast tego można generować pliki. FSI za pomocą kompilatora, dodawać je do projektu, jeśli istnieje, i edytować je, usuwając metody i funkcje, które nie mają być dostępne.

Istnieje kilka reguł dla podpisów typów:

- Skróty typów w pliku implementacji nie mogą być zgodne z typem bez skrótu w pliku sygnatury.

- Rekordy i unie rozłączne muszą uwidaczniać wszystkie lub żadne z ich pól i konstruktorów, a kolejność w podpisie musi być zgodna z kolejnością w pliku implementacji. Klasy mogą ujawniać niektóre, wszystkie lub żadne z ich pól i metod w podpisie.

- Klasy i struktury, które mają konstruktory muszą ujawniać deklaracje ich klas bazowych ( `inherits` deklaracja). Ponadto klasy i struktury, które mają konstruktory muszą uwidaczniać wszystkie metody abstrakcyjne i deklaracje interfejsów.

- Typy interfejsów muszą ujawniać wszystkie metody i interfejsy.

Reguły dla sygnatur wartości są następujące:

- Modyfikatory dla ułatwień`public`dostępu `internal`(,, i `inline` tak dalej) oraz `mutable` modyfikatory i w sygnaturze muszą być zgodne z tymi w implementacji.

- Liczba parametrów typu ogólnego (niejawnie wywnioskowanych lub jawnie zadeklarowanych) musi być zgodna, a typy i ograniczenia typów w parametrach typu ogólnego muszą być zgodne.

- `Literal` Jeśli atrybut jest używany, musi znajdować się zarówno w sygnaturze, jak i implementacji, a ta sama wartość literału musi być użyta dla obu.

- Wzorzec parametrów (znany również jako liczba *argumentów*) sygnatur i implementacji musi być spójny.

- Jeśli nazwy parametrów w pliku sygnatury różnią się od odpowiedniego pliku implementacji, zamiast tego zostanie użyta nazwa w pliku podpisu, co może powodować problemy podczas debugowania lub profilowania. Jeśli chcesz otrzymywać powiadomienia o takich niezgodności, Włącz Ostrzeżenie 3218 w pliku projektu lub podczas wywoływania kompilatora (zobacz `--warnon` w obszarze [Opcje kompilatora](compiler-options.md)).

Poniższy przykład kodu przedstawia przykład pliku sygnatury, który ma sygnatury przestrzeni nazw, modułu, funkcji i typu wraz z odpowiednimi atrybutami. Pokazuje również odpowiedni plik implementacji.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9002.fs)]

Poniższy kod przedstawia plik implementacji.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssignatures/snippet9001.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Kontrola dostępu](access-control.md)
- [Opcje kompilatora](compiler-options.md)
