---
title: 'Porady: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 5856ef871f865b2af0ab9ea637c26242cf99fb34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337925"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Porady: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM (Przewodnik programowania w języku C#)
*Właściwości indeksowanych* ulepszyć sposób, w których COM właściwości, które mają parametry są używane w programowaniu w języku C#. Indeksowane właściwości pracy wraz z innymi funkcjami języka Visual C#, takich jak [argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), nowy typ ([dynamiczne](../../../csharp/language-reference/keywords/dynamic.md)), i [osadzonych informacji o typie](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), do ulepszanie programowania w języku Microsoft Office.  
  
 We wcześniejszych wersjach języka C#, są dostępne jako właściwości tylko wtedy, gdy metody `get` — metoda nie ma parametrów i `set` metoda ma jeden i tylko jeden parametr wartości. Jednak nie wszystkie właściwości modelu COM spełnia te ograniczenia. Na przykład programu Excel [zakres](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) ma właściwość `get` dostępu, który wymaga parametru nazwy zakresu. W przeszłości ponieważ nie można uzyskać dostępu `Range` właściwości bezpośrednio, można było użyć `get_Range` metody zamiast tego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 Właściwości indeksowane umożliwiają zapisu zamiast poniżej:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  W poprzednim przykładzie również użyto [Argumenty opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) funkcji, dzięki czemu można pominąć `Type.Missing`.  
  
 Podobnie jak wartość `Value` właściwość [zakres](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) obiektów w programie Visual C# 2008 i starszych wersji, wymagane są dwa argumenty. Udostępnia jeden argument opcjonalny parametr określający typ wartości zakresu. Druga dostarcza wartość `Value` właściwości. Poniższe przykłady przedstawiają metody te. Obie wartości komórki A1 `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 Właściwości indeksowane pozwalają na zapis zamiast niej następujący kod.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 Nie można utworzyć właściwości indeksowanych własny. Gdy funkcja obsługuje tylko zużycie istniejącej właściwości indeksowane.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia pełny przykład. Aby uzyskać więcej informacji na temat sposobu konfigurowania projektu, który uzyskuje dostęp do interfejsu API usługi Office, zobacz [porady: dostępu do obiektów międzyoperacyjności pakietu Office za pomocą Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [Instrukcje: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 [Wskazówki: Programowanie Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
