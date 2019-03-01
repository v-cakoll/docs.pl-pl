---
title: Argumenty nazwane i opcjonalne — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: c816b9e5e2ed24f60962797428d4b28033068885
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978634"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Argumenty nazwane i opcjonalne (Przewodnik programowania w języku C#)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] wprowadza argumentów nazwanych i opcjonalnych. *Argumenty nazwane* umożliwiają określenie argumentu dla parametru określonego argumentu można skojarzyć z nazwą parametru, a nie za pomocą parametru pozycji na liście parametrów. *Argumenty opcjonalne* umożliwia pominięcie argumentów dla niektórych parametrów. Obu tych technik może służyć za pomocą metod, indeksatorów, konstruktorów i delegatów.  
  
 Użycie argumentów nazwanych i opcjonalnych, argumenty są obliczane w kolejności, w jakiej są wyświetlane na liście argumentów nie listy parametrów.  
  
 Parametry nazwane i opcjonalne, gdy jest używana razem umożliwiają podać argumenty tylko kilka parametrów z listy parametrów opcjonalnych. Ta funkcja znacznie ułatwia wywołania interfejsów COM, takich jak interfejsów API automatyzacji usługi Microsoft Office.  
  
## <a name="named-arguments"></a>Argumenty nazwane  
 Argumenty nazwane pozbawione potrzebę Pamiętaj lub wyszukać kolejność parametrów na liście parametrów wywoływanych metod. Parametr dla każdego argumentu można określić nazwę parametru. Na przykład funkcja, która wyświetla szczegóły zamówienia (takie jak nazwa sprzedawcy, nazwa produktu & liczby zamówienia) może zostać wywołany w sposób standardowy, wysyłając argumentów według pozycji w kolejności, zdefiniowanych przez funkcję.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Jeśli nie pamiętasz kolejności parametrów, ale znasz ich nazw, można wysyłać argumenty w dowolnej kolejności.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Argumenty nazwane również poprawić czytelność kodu, określając, co reprezentuje każdy argument. W metodzie przykład poniżej `sellerName` nie może mieć wartość null lub biały znak. Oba `sellerName` i `productName` są typami parametrów, zamiast wysyłać argumentów według pozycji, dobrym pomysłem będzie używać argumentów nazwanych do odróżniania dwóch i unikanie pomyłek dla każdego, kto kodu.
  
 Nazwane argumenty, gdy jest używane z argumentów pozycyjnych, są prawidłowe tak długo, jak 

- mogą one nie następuje argumenty pozycyjne, lub

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _począwszy od C# 7.2_, są używane w poprawnej pozycji. W przykładzie poniżej, parametr `orderNum` jest w prawidłowym położeniu, ale nie jest jawnie nazwane.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Jednak argumenty nazwane poza kolejnością jest nieprawidłowy, jeśli masz następuje argumentów pozycyjnych.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Przykład  
 Poniższy kod implementuje przykłady w tej sekcji oraz dodatkowe niektóre z nich.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a>Argumenty opcjonalne.  
 Definicję metody, konstruktora, indeksatora lub delegata można określić, że jej parametry są wymagane lub czy są opcjonalne. Każde wywołanie należy podać argumenty dla wszystkich wymaganych parametrów, ale można pominąć argumenty dla parametrów opcjonalnych.  
  
 Każdy parametr opcjonalny ma wartość domyślną, jako część jego definicji. Jeśli żaden argument nie zostanie wysłany dla tego parametru, wartością domyślną jest używany. Wartość domyślna musi być jedną z następujących typów wyrażeń:  
  
-   wyrażenie stałe;  
  
