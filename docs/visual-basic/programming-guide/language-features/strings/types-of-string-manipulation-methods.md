---
title: Typy metod manipulowania ciągami
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: aba9af9c699cf8d07862c5d2967902bec1623500
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363762"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="0c5e2-102">Typy metod manipulowania ciągami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c5e2-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="0c5e2-103">Istnieje kilka różnych sposobów analizowania ciągów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="0c5e2-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="0c5e2-104">Niektóre metody są częścią języka Visual Basic, a inne są związane z `String` klasą.</span><span class="sxs-lookup"><span data-stu-id="0c5e2-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="0c5e2-105">Visual Basic język i .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0c5e2-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="0c5e2-106">Metody Visual Basic są używane jako funkcje związane z językiem.</span><span class="sxs-lookup"><span data-stu-id="0c5e2-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="0c5e2-107">Mogą być używane bez kwalifikacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0c5e2-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="0c5e2-108">W poniższym przykładzie przedstawiono typowe użycie Visual Basic polecenie manipulowania ciągiem:</span><span class="sxs-lookup"><span data-stu-id="0c5e2-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="0c5e2-109">W tym przykładzie `Mid` Funkcja wykonuje operację bezpośrednią na `aString` i przypisuje wartość do `bString` .</span><span class="sxs-lookup"><span data-stu-id="0c5e2-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="0c5e2-110">Aby zapoznać się z listą metod manipulowania ciągami Visual Basic, zobacz [Podsumowanie manipulowania ciągami](../../../language-reference/keywords/string-manipulation-summary.md).</span><span class="sxs-lookup"><span data-stu-id="0c5e2-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="0c5e2-111">Metody udostępnione i metody wystąpień</span><span class="sxs-lookup"><span data-stu-id="0c5e2-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="0c5e2-112">Można również manipulować ciągami przy użyciu metod `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="0c5e2-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="0c5e2-113">Istnieją dwa typy metod w `String` : metody *Shared* i metody *wystąpień* .</span><span class="sxs-lookup"><span data-stu-id="0c5e2-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="0c5e2-114">Metody udostępnione</span><span class="sxs-lookup"><span data-stu-id="0c5e2-114">Shared Methods</span></span>  
 <span data-ttu-id="0c5e2-115">Metoda wspólna to metoda, która jest uruchamiana z `String` samej klasy i nie wymaga wystąpienia tej klasy do działania.</span><span class="sxs-lookup"><span data-stu-id="0c5e2-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="0c5e2-116">Metody te mogą być kwalifikowana nazwą klasy ( `String` ), a nie z wystąpieniem `String` klasy.</span><span class="sxs-lookup"><span data-stu-id="0c5e2-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="0c5e2-117">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0c5e2-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="0c5e2-118">W poprzednim przykładzie <xref:System.String.Copy%2A?displayProperty=nameWithType> Metoda jest metodą statyczną, która operuje na wyrażeniu, które jest określone, i przypisuje wartość wyniki do `bString` .</span><span class="sxs-lookup"><span data-stu-id="0c5e2-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="0c5e2-119">Metody wystąpień</span><span class="sxs-lookup"><span data-stu-id="0c5e2-119">Instance Methods</span></span>  
 <span data-ttu-id="0c5e2-120">Metody wystąpień, które różnią się od określonego wystąpienia `String` i muszą być kwalifikowane przy użyciu nazwy wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0c5e2-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="0c5e2-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0c5e2-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="0c5e2-122">W tym przykładzie <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda jest metodą wystąpienia `String` (to jest, `aString` ).</span><span class="sxs-lookup"><span data-stu-id="0c5e2-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="0c5e2-123">Wykonuje operację na `aString` i przypisuje tę wartość do `bString` .</span><span class="sxs-lookup"><span data-stu-id="0c5e2-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="0c5e2-124">Aby uzyskać więcej informacji, zobacz dokumentację <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="0c5e2-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c5e2-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c5e2-125">See also</span></span>

- [<span data-ttu-id="0c5e2-126">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c5e2-126">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
