---
title: Wpisywanie atrybutów niestandardowych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 114d24c1fc523d5501deb4aa17f9541c5a918276
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574650"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="b8aa4-102">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b8aa4-102">Writing Custom Attributes</span></span>
<span data-ttu-id="b8aa4-103">Projektowanie własnych niestandardowych atrybutów, nie trzeba wzorca wiele nowych pojęć.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="b8aa4-104">Jeśli znasz programowanie zorientowane obiektowo i dowiedzieć się, jak zaprojektować klasy, masz już większość wiedzy potrzebne.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="b8aa4-105">Atrybuty niestandardowe są zasadniczo tradycyjnych klas pochodzących od bezpośrednio lub pośrednio <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8aa4-106">Podobnie jak tradycyjnych klasy atrybutów niestandardowych, które zawierają metod, które przechowują i pobierają dane.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="b8aa4-107">Podstawowe kroki, aby poprawnie projektowania klas niestandardowych atrybutów są następujące:</span><span class="sxs-lookup"><span data-stu-id="b8aa4-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
-   [<span data-ttu-id="b8aa4-108">Stosowanie AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="b8aa4-108">Applying the AttributeUsageAttribute</span></span>](#cpconapplyingattributeusageattribute)  
  
-   [<span data-ttu-id="b8aa4-109">Deklarowanie klasy atrybutów</span><span class="sxs-lookup"><span data-stu-id="b8aa4-109">Declaring the attribute class</span></span>](#cpcondeclaringattributeclass)  
  
-   [<span data-ttu-id="b8aa4-110">Deklarowanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="b8aa4-110">Declaring constructors</span></span>](#cpcondeclaringconstructors)  
  
-   [<span data-ttu-id="b8aa4-111">Deklarowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="b8aa4-111">Declaring properties</span></span>](#cpcondeclaringproperties)  
  
 <span data-ttu-id="b8aa4-112">Ta sekcja zawiera opis każdego z tych kroków i nie zawiera z [przykład atrybutu niestandardowego](#cpconcustomattributeexample).</span><span class="sxs-lookup"><span data-stu-id="b8aa4-112">This section describes each of these steps and concludes with a [custom attribute example](#cpconcustomattributeexample).</span></span>  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="b8aa4-113">Stosowanie AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="b8aa4-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="b8aa4-114">Rozpoczyna się od deklaracji atrybutu niestandardowego **AttributeUsageAttribute**, który definiuje niektóre właściwości klucza klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-114">A custom attribute declaration begins with the **AttributeUsageAttribute**, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="b8aa4-115">Na przykład można określić, czy atrybut może być dziedziczone przez inne klasy lub Określ elementy, które można zastosować atrybut do.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="b8aa4-116">Poniższy fragment kodu przedstawiają sposób użycia **AttributeUsageAttribute**.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-116">The following code fragment demonstrates how to use the **AttributeUsageAttribute**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="b8aa4-117"><xref:System.AttributeUsageAttribute?displayProperty=nameWithType> Ma trzy elementy członkowskie, które są ważne w przypadku tworzenia niestandardowych atrybutów: [attributetargets —](#cpconwritingcustomattributesanchor1), [dziedziczonych](#cpconwritingcustomattributesanchor2), i [AllowMultiple](#cpconwritingcustomattributesanchor3).</span><span class="sxs-lookup"><span data-stu-id="b8aa4-117">The <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> has three members that are important for the creation of custom attributes: [AttributeTargets](#cpconwritingcustomattributesanchor1), [Inherited](#cpconwritingcustomattributesanchor2), and [AllowMultiple](#cpconwritingcustomattributesanchor3).</span></span>  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a><span data-ttu-id="b8aa4-118">Attributetargets — element członkowski</span><span class="sxs-lookup"><span data-stu-id="b8aa4-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="b8aa4-119">W poprzednim przykładzie **AttributeTargets.All** jest określony, wskazując, że ten atrybut można stosować do wszystkich elementów programu.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-119">In the previous example, **AttributeTargets.All** is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="b8aa4-120">Alternatywnie można określić **AttributeTargets.Class**, wskazującą, czy atrybut może odnosić się tylko do klasy, lub **AttributeTargets.Method**, wskazujący, że atrybut może być stosowana tylko do metody.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-120">Alternatively, you can specify **AttributeTargets.Class**, indicating that your attribute can be applied only to a class, or **AttributeTargets.Method**, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="b8aa4-121">Wszystkie elementy programu może być oznaczony opis przez atrybut niestandardowy w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="b8aa4-122">Można również przekazać wiele wystąpień <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-122">You can also pass multiple instances of <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="b8aa4-123">Poniższy fragment kodu Określa, że atrybut niestandardowy może odnosić się do klasy lub metody.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a><span data-ttu-id="b8aa4-124">Właściwość dziedziczona</span><span class="sxs-lookup"><span data-stu-id="b8aa4-124">Inherited Property</span></span>  
 <span data-ttu-id="b8aa4-125"><xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Właściwość wskazuje, czy atrybut może być dziedziczone przez klasy, które są pochodnymi klasy, do których zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="b8aa4-126">Ta właściwość ma albo **true** (ustawienie domyślne) lub **false** flagi.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-126">This property takes either a **true** (the default) or **false** flag.</span></span> <span data-ttu-id="b8aa4-127">Na przykład w poniższym przykładzie `MyAttribute` ma wartość domyślną <xref:System.AttributeUsageAttribute.Inherited%2A> wartość **true**, podczas gdy `YourAttribute` ma <xref:System.AttributeUsageAttribute.Inherited%2A> wartość **false**.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-127">For example, in the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of **true**, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of **false**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="b8aa4-128">Dwa atrybuty zostaną zastosowane do metody w klasie podstawowej `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="b8aa4-129">Ponadto klasa `YourClass` jest dziedziczona z klasy podstawowej `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="b8aa4-130">Metoda `MyMethod` pokazuje `MyAttribute`, ale nie `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a><span data-ttu-id="b8aa4-131">AllowMultiple właściwość</span><span class="sxs-lookup"><span data-stu-id="b8aa4-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="b8aa4-132"><xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Właściwość wskazuje, czy w elemencie może istnieć wiele wystąpień atrybut.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="b8aa4-133">Jeśli ustawiono **true**, wiele wystąpień są dozwolone; Jeśli ustawioną **false** (ustawienie domyślne), jest dozwolone tylko jedno wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-133">If set to **true**, multiple instances are allowed; if set to **false** (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="b8aa4-134">W poniższym przykładzie `MyAttribute` ma wartość domyślną <xref:System.AttributeUsageAttribute.AllowMultiple%2A> wartość **false**, podczas gdy `YourAttribute` ma wartość **true**.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of **false**, while `YourAttribute` has a value of **true**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="b8aa4-135">Gdy zastosowano wiele wystąpień tych atrybutów, `MyAttribute` powoduje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="b8aa4-136">W poniższym przykładzie pokazano sposób użycia prawidłową `YourAttribute` i nieprawidłowe użycie `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="b8aa4-137">Jeśli oba <xref:System.AttributeUsageAttribute.AllowMultiple%2A> właściwości i <xref:System.AttributeUsageAttribute.Inherited%2A> ustawiono właściwość **true**, klasy, które są dziedziczone z innej klasy mogą dziedziczyć atrybutu i inne wystąpienie tego samego atrybutu stosowane w tej samej klasy podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to **true**, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="b8aa4-138">Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple%2A> ustawiono **false**, wartości żadnych atrybutów w klasie nadrzędnej, zostaną zastąpione przez nowe wystąpienia tego samego atrybutu klasy podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to **false**, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="b8aa4-139">Deklarowanie klasy atrybutów</span><span class="sxs-lookup"><span data-stu-id="b8aa4-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="b8aa4-140">Po zastosowaniu <xref:System.AttributeUsageAttribute>, możesz rozpocząć do definiowania specyfice atrybut.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="b8aa4-141">Deklaracja klasy atrybutu wygląda podobnie do deklaracji klasy tradycyjnych, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="b8aa4-142">Ta definicja atrybutu przedstawiono następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="b8aa4-142">This attribute definition demonstrates the following points:</span></span>  
  
-   <span data-ttu-id="b8aa4-143">Atrybut klasy musi być zadeklarowany jako publiczny klasy.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-143">Attribute classes must be declared as public classes.</span></span>  
  
-   <span data-ttu-id="b8aa4-144">Konwencja, nazwa klasy atrybutu kończy się wyrazem **atrybutu**.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="b8aa4-145">Podczas gdy nie jest to wymagane, tę Konwencję jest zalecane dla czytelności.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="b8aa4-146">Gdy jest stosowany atrybut włączenia programu word atrybutu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
-   <span data-ttu-id="b8aa4-147">Wszystkie klasy atrybutu musi dziedziczyć pośrednio lub bezpośrednio z **System.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-147">All attribute classes must inherit directly or indirectly from **System.Attribute**.</span></span>  
  
-   <span data-ttu-id="b8aa4-148">Microsoft Visual Basic, wszystkie klasy atrybutu niestandardowego musi mieć **AttributeUsageAttribute** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-148">In Microsoft Visual Basic, all custom attribute classes must have the **AttributeUsageAttribute** attribute.</span></span>  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a><span data-ttu-id="b8aa4-149">Deklarowanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="b8aa4-149">Declaring Constructors</span></span>  
 <span data-ttu-id="b8aa4-150">Atrybuty są inicjowane z konstruktorów w taki sam sposób jak tradycyjnych klasy.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="b8aa4-151">Poniższy fragment kodu przedstawiono typowe atrybut konstruktora.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="b8aa4-152">Ten konstruktor publiczny przyjmuje parametr i ustawia wartość równą zmiennej elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-152">This public constructor takes a parameter and sets its value equal to a member variable.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="b8aa4-153">Można przeciążać konstruktora, aby zmieścił się w różnych kombinacji wartości.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="b8aa4-154">Jeśli również definiować [właściwości](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) dla klasy atrybutów niestandardowych, można użyć kombinacji parametrów nazwanych i pozycyjnych podczas inicjowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-154">If you also define a [property](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="b8aa4-155">Zazwyczaj określa się wszystkie wymagane parametry jako parametry pozycyjne i wszystkie opcjonalne jako o nazwie.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="b8aa4-156">W takim przypadku atrybutu nie można zainicjować bez wymaganego parametru.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="b8aa4-157">Wszystkie inne parametry są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-157">All other parameters are optional.</span></span> <span data-ttu-id="b8aa4-158">Należy pamiętać, że w języku Visual Basic konstruktory klasę atrybutów nie powinien używać ParamArray argument.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="b8aa4-159">Poniższy przykładowy kod przedstawia jak atrybut, który używa poprzedniej Konstruktor może odnosić się przy użyciu parametrów opcjonalne i wymagane.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="b8aa4-160">Przyjęto założenie, że ten atrybut ma jedną wartość logiczną wymagane, a właściwość jeden opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a><span data-ttu-id="b8aa4-161">Deklarowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="b8aa4-161">Declaring Properties</span></span>  
 <span data-ttu-id="b8aa4-162">Jeśli chcesz zdefiniować nazwany parametr lub umożliwiają łatwe do zwrócenia wartości przechowywanych przez atrybut, Zadeklaruj [właściwości](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="b8aa4-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="b8aa4-163">Właściwości atrybutów powinien być zadeklarowany jako publiczny jednostki z opisu typu danych, które zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="b8aa4-164">Definiowanie zmiennej, która będzie przechowywać wartości z właściwości i skojarz ją z **uzyskać** i **ustawić** metody.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="b8aa4-165">Poniższy przykład kodu pokazuje, jak do zaimplementowania właściwości prostej w atrybut.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a><span data-ttu-id="b8aa4-166">Przykład atrybutu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="b8aa4-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="b8aa4-167">Ta sekcja zawiera informacje o poprzednich i pokazano, jak zaprojektować proste atrybut, który dokumentów informacje o autorze sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="b8aa4-168">Ten atrybut w tym przykładzie są przechowywane nazwy i poziom programisty, i określa, czy kod zostały sprawdzone.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="b8aa4-169">Używa trzech zmiennych prywatnych do przechowywania rzeczywiste wartości do zapisania.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="b8aa4-170">Pobiera i ustawia wartości właściwości publicznej odpowiada każdej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="b8aa4-171">Na koniec Konstruktor jest zdefiniowana z dwóch wymaganych parametrów.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="b8aa4-172">Można użyć tego atrybutu użycie pełnej nazwy `DeveloperAttribute`, lub za pomocą nazwy skróconej `Developer`, w jednym z następujących sposobów.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="b8aa4-173">W pierwszym przykładzie atrybut zastosowany z tylko wymaganymi nazwanych parametrów, a w drugim przykładzie pokazano, atrybut zastosowany o wymaganych i opcjonalnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="b8aa4-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8aa4-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8aa4-174">See Also</span></span>  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="b8aa4-175">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b8aa4-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
