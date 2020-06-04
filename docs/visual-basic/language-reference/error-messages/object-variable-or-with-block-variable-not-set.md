---
title: Zmienna obiektu lub zmienna bloku With nie jest ustawiona
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: d1778e2bb58d32e976f10b3fba1637918278d36e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409286"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Zmienna obiektu lub zmienna bloku With nie jest ustawiona
Odwołuje się do nieprawidłowej zmiennej obiektu.   Ten błąd może wystąpić z kilku powodów:

- Zmienna została zadeklarowana bez określenia typu. Jeśli zmienna jest zadeklarowana bez określenia typu, wartość domyślna to Type `Object` .

    Na przykład zmienna zadeklarowana jako `Dim x` powinna być typu `Object;` Zmienna zadeklarowana z `Dim x As String` być typu `String` .

    > [!TIP]
    > `Option Strict`Instrukcja nie zezwala na niejawne wpisanie, które powoduje wystąpienie `Object` typu. Jeśli pominięto typ, wystąpi błąd w czasie kompilacji. Zobacz [Option Strict, instrukcja](../statements/option-strict-statement.md).

- Próbujesz odwołać się do obiektu, który został ustawiony na `Nothing` .

- Próbujesz uzyskać dostęp do elementu zmiennej tablicowej, która nie została prawidłowo zadeklarowana.

    Na przykład tablica zadeklarowana jako `products() As String` spowoduje wyzwolenie błędu w przypadku próby odwołania się do elementu tablicy `products(3) = "Widget"` . Tablica nie ma elementów i jest traktowana jako obiekt.

- Próbujesz uzyskać dostęp do kodu w `With...End With` bloku przed zainicjowaniem bloku.   `With...End With`Blok musi być zainicjowany przez wykonanie `With` punktu wejścia instrukcji.

> [!NOTE]
> We wcześniejszych wersjach Visual Basic lub VBA ten błąd został również wyzwolony przez przypisanie wartości do zmiennej bez użycia `Set` słowa kluczowego ( `x = "name"` zamiast `Set x = "name"` ). `Set`Słowo kluczowe nie jest już prawidłowe w Visual Basic .NET.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Ustaw `Option Strict` na `On` , dodając następujący kod na początku pliku:

    ```vb
    Option Strict On
    ```

    Po uruchomieniu projektu, w **Lista błędów** dla każdej zmiennej, która została określona bez typu, pojawi się błąd kompilatora.

2. Jeśli nie chcesz włączać `Option Strict` , przeszukaj kod pod kątem zmiennych, które zostały określone bez typu ( `Dim x` zamiast `Dim x As String` ) i Dodaj odpowiedni typ do deklaracji.

3. Upewnij się, że nie odwołujesz się do zmiennej obiektu, która została ustawiona na `Nothing` .  Przeszukaj kod słowa kluczowego `Nothing` i popraw kod, tak aby obiekt nie był ustawiony na wartość `Nothing` until po odwołaniu się do niego.

4. Przed uzyskaniem dostępu należy się upewnić, że wszystkie zmienne tablic są wymiarami. Można przypisać wymiar, gdy najpierw utworzysz tablicę ( `Dim x(5) As String` zamiast `Dim x() As String` ) lub użyć `ReDim` słowa kluczowego, aby ustawić Wymiary tablicy przed pierwszym uzyskaniem do niej dostępu.

5. Upewnij się `With` , że blok jest zainicjowany przez wykonanie `With` punktu wejścia instrukcji.

## <a name="see-also"></a>Zobacz też

- [Deklaracja zmiennej obiektu](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim, instrukcja](../statements/redim-statement.md)
- [With...End With, instrukcja](../statements/with-end-with-statement.md)
