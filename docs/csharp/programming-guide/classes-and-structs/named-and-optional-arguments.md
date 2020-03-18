---
title: Argumenty nazwane i opcjonalne — przewodnik programowania języka C#
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
ms.openlocfilehash: 15b685248730c1f742035612a201d97d180bbc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399813"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Argumenty nazwane i opcjonalne (Przewodnik programowania w języku C#)
C# 4 wprowadza nazwane i opcjonalne argumenty. *Nazwane argumenty* umożliwiają określenie argumentu dla określonego parametru, kojarząc argument z nazwą parametru, a nie z pozycją parametru na liście parametrów. *Opcjonalne argumenty* umożliwiają pominięcie argumentów dla niektórych parametrów. Obie techniki mogą być używane z metodami, indeksatorów, konstruktorów i delegatów.  
  
 W przypadku używania argumentów nazwanych i opcjonalnych argumenty są oceniane w kolejności, w jakiej pojawiają się na liście argumentów, a nie na liście parametrów.  
  
 Parametry nazwane i opcjonalne, gdy są używane razem, umożliwiają dostarczanie argumentów tylko dla kilku parametrów z listy parametrów opcjonalnych. Ta funkcja znacznie ułatwia wywołania interfejsów COM, takich jak interfejsy API automatyzacji pakietu Microsoft Office.  
  
## <a name="named-arguments"></a>Nazwane argumenty  
 Nazwane argumenty uwalniają cię od konieczności zapamiętywania lub wyszukiwania kolejności parametrów na listach parametrów wywoływanych metod. Parametr dla każdego argumentu można określić według nazwy parametru. Na przykład funkcja, która drukuje szczegóły zamówienia (takie jak nazwa sprzedającego, numer zamówienia & nazwa produktu) można wywołać w standardowy sposób, wysyłając argumenty według pozycji, w kolejności zdefiniowanej przez funkcję.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Jeśli nie pamiętasz kolejności parametrów, ale znasz ich nazwy, możesz wysłać argumenty w dowolnej kolejności.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Nazwane argumenty również poprawić czytelność kodu, identyfikując, co reprezentuje każdy argument. W poniższej metodzie `sellerName` przykładowej nie może być null lub biały znak. Ponieważ `sellerName` oba `productName` i są typy ciągów, zamiast wysyłania argumentów według pozycji, ma sens użycie nazwanych argumentów do rozróżniania dwóch i zmniejszyć zamieszanie dla każdego, kto czyta kod.
  
 Nazwane argumenty, używane z argumentami pozycyjnymi, są prawidłowe tak długo, jak

- nie następują po nimi żadne argumenty pozycyjne, lub

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _począwszy od C# 7.2_, są one używane we właściwej pozycji. W poniższym przykładzie `orderNum` parametr znajduje się we właściwej pozycji, ale nie jest jawnie nazwany.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Argumenty pozycyjne, które następują po wszystkich poza kolejnością nazwanych argumentów są nieprawidłowe.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Przykład  
 Poniższy kod implementuje przykłady z tej sekcji wraz z kilkoma dodatkowymi.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]  
  
## <a name="optional-arguments"></a>Argumenty opcjonalne  
 Definicja metody, konstruktora, indeksatora lub delegata można określić, że jego parametry są wymagane lub że są one opcjonalne. Każde wywołanie musi zawierać argumenty dla wszystkich wymaganych parametrów, ale można pominąć argumenty dla parametrów opcjonalnych.  
  
 Każdy parametr opcjonalny ma wartość domyślną jako część jego definicji. Jeśli dla tego parametru nie zostanie wysłany żaden argument, używana jest wartość domyślna. Wartość domyślna musi być jednym z następujących typów wyrażeń:  
  
- wyrażenie stałe;  
  
- wyrażenie formularza `new ValType()`, gdzie `ValType` jest typem wartości, takim jak [wyliczenie](../../language-reference/builtin-types/enum.md) lub [struktura;](../../language-reference/builtin-types/struct.md)  
  
