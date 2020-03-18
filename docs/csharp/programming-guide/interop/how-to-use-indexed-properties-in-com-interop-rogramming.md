---
title: Jak używać właściwości indeksowanych w programowaniu współdziałania COM — Przewodnik po programowaniu języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 864e2274f0e0e79b4843e0bb67b5c4384eac8588
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712068"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="e4fee-102">Jak używać właściwości indeksowanych w programowaniu współdziałania COM (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="e4fee-102">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="e4fee-103">*Właściwości indeksowane* poprawić sposób, w którym właściwości COM, które mają parametry są używane w programowaniu Języka C#.</span><span class="sxs-lookup"><span data-stu-id="e4fee-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="e4fee-104">Właściwości indeksowane współpracują z innymi funkcjami w programie Visual C#, takimi jak [argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md), nowy typ[(dynamiczny)](../../language-reference/builtin-types/reference-types.md)i [osadzone informacje o typie](../../../standard/assembly/embed-types-visual-studio.md), aby ulepszyć programowanie pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="e4fee-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="e4fee-105">We wcześniejszych wersjach języka C#, metody są `get` dostępne jako właściwości tylko `set` wtedy, gdy metoda nie ma parametrów i metoda ma jeden i tylko jeden parametr wartości.</span><span class="sxs-lookup"><span data-stu-id="e4fee-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="e4fee-106">Jednak nie wszystkie właściwości COM spełniają te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="e4fee-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="e4fee-107">Na przykład Właściwość <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> Excel `get` ma akcesor, który wymaga parametru dla nazwy zakresu.</span><span class="sxs-lookup"><span data-stu-id="e4fee-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="e4fee-108">W przeszłości, ponieważ nie można `Range` uzyskać dostępu do właściwości `get_Range` bezpośrednio, trzeba było użyć metody zamiast, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e4fee-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="e4fee-109">Właściwości indeksowane umożliwiają zapisanie następujących metod:</span><span class="sxs-lookup"><span data-stu-id="e4fee-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="e4fee-110">W poprzednim przykładzie użyto również opcjonalnej funkcji `Type.Missing` [argumentów,](../classes-and-structs/named-and-optional-arguments.md) która umożliwia pominięcie .</span><span class="sxs-lookup"><span data-stu-id="e4fee-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="e4fee-111">Podobnie ustawić wartość `Value` właściwości obiektu w <xref:Microsoft.Office.Interop.Excel.Range> języku C# 3.0 i wcześniejszych, wymagane są dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="e4fee-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="e4fee-112">Jeden dostarcza argument dla opcjonalnego parametru, który określa typ wartości zakresu.</span><span class="sxs-lookup"><span data-stu-id="e4fee-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="e4fee-113">Drugi dostarcza wartość `Value` dla nieruchomości.</span><span class="sxs-lookup"><span data-stu-id="e4fee-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="e4fee-114">Poniższe przykłady ilustrują te techniki.</span><span class="sxs-lookup"><span data-stu-id="e4fee-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="e4fee-115">Oba ustawiają wartość komórki `Name`A1 na .</span><span class="sxs-lookup"><span data-stu-id="e4fee-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="e4fee-116">Właściwości indeksowane umożliwiają napisanie następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="e4fee-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="e4fee-117">Nie można tworzyć właściwości indeksowanych własnych.</span><span class="sxs-lookup"><span data-stu-id="e4fee-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="e4fee-118">Funkcja obsługuje tylko zużycie istniejących właściwości indeksowanych.</span><span class="sxs-lookup"><span data-stu-id="e4fee-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4fee-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4fee-119">Example</span></span>  
 <span data-ttu-id="e4fee-120">Poniższy kod przedstawia pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="e4fee-120">The following code shows a complete example.</span></span> <span data-ttu-id="e4fee-121">Aby uzyskać więcej informacji na temat konfigurowania projektu, który uzyskuje dostęp do interfejsu API pakietu Office, zobacz [Jak uzyskać dostęp do obiektów pakietu Office interop przy użyciu funkcji języka C#.](./how-to-access-office-onterop-objects.md)</span><span class="sxs-lookup"><span data-stu-id="e4fee-121">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e4fee-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4fee-122">See also</span></span>

- [<span data-ttu-id="e4fee-123">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="e4fee-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="e4fee-124">Dynamiczne</span><span class="sxs-lookup"><span data-stu-id="e4fee-124">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="e4fee-125">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="e4fee-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="e4fee-126">Porada: użycie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office</span><span class="sxs-lookup"><span data-stu-id="e4fee-126">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="e4fee-127">Uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji języka C#</span><span class="sxs-lookup"><span data-stu-id="e4fee-127">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="e4fee-128">Instruktaż: Programowanie pakietu Office</span><span class="sxs-lookup"><span data-stu-id="e4fee-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
