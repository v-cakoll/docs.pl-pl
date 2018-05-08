---
title: Składnia zapytania i metody w technologii LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 6b943da442d2ec1210911cb9f4b6a0d56c7216d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Składnia zapytania i metody w technologii LINQ (C#)
Większość zapytań w zapytaniu zintegrowane wprowadzające języka ([!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]) dokumentacji zostały napisane przy użyciu składni deklaratywne zapytania LINQ. Jednak składnia zapytania musi można przetłumaczyć jej na wywołania metody dla platformy .NET środowisko uruchomieniowe języka wspólnego (CLR) podczas kompilowania kodu. Standardowe operatory zapytań, które mają nazwy, takie jak wywołania tych wywołań metody `Where`, `Select`, `GroupBy`, `Join`, `Max`, i `Average`. Możesz je wywołać bezpośrednio, używając składni metody zamiast składni zapytań.  
  
 Składnia zapytania a składnia metody są semantycznie identyczne, ale wiele osób znaleźć składnia zapytania prostszy i bardziej czytelne. Niektóre kwerendy muszą być wyrażone jako wywołania metody. Na przykład możesz korzystać wywołania metody Express kwerendę, która pobiera liczbę elementów spełniających określony warunek. Możesz również użyć wywołania metody dla zapytania, które pobiera element, który ma wartość maksymalna w sekwencji źródłowej. Dokumentacja referencyjna dla standardowych operatorów zapytań w <xref:System.Linq> przestrzeń nazw zazwyczaj używa składni metody. W związku z tym nawet wtedy, gdy wprowadzenie zapisu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, warto należy zapoznać się ze sposobem w zapytaniach i w wyrażeniach zapytań, same należy użyć składni metody.  
  
## <a name="standard-query-operator-extension-methods"></a>Metody rozszerzające standardowy operator zapytań  
 W poniższym przykładzie przedstawiono prosty *zapytania wyrażenie* i semantycznie równoważne zapytanie zapisywane jako *zapytania oparte na metodzie*.  
  
 [!code-csharp[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 Dane wyjściowe z dwa przykłady jest identyczne. Widać, że typu zmienną zapytania jest taka sama w obu formach: <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Aby poznać zapytania oparte na metodzie, Przeanalizujmy go lepiej. Po prawej stronie wyrażenia, zwróć uwagę, że `where` klauzuli teraz jest wyrażona jako metodę wystąpienia na `numbers` obiektu, który będzie przypominać jako użytkownik ma typ `IEnumerable<int>`. Jeśli znasz ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejsu, wiadomo, że nie ma `Where` metody. Jednak jeśli wywołanie na liście uzupełniania IntelliSense w środowisku IDE programu Visual Studio, zobaczysz nie tylko `Where` metody, ale wiele innych metod, takich jak `Select`, `SelectMany`, `Join`, i `Orderby`. Są to wszystkie standardowe operatory zapytań.  
  
 ![Standardowe operatory zapytań w Intellisense](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 Mimo że wygląda tak, jakby <xref:System.Collections.Generic.IEnumerable%601> został zdefiniowany ponownie, aby uwzględnić te dodatkowe metody, w rzeczywistości nie jest to. Standardowe operatory zapytań są zaimplementowane jako nowy rodzaj wywołano metodę *metody rozszerzenia*. Metody rozszerzenia "rozszerzenia" istniejący typ; może być wywołana tak jakby były to wystąpienie metody w typie. Rozszerzenie standardowych operatorów zapytań <xref:System.Collections.Generic.IEnumerable%601> i oznacza to dlaczego można napisać `numbers.Where(...)`.  
  
 Aby rozpocząć korzystanie z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], które trzeba wiedzieć o metody rozszerzenia jest sposób w celu zapewnienia ich zakresu w aplikacji przy użyciu prawidłowego `using` dyrektywy. Z punktu widzenia aplikacji metodę rozszerzenia, a także metodę wystąpienia regularne są takie same.  
  
 Aby uzyskać więcej informacji na temat metody rozszerzenia, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Aby uzyskać więcej informacji dotyczących standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md). Niektóre [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawców, takich jak [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], implementują własnych standardowych operatorów zapytań i metody dodatkowe rozszerzenia dla innych typów poza <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 W poprzednim przykładzie, zwróć uwagę, że wyrażenie warunkowe (`num % 2 == 0`) jest przekazywany jako argument w wierszu `Where` metody: `Where(num => num % 2 == 0).` tego wyrażenia wbudowanego nosi nazwę wyrażenia lambda. Jest to wygodny sposób pisania kodu, które byłyby w przeciwnym razie są zapisywane w postaci bardziej kłopotliwy metody anonimowej lub Delegat ogólny drzewo wyrażenia. W języku C# `=>` jest operatora lambda, który jest do odczytu jako "zbliża się do". `num` Po lewej stronie operatora jest wejściowego zmiennej, która odpowiada `num` w wyrażeniu zapytania. Kompilator można wywnioskować typu elementu `num` ponieważ wie, że `numbers` jest rodzajowy <xref:System.Collections.Generic.IEnumerable%601> typu. Treść Wyrażenie lambda jest tę samą jako wyrażenie w składni zapytania lub innych C# wyrażenia lub instrukcji; może zawierać wywołania metody i innych złożonej logiki. "Wartość zwracana" jest tylko do wyniku wyrażenia.  
  
 Aby rozpocząć korzystanie z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], nie trzeba używać wyrażeń lambda często. Jednak niektóre kwerendy można wyrazić tylko wtedy w składni metody i niektóre z tych wymagają wyrażenia lambda. Po więcej zapoznanie się z wyrażenia lambda znajdziesz się wystarczająco wydajny i elastyczny narzędzia w Twojej [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przybornika. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Możliwości tworzenia zapytań  
 W poprzednim przykładzie kodu, należy pamiętać, że `OrderBy` metoda jest wywoływana przy użyciu operatora kropki w wywołaniu `Where`. `Where` Tworzy sekwencję filtrowane, a następnie `Orderby` działa w tej kolejności, sortując go. Ponieważ kwerendy zwracają `IEnumerable`, je utworzyć w składni metody przez tworzenie łańcucha wywołań metody razem. Jest to, jak kompilator działa w tle podczas pisania zapytania przy użyciu składni zapytania. I ponieważ zmienną zapytania nie zapisuje wyniki zapytania, można go zmodyfikować lub używać go jako podstawę dla nowego zapytania w dowolnym momencie, nawet po zostało uruchomione.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