- wyrażenie domyślnego formularza [(ValType),](../../language-reference/operators/default.md) `ValType` gdzie jest typem wartości.  
  
 Parametry opcjonalne są definiowane na końcu listy parametrów, po wszelkich wymaganych parametrach. Jeśli obiekt wywołujący zawiera argument dla jednego z kolejnych parametrów opcjonalnych, musi podać argumenty dla wszystkich poprzednich parametrów opcjonalnych. Odstępy oddzielone przecinkami na liście argumentów nie są obsługiwane. Na przykład w poniższym kodzie metoda `ExampleMethod` wystąpienia jest zdefiniowana z jednym wymaganym i dwoma parametrami opcjonalnymi.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]  
  
 Następujące wywołanie `ExampleMethod` powoduje błąd kompilatora, ponieważ argument jest podany dla trzeciego parametru, ale nie dla drugiego.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Jeśli jednak znasz nazwę trzeciego parametru, możesz użyć nazwanego argumentu do wykonania zadania.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense używa nawiasów do wskazywania parametrów opcjonalnych, jak pokazano na poniższej ilustracji:  
  
 ![Zrzut ekranu przedstawiający szybkie informacje intelliSense dla metody ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)  
  
> [!NOTE]
> Można również zadeklarować parametry opcjonalne <xref:System.Runtime.InteropServices.OptionalAttribute> przy użyciu klasy .NET. `OptionalAttribute`parametry nie wymagają wartości domyślnej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konstruktor ma `ExampleClass` jeden parametr, który jest opcjonalny. Metoda `ExampleMethod` instancji ma jeden `required`wymagany parametr i `optionalstr` dwa `optionalint`parametry opcjonalne i . Kod w `Main` pokazuje różne sposoby, w których można wywołać konstruktora i metody.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]  
  
## <a name="com-interfaces"></a>Interfejsy COM  
 Nazwane i opcjonalne argumenty, a także obsługa obiektów dynamicznych i innych ulepszeń znacznie zwiększają współdziałanie z interfejsami ComI, takimi jak interfejsy API automatyzacji pakietu Office.  
  
 Na przykład <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> metoda w interfejsie <xref:Microsoft.Office.Interop.Excel.Range> programu Microsoft Office Excel ma siedem parametrów, z których wszystkie są opcjonalne. Parametry te przedstawiono na poniższej ilustracji:  
  
 ![Zrzut ekranu przedstawiający szybkie informacje intelliSense dla metody Autoformatowania.](./media/named-and-optional-arguments/autoformat-method-parameters.png)  
  
 W języku C# 3.0 i wcześniejszych wersjach dla każdego parametru wymagany jest argument, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]  
  
 Można jednak znacznie uprościć `AutoFormat` wywołanie przy użyciu argumentów nazwanych i opcjonalnych, wprowadzonych w języku C# 4.0. Nazwane i opcjonalne argumenty umożliwiają pominięcie argumentu dla parametru opcjonalnego, jeśli nie chcesz zmieniać wartości domyślnej parametru. W następującym wywołaniu wartość jest określona tylko dla jednego z siedmiu parametrów.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]  
  
 Aby uzyskać więcej informacji i przykładów, zobacz [Jak używać nazwanych i opcjonalnych argumentów w programowaniu pakietu Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) i jak uzyskać dostęp do obiektów pakietu Office [interop przy użyciu funkcji języka C#.](../interop/how-to-access-office-onterop-objects.md)  
  
## <a name="overload-resolution"></a>Rozpoznanie przeciążenia  
 Użycie nazwanych i opcjonalnych argumentów wpływa na rozpoznawanie przeciążenia w następujący sposób:  
  
- Metoda, indeksator lub konstruktor jest kandydatem do wykonania, jeśli każdy z jego parametrów jest opcjonalny lub odpowiada, według nazwy lub pozycji, pojedynczemu argumentowi w instrukcji wywołującej, a ten argument można przekonwertować na typ parametru.  
  
- Jeśli zostanie znaleziony więcej niż jeden kandydat, reguły rozpoznawania przeciążenia dla preferowanych konwersji są stosowane do argumentów, które są jawnie określone. Pominięte argumenty dla parametrów opcjonalnych są ignorowane.  
  
- Jeśli dwóch kandydatów zostanie ocenionych jako równie dobre, preferencja trafia do kandydata, który nie ma opcjonalnych parametrów, dla których argumenty zostały pominięte w zaproszeniu. Jest to konsekwencją ogólnej preferencji w rozpoznawaniu przeciążenia dla kandydatów, którzy mają mniej parametrów.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Porada: użycie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office](./how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Używanie typu dynamicznego](../types/using-type-dynamic.md)
- [Używanie konstruktorów](./using-constructors.md)
- [Używanie indeksatorów](../indexers/using-indexers.md)
