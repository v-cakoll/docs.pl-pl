---
title: 'Instrukcje: Użycie właściwości indeksowanych w programowaniu usługi Międzyoperacyjnej modelu COM - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 4b064f7042e5e5f0f6d5545c59de2f37897927b4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978036"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="b10a2-102">Instrukcje: Użycie właściwości indeksowanych w programowaniu usługi Międzyoperacyjnej modelu COM (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b10a2-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="b10a2-103">*Właściwości indeksowanych* poprawić sposób, w których COM właściwości, które mają parametry są używane w programowaniu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="b10a2-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="b10a2-104">Indeksowane właściwości pracy w połączeniu z innymi funkcjami w języku Visual C#, takich jak [argumentów nazwanych i opcjonalnych](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), nowy typ ([dynamiczne](../../../csharp/language-reference/keywords/dynamic.md)), i [osadzonych informacji o typie](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), Zwiększ programowania Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="b10a2-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="b10a2-105">We wcześniejszych wersjach języka C#, są dostępne jako właściwości tylko wtedy, gdy metody `get` metoda nie ma parametrów i `set` metoda ma jeden i tylko jeden parametr wartości.</span><span class="sxs-lookup"><span data-stu-id="b10a2-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="b10a2-106">Jednak nie wszystkie właściwości modelu COM spełniać te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="b10a2-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="b10a2-107">Na przykład program Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> właściwość ma `get` metodę dostępu, która wymaga parametru Nazwa zakresu.</span><span class="sxs-lookup"><span data-stu-id="b10a2-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="b10a2-108">W przeszłości ponieważ nie można uzyskać dostępu `Range` właściwości bezpośrednio, trzeba było używać `get_Range` metody zamiast tego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b10a2-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="b10a2-109">Właściwości indeksowane umożliwiają zamiast niego zapisu do następujących:</span><span class="sxs-lookup"><span data-stu-id="b10a2-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
>  <span data-ttu-id="b10a2-110">W poprzednim przykładzie użyto również [opcjonalne argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) funkcji, która pozwala na pominięcie `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="b10a2-110">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="b10a2-111">Podobnie jak wartość `Value` właściwość <xref:Microsoft.Office.Interop.Excel.Range> obiektu w programie Visual C# 2008 i starszych, wymagane są dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="b10a2-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="b10a2-112">Dostarcza jeden argument opcjonalny parametr określający typ wartości zakresu.</span><span class="sxs-lookup"><span data-stu-id="b10a2-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="b10a2-113">Druga dostarcza wartość `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="b10a2-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="b10a2-114">Poniższe przykłady ilustrują tych metod.</span><span class="sxs-lookup"><span data-stu-id="b10a2-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="b10a2-115">Ustawiają wartość komórki A1 do `Name`.</span><span class="sxs-lookup"><span data-stu-id="b10a2-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="b10a2-116">Właściwości indeksowane umożliwiają zamiast tego Zapisz poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="b10a2-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="b10a2-117">Nie można utworzyć właściwości indeksowanych samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="b10a2-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="b10a2-118">Ta funkcja obsługuje tylko użycie istniejącej właściwości indeksowanych.</span><span class="sxs-lookup"><span data-stu-id="b10a2-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b10a2-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="b10a2-119">Example</span></span>  
 <span data-ttu-id="b10a2-120">Poniższy kod przedstawia kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="b10a2-120">The following code shows a complete example.</span></span> <span data-ttu-id="b10a2-121">Aby uzyskać więcej informacji o tym, jak skonfigurować projekt, który uzyskuje dostęp do interfejsu API pakietu Office, zobacz [jak: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b10a2-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b10a2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b10a2-122">See also</span></span>

- [<span data-ttu-id="b10a2-123">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="b10a2-123">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="b10a2-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="b10a2-124">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)
- [<span data-ttu-id="b10a2-125">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="b10a2-125">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="b10a2-126">Instrukcje: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office</span><span class="sxs-lookup"><span data-stu-id="b10a2-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="b10a2-127">Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji</span><span class="sxs-lookup"><span data-stu-id="b10a2-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="b10a2-128">Przewodnik: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="b10a2-128">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
