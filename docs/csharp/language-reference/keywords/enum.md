---
title: enum (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 9714277f87095b709e37b582cd3435374d9a1555
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172231"
---
# <a name="enum-c-reference"></a>enum (odwołanie w C#)
`enum` — Słowo kluczowe służy do deklarowania wyliczenie różne typu, który zawiera zestaw stałe nazwane o nazwie listy modułu wyliczającego.  
  
 Zazwyczaj najlepiej jest zdefiniowanie wyliczenia bezpośrednio z poziomu obszaru nazw, tak aby wszystkie klasy w przestrzeni nazw do niego dostęp z wygody takie same. Jednak wyliczenia mogą być zagnieżdżone w obrębie klasy lub struktury.  
  
 Domyślnie pierwszy modułu wyliczającego ma wartość 0, a wartość każdego kolejnych modułu wyliczającego jest zwiększana o 1. Na przykład w następujących wyliczenia `Sat` jest `0`, `Sun` jest `1`, `Mon` jest `2`, itd.  
  
```csharp  
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Moduły wyliczające umożliwia inicjatory zastąpić wartości domyślne, jak pokazano w poniższym przykładzie.  
  
```csharp  
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 W tym wyliczeniu sekwencję elementów wymusza na uruchamianie z `1` zamiast `0`. Jednak zaleca się tym stałą, który ma wartość 0. Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe](../../../csharp/programming-guide/enumeration-types.md).  
  
 Każdy typ wyliczeniowy ma odpowiedni typ, który może być dowolnego typu całkowitego z wyjątkiem [char](../../../csharp/language-reference/keywords/char.md). Domyślny typ bazowy typu wyliczenia elementów jest [int](../../../csharp/language-reference/keywords/int.md). Aby zadeklarować wyliczenie innego typu całkowitego, takich jak [bajtów](../../../csharp/language-reference/keywords/byte.md), użyj dwukropka po identyfikatorze, a następnie według typu, jak pokazano w poniższym przykładzie.  
  
```csharp  
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 Istnieją typy zatwierdzone dla wyliczenia [bajtów](../../../csharp/language-reference/keywords/byte.md), [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), lub [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Zmienna typu `Day` można przypisać dowolną wartość z zakresu od typu źródłowego; wartości nie są ograniczone do stałe nazwane.  
  
 Wartość domyślna `enum E` jest wartością produkowane przez wyrażenie `(E)0`.  
  
> [!NOTE]
>  Moduł wyliczający nie może zawierać biały znak w nazwie.  
  
 Podstawowy typ Określa, ile miejsca do magazynowania jest przydzielona dla każdego modułu wyliczającego. Jednak jawnego rzutowania jest niezbędne do przekonwertowania z `enum` typu na typ całkowity. Na przykład następująca instrukcja przypisuje modułu wyliczającego `Sun` do zmiennej typu [int](../../../csharp/language-reference/keywords/int.md) przy użyciu rzutowanie do przekonwertowania z `enum` do `int`.  
  
```csharp  
int x = (int)Day.Sun;  
```  
  
 Po zastosowaniu <xref:System.FlagsAttribute?displayProperty=nameWithType> na wyliczenie, który zawiera elementy, które można łączyć z bitowego `OR` operacji, ten atrybut ma wpływ na zachowanie `enum` gdy jest używana z niektóre narzędzia. Można zauważyć tych zmian, korzystając z narzędzi takich jak <xref:System.Console> klas, metod i ewaluatora wyrażenia. (Zobacz przykład trzeci).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Tak jak w przypadku dowolnego stała wszystkie odwołania do poszczególnych wartości wyliczenia są konwertowane na literałach numerycznych w czasie kompilacji. To utworzenie potencjalne problemy z wersjonowaniem, zgodnie z opisem w [stałe](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
 Przypisywanie wartości dodatkowe do nowej wersji wyliczenia lub zmianę wartości członkowie wyliczenia w nowej wersji, mogą powodować problemy dla kodu źródłowego zależnych. Wartości wyliczenia są często używane w [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcje. Jeśli dodatkowe elementy zostały dodane do `enum` typu, domyślnej sekcji instrukcji switch można wybrać nieoczekiwanie.  
  
 Inni deweloperzy użycie kodu, wskazówki dotyczące sposobu ich kod powinien reagują, gdy nowe elementy są dodawane do dowolnego należy zapewnić `enum` typów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wyliczenie `Day`, jest zadeklarowany. Dwa moduły wyliczające jawnie przekonwertować na liczbę całkowitą i przypisane do zmiennych liczby całkowitej.  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie opcji typu base służy do deklarowania `enum` której członkami są typu `long`. Należy zauważyć, że nawet jeśli typ podstawowy wyliczenia jest `long`, elementy członkowskie wyliczenia nadal musi być jawnie przekonwertować na typ `long` przy użyciu rzutowanie.  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia użycie i wpływu <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu `enum` deklaracji.  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a>Komentarze  
 Jeśli usuniesz `Flags`, przykładzie wyświetlane są następujące wartości:  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Typy wyliczeniowe](../../../csharp/programming-guide/enumeration-types.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Konwencje nazewnictwa wyliczenia](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces#naming-enumerations)
