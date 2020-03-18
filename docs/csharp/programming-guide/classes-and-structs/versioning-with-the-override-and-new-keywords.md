---
title: Przechowywanie wersji za pomocą słów kluczowych zastępowania i nowych — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 089d5d7c7a95e2de4629f53255d9d9790fd5508a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705395"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Przechowywanie wersji przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)
Język Języka C# został zaprojektowany tak, aby przechowywanie wersji między klasami [podstawowymi](../../language-reference/keywords/base.md) i pochodnymi w różnych bibliotekach może ewoluować i utrzymywać zgodność z poprzednimi wersjami. Oznacza to na przykład, że wprowadzenie nowego elementu członkowskiego w [klasie podstawowej](../../language-reference/keywords/class.md) o tej samej nazwie jako element członkowski w klasie pochodnej jest całkowicie obsługiwany przez C# i nie prowadzi do nieoczekiwanego zachowania. Oznacza to również, że klasa musi jawnie stwierdzić, czy metoda ma zastąpić dziedziczoną metodę, czy też metoda jest nową metodą, która ukrywa metodę dziedziczoną o podobnej nazwie.  
  
 W języku C#klasy pochodne mogą zawierać metody o tej samej nazwie co metody klasy podstawowej.  
  
- Metoda klasy podstawowej musi być zdefiniowana [wirtualna](../../language-reference/keywords/virtual.md).  
  
- Jeśli metoda w klasie pochodnej nie jest poprzedzona [nowymi](../../language-reference/keywords/new-modifier.md) lub [zastąpić](../../language-reference/keywords/override.md) słowa kluczowe, kompilator `new` wyda ostrzeżenie i metoda będzie zachowywać się tak, jakby słowo kluczowe były obecne.  
  
- Jeśli metoda w klasie pochodnej jest `new` poprzedzona słowem kluczowym, metoda jest definiowana jako niezależna od metody w klasie podstawowej.  
  
- Jeśli metoda w klasie pochodnej jest `override` poprzedzona słowem kluczowym, obiekty klasy pochodnej wywoła tę metodę zamiast metody klasy podstawowej.  
  
- Metoda klasy podstawowej można wywołać z poziomu `base` klasy pochodnej przy użyciu słowa kluczowego.  
  
