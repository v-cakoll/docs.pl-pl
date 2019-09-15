---
title: 'Instrukcje: Korzystanie z właściwości indeksowanych w programowaniu międzyoperacyjnym modelu COM — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: f1be14ad7ddb6973cc89f10c1735ba2ebce13f97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971646"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Instrukcje: Korzystanie z właściwości indeksowanych w programowaniu międzyoperacyjnym modelu COM (C# Przewodnik programowania)
*Właściwości indeksowane* ulepszają sposób, w jaki właściwości com, które mają parametry są C# używane w programowaniu. Właściwości indeksowane współpracują z innymi funkcjami w C#wizualizacji, takimi jak [argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md), nowy typ ([dynamiczny](../../language-reference/keywords/dynamic.md)) i [Informacje o typie osadzonym](../../../standard/assembly/embed-types-visual-studio.md), aby usprawnić programowanie Microsoft Office.  
  
 We wcześniejszych wersjach programu C#metody są dostępne jako właściwości tylko wtedy, gdy `get` Metoda nie ma parametrów, a `set` Metoda ma jeden i tylko jeden parametr value. Jednak nie wszystkie właściwości COM spełniają te ograniczenia. Na przykład właściwość programu Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> `get` ma metodę dostępu, która wymaga parametru dla nazwy zakresu. W przeszłości, ponieważ nie można uzyskać dostępu `Range` do właściwości bezpośrednio, należy `get_Range` użyć metody zamiast tego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Właściwości indeksowane umożliwiają napisanie następujących danych:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> W poprzednim przykładzie jest również stosowana funkcja [argumentów opcjonalnych](../classes-and-structs/named-and-optional-arguments.md) , która pozwala pominąć `Type.Missing`.  
  
 Podobnie, aby ustawić wartość `Value` właściwości <xref:Microsoft.Office.Interop.Excel.Range> obiektu w C# 3,0 i wcześniejszych, wymagane są dwa argumenty. Jeden dostarcza argument dla opcjonalnego parametru, który określa typ wartości zakresu. Pozostałe dostarczają wartość `Value` właściwości. Poniższe przykłady ilustrują te techniki. Obie wartości mają `Name`ustawioną wartość komórki a1.
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Właściwości indeksowane umożliwiają zapisanie w zamian poniższego kodu.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Nie można tworzyć własnych właściwości indeksowanych. Funkcja obsługuje tylko użycie istniejących właściwości indeksowanych.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia kompletny przykład. Aby uzyskać więcej informacji o konfigurowaniu projektu, który uzyskuje dostęp do interfejsu API pakietu Office [, zobacz How to: Dostęp do obiektów międzyoperacyjności pakietu C# Office](./how-to-access-office-onterop-objects.md)za pomocą funkcji wizualnych.  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/keywords/dynamic.md)
- [Używanie typu dynamicznego](../types/using-type-dynamic.md)
- [Instrukcje: Używanie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu C# Office za pomocą funkcji wizualnych](./how-to-access-office-onterop-objects.md)
- [Przewodnik: Programowanie Office](./walkthrough-office-programming.md)
