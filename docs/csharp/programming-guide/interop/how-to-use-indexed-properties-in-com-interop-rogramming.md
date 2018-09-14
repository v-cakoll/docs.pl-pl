---
title: 'Porady: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 0169bfa6eb3ba01a9a88c2b247ad3f78da67d59c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527821"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Porady: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM (Przewodnik programowania w języku C#)
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
 Poniższy kod przedstawia kompletny przykład. Aby uzyskać więcej informacji o tym, jak skonfigurować projekt, który uzyskuje dostęp do interfejsu API pakietu Office, zobacz [porady: uzyskiwanie dostępu do obiektów o międzyoperacyjności pakietu Office za pomocą funkcji Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
- [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
- [Instrukcje: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
- [Wskazówki: Programowanie Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
