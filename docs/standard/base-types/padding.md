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
ms.openlocfilehash: 83d4b348c4de537d9a71363d34898a50a6a74cb3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290399"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="f77f0-102">Uzupełnianie ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="f77f0-102">Padding Strings in .NET</span></span>

<span data-ttu-id="f77f0-103">Użyj jednej z następujących <xref:System.String> metod, aby utworzyć nowy ciąg, który składa się z oryginalnego ciągu, który jest uzupełniony znakami początkowymi lub końcowymi do określonej całkowitej długości.</span><span class="sxs-lookup"><span data-stu-id="f77f0-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="f77f0-104">Znak uzupełniania może być spacją lub określonym znakiem.</span><span class="sxs-lookup"><span data-stu-id="f77f0-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="f77f0-105">Ciąg wyników wydaje się być wyrównany do prawej lub wyrównany do lewej.</span><span class="sxs-lookup"><span data-stu-id="f77f0-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="f77f0-106">Jeśli pierwotna długość ciągu jest już równa lub większa od żądanej całkowitej długości, metody uzupełniania zwracają oryginalny ciąg niezmieniony; Aby uzyskać więcej informacji, zobacz sekcje **zwraca** dwa przeciążenia <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> metod i.</span><span class="sxs-lookup"><span data-stu-id="f77f0-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="f77f0-107">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="f77f0-107">Method name</span></span>|<span data-ttu-id="f77f0-108">Użycie</span><span class="sxs-lookup"><span data-stu-id="f77f0-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="f77f0-109">Tworzy w postaci ciągu znaki wiodące z określoną łączną długością.</span><span class="sxs-lookup"><span data-stu-id="f77f0-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="f77f0-110">Tworzy w postaci ciągu znaki końcowe z określoną całkowitą długością.</span><span class="sxs-lookup"><span data-stu-id="f77f0-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="f77f0-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="f77f0-111">PadLeft</span></span>  
 <span data-ttu-id="f77f0-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType>Metoda tworzy nowy ciąg przez złączenie wystarczającej liczby wiodących znaków pad do oryginalnego ciągu, aby osiągnąć określoną łączną długość.</span><span class="sxs-lookup"><span data-stu-id="f77f0-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="f77f0-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>Metoda używa odstępu jako znaku uzupełniania, a <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> Metoda umożliwia określenie własnego znaku uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="f77f0-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="f77f0-114">Poniższy przykład kodu używa metody, <xref:System.String.PadLeft%2A> Aby utworzyć nowy ciąg o długości dwudziestu znaków.</span><span class="sxs-lookup"><span data-stu-id="f77f0-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="f77f0-115">W przykładzie zostanie wyświetlony komunikat " `--------Hello World!` " w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="f77f0-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="f77f0-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="f77f0-116">PadRight</span></span>  
 <span data-ttu-id="f77f0-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType>Metoda tworzy nowy ciąg, łącząc wystarczającą liczbę końcową znaków uzupełniających do oryginalnego ciągu, aby osiągnąć określoną łączną długość.</span><span class="sxs-lookup"><span data-stu-id="f77f0-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="f77f0-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>Metoda używa odstępu jako znaku uzupełniania, a <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> Metoda umożliwia określenie własnego znaku uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="f77f0-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="f77f0-119">Poniższy przykład kodu używa metody, <xref:System.String.PadRight%2A> Aby utworzyć nowy ciąg o długości dwudziestu znaków.</span><span class="sxs-lookup"><span data-stu-id="f77f0-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="f77f0-120">W przykładzie zostanie wyświetlony komunikat " `Hello World!--------` " w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="f77f0-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f77f0-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f77f0-121">See also</span></span>

- [<span data-ttu-id="f77f0-122">Podstawowe operacje na ciągach</span><span class="sxs-lookup"><span data-stu-id="f77f0-122">Basic String Operations</span></span>](basic-string-operations.md)
