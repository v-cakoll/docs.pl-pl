---
title: 'Instrukcje: Korzystanie z właściwości indeksowanych w programowaniu międzyoperacyjnym modelu COM — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: f1be14ad7ddb6973cc89f10c1735ba2ebce13f97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971646"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="cc82e-102">Instrukcje: Korzystanie z właściwości indeksowanych w programowaniu międzyoperacyjnym modelu COM (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="cc82e-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="cc82e-103">*Właściwości indeksowane* ulepszają sposób, w jaki właściwości com, które mają parametry są C# używane w programowaniu.</span><span class="sxs-lookup"><span data-stu-id="cc82e-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="cc82e-104">Właściwości indeksowane współpracują z innymi funkcjami w C#wizualizacji, takimi jak [argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md), nowy typ ([dynamiczny](../../language-reference/keywords/dynamic.md)) i [Informacje o typie osadzonym](../../../standard/assembly/embed-types-visual-studio.md), aby usprawnić programowanie Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="cc82e-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/keywords/dynamic.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="cc82e-105">We wcześniejszych wersjach programu C#metody są dostępne jako właściwości tylko wtedy, gdy `get` Metoda nie ma parametrów, a `set` Metoda ma jeden i tylko jeden parametr value.</span><span class="sxs-lookup"><span data-stu-id="cc82e-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="cc82e-106">Jednak nie wszystkie właściwości COM spełniają te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="cc82e-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="cc82e-107">Na przykład właściwość programu Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> `get` ma metodę dostępu, która wymaga parametru dla nazwy zakresu.</span><span class="sxs-lookup"><span data-stu-id="cc82e-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="cc82e-108">W przeszłości, ponieważ nie można uzyskać dostępu `Range` do właściwości bezpośrednio, należy `get_Range` użyć metody zamiast tego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cc82e-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="cc82e-109">Właściwości indeksowane umożliwiają napisanie następujących danych:</span><span class="sxs-lookup"><span data-stu-id="cc82e-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="cc82e-110">W poprzednim przykładzie jest również stosowana funkcja [argumentów opcjonalnych](../classes-and-structs/named-and-optional-arguments.md) , która pozwala pominąć `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="cc82e-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="cc82e-111">Podobnie, aby ustawić wartość `Value` właściwości <xref:Microsoft.Office.Interop.Excel.Range> obiektu w C# 3,0 i wcześniejszych, wymagane są dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="cc82e-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="cc82e-112">Jeden dostarcza argument dla opcjonalnego parametru, który określa typ wartości zakresu.</span><span class="sxs-lookup"><span data-stu-id="cc82e-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="cc82e-113">Pozostałe dostarczają wartość `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="cc82e-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="cc82e-114">Poniższe przykłady ilustrują te techniki.</span><span class="sxs-lookup"><span data-stu-id="cc82e-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="cc82e-115">Obie wartości mają `Name`ustawioną wartość komórki a1.</span><span class="sxs-lookup"><span data-stu-id="cc82e-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="cc82e-116">Właściwości indeksowane umożliwiają zapisanie w zamian poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="cc82e-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="cc82e-117">Nie można tworzyć własnych właściwości indeksowanych.</span><span class="sxs-lookup"><span data-stu-id="cc82e-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="cc82e-118">Funkcja obsługuje tylko użycie istniejących właściwości indeksowanych.</span><span class="sxs-lookup"><span data-stu-id="cc82e-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc82e-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc82e-119">Example</span></span>  
 <span data-ttu-id="cc82e-120">Poniższy kod przedstawia kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="cc82e-120">The following code shows a complete example.</span></span> <span data-ttu-id="cc82e-121">Aby uzyskać więcej informacji o konfigurowaniu projektu, który uzyskuje dostęp do interfejsu API pakietu Office [, zobacz How to: Dostęp do obiektów międzyoperacyjności pakietu C# Office](./how-to-access-office-onterop-objects.md)za pomocą funkcji wizualnych.</span><span class="sxs-lookup"><span data-stu-id="cc82e-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](./how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="cc82e-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc82e-122">See also</span></span>

- [<span data-ttu-id="cc82e-123">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="cc82e-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="cc82e-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="cc82e-124">dynamic</span></span>](../../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="cc82e-125">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="cc82e-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="cc82e-126">Instrukcje: Używanie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office</span><span class="sxs-lookup"><span data-stu-id="cc82e-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="cc82e-127">Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu C# Office za pomocą funkcji wizualnych</span><span class="sxs-lookup"><span data-stu-id="cc82e-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="cc82e-128">Przewodnik: Programowanie Office</span><span class="sxs-lookup"><span data-stu-id="cc82e-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
