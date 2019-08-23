---
title: Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c27732de448e19c4227062706c7a7d73c98e5f19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966878"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="b8c02-102">Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera</span><span class="sxs-lookup"><span data-stu-id="b8c02-102">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="b8c02-103">Atrybuty wyświetlania debugera umożliwiają deweloperom typu, którzy określają i najlepiej rozumieją zachowanie środowiska uruchomieniowego tego typu, aby określić, jaki typ będzie wyglądać, gdy zostanie on wyświetlony w debugerze.</span><span class="sxs-lookup"><span data-stu-id="b8c02-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="b8c02-104">Dodatkowo debuger wyświetla atrybuty, które udostępniają `Target` właściwość, można stosować na poziomie zestawu przez użytkowników bez znajomości kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="b8c02-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="b8c02-105">Ten <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut określa sposób wyświetlania typu lub elementu członkowskiego w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="b8c02-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="b8c02-106">Ten <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybut określa, czy i w jaki sposób pole lub właściwość są wyświetlane w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="b8c02-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="b8c02-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut określa typ substytutu lub serwer proxy dla typu i zmienia sposób wyświetlania typu w oknach debugera.</span><span class="sxs-lookup"><span data-stu-id="b8c02-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="b8c02-108">Podczas wyświetlania zmiennej, która ma serwer proxy lub typ zastępczy, serwer proxy znajduje się dla oryginalnego typu w oknie wyświetlania debugera.</span><span class="sxs-lookup"><span data-stu-id="b8c02-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="b8c02-109">W oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="b8c02-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="b8c02-110">Prywatne elementy członkowskie nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b8c02-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="b8c02-111">Korzystanie z DebuggerDisplayAttribute —</span><span class="sxs-lookup"><span data-stu-id="b8c02-111">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="b8c02-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor ma jeden argument: ciąg, który ma być wyświetlany w kolumnie wartości dla wystąpień typu.</span><span class="sxs-lookup"><span data-stu-id="b8c02-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="b8c02-113">Ten ciąg może zawierać nawiasy klamrowe ({i}).</span><span class="sxs-lookup"><span data-stu-id="b8c02-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="b8c02-114">Tekst w parze nawiasów klamrowych jest obliczany jako wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b8c02-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="b8c02-115">Na przykład poniższy C# kod powoduje, że wartość "Count = 4" będzie wyświetlana po wybraniu znaku plus (+), aby rozwinąć debuger wyświetlany dla wystąpienia `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="b8c02-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="b8c02-116">Atrybuty zastosowane do właściwości, do których odwołuje się wyrażenie, nie są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="b8c02-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="b8c02-117">W przypadku C# kompilatora jest dozwolone wyrażenie ogólne, które ma tylko niejawny dostęp do tego odwołania dla bieżącego wystąpienia typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="b8c02-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="b8c02-118">Wyrażenie jest ograniczone; nie ma dostępu do aliasów, zmiennych lokalnych ani wskaźników.</span><span class="sxs-lookup"><span data-stu-id="b8c02-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="b8c02-119">W C# kodzie można użyć wyrażenia ogólnego między nawiasami klamrowymi, które mają niejawny dostęp do `this` wskaźnika dla bieżącego wystąpienia tylko typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="b8c02-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="b8c02-120">Na przykład C# Jeśli obiekt został zastąpiony `ToString()`, debuger wywoła przesłonięcie i pokaże wynik zamiast standardowego `{<typeName>}.` , w związku z tym, jeśli został zastąpiony `ToString()`, nie trzeba używać <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b8c02-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="b8c02-121">Jeśli używasz obu tych metod, <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut ma pierwszeństwo przed `ToString()` przesłonięciem.</span><span class="sxs-lookup"><span data-stu-id="b8c02-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="b8c02-122">Korzystanie z DebuggerBrowsableAttribute</span><span class="sxs-lookup"><span data-stu-id="b8c02-122">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="b8c02-123"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Zastosuj do pola lub właściwości, aby określić, w jaki sposób pole lub właściwość mają być wyświetlane w oknie debugera.</span><span class="sxs-lookup"><span data-stu-id="b8c02-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="b8c02-124">Konstruktor dla tego atrybutu przyjmuje jedną z <xref:System.Diagnostics.DebuggerBrowsableState> wartości wyliczenia, która określa jeden z następujących stanów:</span><span class="sxs-lookup"><span data-stu-id="b8c02-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="b8c02-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never>wskazuje, że element członkowski nie jest wyświetlany w oknie dane.</span><span class="sxs-lookup"><span data-stu-id="b8c02-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="b8c02-126">Na przykład użycie tej wartości dla <xref:System.Diagnostics.DebuggerBrowsableAttribute> pola w polu usuwa pole z hierarchii; pole nie jest wyświetlane po rozwinięciu typu otaczającego przez kliknięcie znaku plus (+) dla wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="b8c02-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="b8c02-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>wskazuje, że element członkowski jest wyświetlany, ale nie jest domyślnie rozwinięty.</span><span class="sxs-lookup"><span data-stu-id="b8c02-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="b8c02-128">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="b8c02-128">This is the default behavior.</span></span>

