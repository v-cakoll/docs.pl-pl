---
title: Argumenty nazwane i opcjonalne — C# Przewodnik programowania
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
ms.openlocfilehash: 30475b637202d3b614ac968897e467956bc78646
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970505"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Argumenty nazwane i opcjonalne (Przewodnik programowania w języku C#)
C#4 wprowadza argumenty nazwane i opcjonalne. *Nazwane argumenty* umożliwiają określenie argumentu dla określonego parametru przez skojarzenie argumentu z nazwą parametru, a nie z pozycją parametru na liście parametrów. *Argumenty opcjonalne* umożliwiają pominięcie argumentów dla niektórych parametrów. Obie techniki mogą być używane z metodami, indeksatorami, konstruktorami i delegatami.  
  
 W przypadku używania argumentów nazwanych i opcjonalnych argumenty są oceniane w kolejności, w jakiej są wyświetlane na liście argumentów, a nie na liście parametrów.  
  
 Parametry nazwane i opcjonalne, gdy są używane razem, umożliwiają dostarczenie argumentów dla tylko kilku parametrów z listy opcjonalnych parametrów. Ta funkcja znacznie ułatwia wywoływanie interfejsów COM, takich jak interfejsy API automatyzacji Microsoft Office.  
  
## <a name="named-arguments"></a>Nazwane argumenty  
 Nazwane argumenty uwalniają użytkownika od konieczności zapamiętania lub wyszukiwania kolejności parametrów na listach parametrów wywoływanych metod. Parametr dla każdego argumentu można określić za pomocą nazwy parametru. Na przykład funkcja, która drukuje szczegóły zamówienia (takie jak nazwa sprzedawcy, numer zamówienia & Nazwa produktu), może być wywoływana w standardowy sposób przez wysłanie argumentów według pozycji w kolejności zdefiniowanej przez funkcję.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Jeśli nie pamiętasz kolejności parametrów, ale znasz ich nazwy, możesz wysłać argumenty w dowolnej kolejności.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Argumenty nazwane również zwiększają czytelność kodu przez zidentyfikowanie, co reprezentuje każdy argument. W poniższym przykładzie metoda `sellerName` nie może mieć wartości null ani być białym znakiem. Zarówno `sellerName`, jak i `productName` są typami ciągów, zamiast wysyłać argumenty według pozycji, warto użyć nazwanych argumentów, aby odróżnić dwa i zmniejszyć liczbę pomyłek dla każdego odczytu kodu.
  
 Argumenty nazwane, gdy są używane z argumentami pozycyjnymi, są prawidłowe tak długo, jak 

- nie są one następują żadnych argumentów pozycyjnych lub

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _począwszy od C# 7,2_, są one używane w poprawnej pozycji. W poniższym przykładzie parametr `orderNum` znajduje się w poprawnej pozycji, ale nie jest jawnie nazwany.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Argumenty pozycyjne, które są zgodne z argumentami nazwanymi poza kolejnością, są nieprawidłowe.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Przykład  
 Poniższy kod implementuje przykłady z tej sekcji wraz z dodatkowymi.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a>Argumenty opcjonalne  
 Definicja metody, konstruktora, indeksatora lub delegata może określać, że parametry są wymagane lub są opcjonalne. Każde wywołanie musi udostępniać argumenty dla wszystkich wymaganych parametrów, ale może pominąć argumenty dla parametrów opcjonalnych.  
  
 Każdy opcjonalny parametr ma wartość domyślną w ramach swojej definicji. Jeśli żaden argument nie jest wysyłany dla tego parametru, zostanie użyta wartość domyślna. Wartość domyślna musi być jednym z następujących typów wyrażeń:  
  
- wyrażenie stałe;  
  
- wyrażenie `new ValType()`, gdzie `ValType` jest typem wartości, na przykład [wyliczeniem](../../language-reference/keywords/enum.md) lub [strukturą](./structs.md);  
  
