---
title: 'Porady: przesłanianie metody ToString (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 86394f5fed55f57df8928648548fcfca117b00d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330710"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Porady: przesłanianie metody ToString (Przewodnik programowania w języku C#)
Każdej klasie lub strukturze w języku C# niejawnie dziedziczy <xref:System.Object> klasy. W związku z tym każdy obiekt w języku C# pobiera <xref:System.Object.ToString%2A> metodę, która zwraca reprezentację ciągu tego obiektu. Na przykład wszystkie zmienne typu `int` ma `ToString` metodę, która pozwala na zwrócenie ich zawartość jako ciąg:  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 Podczas tworzenia niestandardowej klasy lub struktury, należy zastąpić <xref:System.Object.ToString%2A> metody w celu podania informacji o typie, aby kod klienta.  
  
 Aby uzyskać informacje o sposobie używania ciągów formatu i inne typy formatowania niestandardowych z `ToString` metody, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
>  W przypadku podjęcia decyzji informacjach zapewnienie za pomocą tej metody, należy rozważyć, czy Twojej klasie lub strukturze będzie nigdy używana w kodzie niezaufanym. Należy zachować ostrożność upewnić się, że nie udostępniają wszystkie informacje, które mogą być wykorzystywane przez złośliwy kod.  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a>Aby przesłonić metodę ToString w Twojej klasie lub strukturze  
  
1.  Deklarowanie `ToString` metody za pomocą następujących modyfikatorów i typ zwracany:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  Zaimplementuj metodę, tak aby zwracało ciąg.  
  
     Poniższy przykład zwraca nazwę klasy oprócz danych określonej do konkretnego wystąpienia klasy.  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     Możesz przetestować `ToString` metody, jak pokazano w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IFormattable>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Ciągi](../../../csharp/programming-guide/strings/index.md)  
 [string](../../../csharp/language-reference/keywords/string.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [Formatowanie typów](../../../standard/base-types/formatting-types.md)
