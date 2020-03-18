---
title: Analizowanie innych ciągów w .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 08e891501bbefcf8b32eff10dd7294af9d81adac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127572"
---
# <a name="parsing-other-strings-in-net"></a>Analizowanie innych ciągów w .NET
<xref:System.DateTime> Oprócz liczb i ciągów można również analizować ciągi reprezentujące <xref:System.Char>typy <xref:System.Boolean>, <xref:System.Enum> i na typy danych.  
  
## <a name="char"></a>Char  
 Metoda analizy statycznej skojarzonej z typem danych **Char** jest przydatna do konwertowania ciągu zawierającego pojedynczy znak na jego wartość Unicode. Poniższy przykład kodu analizuje ciąg do znaku Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Wartość logiczna  
 Typ danych **logicznych** zawiera metodę **analizy,** której można użyć do konwersji ciągu reprezentującego wartość logiczną na rzeczywisty typ **logiczny.** Ta metoda nie jest rozróżniana od wielkości liter i może pomyślnie przeanalizować ciąg zawierający ciąg "True" lub "False". **Metoda Parse** skojarzona z **typem logicznym** może również analizować ciągi, które są otoczone białymi spacjami. Jeśli inny ciąg jest <xref:System.FormatException> przekazywany, a jest generowany.  
  
 Poniższy przykład kodu używa **Parse** metody do konwersji ciągu do wartości logicznej.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Wyliczenie  
 Można użyć statycznej metody **Parse** do inicjowania typu wyliczenia do wartości ciągu. Ta metoda akceptuje typ wyliczenia, który analizujesz, ciąg do analizy i opcjonalną flagę logiczną wskazującą, czy analizowanie jest rozróżniane. Ciąg analizowany może zawierać kilka wartości oddzielonych przecinkami, które mogą być poprzedzone lub po których mogą następować co najmniej jeden pusty spacje (nazywane również białymi spacjami). Gdy ciąg zawiera wiele wartości, wartość zwróconego obiektu jest wartością wszystkich określonych wartości w połączeniu z operacją bitową LUB.  
  
 W poniższym przykładzie użyto **Metody Parse** do konwertowania reprezentacji ciągu na wartość wyliczenia. Wyliczenie <xref:System.DayOfWeek> jest inicjowane do **czwartku** z ciągu.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- [Analiza składniowa ciągów](../../../docs/standard/base-types/parsing-strings.md)
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Konwersja typów w .NET](../../../docs/standard/base-types/type-conversion.md)
