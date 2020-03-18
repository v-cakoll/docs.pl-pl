---
title: Jak używać właściwości indeksowanych w programowaniu współdziałania COM — Przewodnik po programowaniu języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 864e2274f0e0e79b4843e0bb67b5c4384eac8588
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712068"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Jak używać właściwości indeksowanych w programowaniu współdziałania COM (Przewodnik programowania C#)
*Właściwości indeksowane* poprawić sposób, w którym właściwości COM, które mają parametry są używane w programowaniu Języka C#. Właściwości indeksowane współpracują z innymi funkcjami w programie Visual C#, takimi jak [argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md), nowy typ[(dynamiczny)](../../language-reference/builtin-types/reference-types.md)i [osadzone informacje o typie](../../../standard/assembly/embed-types-visual-studio.md), aby ulepszyć programowanie pakietu Microsoft Office.  
  
 We wcześniejszych wersjach języka C#, metody są `get` dostępne jako właściwości tylko `set` wtedy, gdy metoda nie ma parametrów i metoda ma jeden i tylko jeden parametr wartości. Jednak nie wszystkie właściwości COM spełniają te ograniczenia. Na przykład Właściwość <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> Excel `get` ma akcesor, który wymaga parametru dla nazwy zakresu. W przeszłości, ponieważ nie można `Range` uzyskać dostępu do właściwości `get_Range` bezpośrednio, trzeba było użyć metody zamiast, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Właściwości indeksowane umożliwiają zapisanie następujących metod:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> W poprzednim przykładzie użyto również opcjonalnej funkcji `Type.Missing` [argumentów,](../classes-and-structs/named-and-optional-arguments.md) która umożliwia pominięcie .  
  
 Podobnie ustawić wartość `Value` właściwości obiektu w <xref:Microsoft.Office.Interop.Excel.Range> języku C# 3.0 i wcześniejszych, wymagane są dwa argumenty. Jeden dostarcza argument dla opcjonalnego parametru, który określa typ wartości zakresu. Drugi dostarcza wartość `Value` dla nieruchomości. Poniższe przykłady ilustrują te techniki. Oba ustawiają wartość komórki `Name`A1 na .
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Właściwości indeksowane umożliwiają napisanie następującego kodu.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Nie można tworzyć właściwości indeksowanych własnych. Funkcja obsługuje tylko zużycie istniejących właściwości indeksowanych.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia pełny przykład. Aby uzyskać więcej informacji na temat konfigurowania projektu, który uzyskuje dostęp do interfejsu API pakietu Office, zobacz [Jak uzyskać dostęp do obiektów pakietu Office interop przy użyciu funkcji języka C#.](./how-to-access-office-onterop-objects.md)
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Zobacz też

- [Argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md)
- [Dynamiczne](../../language-reference/builtin-types/reference-types.md)
- [Używanie typu dynamicznego](../types/using-type-dynamic.md)
- [Porada: użycie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji języka C#](./how-to-access-office-onterop-objects.md)
- [Instruktaż: Programowanie pakietu Office](./walkthrough-office-programming.md)
