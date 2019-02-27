---
title: Wpisywanie atrybutów niestandardowych
ms.date: 07/17/2018
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
ms.openlocfilehash: 1d0a0659c99a49770d0d08460026363ecef06654
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836321"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="af831-102">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="af831-102">Writing Custom Attributes</span></span>
<span data-ttu-id="af831-103">Aby zaprojektować atrybutów niestandardowych, nie trzeba opanować wiele nowych pojęć.</span><span class="sxs-lookup"><span data-stu-id="af831-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="af831-104">Jeśli znasz programowanie zorientowane obiektowo i wiedzieć, jak klasy należy projektować, masz już większość wiedzę potrzebną.</span><span class="sxs-lookup"><span data-stu-id="af831-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="af831-105">Atrybuty niestandardowe są zasadniczo tradycyjnych klas, które pochodzą bezpośrednio lub pośrednio z <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af831-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="af831-106">Podobnie jak tradycyjnych klasy atrybutów niestandardowych, które zawierają metody, które przechowywać i pobierać dane.</span><span class="sxs-lookup"><span data-stu-id="af831-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="af831-107">Podstawowe kroki, aby prawidłowo projektowania klas atrybutów niestandardowych, są następujące:</span><span class="sxs-lookup"><span data-stu-id="af831-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="af831-108">Stosowanie AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="af831-108">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="af831-109">Deklarowanie klasy atrybutów</span><span class="sxs-lookup"><span data-stu-id="af831-109">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="af831-110">Deklarowanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="af831-110">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="af831-111">Deklarowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="af831-111">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="af831-112">W tej sekcji opisano każdy z tych kroków i nie zawiera z [przykład atrybutu niestandardowego](#custom-attribute-example).</span><span class="sxs-lookup"><span data-stu-id="af831-112">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="af831-113">Stosowanie AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="af831-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="af831-114">Deklaracji atrybutu niestandardowego, który rozpoczyna się od <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, definiujący niektóre z kluczowych charakterystyk klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="af831-114">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="af831-115">Na przykład można określić, czy atrybut może być dziedziczona przez inne klasy lub Określ elementy, które można zastosować atrybut do.</span><span class="sxs-lookup"><span data-stu-id="af831-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="af831-116">Poniższy fragment kodu pokazuje sposób użycia <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="af831-116">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="af831-117"><xref:System.AttributeUsageAttribute> Ma trzy elementy członkowskie, które są ważne w przypadku tworzenia niestandardowych atrybutów: [Attributetargets —](#attributetargets-member), [dziedziczone](#inherited-property), i [AllowMultiple](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="af831-117">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="af831-118">Attributetargets — element członkowski</span><span class="sxs-lookup"><span data-stu-id="af831-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="af831-119">W poprzednim przykładzie <xref:System.AttributeTargets.All?displayProperty=nameWithType> jest określony, wskazujący, że ten atrybut można stosować do wszystkich elementów programu.</span><span class="sxs-lookup"><span data-stu-id="af831-119">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="af831-120">Alternatywnie, można określić <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, wskazujący, że Twoje atrybut można stosować tylko do klasy, lub <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, wskazujący, że Twoje atrybut można stosować tylko do metody.</span><span class="sxs-lookup"><span data-stu-id="af831-120">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="af831-121">Wszystkie elementy program może być oznaczony jako opis przez atrybut niestandardowy w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="af831-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="af831-122">Można również przekazać wiele <xref:System.AttributeTargets> wartości.</span><span class="sxs-lookup"><span data-stu-id="af831-122">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="af831-123">Poniższy fragment kodu Określa, czy niestandardowy atrybut można stosować do dowolnej klasy lub metody.</span><span class="sxs-lookup"><span data-stu-id="af831-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="af831-124">Właściwość dziedziczona</span><span class="sxs-lookup"><span data-stu-id="af831-124">Inherited Property</span></span>  
 <span data-ttu-id="af831-125"><xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Właściwość wskazuje, czy atrybut może być dziedziczona przez klasy, które są pochodnymi klasy, do których zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="af831-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="af831-126">Ta właściwość ma albo `true` (ustawienie domyślne) lub `false` flagi.</span><span class="sxs-lookup"><span data-stu-id="af831-126">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="af831-127">W poniższym przykładzie `MyAttribute` ma wartość domyślną <xref:System.AttributeUsageAttribute.Inherited%2A> wartość `true`, podczas gdy `YourAttribute` ma <xref:System.AttributeUsageAttribute.Inherited%2A> wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="af831-127">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="af831-128">Dwa atrybuty są następnie stosowane do metody w klasie bazowej `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="af831-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="af831-129">Na koniec klasę `YourClass` jest dziedziczona z klasy bazowej `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="af831-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="af831-130">Metoda `MyMethod` pokazuje `MyAttribute`, ale nie `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="af831-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="af831-131">AllowMultiple właściwość</span><span class="sxs-lookup"><span data-stu-id="af831-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="af831-132"><xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> Właściwość wskazuje, czy na element może istnieć wiele wystąpień usługi atrybutu.</span><span class="sxs-lookup"><span data-stu-id="af831-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="af831-133">Jeśli ustawiono `true`, wielu wystąpień są dozwolone; Jeśli równa `false` (ustawienie domyślne), jest dozwolone tylko jedno wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="af831-133">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="af831-134">W poniższym przykładzie `MyAttribute` ma wartość domyślną <xref:System.AttributeUsageAttribute.AllowMultiple%2A> wartość `false`, podczas gdy `YourAttribute` ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="af831-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="af831-135">Po zastosowaniu wielu wystąpień tych atrybutów, `MyAttribute` powoduje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="af831-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="af831-136">Poniższy przykład kodu pokazuje prawidłowe użycie `YourAttribute` i nieprawidłowe użycie `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="af831-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="af831-137">Jeśli oba <xref:System.AttributeUsageAttribute.AllowMultiple%2A> właściwości i <xref:System.AttributeUsageAttribute.Inherited%2A> ustawioną na `true`, klasę, która jest dziedziczony z innej klasy mogą dziedziczyć atrybutu i inne wystąpienie tego samego atrybutu stosowane w tej samej klasy podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="af831-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="af831-138">Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple%2A> ustawiono `false`, wartości atrybutów w klasie nadrzędnej, zostaną zastąpione przez nowe wystąpienia tego samego atrybutu klasy podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="af831-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="af831-139">Deklarowanie klasy atrybutów</span><span class="sxs-lookup"><span data-stu-id="af831-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="af831-140">Po zastosowaniu <xref:System.AttributeUsageAttribute>, możesz rozpocząć definiowanie szczegółowych informacji z atrybutu.</span><span class="sxs-lookup"><span data-stu-id="af831-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="af831-141">Deklaracja klasy atrybutu wygląda podobnie do deklaracji klasy tradycyjnych, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="af831-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="af831-142">Ta definicja atrybutu pokazuje następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="af831-142">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="af831-143">Klasy atrybutów musi być zadeklarowany jako publiczne klasy.</span><span class="sxs-lookup"><span data-stu-id="af831-143">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="af831-144">Zgodnie z Konwencją Nazwa klasy atrybutu kończy się wyrazem **atrybutu**.</span><span class="sxs-lookup"><span data-stu-id="af831-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="af831-145">Chociaż nie jest to wymagane, ta Konwencja jest zalecana dla czytelności.</span><span class="sxs-lookup"><span data-stu-id="af831-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="af831-146">Jeśli ten atrybut jest stosowany, włączenie word atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="af831-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="af831-147">Wszystkie klasy atrybutu musi dziedziczyć pośrednio lub bezpośrednio <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af831-147">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="af831-148">Microsoft Visual Basic, wszystkie klasy atrybutu niestandardowego musi mieć <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="af831-148">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="af831-149">Deklarowanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="af831-149">Declaring Constructors</span></span>  
 <span data-ttu-id="af831-150">Atrybuty są inicjowane z konstruktorów w taki sam sposób jak tradycyjnych klasy.</span><span class="sxs-lookup"><span data-stu-id="af831-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="af831-151">Poniższy fragment kodu przedstawia typowe atrybut konstruktora.</span><span class="sxs-lookup"><span data-stu-id="af831-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="af831-152">Ten publiczny konstruktor przyjmuje parametr i ustawia zmienną członkowską równa jego wartości.</span><span class="sxs-lookup"><span data-stu-id="af831-152">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="af831-153">Możesz doprowadzić do przeciążenia konstruktora, aby obsłużyć różne kombinacje wartości.</span><span class="sxs-lookup"><span data-stu-id="af831-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="af831-154">Jeśli należy także zdefiniować [właściwość](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) dla swojej klasy atrybutów niestandardowych, można użyć kombinacji parametrów nazwanych i pozycyjnych podczas inicjowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="af831-154">If you also define a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="af831-155">Zazwyczaj można zdefiniować wszystkie wymagane parametry jako parametry pozycyjne i wszystkie opcjonalne jako o nazwie.</span><span class="sxs-lookup"><span data-stu-id="af831-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="af831-156">W tym przypadku atrybut nie można zainicjować bez wymaganego parametru.</span><span class="sxs-lookup"><span data-stu-id="af831-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="af831-157">Wszystkie inne parametry są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="af831-157">All other parameters are optional.</span></span> <span data-ttu-id="af831-158">Należy pamiętać, że w języku Visual Basic konstruktory klasy atrybutów nie należy używać argumentu ParamArray.</span><span class="sxs-lookup"><span data-stu-id="af831-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="af831-159">W poniższym przykładzie kodu przedstawiono sposób atrybut, który korzysta z poprzednich Konstruktor może odnosić się przy użyciu parametrów opcjonalnych i wymaganych.</span><span class="sxs-lookup"><span data-stu-id="af831-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="af831-160">Przyjęto założenie, że ten atrybut ma jedną wartość logiczną wymagane i właściwość jeden opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="af831-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="af831-161">Deklarowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="af831-161">Declaring Properties</span></span>  
 <span data-ttu-id="af831-162">Jeśli chcesz zdefiniować nazwany parametr lub prosty sposób zwracania wartości przechowywane przez atrybut, Zadeklaruj [właściwość](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="af831-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="af831-163">Właściwości atrybutów powinien być zadeklarowany jako publiczny jednostki opis typu danych, który zostanie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="af831-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="af831-164">Zdefiniuj zmienną, która będzie przechowywać wartości właściwości i powiąż ją z **uzyskać** i **ustaw** metody.</span><span class="sxs-lookup"><span data-stu-id="af831-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="af831-165">Poniższy przykład kodu demonstruje sposób implementacji właściwości prostej usługi atrybutu.</span><span class="sxs-lookup"><span data-stu-id="af831-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="af831-166">Przykład atrybutu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="af831-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="af831-167">Ta sekcja zawiera wcześniejszych informacji i pokazuje, jak projektować proste atrybut, który dokumenty, informacje o autorze sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="af831-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="af831-168">Ten atrybut, w tym przykładzie przechowuje nazwę i poziom programisty, i czy zostało poddane przeglądowi kodu.</span><span class="sxs-lookup"><span data-stu-id="af831-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="af831-169">Używa trzech zmiennych prywatnych do przechowywania wartości faktycznych można zapisać.</span><span class="sxs-lookup"><span data-stu-id="af831-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="af831-170">Każda zmienna jest reprezentowany przez właściwość publiczną, która pobiera i ustawia wartości.</span><span class="sxs-lookup"><span data-stu-id="af831-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="af831-171">Na koniec Konstruktor jest zdefiniowana za pomocą dwóch wymaganych parametrów.</span><span class="sxs-lookup"><span data-stu-id="af831-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="af831-172">Można zastosować ten atrybut przy użyciu pełnej nazwy `DeveloperAttribute`, lub za pomocą nazwy skróconej, `Developer`, w jednym z następujących sposobów.</span><span class="sxs-lookup"><span data-stu-id="af831-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="af831-173">Pierwszy przykład pokazuje zastosowany tylko wymagane nazwanych parametrów, podczas gdy drugi przykład przedstawia zastosowany przy użyciu wymaganych i opcjonalnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="af831-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af831-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af831-174">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="af831-175">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="af831-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
