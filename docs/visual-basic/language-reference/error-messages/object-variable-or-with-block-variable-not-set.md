---
title: Zmienna obiektu lub zmienna bloku With nie jest ustawiona
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e1f587e194acf744b6ec9b8f1bede3acef7b753
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Zmienna obiektu lub zmienna bloku With nie jest ustawiona
Odwołuje się do zmiennej nieprawidłowy obiekt.   Ten błąd może wystąpić z kilku powodów:  
  
-   Zmienna została zadeklarowana bez określania typu. Jeśli zmienna została zadeklarowana bez określania typu, domyślnie na typ `Object`.  
  
     Na przykład Zmienna zadeklarowana ze `Dim x` może być typu `Object;` Zmienna zadeklarowana ze `Dim x As String` może być typu `String`.  
  
    > [!TIP]
    >  `Option Strict` Instrukcji nie zezwala na niejawne wpisanie, który daje w `Object` typu. W przypadku pominięcia tego typu, wystąpi błąd kompilacji. Zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
-   Próbujesz się odwołać obiektu, który został ustawiony`Nothing`  
  
     .  
  
-   Podjęto próbę uzyskania dostępu do elementu tablicy zmiennej, która nie została poprawnie zadeklarowane.  
  
     Na przykład Tablica zadeklarowana jako `products() As String` wyzwoli błąd, jeśli zostanie podjęta próba odwołania się do elementu tablicy `products(3) = "Widget"`. Tablica nie ma żadnych elementów i jest traktowany jako obiekt.  
  
-   Podjęto próbę kodu dostępu w ramach `With...End With` zablokować przed bloku został zainicjowany.   A `With...End With` bloku musi zostać zainicjowany, wykonując `With` instrukcji punktu wejścia.  
  
> [!NOTE]
>  We wcześniejszych wersjach programu Visual Basic lub VBA ten błąd został także wywołany przez przypisywanie wartości do zmiennej, bez korzystania z `Set` — słowo kluczowe (`x = "name"` zamiast `Set x = "name"`). `Set` — Słowo kluczowe nie jest już prawidłowy w języku Visual Basic .net.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Ustaw `Option Strict` do `On` przez dodanie poniższego kodu do początku pliku:  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  Jeśli nie chcesz włączyć `Option Strict`, wyszukiwanie kodu zmiennych, które zostały określone bez typu (`Dim x` zamiast `Dim x As String`) i Dodaj do deklaracji danego typu.  
  
3.  Upewnij się, że nie ma odwołanie do zmiennej obiektu, który został ustawiony na `Nothing`.  Wyszukiwanie kodu słowa kluczowego `Nothing`, a zmienić swój kod, aby obiekt nie został skonfigurowany do `Nothing` dopóki po ma on wywołany.  
  
4.  Upewnij się, że wszystkie zmienne tablicy są wymiarów przed ich dostępu. Po utworzeniu tablicy można przypisać wymiaru (`Dim x(5) As String` zamiast `Dim x() As String`), lub użyj `ReDim` — słowo kluczowe ustawienie wymiarów tablicy, zanim zostanie najpierw do niego dostęp.  
  
5.  Upewnij się, że Twoje `With` bloku został zainicjowany, wykonując `With` instrukcji punktu wejścia.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracja zmiennej obiektu](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [ReDim — instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Z... End With — instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
