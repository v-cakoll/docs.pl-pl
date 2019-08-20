---
title: Przechowywanie wersji przy użyciu przesłonięć i nowych słów kluczowych C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 58023498c499569eebb9a0506bea434d2669de45
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596012"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Przechowywanie wersji przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)
C# Język został zaprojektowany tak, aby przechowywanie wersji między klasą [podstawową](../../language-reference/keywords/base.md) i pochodną w różnych bibliotekach można było rozwijać i obsługiwać zgodność z poprzednimi wersjami. Oznacza to na przykład, że wprowadzenie nowego elementu członkowskiego w [klasie](../../language-reference/keywords/class.md) bazowej o takiej samej nazwie jak element członkowski w klasie pochodnej jest w pełni obsługiwane przez C# program i nie prowadzi do nieoczekiwanego zachowania. Oznacza to również, że klasa musi jawnie określać, czy metoda jest przeznaczona do przesłania dziedziczonej metody lub czy metoda jest nową metodą, która ukrywa podobną metodę o nazwie dziedziczone.  
  
 W C#, klasy pochodne mogą zawierać metody o tej samej nazwie co metody klasy bazowej.  
  
- Metoda klasy bazowej musi być zdefiniowana jako [wirtualna](../../language-reference/keywords/virtual.md).  
  
- Jeśli metoda w klasie pochodnej nie jest poprzedzona przez [nowe](../../language-reference/keywords/new-modifier.md) lub zastępujące słowa kluczowe, kompilator wyda ostrzeżenie, a metoda będzie zachowywać się [](../../language-reference/keywords/override.md) `new` tak, jakby słowo kluczowe było obecne.  
  
- Jeśli metoda w klasie pochodnej jest poprzedzona `new` słowem kluczowym, metoda jest definiowana jako niezależna od metody w klasie bazowej.  
  
- Jeśli metoda w klasie pochodnej jest poprzedzona `override` słowem kluczowym, obiekty klasy pochodnej spowodują wywołanie tej metody zamiast metody klasy bazowej.  
  
- Metodę klasy bazowej można wywołać z poziomu klasy pochodnej przy użyciu `base` słowa kluczowego.  
  
