---
title: "Porady: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2538dae8f02b17a77cc1eb2798b8b38a7f1d7db2
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="6d8b5-102">Porady: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6d8b5-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="6d8b5-103">*Właściwości indeksowanych* ulepszyć sposób, w których COM właściwości, które mają parametry są używane w programowaniu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="6d8b5-104">Indeksowane właściwości pracy wraz z innymi funkcjami języka Visual C#, takich jak [argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), nowy typ ([dynamiczne](../../../csharp/language-reference/keywords/dynamic.md)), i [osadzonych informacji o typie](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), do ulepszanie programowania w języku Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="6d8b5-105">We wcześniejszych wersjach języka C#, są dostępne jako właściwości tylko wtedy, gdy metody `get` — metoda nie ma parametrów i `set` metoda ma jeden i tylko jeden parametr wartości.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="6d8b5-106">Jednak nie wszystkie właściwości modelu COM spełnia te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="6d8b5-107">Na przykład programu Excel [zakres](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) ma właściwość `get` dostępu, który wymaga parametru nazwy zakresu.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-107">For example, the Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="6d8b5-108">W przeszłości ponieważ nie można uzyskać dostępu `Range` właściwości bezpośrednio, można było użyć `get_Range` metody zamiast tego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 <span data-ttu-id="6d8b5-109">Właściwości indeksowane umożliwiają zapisu zamiast poniżej:</span><span class="sxs-lookup"><span data-stu-id="6d8b5-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="6d8b5-110">W poprzednim przykładzie również użyto [Argumenty opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) funkcji, dzięki czemu można pominąć `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-110">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="6d8b5-111">Podobnie jak wartość `Value` właściwość [zakres](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) obiektów w programie Visual C# 2008 i starszych wersji, wymagane są dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-111">Similarly to set the value of the `Value` property of a [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="6d8b5-112">Udostępnia jeden argument opcjonalny parametr określający typ wartości zakresu.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="6d8b5-113">Druga dostarcza wartość `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="6d8b5-114">Poniższe przykłady przedstawiają metody te.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="6d8b5-115">Obie wartości komórki A1 `Name`.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 <span data-ttu-id="6d8b5-116">Właściwości indeksowane pozwalają na zapis zamiast niej następujący kod.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 <span data-ttu-id="6d8b5-117">Nie można utworzyć właściwości indeksowanych własny.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="6d8b5-118">Gdy funkcja obsługuje tylko zużycie istniejącej właściwości indeksowane.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d8b5-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d8b5-119">Example</span></span>  
 <span data-ttu-id="6d8b5-120">Poniższy kod przedstawia pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-120">The following code shows a complete example.</span></span> <span data-ttu-id="6d8b5-121">Aby uzyskać więcej informacji na temat sposobu konfigurowania projektu, który uzyskuje dostęp do interfejsu API usługi Office, zobacz [porady: dostępu do obiektów międzyoperacyjności pakietu Office za pomocą Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="6d8b5-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6d8b5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d8b5-122">See Also</span></span>  
 [<span data-ttu-id="6d8b5-123">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="6d8b5-123">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [<span data-ttu-id="6d8b5-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="6d8b5-124">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="6d8b5-125">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="6d8b5-125">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="6d8b5-126">Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu Office</span><span class="sxs-lookup"><span data-stu-id="6d8b5-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [<span data-ttu-id="6d8b5-127">Instrukcje: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C#</span><span class="sxs-lookup"><span data-stu-id="6d8b5-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 [<span data-ttu-id="6d8b5-128">Wskazówki: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="6d8b5-128">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
