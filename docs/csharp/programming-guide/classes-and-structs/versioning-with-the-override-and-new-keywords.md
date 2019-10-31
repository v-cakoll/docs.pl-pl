---
title: Przechowywanie wersji przy użyciu przesłonięć i nowych słów kluczowych C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: c85f5b6b4552dc4a10c7ad66b8f93331f97a8621
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196202"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Przechowywanie wersji przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)
C# Język został zaprojektowany tak, aby przechowywanie wersji między klasą [podstawową](../../language-reference/keywords/base.md) i pochodną w różnych bibliotekach można było rozwijać i obsługiwać zgodność z poprzednimi wersjami. Oznacza to na przykład, że wprowadzenie nowego elementu członkowskiego w [klasie](../../language-reference/keywords/class.md) bazowej o takiej samej nazwie jak element członkowski w klasie pochodnej jest w pełni obsługiwane przez C# program i nie prowadzi do nieoczekiwanego zachowania. Oznacza to również, że klasa musi jawnie określać, czy metoda jest przeznaczona do przesłania dziedziczonej metody lub czy metoda jest nową metodą, która ukrywa podobną metodę o nazwie dziedziczone.  
  
 W C#, klasy pochodne mogą zawierać metody o tej samej nazwie co metody klasy bazowej.  
  
- Metoda klasy bazowej musi być zdefiniowana jako [wirtualna](../../language-reference/keywords/virtual.md).  
  
- Jeśli metoda w klasie pochodnej nie jest poprzedzona przez [nowe](../../language-reference/keywords/new-modifier.md) lub [zastępujące](../../language-reference/keywords/override.md) słowa kluczowe, kompilator wyda ostrzeżenie, a metoda będzie zachowywać się tak, jakby słowo kluczowe `new` było obecne.  
  
- Jeśli metoda w klasie pochodnej jest poprzedzona słowem kluczowym `new`, metoda jest definiowana jako niezależna od metody w klasie bazowej.  
  
- Jeśli metoda w klasie pochodnej jest poprzedzona słowem kluczowym `override`, obiekty klasy pochodnej spowodują wywołanie tej metody zamiast metody klasy bazowej.  
  
- Metodę klasy bazowej można wywołać z poziomu klasy pochodnej przy użyciu słowa kluczowego `base`.  
  
