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
ms.openlocfilehash: 6570c6994c0f2e6571361c3eadc73b02a55f1584
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140584"
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="7538f-102">Wpisywanie atrybutów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="7538f-102">Writing Custom Attributes</span></span>
<span data-ttu-id="7538f-103">Do zaprojektowania własnych atrybutów niestandardowych nie ma potrzeby tworzenia wzorców wielu nowych koncepcji.</span><span class="sxs-lookup"><span data-stu-id="7538f-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="7538f-104">Jeśli znasz programowanie zorientowane obiektowo i wiesz, jak projektować klasy, masz już większość koniecznych informacji.</span><span class="sxs-lookup"><span data-stu-id="7538f-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="7538f-105">Atrybuty niestandardowe są zasadniczo tradycyjnymi klasami, które są wyprowadzane bezpośrednio lub pośrednio z <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7538f-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7538f-106">Podobnie jak tradycyjne klasy, atrybuty niestandardowe zawierają metody, które przechowują i pobierają dane.</span><span class="sxs-lookup"><span data-stu-id="7538f-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="7538f-107">Podstawowe kroki w celu prawidłowego projektowania klas atrybutów niestandardowych są następujące:</span><span class="sxs-lookup"><span data-stu-id="7538f-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
- [<span data-ttu-id="7538f-108">Stosowanie AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="7538f-108">Applying the AttributeUsageAttribute</span></span>](#applying-the-attributeusageattribute)  
  
- [<span data-ttu-id="7538f-109">Deklarowanie klasy atrybutów</span><span class="sxs-lookup"><span data-stu-id="7538f-109">Declaring the attribute class</span></span>](#declaring-the-attribute-class)  
  
- [<span data-ttu-id="7538f-110">Deklarowanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="7538f-110">Declaring constructors</span></span>](#declaring-constructors)  
  
- [<span data-ttu-id="7538f-111">Deklarowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="7538f-111">Declaring properties</span></span>](#declaring-properties)  
  
 <span data-ttu-id="7538f-112">W tej sekcji opisano wszystkie te kroki i zakończymy z [przykładem atrybutu niestandardowego](#custom-attribute-example).</span><span class="sxs-lookup"><span data-stu-id="7538f-112">This section describes each of these steps and concludes with a [custom attribute example](#custom-attribute-example).</span></span>  
  
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="7538f-113">Stosowanie AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="7538f-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="7538f-114">Deklaracja atrybutu niestandardowego rozpoczyna się od <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, który definiuje niektóre kluczowe cechy klasy atrybutów.</span><span class="sxs-lookup"><span data-stu-id="7538f-114">A custom attribute declaration begins with the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="7538f-115">Na przykład można określić, czy atrybut może być dziedziczony przez inne klasy, czy też określić, do których elementów można zastosować atrybut.</span><span class="sxs-lookup"><span data-stu-id="7538f-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="7538f-116">Poniższy fragment kodu ilustruje sposób używania <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7538f-116">The following code fragment demonstrates how to use the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="7538f-117"><xref:System.AttributeUsageAttribute> ma trzy składowe, które są ważne dla tworzenia atrybutów niestandardowych: [AttributeTargets](#attributetargets-member), [Odziedziczone](#inherited-property)i [AllowMultiple](#allowmultiple-property).</span><span class="sxs-lookup"><span data-stu-id="7538f-117">The <xref:System.AttributeUsageAttribute> has three members that are important for the creation of custom attributes: [AttributeTargets](#attributetargets-member), [Inherited](#inherited-property), and [AllowMultiple](#allowmultiple-property).</span></span>  
  
### <a name="attributetargets-member"></a><span data-ttu-id="7538f-118">AttributeTargets element członkowski</span><span class="sxs-lookup"><span data-stu-id="7538f-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="7538f-119">W poprzednim przykładzie określono <xref:System.AttributeTargets.All?displayProperty=nameWithType>, wskazujący, że ten atrybut może być stosowany do wszystkich elementów programu.</span><span class="sxs-lookup"><span data-stu-id="7538f-119">In the previous example, <xref:System.AttributeTargets.All?displayProperty=nameWithType> is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="7538f-120">Alternatywnie można określić <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, wskazując, że atrybut może być stosowany tylko do klasy lub <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, co oznacza, że atrybut może być stosowany tylko do metody.</span><span class="sxs-lookup"><span data-stu-id="7538f-120">Alternatively, you can specify <xref:System.AttributeTargets.Class?displayProperty=nameWithType>, indicating that your attribute can be applied only to a class, or <xref:System.AttributeTargets.Method?displayProperty=nameWithType>, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="7538f-121">Wszystkie elementy programu mogą być oznaczone do opisu przez atrybut niestandardowy w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="7538f-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="7538f-122">Można również przekazać wiele wartości <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="7538f-122">You can also pass multiple <xref:System.AttributeTargets> values.</span></span> <span data-ttu-id="7538f-123">Poniższy fragment kodu określa, że atrybut niestandardowy można zastosować do dowolnej klasy lub metody.</span><span class="sxs-lookup"><span data-stu-id="7538f-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a><span data-ttu-id="7538f-124">Właściwość dziedziczona</span><span class="sxs-lookup"><span data-stu-id="7538f-124">Inherited Property</span></span>  
 <span data-ttu-id="7538f-125">Właściwość <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> wskazuje, czy atrybut może być dziedziczony przez klasy, które pochodzą od klas, do których zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="7538f-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="7538f-126">Ta właściwość przyjmuje `true` (wartość domyślna) lub `false`.</span><span class="sxs-lookup"><span data-stu-id="7538f-126">This property takes either a `true` (the default) or `false` flag.</span></span> <span data-ttu-id="7538f-127">W poniższym przykładzie `MyAttribute` ma domyślną wartość <xref:System.AttributeUsageAttribute.Inherited%2A> `true`, podczas gdy `YourAttribute` ma <xref:System.AttributeUsageAttribute.Inherited%2A> wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="7538f-127">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of `true`, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of `false`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="7538f-128">Te dwa atrybuty są następnie stosowane do metody w klasie bazowej `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="7538f-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="7538f-129">Na koniec Klasa `YourClass` jest dziedziczona z klasy bazowej `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="7538f-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="7538f-130">Metoda `MyMethod` zawiera `MyAttribute`, ale nie `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="7538f-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a><span data-ttu-id="7538f-131">Właściwość AllowMultiple</span><span class="sxs-lookup"><span data-stu-id="7538f-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="7538f-132">Właściwość <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> wskazuje, czy w elemencie może istnieć wiele wystąpień atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7538f-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="7538f-133">Jeśli ustawiono `true`, dozwolone są wiele wystąpień; Jeśli jest ustawiona na `false` (wartość domyślna), dozwolone jest tylko jedno wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="7538f-133">If set to `true`, multiple instances are allowed; if set to `false` (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="7538f-134">W poniższym przykładzie `MyAttribute` ma domyślną wartość <xref:System.AttributeUsageAttribute.AllowMultiple%2A> `false`, podczas gdy `YourAttribute` ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="7538f-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of `false`, while `YourAttribute` has a value of `true`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="7538f-135">Jeśli zastosowano wiele wystąpień tych atrybutów, `MyAttribute` generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="7538f-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="7538f-136">Poniższy przykład kodu pokazuje prawidłowe użycie `YourAttribute` i nieprawidłowe użycie `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="7538f-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="7538f-137">Jeśli właściwość <xref:System.AttributeUsageAttribute.AllowMultiple%2A> i Właściwość <xref:System.AttributeUsageAttribute.Inherited%2A> są ustawione na `true`, Klasa dziedziczona z innej klasy może dziedziczyć atrybut i mieć inne wystąpienie tego samego atrybutu stosowane w tej samej klasie podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="7538f-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to `true`, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="7538f-138">Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple%2A> jest ustawiona na `false`, wartości wszelkich atrybutów w klasie nadrzędnej zostaną zastąpione przez nowe wystąpienia tego samego atrybutu w klasie podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="7538f-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to `false`, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="7538f-139">Deklarowanie klasy atrybutów</span><span class="sxs-lookup"><span data-stu-id="7538f-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="7538f-140">Po zastosowaniu <xref:System.AttributeUsageAttribute>można rozpocząć Definiowanie określonych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="7538f-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="7538f-141">Deklaracja klasy atrybutu wygląda podobnie do deklaracji tradycyjnej klasy, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7538f-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="7538f-142">Ta definicja atrybutu ilustruje następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="7538f-142">This attribute definition demonstrates the following points:</span></span>  
  
- <span data-ttu-id="7538f-143">Klasy atrybutów muszą być zadeklarowane jako klasy publiczne.</span><span class="sxs-lookup"><span data-stu-id="7538f-143">Attribute classes must be declared as public classes.</span></span>  
  
- <span data-ttu-id="7538f-144">Zgodnie z Konwencją nazwa klasy ma kończyć się **atrybutem**programu Word.</span><span class="sxs-lookup"><span data-stu-id="7538f-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="7538f-145">Chociaż nie jest to wymagane, ta konwencja jest zalecana dla czytelności.</span><span class="sxs-lookup"><span data-stu-id="7538f-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="7538f-146">Gdy atrybut jest stosowany, włączenie atrybutu słowa jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="7538f-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
- <span data-ttu-id="7538f-147">Wszystkie klasy atrybutów muszą dziedziczyć bezpośrednio lub pośrednio z <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7538f-147">All attribute classes must inherit directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="7538f-148">W programie Microsoft Visual Basic wszystkie klasy atrybutów niestandardowych muszą mieć atrybut <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7538f-148">In Microsoft Visual Basic, all custom attribute classes must have the <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> attribute.</span></span>  
  
## <a name="declaring-constructors"></a><span data-ttu-id="7538f-149">Deklarowanie konstruktorów</span><span class="sxs-lookup"><span data-stu-id="7538f-149">Declaring Constructors</span></span>  
 <span data-ttu-id="7538f-150">Atrybuty są inicjowane za pomocą konstruktorów w taki sam sposób jak w przypadku tradycyjnych klas.</span><span class="sxs-lookup"><span data-stu-id="7538f-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="7538f-151">Poniższy fragment kodu ilustruje typowy Konstruktor atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7538f-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="7538f-152">Ten konstruktor publiczny przyjmuje parametr i ustawia zmienną członkowską równą jej wartości.</span><span class="sxs-lookup"><span data-stu-id="7538f-152">This public constructor takes a parameter and sets a member variable equal to its value.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="7538f-153">Można przeciążyć konstruktora, aby pomieścić różne kombinacje wartości.</span><span class="sxs-lookup"><span data-stu-id="7538f-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="7538f-154">Jeśli zdefiniowano również [Właściwość](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) klasy atrybutów niestandardowych, podczas inicjowania atrybutu można użyć kombinacji nazwanych i pozycyjnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="7538f-154">If you also define a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="7538f-155">Zwykle wszystkie wymagane parametry są definiowane jako położenie i wszystkie parametry opcjonalne jako nazwane.</span><span class="sxs-lookup"><span data-stu-id="7538f-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="7538f-156">W tym przypadku nie można zainicjować atrybutu bez wymaganego parametru.</span><span class="sxs-lookup"><span data-stu-id="7538f-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="7538f-157">Wszystkie inne parametry są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="7538f-157">All other parameters are optional.</span></span> <span data-ttu-id="7538f-158">Należy zauważyć, że w Visual Basic konstruktory dla klasy atrybutów nie powinny używać argumentu ParamArray.</span><span class="sxs-lookup"><span data-stu-id="7538f-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="7538f-159">Poniższy przykład kodu pokazuje, jak atrybut, który używa poprzedniego konstruktora można zastosować przy użyciu opcjonalnych i wymaganych parametrów.</span><span class="sxs-lookup"><span data-stu-id="7538f-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="7538f-160">Przyjęto założenie, że atrybut ma jedną wymaganą wartość logiczną i jedną opcjonalną Właściwość ciągu.</span><span class="sxs-lookup"><span data-stu-id="7538f-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a><span data-ttu-id="7538f-161">Deklarowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="7538f-161">Declaring Properties</span></span>  
 <span data-ttu-id="7538f-162">Jeśli chcesz zdefiniować nazwany parametr lub podać łatwy sposób zwracania wartości przechowywanych przez atrybut, zadeklaruj [Właściwość](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="7538f-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)).</span></span> <span data-ttu-id="7538f-163">Właściwości atrybutu należy zadeklarować jako jednostki publiczne z opisem typu danych, które zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="7538f-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="7538f-164">Zdefiniuj zmienną, która będzie przechowywać wartość właściwości i skojarz ją z metodami **Get** i **Set** .</span><span class="sxs-lookup"><span data-stu-id="7538f-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="7538f-165">Poniższy przykład kodu demonstruje sposób implementacji prostej właściwości w atrybucie.</span><span class="sxs-lookup"><span data-stu-id="7538f-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a><span data-ttu-id="7538f-166">Przykład atrybutu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="7538f-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="7538f-167">Ta sekcja obejmuje poprzednie informacje i pokazuje sposób projektowania prostego atrybutu, który dokumentuje informacje o autorze sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="7538f-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="7538f-168">Atrybut w tym przykładzie przechowuje nazwę i poziom programisty oraz czy kod został sprawdzony.</span><span class="sxs-lookup"><span data-stu-id="7538f-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="7538f-169">Używa trzech prywatnych zmiennych do przechowywania rzeczywistych wartości do zapisania.</span><span class="sxs-lookup"><span data-stu-id="7538f-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="7538f-170">Każda zmienna jest reprezentowana przez publiczną właściwość, która pobiera i ustawia wartości.</span><span class="sxs-lookup"><span data-stu-id="7538f-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="7538f-171">Na koniec Konstruktor jest zdefiniowany przy użyciu dwóch wymaganych parametrów.</span><span class="sxs-lookup"><span data-stu-id="7538f-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="7538f-172">Można zastosować ten atrybut przy użyciu pełnej nazwy, `DeveloperAttribute`lub przy użyciu skróconej nazwy, `Developer`, w jeden z następujących sposobów.</span><span class="sxs-lookup"><span data-stu-id="7538f-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="7538f-173">Pierwszy przykład pokazuje atrybut zastosowany z tylko wymaganymi nazwanymi parametrami, podczas gdy drugi przykład pokazuje atrybut zastosowany do parametrów wymaganych i opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="7538f-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7538f-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7538f-174">See also</span></span>

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="7538f-175">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7538f-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
