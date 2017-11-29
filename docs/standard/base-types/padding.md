---
title: "Uzupełnianie ciągów w .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a>Uzupełnianie ciągów w .NET
Użyj jednej z następujących <xref:System.String> metody tworzenia nowego składający się z oryginalnego ciąg, który jest wypełniane początkowe lub końcowe znaki do określonego całkowita długość ciągu. Znak dopełnienia może być spacji lub określony znak, a w związku z tym wydaje się być wyrównany do prawej albo wyrównane do lewej.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Dopełnia ciąg zawierający znaki wiodące do określonej długości całkowitej.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Dopełnia ciągu z końcowych znaków do określonej długości całkowitej.|  
  
## <a name="padleft"></a>PadLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> Metoda tworzy nowy ciąg łącząc wystarczającej liczby wiodących znaków konsoli do oryginalnego ciągu dla osiągnięcia określonej całkowita długość. <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Metoda używa biały znak jako znak dopełnienia i <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metody umożliwia określenie własnych znak dopełnienia.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.String.PadLeft%2A> metodę w celu utworzenia nowego ciąg, który jest 20 znaków. W przykładzie przedstawiono "`--------Hello World!`" do konsoli.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType> Metoda tworzy nowy ciąg łącząc za mało znakami konsoli do oryginalnego ciągu dla osiągnięcia określonej całkowita długość. <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Metoda używa biały znak jako znak dopełnienia i <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metody umożliwia określenie własnych znak dopełnienia.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.String.PadRight%2A> metodę w celu utworzenia nowego ciąg, który jest 20 znaków. W przykładzie przedstawiono "`Hello World!--------`" do konsoli.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