- Słowa kluczowe `override`, `virtual`i `new` mogą być również stosowane do właściwości, indeksatorów i zdarzeń.  
  
 Domyślnie C# metody nie są wirtualne. Jeśli metoda jest zadeklarowana jako wirtualna, każda klasa, która dziedziczy metodę, może zaimplementować własną wersję. Aby można było wykonać wirtualną metodę, modyfikator `virtual` jest używany w deklaracji metody klasy bazowej. Klasa pochodna może następnie zastąpić podstawową metodę wirtualną za pomocą słowa kluczowego `override` lub ukryć metodę wirtualną w klasie bazowej za pomocą słowa kluczowego `new`. Jeśli nie określono słowa kluczowego `override` ani słowa kluczowego `new`, kompilator wyda ostrzeżenie, a metoda w klasie pochodnej spowoduje ukrycie metody w klasie bazowej.  
  
 Aby to zademonstrować, założono, że firma A utworzyła klasę o nazwie `GraphicsClass`, której używa program. Poniżej przedstawiono `GraphicsClass`:  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Firma używa tej klasy i używa jej do uzyskania własnej klasy, dodając nową metodę:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Aplikacja jest używana bez problemów, do momentu wydania przez firmę A nowej wersji `GraphicsClass`, która przypomina następujący kod:  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 Nowa wersja `GraphicsClass` zawiera teraz metodę o nazwie `DrawRectangle`. Początkowo nic się nie dzieje. Nowa wersja jest nadal zgodna ze standardem binarnym ze starszą wersją. Wdrożone oprogramowanie będzie nadal działało, nawet jeśli nowa klasa jest zainstalowana w tych systemach komputerowych. Wszystkie istniejące wywołania metody `DrawRectangle` będą nadal odwoływać się do Twojej wersji w klasie pochodnej.  
  
 Jednak po ponownym skompilowaniu aplikacji za pomocą nowej wersji `GraphicsClass`zostanie wyświetlone ostrzeżenie z kompilatora, CS0108. To ostrzeżenie informuje o tym, że należy wziąć pod uwagę sposób działania metody `DrawRectangle` w aplikacji.  
  
 Jeśli chcesz, aby Metoda przesłaniał nową metodę klasy bazowej, użyj słowa kluczowego `override`:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 Słowo kluczowe `override` zapewnia, że wszystkie obiekty pochodne od `YourDerivedGraphicsClass` będą używały wersji klasy pochodnej `DrawRectangle`. Obiekty pochodzące z `YourDerivedGraphicsClass` mogą nadal uzyskiwać dostęp do wersji klasy bazowej `DrawRectangle` za pomocą słowa kluczowego Base:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Jeśli nie chcesz, aby Metoda przesłaniał nową metodę klasy bazowej, mają zastosowanie następujące zagadnienia. Aby uniknąć pomyłek między tymi dwoma metodami, można zmienić nazwę metody. Może to być czasochłonne i podatne na błędy, a w niektórych przypadkach nie jest to praktycznie praktyczne. Jeśli jednak projekt jest stosunkowo mały, możesz użyć opcji refaktoryzacji programu Visual Studio, aby zmienić nazwę metody. Aby uzyskać więcej informacji, zobacz [Refaktoryzacja klas i typów (Projektant klas)](/visualstudio/ide/class-designer/refactoring-classes-and-types).  
  
 Alternatywnie można zapobiec ostrzeżeniu za pomocą słowa kluczowego `new` w definicji klasy pochodnej:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 Użycie słowa kluczowego `new` informuje kompilator, że definicja ukrywa definicję, która jest zawarta w klasie bazowej. Jest to zachowanie domyślne.  
  
## <a name="override-and-method-selection"></a>Przesłoń i wybór metody  
 Gdy metoda jest nazywana w klasie, C# kompilator wybiera najlepszą metodę wywołania, jeśli więcej niż jedna metoda jest zgodna z wywołaniem, na przykład wtedy, gdy istnieją dwie metody o tej samej nazwie i parametry, które są zgodne z przekazaniem parametru. Następujące metody byłyby zgodne:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 Gdy `DoWork` jest wywoływana w wystąpieniu `Derived`, C# kompilator najpierw podejmie próbę wykonania wywołania zgodnego z wersjami `DoWork` zadeklarowanymi pierwotnie na `Derived`. Metody override nie są uznawane za zadeklarowane w klasie, są to nowe implementacje metody zadeklarowanej w klasie bazowej. Tylko wtedy, C# gdy kompilator nie może dopasować wywołania metody do oryginalnej metody w `Derived`, podejmie próbę dopasowania wywołania do zastąpionej metody z tą samą nazwą i zgodnymi parametrami. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Ponieważ zmienna `val` może być konwertowana na podwójnie niejawnie, C# kompilator wywołuje `DoWork(double)` zamiast `DoWork(int)`. Istnieją dwa sposoby, aby tego uniknąć. Najpierw należy unikać deklarowania nowych metod o takiej samej nazwie jak metody wirtualne. Następnie można wydać C# kompilatorowi wywołanie metody wirtualnej, przeszukiwanie listy metod klasy podstawowej przez wyrzucanie wystąpienia `Derived` do `Base`. Ponieważ metoda jest wirtualna, implementacja `DoWork(int)` w `Derived` zostanie wywołana. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 Więcej przykładów `new` i `override`można znaleźć w artykule [wiedzą, kiedy używać przesłonięć i nowych słów kluczowych](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Metody](./methods.md)
- [Dziedziczenie](./inheritance.md)
