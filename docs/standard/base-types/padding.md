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
# <a name="padding-strings-in-net"></a><span data-ttu-id="8381a-102">Uzupełnianie ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="8381a-102">Padding Strings in .NET</span></span>

<span data-ttu-id="8381a-103">Użyj jednej z następujących metod <xref:System.String>, aby utworzyć nowy ciąg, który składa się z oryginalnego ciągu, który jest uzupełniony znakami początkowymi lub końcowymi, do określonej całkowitej długości.</span><span class="sxs-lookup"><span data-stu-id="8381a-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="8381a-104">Znak uzupełniania może być spacją lub określonym znakiem.</span><span class="sxs-lookup"><span data-stu-id="8381a-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="8381a-105">Ciąg wyników wydaje się być wyrównany do prawej lub wyrównany do lewej.</span><span class="sxs-lookup"><span data-stu-id="8381a-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="8381a-106">Jeśli pierwotna długość ciągu jest już równa lub większa od żądanej całkowitej długości, metody uzupełniania zwracają oryginalny ciąg niezmieniony; Aby uzyskać więcej informacji, zobacz sekcje **zwracające** dwa przeciążenia metod <xref:System.String.PadLeft%2A?displayProperty=nameWithType> i <xref:System.String.PadRight%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8381a-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="8381a-107">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="8381a-107">Method name</span></span>|<span data-ttu-id="8381a-108">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="8381a-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="8381a-109">Tworzy w postaci ciągu znaki wiodące z określoną łączną długością.</span><span class="sxs-lookup"><span data-stu-id="8381a-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="8381a-110">Tworzy w postaci ciągu znaki końcowe z określoną całkowitą długością.</span><span class="sxs-lookup"><span data-stu-id="8381a-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="8381a-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="8381a-111">PadLeft</span></span>  
 <span data-ttu-id="8381a-112">Metoda <xref:System.String.PadLeft%2A?displayProperty=nameWithType> tworzy nowy ciąg przez złączenie wystarczającej liczby wiodących znaków pad do oryginalnego ciągu, aby osiągnąć określoną całkowitą długość.</span><span class="sxs-lookup"><span data-stu-id="8381a-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="8381a-113">Metoda <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> używa odstępu jako znaku uzupełniania, a metoda <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> umożliwia określenie własnego znaku uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="8381a-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="8381a-114">Poniższy przykład kodu używa metody <xref:System.String.PadLeft%2A>, aby utworzyć nowy ciąg o długości dwudziestu znaków.</span><span class="sxs-lookup"><span data-stu-id="8381a-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="8381a-115">W przykładzie zostanie wyświetlony komunikat "`--------Hello World!`" w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="8381a-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="8381a-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="8381a-116">PadRight</span></span>  
 <span data-ttu-id="8381a-117">Metoda <xref:System.String.PadRight%2A?displayProperty=nameWithType> tworzy nowy ciąg, łącząc wystarczającą liczbę końcową znaków uzupełniających do oryginalnego ciągu, aby osiągnąć określoną łączną długość.</span><span class="sxs-lookup"><span data-stu-id="8381a-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="8381a-118">Metoda <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> używa odstępu jako znaku uzupełniania, a metoda <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> umożliwia określenie własnego znaku uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="8381a-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="8381a-119">Poniższy przykład kodu używa metody <xref:System.String.PadRight%2A>, aby utworzyć nowy ciąg o długości dwudziestu znaków.</span><span class="sxs-lookup"><span data-stu-id="8381a-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="8381a-120">W przykładzie zostanie wyświetlony komunikat "`Hello World!--------`" w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="8381a-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8381a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8381a-121">See also</span></span>

- [<span data-ttu-id="8381a-122">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="8381a-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
