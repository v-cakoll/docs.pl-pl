---
title: Jak zastąpić ToString metody - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 7c7196df56821c134b31982d7956a75039e9f929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705577"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Jak zastąpić ToString metody (C# Programming Guide)

Każda klasa lub struktura w języku <xref:System.Object> C# niejawnie dziedziczy klasę. W związku z tym każdy <xref:System.Object.ToString%2A> obiekt w języku C# pobiera metodę, która zwraca reprezentację ciągu tego obiektu. Na przykład wszystkie zmienne `int` typu `ToString` mają metodę, która umożliwia im zwracanie ich zawartości jako ciągu:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Podczas tworzenia klasy niestandardowej lub struktury, należy <xref:System.Object.ToString%2A> zastąpić metodę w celu dostarczenia informacji o typie do kodu klienta.  
  
 Aby uzyskać informacje dotyczące używania ciągów formatu i innych `ToString` typów formatowania niestandardowego z tą metodą, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Po podjęciu decyzji, jakie informacje należy podać za pomocą tej metody, należy wziąć pod uwagę, czy klasy lub struktury będą kiedykolwiek używane przez niezaufany kod. Należy zachować ostrożność, aby upewnić się, że nie podasz żadnych informacji, które mogą być wykorzystane przez złośliwy kod.  
  
Aby zastąpić `ToString` metodę w klasie lub strukturze:
  
1. Deklaruj `ToString` metodę za pomocą następujących modyfikatorów i typu zwracanego:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Zaimplementuj metodę tak, aby zwracaciąg.  
  
     Poniższy przykład zwraca nazwę klasy oprócz danych specyficznych dla określonego wystąpienia klasy.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Można przetestować `ToString` metodę, jak pokazano w poniższym przykładzie kodu:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IFormattable>
- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Ciągi](../strings/index.md)
- [ciąg](../../language-reference/builtin-types/reference-types.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