- <span data-ttu-id="b8c02-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>wskazuje, że sama składowa nie jest wyświetlana, ale jego obiekty składowe są wyświetlane, jeśli jest tablicą lub kolekcją.</span><span class="sxs-lookup"><span data-stu-id="b8c02-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
> <span data-ttu-id="b8c02-130">Program <xref:System.Diagnostics.DebuggerBrowsableAttribute> nie jest obsługiwany przez Visual Basic w .NET Framework wersja 2,0.</span><span class="sxs-lookup"><span data-stu-id="b8c02-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="b8c02-131">Poniższy przykład kodu pokazuje użycie elementu, <xref:System.Diagnostics.DebuggerBrowsableAttribute> aby zapobiec wyświetlaniu właściwości, która nie jest wyświetlana w oknie debugowania dla klasy.</span><span class="sxs-lookup"><span data-stu-id="b8c02-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="b8c02-132">Korzystanie z DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="b8c02-132">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="b8c02-133">Użyj atrybutu <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , gdy trzeba znacząco i w sposób istotny zmienić widok debugowania typu, ale nie zmieniać samego typu.</span><span class="sxs-lookup"><span data-stu-id="b8c02-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="b8c02-134">Ten <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybut służy do określania serwera proxy dla typu, co umożliwia deweloperom Dostosowywanie widoku dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="b8c02-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="b8c02-135">Ten atrybut, podobnie jak <xref:System.Diagnostics.DebuggerDisplayAttribute>, może być używany na poziomie zestawu, w tym <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> przypadku Właściwość określa typ, dla którego zostanie użyty serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="b8c02-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="b8c02-136">Zalecane użycie polega na tym, że ten atrybut określa prywatny Typ zagnieżdżony, który występuje w typie, do którego zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="b8c02-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="b8c02-137">Ewaluatora wyrażeń, które obsługują osoby przeglądające typy sprawdzają ten atrybut, gdy zostanie wyświetlony typ.</span><span class="sxs-lookup"><span data-stu-id="b8c02-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="b8c02-138">Jeśli atrybut zostanie znaleziony, ewaluatora wyrażeń zastępuje typ wyświetlanego serwera proxy dla typu, do którego zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="b8c02-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="b8c02-139"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Gdy jest obecny, w oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="b8c02-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="b8c02-140">Prywatne elementy członkowskie nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b8c02-140">Private members are not displayed.</span></span> <span data-ttu-id="b8c02-141">Zachowanie okna dane nie jest zmieniane przez widoki z rozszerzonymi atrybutami.</span><span class="sxs-lookup"><span data-stu-id="b8c02-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="b8c02-142">Aby uniknąć niepotrzebnych kar z wydajnością, atrybuty wyświetlanego serwera proxy nie są przetwarzane do momentu, gdy obiekt nie zostanie rozwinięty, przez kliknięcie przez użytkownika kliknięcia znaku plusa (+) obok typu w oknie danych lub przez aplikację <xref:System.Diagnostics.DebuggerBrowsableAttribute> przypisane.</span><span class="sxs-lookup"><span data-stu-id="b8c02-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="b8c02-143">Dlatego zaleca się, aby nie stosować atrybutów do typu wyświetlanego.</span><span class="sxs-lookup"><span data-stu-id="b8c02-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="b8c02-144">Atrybuty mogą i powinny być stosowane w treści typu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="b8c02-144">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="b8c02-145">Poniższy przykład kodu pokazuje użycie, <xref:System.Diagnostics.DebuggerTypeProxyAttribute> aby określić typ, który ma być używany jako serwer proxy wyświetlania debugera.</span><span class="sxs-lookup"><span data-stu-id="b8c02-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="b8c02-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8c02-146">Example</span></span>

### <a name="description"></a><span data-ttu-id="b8c02-147">Opis</span><span class="sxs-lookup"><span data-stu-id="b8c02-147">Description</span></span>

<span data-ttu-id="b8c02-148">Poniższy przykład kodu można wyświetlić w programie Visual Studio, aby zobaczyć wyniki zastosowania <xref:System.Diagnostics.DebuggerDisplayAttribute>atrybutów, <xref:System.Diagnostics.DebuggerBrowsableAttribute>i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> .</span><span class="sxs-lookup"><span data-stu-id="b8c02-148">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="b8c02-149">Kod</span><span class="sxs-lookup"><span data-stu-id="b8c02-149">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="b8c02-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8c02-150">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
