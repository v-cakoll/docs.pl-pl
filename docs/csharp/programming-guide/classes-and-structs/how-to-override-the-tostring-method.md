---
title: 'Instrukcje: Przesłanianie metody ToString - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 0be35b64e9df3ec2a78c62735b1b7072e092f073
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240742"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Instrukcje: Przesłanianie metody ToString (C# Programming Guide)
Każdej klasy lub struktury w języku C# dziedziczy niejawnie <xref:System.Object> klasy. W związku z tym, każdy obiekt w języku C# pobiera <xref:System.Object.ToString%2A> metody, która zwraca reprezentację ciągu tego obiektu. Na przykład, wszystkie zmienne typu `int` mają `ToString` metody, która pozwala na zwrócenie ich zawartość jako ciąg:  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 Podczas tworzenia niestandardowej klasy lub struktury, należy zastąpić <xref:System.Object.ToString%2A> metody w celu zapewnienia informacji na temat danego typu kodu klienta.  
  
 Aby uzyskać informacje o sposobie używania ciągów formatu oraz inne rodzaje niestandardowe formatowanie przy użyciu `ToString` metody, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
>  Gdy zdecydujesz, jakie informacje, aby zapewnić za pośrednictwem tej metody, należy rozważyć, czy swojej klasy lub struktury nigdy nie będzie służyć przez niezaufany kod. Uważaj upewnić się, nie podano żadnych informacji, które mogą zostać wykorzystane przez złośliwego kodu.  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a>Aby przesłonięcie metody ToString w swojej klasie lub strukturze  
  
1.  Zadeklaruj `ToString` następujące Modyfikatory oraz zwracany typ metody:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  Implementowanie metoda zwraca ciąg.  
  
     Poniższy przykład zwraca nazwę klasy, oprócz danych określonej do konkretnego wystąpienia klasy.  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     Możesz przetestować `ToString` metody, jak pokazano w poniższym przykładzie kodu:  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IFormattable>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Ciągi](../../../csharp/programming-guide/strings/index.md)  
- [string](../../../csharp/language-reference/keywords/string.md)  
- [new](../../../csharp/language-reference/keywords/new.md)  
- [override](../../../csharp/language-reference/keywords/override.md)  
- [virtual](../../../csharp/language-reference/keywords/virtual.md)  
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
