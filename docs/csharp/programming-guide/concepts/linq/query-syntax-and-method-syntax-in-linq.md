---
title: Składnia zapytania i metody w technologii LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 5ad58e921b16498139abe403a45b21bb22ef895d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564321"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Składnia zapytania i metody w technologii LINQ (C#)
Większość zapytań w wprowadzające Language Integrated Query ([!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]) dokumentacji są tworzone za pomocą składni deklaratywne zapytań LINQ. Jednak składnia zapytania muszą być przetłumaczone do wywołania metody dla platformy .NET środowisko uruchomieniowe języka wspólnego (CLR), gdy kod jest kompilowany. Te wywołania metody wywołania standardowych operatorów zapytań, które mają nazwy, takie jak `Where`, `Select`, `GroupBy`, `Join`, `Max`, i `Average`. Możesz je wywołać bezpośrednio przy użyciu składni metody zamiast składni zapytań.  
  
 Składnia zapytania a składnia metody są semantycznie identyczne, ale wiele osób uważa składni zapytań, prostsze i łatwiejsze do odczytania. Niektóre zapytania musi być wyrażona jako wywołania metody. Na przykład użytkownik musi być wywołanie metody express kwerendę, która pobiera liczbę elementów, które pasują do określonego warunku. Możesz także użyć wywołania metody dla zapytania, które pobiera element, który ma maksymalną wartość w sekwencji źródłowej. Dokumentacja referencyjna dla standardowych operatorów zapytań w <xref:System.Linq> przestrzeń nazw zazwyczaj używa składni metody. W związku z tym, nawet wtedy, gdy wprowadzenie do pisania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, warto znać, jak użyć metody składni w zapytaniach i w wyrażeniach zapytań, samodzielnie.  
  
## <a name="standard-query-operator-extension-methods"></a>Metody rozszerzające standardowy operator zapytań  
 W poniższym przykładzie przedstawiono prosty *wyrażeniu zapytania* i semantycznie równoważne zapytania zapisane jako *kwerendy oparte na metodzie*.  
  
 [!code-csharp[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 Dane wyjściowe z dwóch przykładach jest identyczna. Widać, że typ zmiennej zapytania jest taka sama w obu formach: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Aby dowiedzieć się kwerendy oparte na metodzie, Przeanalizujmy jej dokładniej. Po prawej stronie wyrażenia, zwróć uwagę, że `where` klauzuli teraz jest wyrażona jako metodę wystąpienia na `numbers` obiektu, który będzie przypominać, jak ma typ `IEnumerable<int>`. Jeśli znasz nazwę rodzajową <xref:System.Collections.Generic.IEnumerable%601> interfejsu, wiesz, że nie ma `Where` metody. Jednak jeśli wywołujesz lista dokańczania IntelliSense w środowisku IDE programu Visual Studio, zobaczysz nie tylko `Where` metody, ale także wiele innych metod, takich jak `Select`, `SelectMany`, `Join`, i `Orderby`. Są to wszystkie standardowe operatory zapytań.  
  
 ![Standardowe operatory zapytań w technologii Intellisense](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 Chociaż wygląda tak, jakby <xref:System.Collections.Generic.IEnumerable%601> został zdefiniowany ponownie, aby uwzględnić te dodatkowe metody, w rzeczywistości nie jest to wymagane. Standardowe operatory zapytań są implementowane jako nowego rodzaju metody o nazwie *metody rozszerzenia*. Metody rozszerzenia "rozszerzenia" istniejącego typu; może być wywoływana tak, jakby były metodami wystąpień w typie. Rozszerzenie standardowych operatorów zapytań <xref:System.Collections.Generic.IEnumerable%601> i oznacza to dlaczego możesz zapisywać `numbers.Where(...)`.  
  
 Aby rozpocząć pracę, przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], wszystko, co trzeba wiedzieć o metody rozszerzenia jest jak przenieść je do zakresu w aplikacji przy użyciu prawidłowego `using` dyrektywy. Z punktu widzenia aplikacji metody rozszerzenia a metoda regularnych wystąpieniach są takie same.  
  
 Aby uzyskać więcej informacji dotyczących metod rozszerzających, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Przegląd (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md). Niektóre [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawców, takich jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], implementują własnych standardowych operatorów zapytań i metody dodatkowe rozszerzenia dla innych typów, oprócz <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 W poprzednim przykładzie należy zauważyć, że wyrażenie warunkowe (`num % 2 == 0`) jest przekazywany jako argument w wierszu `Where` metody: `Where(num => num % 2 == 0).` To wyrażenie wbudowane nosi nazwę wyrażenia lambda. Jest to wygodny sposób napisać kod, który mieliby ma zostać zapisany w postaci bardziej kłopotliwy jako metoda anonimowa lub delegatem ogólnym lub drzewo wyrażenia. W języku C# `=>` operatora lambda, który zostanie odczytany jako "zbliża się do". `num` Po lewej stronie operatora jest zmienna wejściowa, który odpowiada `num` w wyrażeniu zapytania. Kompilator może wywnioskować typ `num` ponieważ wie, że `numbers` jest rodzajowa <xref:System.Collections.Generic.IEnumerable%601> typu. Treść wyrażenia lambda jest w taki sam jak wyrażenia w składni zapytania lub inne wyrażenie języka C# lub instrukcji; może zawierać wywołania metody i innych złożonej logiki. "Wartość zwracana" jest tylko wynik wyrażenia.  
  
 Aby rozpocząć pracę, przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], nie trzeba używać wyrażeń lambda często. Jednak niektóre zapytania tylko mogą być wyrażone w składni metody i niektóre z nich wymaga wyrażenia lambda. Po bardziej zapoznanie się z wyrażenia lambda można zauważyć, że są wydajne i elastyczne narzędzia w swojej [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przybornika. Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Możliwości tworzenia zapytań  
 W poprzednim przykładzie kodu należy pamiętać, że `OrderBy` metoda jest wywoływana za pomocą operatora kropki na wywołanie `Where`. `Where` Tworzy sekwencję filtrowane, a następnie `Orderby` działa w tej sekwencji przez posortowanie jej. Ponieważ zapytania zwracają `IEnumerable`, tworzysz je przy użyciu składni metody przez łączenie łańcuchowe wywołania metody. Jest to, jak kompilator działa w tle podczas pisania zapytań za pomocą składni zapytania. A ponieważ zmienna zapytania nie przechowuje wyników kwerendy, można go modyfikować lub używać go jako podstawy dla nowego zapytania w dowolnym momencie, nawet po zakończeniu zostało uruchomione.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