- Słowa kluczowe `virtual` ,i`new` można również zastosować do właściwości, indeksatorów i zdarzeń. `override`  
  
 Domyślnie C# metody nie są wirtualne. Jeśli metoda jest zadeklarowana jako wirtualna, każda klasa, która dziedziczy metodę, może zaimplementować własną wersję. Aby można było wykonać wirtualną metodę, `virtual` modyfikator jest używany w deklaracji metody klasy bazowej. Klasa pochodna może następnie zastąpić podstawową metodę wirtualną za pomocą `override` słowa kluczowego lub ukryć metodę wirtualną w klasie podstawowej przy `new` użyciu słowa kluczowego. Jeśli nie `override` określono słowa kluczowego `new` ani słowa kluczowego, kompilator wyda ostrzeżenie, a metoda w klasie pochodnej spowoduje ukrycie metody w klasie bazowej.  
  
 Aby to zademonstrować, założono, że firma a utworzyła klasę o nazwie `GraphicsClass`, która jest używana przez program. Poniżej przedstawiono następujące `GraphicsClass`elementy:  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Firma używa tej klasy i używa jej do uzyskania własnej klasy, dodając nową metodę:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Aplikacja jest używana bez problemów, dopóki Firma A nie wydzieli nowej wersji `GraphicsClass`programu, która będzie podobna do następującego kodu:  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 Nowa wersja programu `GraphicsClass` zawiera teraz metodę o nazwie `DrawRectangle`. Początkowo nic się nie dzieje. Nowa wersja jest nadal zgodna ze standardem binarnym ze starszą wersją. Wdrożone oprogramowanie będzie nadal działało, nawet jeśli nowa klasa jest zainstalowana w tych systemach komputerowych. Wszystkie istniejące wywołania metody `DrawRectangle` będą nadal odwoływać się do Twojej wersji w klasie pochodnej.  
  
 Jednak po ponownym skompilowaniu aplikacji przy użyciu nowej wersji programu `GraphicsClass`zostanie wyświetlone ostrzeżenie z kompilatora, CS0108. To ostrzeżenie informuje o tym, że należy rozważyć sposób, w jaki `DrawRectangle` Metoda ma działać w aplikacji.  
  
 Jeśli chcesz, aby Metoda przesłaniał nową metodę klasy bazowej, użyj `override` słowa kluczowego:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 Słowo kluczowe upewnia się, że wszystkie obiekty `YourDerivedGraphicsClass` pochodne będą używały wersji `DrawRectangle`klasy pochodnej. `override` Obiekty pochodne od `YourDerivedGraphicsClass` mogą nadal uzyskiwać dostęp do `DrawRectangle` wersji klasy bazowej przy użyciu słowa kluczowego Base:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Jeśli nie chcesz, aby Metoda przesłaniał nową metodę klasy bazowej, mają zastosowanie następujące zagadnienia. Aby uniknąć pomyłek między tymi dwoma metodami, można zmienić nazwę metody. Może to być czasochłonne i podatne na błędy, a w niektórych przypadkach nie jest to praktycznie praktyczne. Jeśli jednak projekt jest stosunkowo mały, możesz użyć opcji refaktoryzacji programu Visual Studio, aby zmienić nazwę metody. Aby uzyskać więcej informacji, zobacz [Refaktoryzacja klas i typów (Projektant klas)](/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Alternatywnie można zapobiec ostrzeżeniu za pomocą słowa kluczowego `new` w definicji klasy pochodnej:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 `new` Użycie słowa kluczowego informuje kompilator, że definicja ukrywa definicję, która jest zawarta w klasie bazowej. Jest to zachowanie domyślne.  
  
## <a name="override-and-method-selection"></a>Przesłoń i wybór metody  
 Gdy metoda jest nazywana w klasie, C# kompilator wybiera najlepszą metodę wywołania, jeśli więcej niż jedna metoda jest zgodna z wywołaniem, na przykład wtedy, gdy istnieją dwie metody o tej samej nazwie i parametry, które są zgodne z przekazaniem parametru. Następujące metody byłyby zgodne:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 Gdy `DoWork` jest wywoływana w `Derived`wystąpieniu, C# kompilator najpierw podejmie próbę wykonania wywołania zgodnego `DoWork` `Derived`z wersjami zadeklarowanymi oryginalnie. Metody override nie są uznawane za zadeklarowane w klasie, są to nowe implementacje metody zadeklarowanej w klasie bazowej. Tylko wtedy, C# gdy kompilator nie może dopasować wywołania metody do oryginalnej metody w `Derived` programie, podejmie próbę dopasowania wywołania do zastąpionej metody z tą samą nazwą i zgodnymi parametrami. Przykład:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Ponieważ zmienna `val` może być konwertowana na podwójnie niejawnie, wywołania C# `DoWork(double)` `DoWork(int)`kompilatora zamiast. Istnieją dwa sposoby, aby tego uniknąć. Najpierw należy unikać deklarowania nowych metod o takiej samej nazwie jak metody wirtualne. Następnie można wydać C# kompilatorowi wywołanie metody wirtualnej, przeszukiwanie listy metod klasy podstawowej przez rzutowanie wystąpienia `Derived` na. `Base` Ponieważ metoda jest wirtualna, implementacja `DoWork(int)` metody on `Derived` zostanie wywołana. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 Aby uzyskać więcej przykładów `new` dla `override`i, zobacz artykuł [wiedzą, kiedy używać przesłonięć i nowych słów kluczowych](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Metody](./methods.md)
- [Dziedziczenie](./inheritance.md)
