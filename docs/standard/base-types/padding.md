---
title: "Uzupełnianie ciągów w .NET"
ms.custom: 
ms.date: 03/15/2018
ms.prod: .net
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
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bf90c841c8fff21dd423fcd19613b5eb46a2c80c
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="padding-strings-in-net"></a>Uzupełnianie ciągów w .NET

Użyj jednej z następujących <xref:System.String> metody tworzenia nowego składający się z oryginalnego ciąg, który jest wypełniane początkowe lub końcowe znaki do określonego całkowita długość ciągu. Znak dopełnienia może być spacji ani znaków określony. Wynikowy ciąg wydaje się być wyrównany do prawej lub lewej. Jeśli długość ciągu oryginalnego jest już równa lub większa niż całkowita długość żądanej, metody dopełnienie zwracają oryginalnego ciągu bez zmian; Aby uzyskać więcej informacji, zobacz **zwraca** sekcje dwóch przeciążeń <xref:System.String.PadLeft%2A?displayProperty=nameWithType> i <xref:System.String.PadRight%2A?displayProperty=nameWithType> metody.
  
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
