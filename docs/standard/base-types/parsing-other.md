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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7becf993db866e24381fe9013c82d74dd91ee9a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="parsing-other-strings-in-net"></a>Analizowanie innych ciągów w .NET
Oprócz numeryczne i <xref:System.DateTime> ciągi, możesz również przeanalizować ciągów, które reprezentują typy <xref:System.Char>, <xref:System.Boolean>, i <xref:System.Enum> do typów danych.  
  
## <a name="char"></a>Char  
 Metoda analizy statycznej skojarzona z **Char** — typ danych jest przydatne w przypadku konwertowania ciągu zawierający pojedynczy znak w jego wartości Unicode. Poniższy przykład kodu analizuje ciąg na znak Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boolean  
 **Logiczna** zawiera typ danych **przeanalizować** metodę, która służy do konwertowania ciąg reprezentujący wartość logiczna, do rzeczywistych **logiczna** typu. Ta metoda nie jest rozróżniana wielkość liter i pomyślnie można analizować ciąg zawierający "wartość prawda" lub "False". **Przeanalizować** metoda skojarzona z **logiczna** typu również mogą analizować ciągów, które są ujęte w białe znaki. Jeśli inne parametry są przekazywane, <xref:System.FormatException> jest generowany.  
  
 Poniższy przykład kodu wykorzystuje **przeanalizować** metody do przekonwertowania ciągu na wartość logiczną.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Wyliczenie  
 Można użyć statycznych **przeanalizować** metoda inicjowania typu wyliczenia na wartość ciągu. Ta metoda akceptuje typ wyliczenia, które są analizy, można przeanalizować ciągu i opcjonalna Flaga wartości logicznej wskazująca, czy analizy jest rozróżniana wielkość liter. Ciąg, do którego są analizy może zawierać kilka wartości rozdzielonych przecinkami, które mogą być przed lub po co najmniej jedną spację pusty (nazywanych również zawierać białych znaków). Jeśli ciąg zawiera wiele wartości, wartość zwrócony obiekt jest wartość wszystkie określone wartości połączone z bitowego operacji lub.  
  
 W poniższym przykładzie użyto **przeanalizować** metody, aby przekonwertować reprezentacja ciągu wartości wyliczenia. <xref:System.DayOfWeek> Wyliczenie jest ustawiana na **czwartek** z ciągu.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 [Konwersja typów w ramach platformy .NET](../../../docs/standard/base-types/type-conversion.md)
