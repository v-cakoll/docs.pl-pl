---
title: sizeof (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 83038255160ec778c71120566cf8f99092761add
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270581"
---
# <a name="sizeof-c-reference"></a>sizeof (odwołanie w C#)
Używany do uzyskania rozmiar w bajtach dla typu niezarządzanego. Niezarządzane na typy wbudowane typy, które są wymienione w tabeli poniżej, a także następujące:  
  
-   Typy wyliczeniowe  
  
-   Typy wskaźnika  
  
-   Struktury zdefiniowane przez użytkownika, które nie zawierają żadnych pól lub właściwości, które są typy odwołań  
  
 Poniższy przykład przedstawia sposób pobrać rozmiar `int`:  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od wersji 2.0 C#, stosowania `sizeof` do wbudowanych typów nie wymaga, aby [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) można używać trybu.  
  
 `sizeof` Operator nie może być przeciążony. Wartości zwracane przez `sizeof` operator są typu `int`. W poniższej tabeli przedstawiono stałe wartości, które są zastępowane dla `sizeof` wyrażeń, które mają określone typy wbudowane jako argumentów.  
  
|Wyrażenie|Stała wartość|  
|----------------|--------------------|  
|`sizeof(sbyte)`|1|  
|`sizeof(byte)`|1|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 (Unicode)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1|  
  
 Struktury, łącznie z dla wszystkich innych typów `sizeof` operatora można używać tylko w blokach niebezpieczny kod. Chociaż można używać <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, wartość zwracana przez tę metodę nie zawsze jest taka sama jak wartość zwracana przez `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> Zwraca rozmiar po organizowanego typ, podczas gdy `sizeof` zwraca rozmiar, ponieważ zawiera ona przydzielone przez środowisko uruchomieniowe języka wspólnego, w tym wszelkie uzupełnienia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [enum](../../../csharp/language-reference/keywords/enum.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Stałe](../../../csharp/programming-guide/classes-and-structs/constants.md)