- wyrażenie [domyślne (ValType)](../../language-reference/operators/default.md), gdzie `ValType` jest typem wartości.  
  
 Parametry opcjonalne są definiowane na końcu listy parametrów po dowolnych wymaganych parametrach. Jeśli obiekt wywołujący zawiera argument dla dowolnego z parametrów opcjonalnych, musi podać argumenty dla wszystkich poprzedzających parametry opcjonalne. Luki rozdzielane przecinkami na liście argumentów nie są obsługiwane. Na przykład, w poniższym kodzie metoda wystąpienia `ExampleMethod` jest zdefiniowana z jednym wymaganym i dwoma opcjonalnymi parametrami.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Następujące wywołanie `ExampleMethod` powoduje wystąpienie błędu kompilatora, ponieważ argument jest dostarczany dla trzeciego parametru, ale nie w drugim.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Jeśli jednak znasz nazwę trzeciego parametru, możesz użyć argumentu nazwanego do wykonania zadania.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 Funkcja IntelliSense używa nawiasów, aby wskazać parametry opcjonalne, jak pokazano na poniższej ilustracji:  
  
 ![Zrzut ekranu przedstawiający funkcję IntelliSense Quick info dla metody ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> Można również zadeklarować parametry opcjonalne przy użyciu klasy .NET <xref:System.Runtime.InteropServices.OptionalAttribute>. parametry `OptionalAttribute` nie wymagają wartości domyślnej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie Konstruktor dla `ExampleClass` ma jeden parametr, który jest opcjonalny. Metoda wystąpienia `ExampleMethod` ma jeden wymagany parametr, `required`i dwa parametry opcjonalne, `optionalstr` i `optionalint`. Kod w `Main` pokazuje różne sposoby wywoływania konstruktora i metody.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>Interfejsy COM  
 Argumenty nazwane i opcjonalne wraz z obsługą obiektów dynamicznych i innych ulepszeń znacznie zwiększają współdziałanie z interfejsami API modelu COM, takimi jak interfejsy API usługi Office Automation.  
  
 Na przykład Metoda <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> w interfejsie Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> ma siedem parametrów, które są opcjonalne. Te parametry przedstawiono na poniższej ilustracji:  
  
 ![Zrzut ekranu przedstawiający funkcję IntelliSense Quick info dla metody Autoformatowania.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 W C# 3,0 i wcześniejszych wersjach argument jest wymagany dla każdego parametru, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Można jednak znacznie uprościć wywołanie do `AutoFormat` za pomocą argumentów nazwanych i opcjonalnych wprowadzonych w C# 4,0. Argumenty nazwane i opcjonalne umożliwiają pominięcie argumentu dla opcjonalnego parametru, jeśli nie chcesz zmieniać wartości domyślnej parametru. W poniższym wywołaniu wartość jest określona tylko dla jednego z siedmiu parametrów.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Aby uzyskać więcej informacji i przykładów, zobacz [jak używać argumentów nazwanych i opcjonalnych w programowaniu pakietu Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) oraz [jak: uzyskiwać dostęp do obiektów międzyoperacyjności pakietu Office za pomocą funkcji wizualnych C# ](../interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Rozpoznanie przeciążenia  
 Użycie argumentów nazwanych i opcjonalnych wpływa na rozpoznawanie przeciążenia w następujący sposób:  
  
- Metoda, indeksator lub Konstruktor jest kandydatem do wykonania, jeśli każdy z jego parametrów jest opcjonalny lub odpowiada według nazwy lub według pozycji, do pojedynczego argumentu w instrukcji wywołującej i ten argument można przekonwertować na typ parametru.  
  
- W przypadku znalezienia więcej niż jednego kandydata reguły rozpoznawania przeciążenia dla preferowanych konwersji są stosowane do argumentów, które są jawnie określone. Pominięte argumenty dla parametrów opcjonalnych są ignorowane.  
  
- Jeśli dwie kandydaci są uważane za równie dobre, preferencja przechodzi do kandydata, który nie ma parametrów opcjonalnych, dla których argumenty zostały pominięte w wywołaniu. Jest to konsekwencja ogólne preferencje rozpoznawania przeciążenia dla kandydatów, które mają mniej parametrów.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Używanie typu dynamicznego](../types/using-type-dynamic.md)
- [Używanie konstruktorów](./using-constructors.md)
- [Używanie indeksatorów](../indexers/using-indexers.md)
