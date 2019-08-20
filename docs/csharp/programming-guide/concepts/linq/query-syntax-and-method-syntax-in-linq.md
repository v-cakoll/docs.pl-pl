---
title: Składnia zapytania i metody w technologii LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 8351661bdb7eaf841577eb128a8fec12efed2360
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591424"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Składnia zapytania i metody w technologii LINQ (C#)
Większość zapytań w dokumentacji języka wprowadzającego Integrated Query[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]() jest zapisywana przy użyciu składni zapytania deklaracyjnego LINQ. Jednak Składnia zapytania musi być przetłumaczona na wywołania metody dla środowiska uruchomieniowego języka wspólnego (CLR) platformy .NET podczas kompilowania kodu. Te wywołania metody wywołują standardowe operatory zapytań, które mają nazwy takie jak `Where`, `Select`, `GroupBy`, `Join` `Max`, i `Average`. Można wywołać je bezpośrednio przy użyciu składni metody zamiast składni zapytania.  
  
 Składnia zapytań i składnia metody są semantycznie takie same, ale wiele osób może łatwiej odczytywać składnię zapytań. Niektóre zapytania muszą być wyrażone jako wywołania metod. Na przykład należy użyć wywołania metody, aby wyrazić zapytanie, które pobiera liczbę elementów zgodnych z określonym warunkiem. Należy również użyć wywołania metody dla zapytania pobierającego element, który ma wartość maksymalną w sekwencji źródłowej. Dokumentacja referencyjna dla standardowych operatorów zapytań w <xref:System.Linq> przestrzeni nazw zwykle używa składni metody. W związku z tym nawet gdy zaczynasz pisać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, warto zapoznać się z tematem jak używać składni metody w zapytaniach i w samych wyrażeniach zapytania.  
  
## <a name="standard-query-operator-extension-methods"></a>Metody rozszerzające standardowy operator zapytań  
 W poniższym przykładzie pokazano proste *wyrażenie zapytania* i semantycznie równoważne zapytanie zapisywane jako *zapytanie oparte*na metodzie.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 Dane wyjściowe z dwóch przykładów są identyczne. Można zobaczyć, że typ zmiennej zapytania jest taka sama w obu formach: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Aby zrozumieć zapytanie oparte na metodzie, Przeanalizujmy ją dokładniej. Po prawej stronie wyrażenia Zauważ, że `where` klauzula jest teraz wyrażona jako metoda wystąpienia `numbers` na obiekcie, co oznacza, że `IEnumerable<int>`odwołanie ma typ. Jeśli znasz interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601> , wiesz, że nie `Where` ma metody. Jeśli jednak zostanie wywołana lista uzupełniania IntelliSense w środowisku IDE programu Visual `Where` Studio, zobaczysz nie tylko metodę, ale wiele innych metod, takich jak `Select`, `SelectMany` `Join`, i `Orderby`. To są wszystkie standardowe operatory zapytań.  
  
 ![Zrzut ekranu przedstawiający wszystkie standardowe operatory zapytań w IntelliSense.](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 Mimo że został on <xref:System.Collections.Generic.IEnumerable%601> ponownie zdefiniowany w celu uwzględnienia tych dodatkowych metod, w rzeczywistości nie jest to przypadek. Standardowe operatory zapytań są implementowane jako nowy rodzaj metody wywoływanie *metod rozszerzających*. Metody rozszerzeń "rozszerzają" istniejący typ; mogą być wywoływane tak, jakby były metodami wystąpień w typie. Standardowe operatory zapytań zwiększają <xref:System.Collections.Generic.IEnumerable%601> się i dlatego można pisać. `numbers.Where(...)`  
  
 Aby rozpocząć korzystanie z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]programu, wszystko, co naprawdę trzeba wiedzieć na temat metod rozszerzających, polega na tym, jak przenieść je do zakresu w aplikacji `using` za pomocą odpowiednich dyrektyw. Z punktu widzenia aplikacji Metoda rozszerzająca i zwykła metoda wystąpienia są takie same.  
  
 Aby uzyskać więcej informacji na temat metod rozszerzających, zobacz [metody rozszerzenia](../../classes-and-structs/extension-methods.md). Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytańC#— omówienie ()](./standard-query-operators-overview.md). Niektórzy [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy, takie jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], implementują własne standardowe operatory zapytań <xref:System.Collections.Generic.IEnumerable%601>i dodatkowe metody rozszerzające dla innych typów.  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 W poprzednim przykładzie należy zauważyć, że wyrażenie warunkowe (`num % 2 == 0`) jest przekazywany jako argument w wierszu `Where` do metody: `Where(num => num % 2 == 0).`To wyrażenie wbudowane jest nazywane wyrażeniem lambda. Jest to wygodny sposób pisania kodu, który w przeciwnym razie musi być napisany w bardziej skomplikowany sposób jako metoda anonimowa lub Delegat ogólny lub drzewo wyrażenia. W C# `=>` programie jest operatorem lambda, który jest odczytywany jako "przechodzi do". Po lewej stronie operatora jest zmienną wejściową, która odnosi się do `num` w wyrażeniu zapytania. `num` Kompilator może wywnioskować typ `num` , ponieważ wie, że `numbers` jest typem ogólnym. <xref:System.Collections.Generic.IEnumerable%601> Treść wyrażenia lambda jest taka sama jak wyrażenie w składni zapytania lub w dowolnym innym C# wyrażeniu lub instrukcji. może obejmować wywołania metod i inne złożone logiki. "Zwracana wartość" jest tylko wynikiem wyrażenia.  
  
 Aby rozpocząć korzystanie z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]programu, nie musisz używać wyrażeń lambda w szerokim stopniu. Jednak niektóre zapytania można wyrazić tylko w składni metody, a niektóre z nich wymagają wyrażenia lambda. Po poznaniu się z wyrażeniami lambda można się dowiedzieć, że są one zaawansowanym i elastycznym narzędziem w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przyborniku. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../../statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Możliwości tworzenia zapytań  
 W poprzednim przykładzie kodu należy zauważyć, że `OrderBy` Metoda jest wywoływana przy użyciu operatora kropki w `Where`wywołaniu. `Where`tworzy filtrowaną sekwencję, a następnie `Orderby` działa w tej sekwencji, sortując ją. Ponieważ zapytania zwracają `IEnumerable`, należy je złożyć w składni metody przez łańcuch wywołań metod. Jest to działanie kompilatora w tle podczas pisania zapytań przy użyciu składni zapytania. A ponieważ zmienna zapytania nie przechowuje wyników zapytania, można je zmodyfikować lub użyć jako podstawy dla nowego zapytania w dowolnym momencie, nawet po jego wykonaniu.  
