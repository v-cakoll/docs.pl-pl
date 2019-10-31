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
ms.openlocfilehash: 2cf114296005456f354d286aa2804fa8a95160dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127625"
---
# <a name="padding-strings-in-net"></a>Uzupełnianie ciągów w programie .NET

Użyj jednej z następujących metod <xref:System.String>, aby utworzyć nowy ciąg, który składa się z oryginalnego ciągu, który jest uzupełniony znakami początkowymi lub końcowymi, do określonej całkowitej długości. Znak uzupełniania może być spacją lub określonym znakiem. Ciąg wyników wydaje się być wyrównany do prawej lub wyrównany do lewej. Jeśli pierwotna długość ciągu jest już równa lub większa od żądanej całkowitej długości, metody uzupełniania zwracają oryginalny ciąg niezmieniony; Aby uzyskać więcej informacji, zobacz sekcje **zwracające** dwa przeciążenia metod <xref:System.String.PadLeft%2A?displayProperty=nameWithType> i <xref:System.String.PadRight%2A?displayProperty=nameWithType>.
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Tworzy w postaci ciągu znaki wiodące z określoną łączną długością.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Tworzy w postaci ciągu znaki końcowe z określoną całkowitą długością.|  
  
## <a name="padleft"></a>PadLeft  
 Metoda <xref:System.String.PadLeft%2A?displayProperty=nameWithType> tworzy nowy ciąg przez złączenie wystarczającej liczby wiodących znaków pad do oryginalnego ciągu, aby osiągnąć określoną całkowitą długość. Metoda <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> używa odstępu jako znaku uzupełniania, a metoda <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> umożliwia określenie własnego znaku uzupełniania.  
  
 Poniższy przykład kodu używa metody <xref:System.String.PadLeft%2A>, aby utworzyć nowy ciąg o długości dwudziestu znaków. W przykładzie zostanie wyświetlony komunikat "`--------Hello World!`" w konsoli programu.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 Metoda <xref:System.String.PadRight%2A?displayProperty=nameWithType> tworzy nowy ciąg, łącząc wystarczającą liczbę końcową znaków uzupełniających do oryginalnego ciągu, aby osiągnąć określoną łączną długość. Metoda <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> używa odstępu jako znaku uzupełniania, a metoda <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> umożliwia określenie własnego znaku uzupełniania.  
  
 Poniższy przykład kodu używa metody <xref:System.String.PadRight%2A>, aby utworzyć nowy ciąg o długości dwudziestu znaków. W przykładzie zostanie wyświetlony komunikat "`Hello World!--------`" w konsoli programu.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
