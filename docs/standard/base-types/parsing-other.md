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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85bb6dcdaa198b6b038cc80e1e38fa7d11123678
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086384"
---
# <a name="parsing-other-strings-in-net"></a>Analizowanie innych ciągów w programie .NET
Oprócz liczbowych i <xref:System.DateTime> ciągów, można również przeanalizować ciągi, które reprezentują typy <xref:System.Char>, <xref:System.Boolean>, i <xref:System.Enum> do typów danych.  
  
## <a name="char"></a>Char  
 Metoda analizy statycznej, skojarzona z **Char** — typ danych jest przydatne w przypadku konwertowania ciągu zawierający pojedynczy znak w jego wartość Unicode. Poniższy przykład kodu analizuje ciąg na znak Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boolean  
 **Logiczna** zawiera typ danych **przeanalizować** metodę, która służy do przekonwertowania na ciąg reprezentujący wartość typu Boolean do rzeczywistego **logiczna** typu. Ta metoda nie jest rozróżniana wielkość liter i może pomyślnie przeanalizować ciąg zawierający "wartość prawda" lub "False". **Przeanalizować** metoda skojarzona z **logiczna** typu, również mogą analizować ciągi, które są ujęte w białych znaków. Jeśli inny ciąg jest przekazywany, <xref:System.FormatException> zgłaszany.  
  
 Poniższy przykład kodu wykorzystuje **przeanalizować** metodę, aby skonwertować ciąg na wartość logiczną.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Wyliczenie  
 Można użyć statycznej **przeanalizować** metodę, aby zainicjować typem wyliczenia na wartość ciągu. Ta metoda akceptuje typ wyliczeniowy, który jest analiza kodu, ciąg do analizy i opcjonalna Flaga wartości logicznej wskazująca, czy analizy jest rozróżniana wielkość liter. Ciąg, który jest analizowania może zawierać kilka wartości rozdzielonych przecinkami, które mogą być poprzedza lub następuje co najmniej jeden pusty miejsca do magazynowania (zwane również białych znaków). Jeśli ciąg zawiera wiele wartości, wartość zwróconego obiektu jest wartość wszystkie wartości określonej w połączeniu z operacją bitowe OR.  
  
 W poniższym przykładzie użyto **przeanalizować** metody, aby przekonwertować ciąg reprezentujący wartość wyliczenia. <xref:System.DayOfWeek> Wyliczenia jest inicjowany do **czwartek** z ciągu.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)  
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
- [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
