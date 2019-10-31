---
title: Analizowanie innych ciągów w programie .NET
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127572"
---
# <a name="parsing-other-strings-in-net"></a>Analizowanie innych ciągów w programie .NET
Oprócz ciągów numerycznych i <xref:System.DateTime>, można również analizować ciągi reprezentujące typy <xref:System.Char>, <xref:System.Boolean>i <xref:System.Enum> do typów danych.  
  
## <a name="char"></a>Char  
 Statyczna metoda analizy skojarzona z typem danych **char** jest przydatna do konwertowania ciągu, który zawiera pojedynczy znak do jego wartości Unicode. Poniższy przykład kodu analizuje ciąg w znak Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boolean  
 Typ danych **Boolean** zawiera metodę **analizy** , której można użyć do przekonwertowania ciągu, który reprezentuje wartość logiczną w rzeczywistym typie **Boolean** . W tej metodzie nie jest rozróżniana wielkość liter i można pomyślnie przeanalizować ciąg zawierający wartość "true" lub "false". Metoda **Parse** skojarzona z typem **Boolean** może również analizować ciągi, które są ujęte w białe znaki. W przypadku przekazanie dowolnego innego ciągu zostanie zgłoszony <xref:System.FormatException>.  
  
 Poniższy przykład kodu używa metody **Parse** do przekonwertowania ciągu na wartość logiczną.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Wyliczenie  
 Możesz użyć statycznej metody **Parse** , aby zainicjować typ wyliczeniowy jako wartość ciągu. Ta metoda akceptuje analizowany typ wyliczeniowy, ciąg do przeanalizowania i opcjonalną flagę logiczną wskazującą, czy podczas analizy jest rozróżniana wielkość liter. Analizowany ciąg może zawierać kilka wartości rozdzielonych przecinkami, które mogą być poprzedzone lub po którym następuje jedna lub więcej pustych spacji (nazywanych również białymi spacjami). Gdy ciąg zawiera wiele wartości, wartość zwracanego obiektu jest wartością wszystkich określonych wartości połączonych z bitową lub operacją.  
  
 W poniższym przykładzie zastosowano metodę **Parse** do przekonwertowania ciągu na wartość wyliczenia. Wyliczenie <xref:System.DayOfWeek> jest inicjowane w **czwartek** od ciągu.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
- [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
