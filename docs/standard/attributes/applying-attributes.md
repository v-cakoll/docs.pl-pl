---
title: Stosowanie atrybutów
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a2e34d0544c8105b539d36a4231c6efb4df0ee5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337698"
---
# <a name="applying-attributes"></a><span data-ttu-id="b87ee-102">Stosowanie atrybutów</span><span class="sxs-lookup"><span data-stu-id="b87ee-102">Applying Attributes</span></span>
<span data-ttu-id="b87ee-103">W celu zastosowania atrybutu do elementu kodu należy wykonać procedurę opisaną poniżej.</span><span class="sxs-lookup"><span data-stu-id="b87ee-103">Use the following process to apply an attribute to an element of your code.</span></span>  
  
1. <span data-ttu-id="b87ee-104">Zdefiniuj nowy atrybut lub użyj istniejącego atrybutu, importując jego przestrzeń nazw ze środowiska .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b87ee-104">Define a new attribute or use an existing attribute by importing its namespace from the .NET Framework.</span></span>  
  
2. <span data-ttu-id="b87ee-105">Zastosuj atrybut do elementu kodu, umieszczając go bezpośrednio przed elementem.</span><span class="sxs-lookup"><span data-stu-id="b87ee-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>  
  
     <span data-ttu-id="b87ee-106">Każdy język ma własną składnię atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b87ee-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="b87ee-107">W językach C++ i C# atrybut jest ujęty w nawiasy kwadratowe i oddzielony od elementu znakiem odstępu, który może zawierać znak podziału wiersza.</span><span class="sxs-lookup"><span data-stu-id="b87ee-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="b87ee-108">W języku Visual Basic atrybut jest ujęty w nawiasy kątowe i musi się znajdować w tym samym wierszu logicznym. Jeśli trzeba użyć podziału wiersza, można wstawić znak kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="b87ee-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>
  
3. <span data-ttu-id="b87ee-109">Określ parametry pozycyjne i nazwane atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b87ee-109">Specify positional parameters and named parameters for the attribute.</span></span>  
  
     <span data-ttu-id="b87ee-110">Parametry pozycyjne są wymagane i muszą się znajdować przed parametrami nazwanymi. Odpowiadają parametrom jednego z konstruktorów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b87ee-110">Positional parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="b87ee-111">Parametry nazwane są opcjonalne i odnoszą się do właściwości odczytu/zapisu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b87ee-111">Named parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="b87ee-112">W języku C++ i C#, określ `name` = `value` dla każdego opcjonalnego parametru, gdzie `name` jest nazwą właściwości.</span><span class="sxs-lookup"><span data-stu-id="b87ee-112">In C++, and C#, specify `name`=`value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="b87ee-113">W języku Visual Basic należy określić przyporządkowanie `name`:=`value`.</span><span class="sxs-lookup"><span data-stu-id="b87ee-113">In Visual Basic, specify `name`:=`value`.</span></span>  
  
 <span data-ttu-id="b87ee-114">Atrybut jest emitowany do metadanych podczas kompilowania kodu. Jego udostępnianie środowisku uruchomieniowemu języka wspólnego i niestandardowym narzędziom lub aplikacjom odbywa się za pośrednictwem usług odbicia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b87ee-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>  
  
 <span data-ttu-id="b87ee-115">Zgodnie z konwencją wszystkie nazwy atrybutu kończą się ciągiem Attribute.</span><span class="sxs-lookup"><span data-stu-id="b87ee-115">By convention, all attribute names end with Attribute.</span></span> <span data-ttu-id="b87ee-116">Jednak niektóre języki przeznaczone dla tego środowiska uruchomieniowego, np. Visual Basic i C#, nie wymagają określania pełnej nazwy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b87ee-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="b87ee-117">Na przykład, jeśli chcesz zainicjować <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, należy odwołać się do niego jako **Obsolete**.</span><span class="sxs-lookup"><span data-stu-id="b87ee-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete**.</span></span>  
  
## <a name="applying-an-attribute-to-a-method"></a><span data-ttu-id="b87ee-118">Stosowanie atrybutu do metody</span><span class="sxs-lookup"><span data-stu-id="b87ee-118">Applying an Attribute to a Method</span></span>  
 <span data-ttu-id="b87ee-119">Poniższy przykład kodu pokazuje sposób deklarowania **System.ObsoleteAttribute**, który oznacza kod jako przestarzały.</span><span class="sxs-lookup"><span data-stu-id="b87ee-119">The following code example shows how to declare **System.ObsoleteAttribute**, which marks code as obsolete.</span></span> <span data-ttu-id="b87ee-120">Ciąg tekstowy `"Will be removed in next version"` jest przekazywany do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b87ee-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="b87ee-121">Atrybut sprawia, że podczas wywoływania kodu opisywanego przez atrybut kompilator generuje ostrzeżenie pokazujące przekazany ciąg.</span><span class="sxs-lookup"><span data-stu-id="b87ee-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a><span data-ttu-id="b87ee-122">Stosowanie atrybutów na poziomie zestawów</span><span class="sxs-lookup"><span data-stu-id="b87ee-122">Applying Attributes at the Assembly Level</span></span>  
 <span data-ttu-id="b87ee-123">Aby zastosować atrybut na poziomie zestawu, należy użyć **zestawu** (`Assembly` w języku Visual Basic) słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="b87ee-123">If you want to apply an attribute at the assembly level, use the **assembly** (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="b87ee-124">Poniższy kod przedstawia **AssemblyTitleAttribute** stosowane na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="b87ee-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 <span data-ttu-id="b87ee-125">Zastosowanie tego atrybutu sprawia, że w manifeście zestawu w części pliku określającej metadane jest umieszczany ciąg `"My Assembly"`.</span><span class="sxs-lookup"><span data-stu-id="b87ee-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="b87ee-126">Ten atrybut można wyświetlić za pomocą [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub tworząc niestandardowy program do pobrania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b87ee-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b87ee-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b87ee-127">See also</span></span>

- [<span data-ttu-id="b87ee-128">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b87ee-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="b87ee-129">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="b87ee-129">Retrieving Information Stored in Attributes</span></span>](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="b87ee-130">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="b87ee-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)
- [<span data-ttu-id="b87ee-131">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="b87ee-131">Attributes (C#)</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="b87ee-132">Omówienie atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b87ee-132">Attributes overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/attributes/index.md)
