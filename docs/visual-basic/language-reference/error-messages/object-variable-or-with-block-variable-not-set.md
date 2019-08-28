---
title: Zmienna obiektu lub zmienna bloku With nie jest ustawiona
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040560"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Zmienna obiektu lub zmienna bloku With nie jest ustawiona
Odwołuje się do nieprawidłowej zmiennej obiektu.   Ten błąd może wystąpić z kilku powodów:

- Zmienna została zadeklarowana bez określenia typu. Jeśli zmienna jest zadeklarowana bez określenia typu, wartość domyślna to Type `Object`.

    Na `Dim x` przykład zmienna zadeklarowana jako powinna być typu `Object;` zmienna zadeklarowana z `Dim x As String` być typu `String`.

    > [!TIP]
    > Instrukcja nie zezwala na niejawne wpisanie, które powoduje `Object` wystąpienie typu. `Option Strict` Jeśli pominięto typ, wystąpi błąd w czasie kompilacji. Zobacz [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).

- Próbujesz odwołać się do obiektu, który został ustawiony na `Nothing`.

- Próbujesz uzyskać dostęp do elementu zmiennej tablicowej, która nie została prawidłowo zadeklarowana.

    Na przykład tablica zadeklarowana jako `products() As String` spowoduje wyzwolenie błędu w przypadku próby odwołania się do elementu tablicy. `products(3) = "Widget"` Tablica nie ma elementów i jest traktowana jako obiekt.

- Próbujesz uzyskać dostęp do kodu w `With...End With` bloku przed zainicjowaniem bloku.   Blok musi być zainicjowany przez `With` wykonanie punktu wejścia instrukcji. `With...End With`

> [!NOTE]
> We wcześniejszych wersjach Visual Basic lub VBA ten błąd został również wyzwolony przez przypisanie wartości do zmiennej bez użycia `Set` słowa kluczowego (`x = "name"` zamiast `Set x = "name"`). `Set` Słowo kluczowe nie jest już prawidłowe w Visual Basic .NET.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Ustaw `Option Strict` na`On` , dodając następujący kod na początku pliku:

    ```vb
    Option Strict On
    ```

    Po uruchomieniu projektu, w **Lista błędów** dla każdej zmiennej, która została określona bez typu, pojawi się błąd kompilatora.

2. Jeśli nie chcesz włączać `Option Strict`, przeszukaj kod pod kątem zmiennych, które zostały określone bez typu (`Dim x` zamiast `Dim x As String`) i Dodaj odpowiedni typ do deklaracji.

3. Upewnij się, że nie odwołujesz się do zmiennej obiektu, która `Nothing`została ustawiona na.  Przeszukaj kod słowa kluczowego `Nothing`i popraw kod, tak aby obiekt nie był ustawiony na `Nothing` wartość until po odwołaniu się do niego.

4. Przed uzyskaniem dostępu należy się upewnić, że wszystkie zmienne tablic są wymiarami. Można przypisać wymiar, gdy najpierw utworzysz tablicę (`Dim x(5) As String` `Dim x() As String`zamiast `ReDim` ) lub użyć słowa kluczowego, aby ustawić Wymiary tablicy przed pierwszym uzyskaniem do niej dostępu.

5. Upewnij się, `With` że blok jest zainicjowany przez `With` wykonanie punktu wejścia instrukcji.

## <a name="see-also"></a>Zobacz także

- [Deklaracja zmiennej obiektu](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With, instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
