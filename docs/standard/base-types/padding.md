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
# <a name="padding-strings-in-net"></a><span data-ttu-id="783b4-102">Dopełnianie ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="783b4-102">Padding Strings in .NET</span></span>

<span data-ttu-id="783b4-103">Użyj jednej z <xref:System.String> następujących metod, aby utworzyć nowy ciąg, który składa się z oryginalnego ciągu, który jest wyściełane znakami wiodącymi lub końcowymi do określonej długości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="783b4-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="783b4-104">Znak dopełnienia może być spacji lub określonego znaku.</span><span class="sxs-lookup"><span data-stu-id="783b4-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="783b4-105">Wynikowy ciąg wydaje się być wyrównany do prawej lub wyrównany do lewej.</span><span class="sxs-lookup"><span data-stu-id="783b4-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="783b4-106">Jeśli długość oryginalnego ciągu jest już równa lub większa niż żądana całkowita długość, metody dopełnienia zwracają oryginalny ciąg bez zmian; Aby uzyskać więcej informacji, zobacz **Zwraca** sekcje <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> dwóch przeciążeń i metod.</span><span class="sxs-lookup"><span data-stu-id="783b4-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="783b4-107">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="783b4-107">Method name</span></span>|<span data-ttu-id="783b4-108">Użycie</span><span class="sxs-lookup"><span data-stu-id="783b4-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="783b4-109">Klocki ciąg z wiodącymi znakami o określonej długości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="783b4-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="783b4-110">Klocki ciąg znaków końcowych do określonej długości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="783b4-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="783b4-111">Padleft</span><span class="sxs-lookup"><span data-stu-id="783b4-111">PadLeft</span></span>  
 <span data-ttu-id="783b4-112">Metoda <xref:System.String.PadLeft%2A?displayProperty=nameWithType> tworzy nowy ciąg, konkwentując wystarczającą liczbę wiodących znaków pad do oryginalnego ciągu, aby osiągnąć określoną całkowitą długość.</span><span class="sxs-lookup"><span data-stu-id="783b4-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="783b4-113">Metoda <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> używa biały znak jako znak <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> dopełnienia i metoda umożliwia określenie własnego znaku dopełnienia.</span><span class="sxs-lookup"><span data-stu-id="783b4-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="783b4-114">Poniższy przykład kodu <xref:System.String.PadLeft%2A> używa metody do tworzenia nowego ciągu, który jest dwadzieścia znaków długości.</span><span class="sxs-lookup"><span data-stu-id="783b4-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="783b4-115">Przykład wyświetla "`--------Hello World!`" na konsoli.</span><span class="sxs-lookup"><span data-stu-id="783b4-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="783b4-116">Padright</span><span class="sxs-lookup"><span data-stu-id="783b4-116">PadRight</span></span>  
 <span data-ttu-id="783b4-117">Metoda <xref:System.String.PadRight%2A?displayProperty=nameWithType> tworzy nowy ciąg, konkwentując wystarczającą liczbę znaków końcowej konsoli do oryginalnego ciągu, aby osiągnąć określoną całkowitą długość.</span><span class="sxs-lookup"><span data-stu-id="783b4-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="783b4-118">Metoda <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> używa biały znak jako znak <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> dopełnienia i metoda umożliwia określenie własnego znaku dopełnienia.</span><span class="sxs-lookup"><span data-stu-id="783b4-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="783b4-119">Poniższy przykład kodu <xref:System.String.PadRight%2A> używa metody do tworzenia nowego ciągu, który jest dwadzieścia znaków długości.</span><span class="sxs-lookup"><span data-stu-id="783b4-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="783b4-120">Przykład wyświetla "`Hello World!--------`" na konsoli.</span><span class="sxs-lookup"><span data-stu-id="783b4-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="783b4-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="783b4-121">See also</span></span>

- [<span data-ttu-id="783b4-122">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="783b4-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
