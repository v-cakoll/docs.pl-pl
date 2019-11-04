---
title: 'Instrukcje: Zastępowanie metody ToString — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 9dd567e537768ceb8b9f61ce58dccd443db38ec7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419341"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Porady: przesłanianie metody ToString (Przewodnik programowania w języku C#)

Każda klasa lub struktura w C# niejawnie dziedziczy klasy <xref:System.Object>. W związku z tym każdy C# obiekt w pobiera metodę <xref:System.Object.ToString%2A>, która zwraca ciąg reprezentujący ten obiekt. Na przykład wszystkie zmienne typu `int` mają metodę `ToString`, która umożliwia im zwracanie zawartości jako ciągu:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Podczas tworzenia niestandardowej klasy lub struktury należy zastąpić metodę <xref:System.Object.ToString%2A>, aby podać informacje o typie kodu klienta.  
  
 Aby uzyskać informacje dotyczące sposobu używania ciągów formatowania i innych typów formatowania niestandardowego z metodą `ToString`, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> W przypadku podjęcia decyzji o tym, jakie informacje mają być zawarte w tej metodzie, należy rozważyć, czy dana klasa lub struktura będzie kiedykolwiek używana przez kod niezaufany. Należy zachować ostrożność, aby upewnić się, że nie podano żadnych informacji, które mogą być wykorzystywane przez złośliwy kod.  
  
Aby zastąpić metodę `ToString` w klasie lub strukturze:
  
1. Zadeklaruj metodę `ToString` z następującymi modyfikatorami i zwracanym typem:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Zaimplementuj metodę, tak aby zwracała ciąg.  
  
     Poniższy przykład zwraca nazwę klasy oprócz danych specyficznych dla określonego wystąpienia klasy.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Możesz przetestować metodę `ToString`, jak pokazano w poniższym przykładzie kodu:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IFormattable>
- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Ciągi](../strings/index.md)
- [string](../../language-reference/builtin-types/reference-types.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
