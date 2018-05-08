---
title: Przechowywanie wersji przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 2a6a6f59320d94cf97b1a07448000bd708d95559
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Przechowywanie wersji przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)
Zaprojektowano w języku C#, aby versioning między [podstawowej](../../../csharp/language-reference/keywords/base.md) i klas pochodnych w różne biblioteki można rozwijać i zachować zgodność z poprzednimi wersjami. Oznacza to, na przykład, że wprowadzenie nowego elementu członkowskiego w podstawowym [klasy](../../../csharp/language-reference/keywords/class.md) z taką samą nazwę jak element członkowski w klasie pochodnej jest całkowicie obsługiwana w języku C# i nie prowadzić do nieoczekiwanego zachowania. Oznacza to również, że klasa musi jawnie określać, czy metoda jest przeznaczona do przesłonięcia dziedziczonej metody, lub czy metoda jest nowa metoda, która ukrywa o podobnej nazwie dziedziczone — metoda.  
  
 W języku C# klasy pochodne mogą zawierać metody z taką samą nazwę jak metod klasy podstawowej.  
  
-   Klasa podstawowa metoda musi być zdefiniowana [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Jeśli nie jest poprzedzony metody w klasie pochodnej [nowego](../../../csharp/language-reference/keywords/new.md) lub [zastąpienie](../../../csharp/language-reference/keywords/override.md) słów kluczowych, kompilator zgłosi ostrzeżenie i metody będą zachowywać się tak, jakby `new` — słowo kluczowe były dostępne.  
  
-   Jeśli metoda w klasie pochodnej jest poprzedzony `new` — słowo kluczowe, metoda jest zdefiniowany jako niezależny od metody w klasie podstawowej.  
  
-   Jeśli metoda w klasie pochodnej jest poprzedzony `override` — słowo kluczowe, obiekty pochodne klasy będzie wywoływać tej metody zamiast metody klasy podstawowej.  
  
-   Można wywołać metody klasy podstawowej z wewnątrz klasy pochodnej przy użyciu `base` — słowo kluczowe.  
  
-   `override`, `virtual`, I `new` słów kluczowych mogą również będą stosowane do właściwości, indeksatorów i zdarzeń.  
  
 Domyślnie metody C# nie są wirtualnego. Jeśli metoda jest zadeklarowany jako wirtualny, każda klasa dziedziczy metody można zaimplementować własną wersję. Aby metody wirtualne, `virtual` modyfikator jest używany w deklaracji metody klasy podstawowej. Klasa pochodna może następnie przesłonić metodę wirtualną podstawowej za pomocą `override` — słowo kluczowe lub ukryć metodę wirtualną w klasie podstawowej za pomocą `new` — słowo kluczowe. Jeśli żadna `override` — słowo kluczowe ani `new` zostanie określone słowo kluczowe, kompilator zgłosi ostrzeżenie i metody w klasie pochodnej spowoduje ukrycie metody w klasie podstawowej.  
  
 Aby pokazać to w praktyce, Przyjmijmy na chwilę utworzony w firmie A klasę o nazwie `GraphicsClass`, który używa programu. Poniżej przedstawiono `GraphicsClass`:  
  
 [!code-csharp[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 Firma korzysta z tej klasy i można go użyć do uzyskania własne klasy Dodawanie nowej metody:  
  
 [!code-csharp[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 Aplikacja jest używana bez problemów, dopóki firmy A zwalnia nowej wersji `GraphicsClass`, który podobny do następującego kodu:  
  
 [!code-csharp[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 Nowa wersja `GraphicsClass` teraz zawiera metodę o nazwie `DrawRectangle`. Początkowo nic się nie dzieje. Nowa wersja jest nadal binarne zgodna ze starą wersję. Dowolne oprogramowanie, które zostały wdrożone będą nadal działać, nawet jeśli nowa klasa jest zainstalowana na tych komputerach. Istniejące połączenia do metody `DrawRectangle` będą nadal odwoływać wersji w klasie pochodnej.  
  
 Jednak tak szybko, jak ponownie skompilować aplikację przy użyciu nowej wersji `GraphicsClass`, zostanie wyświetlone ostrzeżenie kompilatora CS0108. To ostrzeżenie informuje, że należy wziąć pod uwagę sposób Twojej `DrawRectangle` metody mają zachowywać się w aplikacji.  
  
 Metodę Aby przesłonić metodę nowej klasy podstawowej, należy użyć `override` — słowo kluczowe:  
  
 [!code-csharp[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 `override` — Słowo kluczowe upewnia się, że wszystkie obiekty pochodne `YourDerivedGraphicsClass` użyje wersja klasy pochodnej `DrawRectangle`. Obiekty pochodne `YourDerivedGraphicsClass` nadal może uzyskać dostępu do klasy podstawowej wersji `DrawRectangle` przy użyciu base — słowo kluczowe:  
  
 [!code-csharp[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 Jeśli nie chcesz, aby metodę Aby przesłonić metodę nowej klasy podstawowej, zastosuj następujące kwestie. Aby uniknąć nieporozumień między obiema metodami, można zmienić nazwę metody. Może to być czasochłonne i podatne na błędy i nie jest praktyczne w niektórych przypadkach. Jednak jeśli Twój projekt jest stosunkowo mały, można zmienić nazwy metody można użyć opcji Refactoring programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Refaktoryzacja klas i typów (Projektant klas)](/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Można również wyłączyć ostrzeżenia przy użyciu słowa kluczowego `new` w definicji klasy pochodnej:  
  
 [!code-csharp[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 Przy użyciu `new` — słowo kluczowe informuje kompilator, że definicja ukrywa definicji, który jest zawarty w klasie podstawowej. Jest to zachowanie domyślne.  
  
## <a name="override-and-method-selection"></a>Zastąpienie i wybór metody  
 Gdy dla klasy, nosi nazwę metody, kompilator języka C# wybiera najlepszą metodę do wywołania w przypadku więcej niż jednej metody jest zgodny z wywołań, takich jak gdy istnieją dwie metody z tej samej nazwy i parametry, które są zgodne z przekazany parametr. Następujące metody są niezgodne:  
  
 [!code-csharp[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 Gdy `DoWork` jest wywoływana w wystąpieniu programu `Derived`, kompilator języka C# najpierw spróbuje wykonać wywołanie zgodny z wersjami programu `DoWork` pierwotnie zadeklarowana w `Derived`. Zastąpienie metody nie są traktowane jako zadeklarowana w klasie, są nowe implementacje metody zadeklarowanej w klasie podstawowej. Tylko wtedy, gdy kompilator języka C# nie pasuje do wywołania metody do oryginalnej metody w `Derived` będzie również podjąć próbę dopasowania wywołania do przesłoniętej metody o tej samej nazwie i zgodnych parametrów. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 Ponieważ zmiennej `val` można przekonwertować na wartość o podwójnej precyzji niejawnie wywołania kompilatora C# `DoWork(double)` zamiast `DoWork(int)`. Istnieją dwa sposoby, aby zapobiec tej sytuacji. Najpierw należy unikać deklarowanie nowych metod z taką samą nazwę jak metodach wirtualnych. Po drugie, można zmodyfikować kompilatora C# do wywołania metody wirtualnej czyniąc ją listy metody klasy podstawowej wyszukiwania przez rzutowanie wystąpienie `Derived` do `Base`. Ponieważ metoda jest wirtualny, implementacja `DoWork(int)` na `Derived` zostanie wywołana. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 Aby uzyskać więcej przykładów `new` i `override`, zobacz [wiedząc, gdy użycie zastępowania i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
