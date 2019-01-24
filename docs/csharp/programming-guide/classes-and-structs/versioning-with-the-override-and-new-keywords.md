---
title: Przechowywanie wersji przesłonięć i nowych słów kluczowych — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 5c83ce79bede1ee4e5752ac0b1dcf9647df1f36c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555989"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Przechowywanie wersji przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)
Zaprojektowano w języku C#, aby versioning między [podstawowy](../../../csharp/language-reference/keywords/base.md) i klasy pochodne w różnych bibliotek mogą ewoluować i zachować zgodność z poprzednimi wersjami. Oznacza to, na przykład, że wprowadzenie nowego członka w podstawowym [klasy](../../../csharp/language-reference/keywords/class.md) z taką samą nazwę jak element członkowski w klasie pochodnej jest w pełni obsługiwane w języku C# i nie prowadzi do nieoczekiwanego zachowania. Oznacza to również, że klasy musi jawnie określać, czy metoda jest przeznaczona do zastępowania metody dziedziczonej, lub czy metoda jest nowa metoda, która ukrywa o podobnej nazwie dziedziczone metody.  
  
 W języku C# klasy pochodne mogą zawierać metody o nazwie identycznej z nazwą metody klasy bazowej.  
  
-   Należy zdefiniować metodę klasy bazowej [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Jeśli metoda w klasie pochodnej nie jest poprzedzony przez [nowe](../../../csharp/language-reference/keywords/new.md) lub [zastąpienia](../../../csharp/language-reference/keywords/override.md) słów kluczowych, kompilator zgłosi ostrzeżenie i metody będą zachowywać się tak, jakby `new` — słowo kluczowe były obecne.  
  
-   Jeśli metoda w klasie pochodnej jest poprzedzony znakiem `new` — słowo kluczowe, metoda jest zdefiniowana jako będące niezależnymi metody w klasie bazowej.  
  
-   Jeśli metoda w klasie pochodnej jest poprzedzony znakiem `override` — słowo kluczowe, obiekty klasy pochodnej wywoła tę metodę, zamiast metody klasy bazowej.  
  
-   Metody klasy bazowej można wywołać z w obrębie klasy pochodnej, za pomocą `base` — słowo kluczowe.  
  
-   `override`, `virtual`, I `new` słów kluczowych, można również będą stosowane do właściwości, indeksatory i zdarzenia.  
  
 Domyślnie metody języka C# nie są wirtualne. Jeśli metoda jest zadeklarowana jako wirtualna, każdej klasy dziedziczącej metody można zaimplementować własną wersję. Zapewnienie metody wirtualne, `virtual` modyfikator jest używany w deklaracji metody klasy bazowej. Klasa pochodna następnie można zastąpić metody wirtualnej podstawowej za pomocą `override` — słowo kluczowe lub ukryć metodę wirtualną w klasie bazowej, przy użyciu `new` — słowo kluczowe. Jeśli żadna `override` — słowo kluczowe ani `new` — słowo kluczowe jest określony, kompilator zgłosi ostrzeżenie i metody w klasie pochodnej ukrywa metodę w klasie bazowej.  
  
 Aby zademonstrować, to w praktyce, przyjęto założenie, przez chwilę utworzony w firmie A klasę o nazwie `GraphicsClass`, który program używa. Poniżej przedstawiono `GraphicsClass`:  
  
 [!code-csharp[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 Firma korzysta z tej klasy i użyjesz do wyprowadzenia własne klasy Dodawanie nowej metody:  
  
 [!code-csharp[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 Korzystania z aplikacji bez problemów, dopóki firmy A wydaje nową wersję `GraphicsClass`, który przypomina następujący kod:  
  
 [!code-csharp[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 Nowa wersja `GraphicsClass` teraz zawiera metodę o nazwie `DrawRectangle`. Początkowo nic się nie dzieje. Nowa wersja jest nadal binarne zgodna ze starej wersji. Dowolne oprogramowanie, które zostały wdrożone będą nadal działać, nawet jeśli nowa klasa jest zainstalowana w tych systemach komputerowych. Istniejące połączenia do metody `DrawRectangle` będą nadal odwoływać się do wersji w klasie pochodnej.  
  
 Jednak tak szybko, jak ponownie skompilować aplikację przy użyciu nowej wersji `GraphicsClass`, zostanie wyświetlone ostrzeżenie z kompilatora CS0108. To ostrzeżenie informuje, czy należy wziąć pod uwagę, jak chcesz, aby Twoje `DrawRectangle` metodę, aby zachowywać się w aplikacji.  
  
 Metodę można przesłonić nowe metody klasy bazowej, użyć `override` — słowo kluczowe:  
  
 [!code-csharp[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 `override` — Słowo kluczowe upewnia się, że wszystkie obiekty pochodne `YourDerivedGraphicsClass` użyje wersję klasy pochodnej `DrawRectangle`. Obiekty pochodzące z `YourDerivedGraphicsClass` nadal może uzyskać dostępu do klasy bazowej wersję `DrawRectangle` przy użyciu base — słowo kluczowe:  
  
 [!code-csharp[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 Jeśli użytkownik nie chce metodę można przesłonić nowe metody klasy bazowej, mają zastosowanie następujące kwestie. Aby uniknąć nieporozumień między obiema metodami, można zmienić metodę. Może to być czasochłonne i podatne na błędy i po prostu nie jest praktyczne w niektórych przypadkach. Jednak jeśli projekt jest stosunkowo mały, umożliwia programu Visual Studio Refactoring opcji Zmień nazwę metody. Aby uzyskać więcej informacji, zobacz [Refaktoryzacja klas i typów (Projektant klas)](/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Alternatywnie, można zapobiec ostrzeżenie za pomocą słowa kluczowego `new` w definicji klasy pochodnej:  
  
 [!code-csharp[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 Za pomocą `new` — słowo kluczowe informuje kompilator, że swojej definicji ukrywa definicji, który jest zawarty w klasie bazowej. Jest to zachowanie domyślne.  
  
## <a name="override-and-method-selection"></a>Zastąpienie i wybór metody  
 Gdy metoda nosi nazwę klasy, kompilator języka C# wybiera najlepszą metodę do wywołania w przypadku więcej niż jednej metody jest zgodny z wywołania, takie jak gdy istnieją dwie metody z taką samą nazwę i parametry, które są zgodne z przekazanego parametru. Następujące metody są zgodne:  
  
 [!code-csharp[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 Gdy `DoWork` jest wywoływana w wystąpieniu `Derived`, kompilator języka C# najpierw spróbuje wykonać wywołanie jest zgodny z wersjami programu `DoWork` pierwotnie zadeklarowana w `Derived`. Zastąpienie metody nie są uważane za zadeklarowana w klasie, są one nowych implementacji metody zadeklarowanej w klasie bazowej. Tylko wtedy, gdy kompilator języka C# nie można dopasować wywołanie metody do oryginalnej metody na `Derived` zostanie on próbę dopasowania wywołania do metody zastąpione przy użyciu tej samej nazwie i zgodnych parametrów. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 Ponieważ zmienna `val` mogą być niejawnie konwertowane na wartość o podwójnej precyzji wywołań kompilatora C# `DoWork(double)` zamiast `DoWork(int)`. Istnieją dwa sposoby, aby tego uniknąć. Po pierwsze należy unikać deklarowania nowych metod z taką samą nazwę jak metody wirtualne. Po drugie, można nakazać kompilatorowi języka C# do wywołania metody wirtualnej czyniąc ją wyszukiwania na liście metoda klasy bazowej przez rzutowanie wystąpienie `Derived` do `Base`. Ponieważ metoda jest wirtualna wykonania `DoWork(int)` na `Derived` zostanie wywołana. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 Aby uzyskać więcej przykładów `new` i `override`, zobacz [, wiedząc, gdy użycie zastępowania i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
