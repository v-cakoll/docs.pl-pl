---
title: Zmienna obiektu lub zmienna bloku With nie jest ustawiona
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: b2c0c47b359e218111c1629ea574303a6d663046
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297931"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Zmienna obiektu lub zmienna bloku With nie jest ustawiona
Odwołuje się do nieprawidłowego obiektu zmiennej.   Ten błąd może wystąpić z kilku powodów:  
  
-   Zmienna została zadeklarowana bez określania typu. Jeśli zmienna jest zadeklarowana bez określania typu, jego wartość domyślna to typ `Object`.  
  
     Na przykład, Zmienna zadeklarowana ze `Dim x` byłoby typu `Object;` Zmienna zadeklarowana ze `Dim x As String` byłoby typu `String`.  
  
    > [!TIP]
    >  `Option Strict` Instrukcji nie zezwalają na niejawnego wpisywania, które spowodowało, że `Object` typu. Jeżeli pominięto ten typ, wystąpi błąd kompilacji. Zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
-   Podjęto próbę odwołują się do obiektu, który został ustawiony na `Nothing`  
  
     .  
  
-   Podjęto próbę uzyskania dostępu do elementu zmienną tablicy, która nie została prawidłowo zadeklarowana.  
  
     Na przykład Tablica zadeklarowana jako `products() As String` wyzwoli ten błąd, jeśli zostanie podjęta próba odwołania się do elementu tablicy `products(3) = "Widget"`. Tablica nie ma żadnych elementów i jest traktowany jako obiekt.  
  
-   Podjęto próbę dostępu do kodu w ramach `With...End With` blokowania, zanim blok został zainicjowany.   A `With...End With` bloku musi zostać zainicjowany, wykonując `With` instrukcji punktu wejścia.  
  
> [!NOTE]
>  We wcześniejszych wersjach programu Visual Basic lub VBA ten błąd również została wyzwolona przez przypisywanie wartości do zmiennej bez użycia `Set` — słowo kluczowe (`x = "name"` zamiast `Set x = "name"`). `Set` — Słowo kluczowe nie jest już prawidłowy w języku Visual Basic .net.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Ustaw `Option Strict` do `On` , dodając następujący kod na początku pliku:  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2. Jeśli nie chcesz umożliwić `Option Strict`, wyszukiwanie w kodzie żadnych zmiennych, które zostały określone bez typu (`Dim x` zamiast `Dim x As String`) i Dodaj zamierzony typ oświadczenia.  
  
3. Upewnij się, że nie są odwołujesz się do zmiennej obiektu, który został ustawiony na `Nothing`.  Wyszukiwanie w kodzie słowa kluczowego `Nothing`i popraw swój kod, aby obiekt nie jest ustawiony na `Nothing` dopóki po ma on wywołany.  
  
4. Upewnij się, że wszystkie zmienne tablicy są wymiary przed można uzyskiwać do nich dostęp. Po utworzeniu tablicy można przypisać wymiaru (`Dim x(5) As String` zamiast `Dim x() As String`), lub użyj `ReDim` słowo kluczowe, aby ustawić wymiary tablicy, zanim zostanie najpierw uzyskać do niego dostęp.  
  
5. Upewnij się, że Twoje `With` bloku jest inicjowany przez wykonanie `With` instrukcji punktu wejścia.  
  
## <a name="see-also"></a>Zobacz także

- [Deklaracja zmiennej obiektu](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim, instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With, instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
