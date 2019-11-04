---
title: 'Instrukcje: korzystanie z właściwości indeksowanych w programowaniu międzyoperacyjnym modelu COM — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 0d4e85646a1e7f8c4ee9a73fbf7bf5a01b10b14b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423221"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Porady: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM (Przewodnik programowania w języku C#)
*Właściwości indeksowane* ulepszają sposób, w jaki właściwości com, które mają parametry są C# używane w programowaniu. Właściwości indeksowane współpracują z innymi funkcjami w C#wizualizacji, takimi jak [argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md), nowy typ ([dynamiczny](../../language-reference/builtin-types/reference-types.md)) i [Informacje o typie osadzonym](../../../standard/assembly/embed-types-visual-studio.md), aby usprawnić programowanie Microsoft Office.  
  
 We wcześniejszych wersjach programu C#metody są dostępne jako właściwości tylko wtedy, gdy metoda `get` nie ma parametrów, a metoda `set` ma jeden i tylko jeden parametr value. Jednak nie wszystkie właściwości COM spełniają te ograniczenia. Na przykład właściwość <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> programu Excel ma metodę dostępu `get`, która wymaga parametru dla nazwy zakresu. W przeszłości, ponieważ nie można uzyskać dostępu do właściwości `Range` bezpośrednio, zamiast tego należy użyć metody `get_Range`, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Właściwości indeksowane umożliwiają napisanie następujących danych:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> W poprzednim przykładzie jest również stosowana funkcja [argumentów opcjonalnych](../classes-and-structs/named-and-optional-arguments.md) , która pozwala pominąć `Type.Missing`.  
  
 Podobnie, aby ustawić wartość właściwości `Value` obiektu <xref:Microsoft.Office.Interop.Excel.Range> w C# 3,0 i wcześniejszych, wymagane są dwa argumenty. Jeden dostarcza argument dla opcjonalnego parametru, który określa typ wartości zakresu. Pozostałe dostarczają wartość właściwości `Value`. Poniższe przykłady ilustrują te techniki. Ustaw wartość komórki a1 na `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Właściwości indeksowane umożliwiają zapisanie w zamian poniższego kodu.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Nie można tworzyć własnych właściwości indeksowanych. Funkcja obsługuje tylko użycie istniejących właściwości indeksowanych.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia kompletny przykład. Aby uzyskać więcej informacji o konfigurowaniu projektu, który uzyskuje dostęp do interfejsu API pakietu Office, zobacz [How to: dostęp do obiektów międzyoperacyjności pakietu Office za pomocą funkcji wizualnych C# ](./how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Używanie typu dynamicznego](../types/using-type-dynamic.md)
- [Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Instrukcje: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#](./how-to-access-office-onterop-objects.md)
- [Przewodnik: Programowanie Office](./walkthrough-office-programming.md)
