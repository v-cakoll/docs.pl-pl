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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea903c1f950e7c226e043c1fa7276a66126b2512
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="01d7d-102">Uzupełnianie ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="01d7d-102">Padding Strings in .NET</span></span>
<span data-ttu-id="01d7d-103">Użyj jednej z następujących <xref:System.String> metody tworzenia nowego składający się z oryginalnego ciąg, który jest wypełniane początkowe lub końcowe znaki do określonego całkowita długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="01d7d-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="01d7d-104">Znak dopełnienia może być spacji lub określony znak, a w związku z tym wydaje się być wyrównany do prawej albo wyrównane do lewej.</span><span class="sxs-lookup"><span data-stu-id="01d7d-104">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>  
  
|<span data-ttu-id="01d7d-105">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="01d7d-105">Method name</span></span>|<span data-ttu-id="01d7d-106">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="01d7d-106">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="01d7d-107">Dopełnia ciąg zawierający znaki wiodące do określonej długości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="01d7d-107">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="01d7d-108">Dopełnia ciągu z końcowych znaków do określonej długości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="01d7d-108">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="01d7d-109">PadLeft</span><span class="sxs-lookup"><span data-stu-id="01d7d-109">PadLeft</span></span>  
 <span data-ttu-id="01d7d-110"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> Metoda tworzy nowy ciąg łącząc wystarczającej liczby wiodących znaków konsoli do oryginalnego ciągu dla osiągnięcia określonej całkowita długość.</span><span class="sxs-lookup"><span data-stu-id="01d7d-110">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="01d7d-111"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Metoda używa biały znak jako znak dopełnienia i <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metody umożliwia określenie własnych znak dopełnienia.</span><span class="sxs-lookup"><span data-stu-id="01d7d-111">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="01d7d-112">Poniższy przykład kodu wykorzystuje <xref:System.String.PadLeft%2A> metodę w celu utworzenia nowego ciąg, który jest 20 znaków.</span><span class="sxs-lookup"><span data-stu-id="01d7d-112">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="01d7d-113">W przykładzie przedstawiono "`--------Hello World!`" do konsoli.</span><span class="sxs-lookup"><span data-stu-id="01d7d-113">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="01d7d-114">PadRight</span><span class="sxs-lookup"><span data-stu-id="01d7d-114">PadRight</span></span>  
 <span data-ttu-id="01d7d-115"><xref:System.String.PadRight%2A?displayProperty=nameWithType> Metoda tworzy nowy ciąg łącząc za mało znakami konsoli do oryginalnego ciągu dla osiągnięcia określonej całkowita długość.</span><span class="sxs-lookup"><span data-stu-id="01d7d-115">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="01d7d-116"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Metoda używa biały znak jako znak dopełnienia i <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metody umożliwia określenie własnych znak dopełnienia.</span><span class="sxs-lookup"><span data-stu-id="01d7d-116">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="01d7d-117">Poniższy przykład kodu wykorzystuje <xref:System.String.PadRight%2A> metodę w celu utworzenia nowego ciąg, który jest 20 znaków.</span><span class="sxs-lookup"><span data-stu-id="01d7d-117">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="01d7d-118">W przykładzie przedstawiono "`Hello World!--------`" do konsoli.</span><span class="sxs-lookup"><span data-stu-id="01d7d-118">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="01d7d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01d7d-119">See Also</span></span>  
 [<span data-ttu-id="01d7d-120">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="01d7d-120">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
