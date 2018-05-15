---
title: Uzupełnianie ciągów w .NET
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
ms.openlocfilehash: f8b71908d817625ca38f3b53a10fc20e9103ee15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="27127-102">Uzupełnianie ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="27127-102">Padding Strings in .NET</span></span>

<span data-ttu-id="27127-103">Użyj jednej z następujących <xref:System.String> metody tworzenia nowego składający się z oryginalnego ciąg, który jest wypełniane początkowe lub końcowe znaki do określonego całkowita długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="27127-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="27127-104">Znak dopełnienia może być spacji ani znaków określony.</span><span class="sxs-lookup"><span data-stu-id="27127-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="27127-105">Wynikowy ciąg wydaje się być wyrównany do prawej lub lewej.</span><span class="sxs-lookup"><span data-stu-id="27127-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="27127-106">Jeśli długość ciągu oryginalnego jest już równa lub większa niż całkowita długość żądanej, metody dopełnienie zwracają oryginalnego ciągu bez zmian; Aby uzyskać więcej informacji, zobacz **zwraca** sekcje dwóch przeciążeń <xref:System.String.PadLeft%2A?displayProperty=nameWithType> i <xref:System.String.PadRight%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="27127-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="27127-107">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="27127-107">Method name</span></span>|<span data-ttu-id="27127-108">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="27127-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="27127-109">Dopełnia ciąg zawierający znaki wiodące do określonej długości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="27127-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="27127-110">Dopełnia ciągu z końcowych znaków do określonej długości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="27127-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="27127-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="27127-111">PadLeft</span></span>  
 <span data-ttu-id="27127-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> Metoda tworzy nowy ciąg łącząc wystarczającej liczby wiodących znaków konsoli do oryginalnego ciągu dla osiągnięcia określonej całkowita długość.</span><span class="sxs-lookup"><span data-stu-id="27127-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="27127-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Metoda używa biały znak jako znak dopełnienia i <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metody umożliwia określenie własnych znak dopełnienia.</span><span class="sxs-lookup"><span data-stu-id="27127-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="27127-114">Poniższy przykład kodu wykorzystuje <xref:System.String.PadLeft%2A> metodę w celu utworzenia nowego ciąg, który jest 20 znaków.</span><span class="sxs-lookup"><span data-stu-id="27127-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="27127-115">W przykładzie przedstawiono "`--------Hello World!`" do konsoli.</span><span class="sxs-lookup"><span data-stu-id="27127-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="27127-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="27127-116">PadRight</span></span>  
 <span data-ttu-id="27127-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType> Metoda tworzy nowy ciąg łącząc za mało znakami konsoli do oryginalnego ciągu dla osiągnięcia określonej całkowita długość.</span><span class="sxs-lookup"><span data-stu-id="27127-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="27127-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Metoda używa biały znak jako znak dopełnienia i <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metody umożliwia określenie własnych znak dopełnienia.</span><span class="sxs-lookup"><span data-stu-id="27127-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="27127-119">Poniższy przykład kodu wykorzystuje <xref:System.String.PadRight%2A> metodę w celu utworzenia nowego ciąg, który jest 20 znaków.</span><span class="sxs-lookup"><span data-stu-id="27127-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="27127-120">W przykładzie przedstawiono "`Hello World!--------`" do konsoli.</span><span class="sxs-lookup"><span data-stu-id="27127-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="27127-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27127-121">See Also</span></span>  
 [<span data-ttu-id="27127-122">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="27127-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