-   wyrażenie w formie `new ValType()`, gdzie `ValType` jest typem wartości, takich jak [wyliczenia](../../../csharp/language-reference/keywords/enum.md) lub [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
-   wyrażenie w formie [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), gdzie `ValType` jest typem wartości.  
  
 Opcjonalne parametry są definiowane na końcu listy parametrów po wszelkie wymagane parametry. Obiekt wywołujący dostarcza argumentu jednego z kolejnych następujące parametry opcjonalne, wymagają podania dla wszystkich poprzednich parametry opcjonalne argumenty. Rozdzielana przecinkami przerwy na liście argumentów nie są obsługiwane. Na przykład w poniższym kodzie metodę wystąpienia `ExampleMethod` jest zdefiniowana za pomocą jednego wymagany i dwa parametry opcjonalne.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Następujące wywołanie `ExampleMethod` powoduje błąd kompilatora, ponieważ argument zostanie podany, trzeci parametr, ale nie do drugiego.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Jednak jeśli znasz nazwę trzeci parametr służy nazwany argument do wykonania zadania.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 Funkcja IntelliSense używa nawiasów, aby wskazać parametry opcjonalne, jak pokazano na poniższej ilustracji.  
  
 ![Szybkie informacje technologii IntelliSense dla metody ExampleMethod. ](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")  
Parametry opcjonalne w ExampleMethod  
  
> [!NOTE]
>  Można również zadeklarować następujące parametry opcjonalne przy użyciu platformy .NET <xref:System.Runtime.InteropServices.OptionalAttribute> klasy. `OptionalAttribute` Parametry nie wymagają wartości domyślnej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie, Konstruktor `ExampleClass` ma jeden parametr, który jest opcjonalny. Metodę wystąpienia `ExampleMethod` ma jeden parametr wymagany, `required`i dwa parametry opcjonalne, `optionalstr` i `optionalint`. Kod w `Main` pokazano różne sposoby, w którym można wywołać konstruktora i metody.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>Interfejsy modelu COM  
 Argumenty nazwane i opcjonalne oraz obsługę obiektów dynamicznych i inne ulepszenia znacznie poprawić współdziałanie z interfejsów API modelu COM, takich jak interfejsy API usługi Automation pakietu Office.  
  
 Na przykład <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> metodę w programie Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interfejs ma siedem parametry, z których wszystkie są opcjonalne. Te parametry są wyświetlane na poniższej ilustracji.  
  
 ![Szybkie informacje technologii IntelliSense dla metody AutoFormat. ](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")  
Autoformat — parametry  
  
 W języku C# 3.0 i wcześniejszych wersjach argument jest wymagany dla każdego parametru, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Jednak znacznie upraszczają wywołanie `AutoFormat` przy użyciu argumentów nazwanych i opcjonalnych, wprowadzona w języku C# 4.0. Nazwę i opcjonalne argumenty umożliwiają pominięcia argumentu dla parametru opcjonalnego, jeśli nie chcesz zmienić wartość domyślną parametru. W poniższym wywołaniu określono wartość tylko dla jednego z siedmiu parametrów.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Aby uzyskać więcej informacji i przykładów, zobacz [jak: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) i [jak: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Rozpoznanie przeciążenia  
 Użycie argumentów nazwanych i opcjonalnych wpływa na rozpoznanie przeciążenia w następujący sposób:  
  
-   Metoda, indeksator lub Konstruktor jest kandydatem do wykonywania w przypadku każdego z jego parametrów jest opcjonalny albo odpowiada według nazwy lub pozycji, aby jeden argument w instrukcji wywołujące, i że argument można przekonwertować na typ parametru.  
  
-   Jeśli zostanie znalezione więcej niż jeden Release candidate, zasady rozpoznawania przeciążenia preferowanych konwersje są stosowane do argumentów, które są jawnie określone. Pominięty Argumenty opcjonalne parametry są ignorowane.  
  
-   Jeśli dwa kandydatów zostaną ocenione one równie dobrze, preferencji jest przesyłany do Release candidate, który nie ma parametrów opcjonalnych, które zostały pominięte argumentów w wywołaniu. Jest to konsekwencją Ogólne preferencji w przeciążeniu rozdzielczości dla kandydatów, które mają mniej parametrów.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Używanie konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [Używanie indeksatorów](../../../csharp/programming-guide/indexers/using-indexers.md)
