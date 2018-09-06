---
title: Uzupełnianie ciągów w programie .NET
ms.date: 03/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f58e1c3a9e42f48ecc219a2db1649051f9ca20b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890730"
---
# <a name="padding-strings-in-net"></a>Uzupełnianie ciągów w programie .NET

Użyj jednej z następujących <xref:System.String> metody, aby utworzyć nowy ciąg, który składa się z oryginalnego ciągu, który jest dopełniana wiodących albo końcowych znaków do określonej długości łączna liczba. Znak dopełnienia może być spacji ani znaków określony. Wynikowy ciąg wydaje się być wyrównany do prawej lub wyrównane do lewej. Jeśli oryginalny ciąg, długość jest już równa lub większa niż żądany całkowita długość, metod dopełnienie zwraca oryginalny ciąg bez zmian; Aby uzyskać więcej informacji, zobacz **zwraca** sekcje dwa przeciążenia metody <xref:System.String.PadLeft%2A?displayProperty=nameWithType> i <xref:System.String.PadRight%2A?displayProperty=nameWithType> metody.
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Dopełnia ciągu za pomocą prowadzące znaki do określonej długości całkowitej.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Dopełnia ciąg ze znakami do określonej długości całkowitej.|  
  
## <a name="padleft"></a>padLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> Metoda tworzy nowy ciąg przez złączenie wystarczająco dużo początkowe znaki konsolę na oryginalny ciąg do osiągnięcia określonej całkowita długość. <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Metoda używa biały znak dopełnienia i <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metody umożliwia określenie własnych znak dopełnienia.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.String.PadLeft%2A> metodę, aby utworzyć nowy ciąg, który składa się z 20 znaków. W przykładzie są wyświetlane "`--------Hello World!`" do konsoli.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>Padright —  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType> Metoda tworzy nowy ciąg przez złączenie wystarczająco dużo nieprawidłowymi znakami konsolę na oryginalny ciąg do osiągnięcia określonej całkowita długość. <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Metoda używa biały znak dopełnienia i <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metody umożliwia określenie własnych znak dopełnienia.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.String.PadRight%2A> metodę, aby utworzyć nowy ciąg, który składa się z 20 znaków. W przykładzie są wyświetlane "`Hello World!--------`" do konsoli.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
