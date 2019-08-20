---
title: 'Instrukcje: Zastąpienie metody ToString — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: a2cf05dc6b288ffdaf1a20cf594231f48046a724
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596749"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Instrukcje: Zastąp metodę ToString (C# Przewodnik programowania)

Każda klasa lub struktura w C# niejawnie dziedziczy <xref:System.Object> klasy. W związku z tym każdy C# obiekt w <xref:System.Object.ToString%2A> Pobiera metodę, która zwraca ciąg reprezentujący ten obiekt. Na przykład wszystkie zmienne typu `int` `ToString` mają metodę, która umożliwia im zwracanie ich zawartości jako ciągu:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Podczas tworzenia niestandardowej klasy lub struktury należy zastąpić <xref:System.Object.ToString%2A> metodę, aby podać informacje o typie kodu klienta.  
  
 Aby uzyskać informacje o sposobach używania ciągów formatowania i innych typów formatowania niestandardowego z `ToString` metodą, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> W przypadku podjęcia decyzji o tym, jakie informacje mają być zawarte w tej metodzie, należy rozważyć, czy dana klasa lub struktura będzie kiedykolwiek używana przez kod niezaufany. Należy zachować ostrożność, aby upewnić się, że nie podano żadnych informacji, które mogą być wykorzystywane przez złośliwy kod.  
  
Aby zastąpić `ToString` metodę w klasie lub strukturze:
  
1. Zadeklaruj `ToString` metodę z następującymi modyfikatorami i zwracanym typem:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Zaimplementuj metodę, tak aby zwracała ciąg.  
  
     Poniższy przykład zwraca nazwę klasy oprócz danych specyficznych dla określonego wystąpienia klasy.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Możesz przetestować `ToString` metodę, jak pokazano w poniższym przykładzie kodu:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IFormattable>
- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Ciągi](../strings/index.md)
- [string](../../language-reference/keywords/string.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
