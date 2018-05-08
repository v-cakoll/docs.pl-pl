---
title: const (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 0038c1472964e618ee52ded9731fcb3e1e3ca204
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="const-c-reference"></a>const (odwołanie w C#)
Możesz użyć `const` — słowo kluczowe, aby zadeklarować pole stałej lub stałej lokalnej. Pola stałych i zmiennych lokalnych nie są zmienne i nie może być modyfikowany. Stałe można liczb, wartości logiczna, ciągi lub odwołanie o wartości null. Nie należy tworzyć stała do reprezentowania informacji, który będzie można zmienić w dowolnym momencie. Na przykład nie używaj pola stałej do przechowywania ceny usługi, numer wersji produktu lub nazwę firmy. Te wartości mogą ulec zmianie, a ponieważ kompilatory propagowane stałe, innych kodu skompilowanego za pomocą bibliotek będzie musiał ponownie skompilowana, aby zobaczyć zmiany. Zobacz też [tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md) — słowo kluczowe. Na przykład:  
  
```csharp
const int x = 0;  
public const double gravitationalConstant = 6.673e-11;  
private const string productName = "Visual C#";  
```  
  
## <a name="remarks"></a>Uwagi  
 Typ deklaracji stałej Określa typ elementów członkowskich, które wprowadza deklaracji. Inicjatora stałej lokalne lub pola stałej musi być wyrażenie stałe, który można niejawnie przekonwertować na typ docelowy.  
  
 Wyrażenie stałe jest wyrażenie, które może przyjąć pełni w czasie kompilacji. W związku z tym tylko to możliwe wartości to stałe typów referencyjnych `string` i odwołanie o wartości null.  
  
 Deklaracja stałej można zadeklarować wiele stałych, takich jak:  
  
```csharp
public const double x = 1.0, y = 2.0, z = 3.0;  
```  
  
 `static` Modyfikator nie jest dozwolony w deklaracji stałej.  
  
 Stała mogą uczestniczyć w wyrażeniu stałym w następujący sposób:  
  
```csharp
public const int c1 = 5;  
public const int c2 = c1 + 100;  
```  
  
> [!NOTE]
>  [Tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md) — słowo kluczowe różni się od `const` — słowo kluczowe. A `const` pól mogą być inicjowane tylko w deklaracji pola. A `readonly` pól mogą być inicjowane w deklaracji lub w konstruktorze. W związku z tym `readonly` pola mogą mieć różne wartości w zależności od Konstruktor używany. Ponadto mimo że `const` pole jest stałą czasu kompilacji `readonly` pole może być używane dla środowiska wykonawczego stałe, tak jak ten wiersz: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak używać stałych jako zmienne lokalne.  
  
 [!code-csharp[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [readonly](../../../csharp/language-reference/keywords/readonly.md)
