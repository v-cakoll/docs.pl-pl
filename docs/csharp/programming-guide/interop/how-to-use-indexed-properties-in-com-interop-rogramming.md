---
title: 'Instrukcje: Użycie właściwości indeksowanych w programowaniu usługi Międzyoperacyjnej modelu COM - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 920b9ad28bb3bd26b7606fba12bdf2e042be49fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509860"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Instrukcje: Użycie właściwości indeksowanych w programowaniu usługi Międzyoperacyjnej modelu COM (C# Programming Guide)
*Właściwości indeksowanych* poprawić sposób, w których COM właściwości, które mają parametry są używane w programowaniu w języku C#. Indeksowane właściwości pracy w połączeniu z innymi funkcjami w języku Visual C#, takich jak [argumentów nazwanych i opcjonalnych](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), nowy typ ([dynamiczne](../../../csharp/language-reference/keywords/dynamic.md)), i [osadzonych informacji o typie](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), Zwiększ programowania Microsoft Office.  
  
 We wcześniejszych wersjach języka C#, są dostępne jako właściwości tylko wtedy, gdy metody `get` metoda nie ma parametrów i `set` metoda ma jeden i tylko jeden parametr wartości. Jednak nie wszystkie właściwości modelu COM spełniać te ograniczenia. Na przykład program Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> właściwość ma `get` metodę dostępu, która wymaga parametru Nazwa zakresu. W przeszłości ponieważ nie można uzyskać dostępu `Range` właściwości bezpośrednio, trzeba było używać `get_Range` metody zamiast tego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 Właściwości indeksowane umożliwiają zamiast niego zapisu do następujących:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  W poprzednim przykładzie użyto również [opcjonalne argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) funkcji, która pozwala na pominięcie `Type.Missing`.  
  
 Podobnie jak wartość `Value` właściwość <xref:Microsoft.Office.Interop.Excel.Range> obiektu w programie Visual C# 2008 i starszych, wymagane są dwa argumenty. Dostarcza jeden argument opcjonalny parametr określający typ wartości zakresu. Druga dostarcza wartość `Value` właściwości. Poniższe przykłady ilustrują tych metod. Ustawiają wartość komórki A1 do `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 Właściwości indeksowane umożliwiają zamiast tego Zapisz poniższy kod.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 Nie można utworzyć właściwości indeksowanych samodzielnie. Ta funkcja obsługuje tylko użycie istniejącej właściwości indeksowanych.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia kompletny przykład. Aby uzyskać więcej informacji o tym, jak skonfigurować projekt, który uzyskuje dostęp do interfejsu API pakietu Office, zobacz [jak: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)
- [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Instrukcje: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)
- [Przewodnik: Programowanie Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
