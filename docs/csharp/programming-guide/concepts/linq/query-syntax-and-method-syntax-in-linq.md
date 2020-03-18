---
title: Składnia zapytania i metody w technologii LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 17280daaf98010245bbd019652a2a46d7f66ab59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635499"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Składnia zapytania i metody w technologii LINQ (C#)
Większość zapytań w dokumentacji introductory Language Integrated Query (LINQ) jest zapisywana przy użyciu składni kwerendy deklaratywnej LINQ. Jednak składnia kwerendy musi zostać przetłumaczona na wywołania metody dla programu runtime języka wspólnego .NET (CLR) podczas kompilowania kodu. Te wywołania metody wywołać standardowych operatorów zapytań, `Join`które `Max`mają `Average`nazwy, takie jak `Where`, `Select`, `GroupBy`, , i . Można wywołać je bezpośrednio przy użyciu składni metody zamiast składni kwerendy.  
  
 Składnia kwerendy i składnia metody są semantycznie identyczne, ale wiele osób uważa składnię zapytania prostsze i łatwiejsze do odczytania. Niektóre zapytania muszą być wyrażone jako wywołania metody. Na przykład należy użyć wywołania metody do wyrażenia kwerendy, która pobiera liczbę elementów, które pasują do określonego warunku. Należy również użyć wywołania metody dla kwerendy, która pobiera element, który ma maksymalną wartość w sekwencji źródłowej. Dokumentacja referencyjna dla standardowych <xref:System.Linq> operatorów kwerend w obszarze nazw zazwyczaj używa składni metody. W związku z tym nawet podczas rozpoczynania pisania zapytań LINQ, warto zapoznać się z tym, jak używać składni metody w kwerendach i w samych wyrażeniach kwerend.  
  
## <a name="standard-query-operator-extension-methods"></a>Metody rozszerzające standardowy operator zapytań  
 W poniższym przykładzie przedstawiono proste *wyrażenie zapytania* i semantycznie równoważne zapytanie zapisane jako *zapytanie oparte na metodach*.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 Dane wyjściowe z dwóch przykładów jest identyczna. Widać, że typ zmiennej kwerendy jest taki <xref:System.Collections.Generic.IEnumerable%601>sam w obu formach: .  
  
 Aby zrozumieć zapytanie oparte na metodach, zbadajmy ją bliżej. Po prawej stronie wyrażenia należy zauważyć, że klauzula `where` jest teraz `numbers` wyrażona jako metoda wystąpienia na `IEnumerable<int>`obiekcie, który jak będzie odwołanie ma typ . Jeśli znasz <xref:System.Collections.Generic.IEnumerable%601> ogólny interfejs, wiesz, że nie `Where` ma metody. Jeśli jednak wywołasz listę uzupełniania IntelliSense w programie Visual Studio `Where` IDE, zobaczysz nie `Select`tylko `SelectMany` `Join`metodę, `Orderby`ale wiele innych metod, takich jak , , i . Są to wszystkie standardowe operatory zapytań.  
  
 ![Zrzut ekranu przedstawiający wszystkie standardowe operatory zapytań w intellisense.](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 Chociaż wygląda na <xref:System.Collections.Generic.IEnumerable%601> to, że został ponownie zdefiniowany w celu uwzględnienia tych dodatkowych metod, w rzeczywistości tak nie jest. Standardowe operatory zapytań są implementowane jako nowy rodzaj metody o nazwie *metody rozszerzenia*. Metody rozszerzeń "rozszerzają" istniejący typ; można je wywołać tak, jakby były metody wystąpienia na typ. Standardowe operatory <xref:System.Collections.Generic.IEnumerable%601> zapytań rozszerzają się `numbers.Where(...)`i dlatego można pisać .  
  
 Aby rozpocząć korzystanie z LINQ, wszystko, co naprawdę trzeba wiedzieć o metodach rozszerzenia jest `using` jak doprowadzić je do zakresu w aplikacji przy użyciu odpowiednich dyrektyw. Z punktu widzenia aplikacji metoda rozszerzenia i metoda zwykłego wystąpienia są takie same.  
  
 Aby uzyskać więcej informacji na temat metod rozszerzenia, zobacz [Metody rozszerzenia](../../classes-and-structs/extension-methods.md). Aby uzyskać więcej informacji o standardowych operatorach kwerend, zobacz [Omówienie standardowych operatorów kwerend (C#)](./standard-query-operators-overview.md). Niektórzy dostawcy LINQ, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] takich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jak i , implementują własne standardowe operatory zapytań i dodatkowe metody rozszerzenia dla innych typów oprócz <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 W poprzednim przykładzie należy zauważyć,`num % 2 == 0`że wyrażenie warunkowe ( ) jest `Where` przekazywana jako argument w wierszu do metody: `Where(num => num % 2 == 0).` To wyrażenie w wierszu jest nazywany wyrażenie lambda. Jest to wygodny sposób pisania kodu, który w przeciwnym razie musiałby być napisany w bardziej kłopotliwej formie jako metoda anonimowa lub ogólny delegat lub drzewo wyrażeń. W języku C# `=>` jest operator lambda, który jest odczytywany jako "idzie do". Po `num` lewej stronie operatora jest zmienna wejściowa, która odpowiada `num` w wyrażeniu kwerendy. Kompilator można wywnioskować typ, `num` ponieważ wie, że `numbers` jest typem rodzajowym. <xref:System.Collections.Generic.IEnumerable%601> Treść lambda jest taka sama jak wyrażenie w składni kwerendy lub w innych wyrażeniach lub instrukcji C#; może zawierać wywołania metody i inne złożone logiki. "Wartość zwracana" jest tylko wynikiem wyrażenia.  
  
 Aby rozpocząć korzystanie z LINQ, nie trzeba używać lambdas szeroko. Jednak niektóre zapytania mogą być wyrażone tylko w składni metody, a niektóre z nich wymagają wyrażenia lambda. Po zapoznaniu się z lambdas, przekonasz się, że są one potężnym i elastycznym narzędziem w swoim przyborniku LINQ. Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](../../statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Możliwości tworzenia zapytań  
 W poprzednim przykładzie kodu należy `OrderBy` pamiętać, że metoda jest wywoływana przy `Where`użyciu operatora kropki na wywołanie . `Where`tworzy filtrowaną sekwencję, `Orderby` a następnie działa na tej sekwencji, sortując ją. Ponieważ kwerendy `IEnumerable`zwracają , można je skomponować w składni metody, łącząc kombinacje metody razem. To, co kompilator robi za kulisami podczas pisania zapytań przy użyciu składni kwerendy. A ponieważ zmienna kwerendy nie przechowuje wyników kwerendy, można ją zmodyfikować lub użyć jako podstawy dla nowej kwerendy w dowolnym momencie, nawet po jej wykonaniu.  
