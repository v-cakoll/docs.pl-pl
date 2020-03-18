---
title: Dopełnianie ciągów w .NET
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
ms.openlocfilehash: 2cf114296005456f354d286aa2804fa8a95160dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127625"
---
# <a name="padding-strings-in-net"></a>Dopełnianie ciągów w .NET

Użyj jednej z <xref:System.String> następujących metod, aby utworzyć nowy ciąg, który składa się z oryginalnego ciągu, który jest wyściełane znakami wiodącymi lub końcowymi do określonej długości całkowitej. Znak dopełnienia może być spacji lub określonego znaku. Wynikowy ciąg wydaje się być wyrównany do prawej lub wyrównany do lewej. Jeśli długość oryginalnego ciągu jest już równa lub większa niż żądana całkowita długość, metody dopełnienia zwracają oryginalny ciąg bez zmian; Aby uzyskać więcej informacji, zobacz **Zwraca** sekcje <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> dwóch przeciążeń i metod.
  
|Nazwa metody|Użycie|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Klocki ciąg z wiodącymi znakami o określonej długości całkowitej.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Klocki ciąg znaków końcowych do określonej długości całkowitej.|  
  
## <a name="padleft"></a>Padleft  
 Metoda <xref:System.String.PadLeft%2A?displayProperty=nameWithType> tworzy nowy ciąg, konkwentując wystarczającą liczbę wiodących znaków pad do oryginalnego ciągu, aby osiągnąć określoną całkowitą długość. Metoda <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> używa biały znak jako znak <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> dopełnienia i metoda umożliwia określenie własnego znaku dopełnienia.  
  
 Poniższy przykład kodu <xref:System.String.PadLeft%2A> używa metody do tworzenia nowego ciągu, który jest dwadzieścia znaków długości. Przykład wyświetla "`--------Hello World!`" na konsoli.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>Padright  
 Metoda <xref:System.String.PadRight%2A?displayProperty=nameWithType> tworzy nowy ciąg, konkwentując wystarczającą liczbę znaków końcowej konsoli do oryginalnego ciągu, aby osiągnąć określoną całkowitą długość. Metoda <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> używa biały znak jako znak <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> dopełnienia i metoda umożliwia określenie własnego znaku dopełnienia.  
  
 Poniższy przykład kodu <xref:System.String.PadRight%2A> używa metody do tworzenia nowego ciągu, który jest dwadzieścia znaków długości. Przykład wyświetla "`Hello World!--------`" na konsoli.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