- Słowa `override` `virtual`kluczowe `new` , i słowa kluczowe mogą być również stosowane do właściwości, indeksatorów i zdarzeń.  
  
 Domyślnie metody Języka C# nie są wirtualne. Jeśli metoda jest zadeklarowana jako wirtualna, każda klasa dziedzicząca metodę można zaimplementować własną wersję. Aby metoda była wirtualna, `virtual` modyfikator jest używany w deklaracji metody klasy podstawowej. Klasa pochodna może następnie zastąpić podstawową metodę `override` wirtualną przy użyciu słowa kluczowego `new` lub ukryć metodę wirtualną w klasie podstawowej przy użyciu słowa kluczowego. Jeśli nie `override` określono słowa `new` kluczowego ani słowa kluczowego, kompilator wyda ostrzeżenie, a metoda w klasie pochodnej ukryje metodę w klasie podstawowej.  
  
 Aby zademonstrować to w praktyce, załóżmy przez `GraphicsClass`chwilę, że firma A utworzyła klasę o nazwie , której używa program. Oto: `GraphicsClass`  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Firma używa tej klasy i używasz jej do uzyskania własnej klasy, dodając nową metodę:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Aplikacja jest używana bez problemów, dopóki firma A `GraphicsClass`nie wyda nowej wersji , która przypomina następujący kod:  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 Nowa wersja `GraphicsClass` teraz zawiera metodę `DrawRectangle`o nazwie . Początkowo nic się nie dzieje. Nowa wersja jest nadal binarna kompatybilna ze starą wersją. Każde wdrożone oprogramowanie będzie nadal działać, nawet jeśli nowa klasa jest zainstalowana w tych systemach komputerowych. Wszelkie istniejące wywołania `DrawRectangle` metody będzie nadal odwoływać się do wersji, w klasie pochodnej.  
  
 Jednak gdy tylko ponownie skompilować aplikację przy użyciu `GraphicsClass`nowej wersji , otrzymasz ostrzeżenie od kompilatora, CS0108. To ostrzeżenie informuje, że należy wziąć `DrawRectangle` pod uwagę, jak chcesz, aby metoda zachowywała się w aplikacji.  
  
 Jeśli chcesz, aby metoda zastępowała nową metodę `override` klasy podstawowej, użyj słowa kluczowego:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 Słowo `override` kluczowe upewnia się, `YourDerivedGraphicsClass` że wszystkie obiekty pochodzące `DrawRectangle`z użyje wersji klasy pochodnej . Obiekty pochodzące `YourDerivedGraphicsClass` z nadal można uzyskać `DrawRectangle` dostęp do wersji klasy podstawowej za pomocą podstawowego słowa kluczowego:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Jeśli nie chcesz, aby metoda zastąpić nową metodę klasy podstawowej, mają zastosowanie następujące zagadnienia. Aby uniknąć pomyłek między dwiema metodami, można zmienić nazwę metody. Może to być czasochłonne i podatne na błędy, a w niektórych przypadkach po prostu nie praktyczne. Jednak jeśli projekt jest stosunkowo mały, można użyć opcji refaktoryzacji programu Visual Studio, aby zmienić nazwę metody. Aby uzyskać więcej informacji, zobacz [Refaktoryzowanie klas i typów (projektant klas)](/visualstudio/ide/class-designer/refactoring-classes-and-types).  
  
 Alternatywnie można zapobiec ostrzeżenie przy `new` użyciu słowa kluczowego w definicji klasy pochodnej:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 Za `new` pomocą słowa kluczowego informuje kompilator, że definicja ukrywa definicji, która jest zawarta w klasie podstawowej. Jest to zachowanie domyślne.  
  
## <a name="override-and-method-selection"></a>Zastępowanie i wybór metody  
 Gdy metoda jest nazwany na klasy, kompilator C# wybiera najlepszą metodę do wywołania, jeśli więcej niż jedna metoda jest zgodna z wywołaniem, na przykład, gdy istnieją dwie metody o tej samej nazwie i parametry, które są zgodne z parametrem przekazany. Następujące metody byłyby zgodne:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 Gdy `DoWork` jest wywoływana `Derived`na wystąpienie , kompilator C# najpierw spróbuje `DoWork` dokonać `Derived`połączenia zgodne z wersjami zadeklarowane pierwotnie na . Metody zastępowania nie są traktowane jako zadeklarowane w klasie, są to nowe implementacje metody zadeklarowanej w klasie podstawowej. Tylko wtedy kompilator C# nie może dopasować `Derived` wywołania metody do oryginalnej metody na będzie próbował dopasować wywołanie do metody zastąpione o tej samej nazwie i parametrów zgodnych. Przykład:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Ponieważ zmienna `val` może zostać przekonwertowana na podwójnie niejawnie, kompilator C# wywołuje `DoWork(double)` zamiast . `DoWork(int)` Istnieją dwa sposoby, aby tego uniknąć. Najpierw należy unikać deklarowania nowych metod o takiej samej nazwie jak metody wirtualne. Po drugie można poinstruować kompilator C# wywołać metodę wirtualną, wykonując wyszukiwanie `Derived` `Base`listy metod klasy podstawowej przez rzutowanie wystąpienia do . Ponieważ metoda jest wirtualna, `DoWork(int)` `Derived` zostanie wywołana implementacja on. Przykład:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 Aby uzyskać więcej `new` `override`przykładów i zobacz [Wiedza, kiedy używać zastępowania i nowe słowa kluczowe](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Metody](./methods.md)
- [Dziedziczenie](./inheritance.md)
