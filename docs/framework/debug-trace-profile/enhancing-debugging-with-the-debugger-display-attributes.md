---
title: Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera
description: Wprowadzenie do atrybutów wyświetlania debugera w programie .NET, które pozwalają deweloperom typu określić, jak będzie wyglądać typ, gdy zostanie on wyświetlony w debugerze.
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
ms.openlocfilehash: f266bf7278f472c51dd355df5ba04a123cbd7df0
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415969"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="4d9d1-103">Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera</span><span class="sxs-lookup"><span data-stu-id="4d9d1-103">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="4d9d1-104">Atrybuty wyświetlania debugera umożliwiają deweloperom typu, którzy określają i najlepiej rozumieją zachowanie środowiska uruchomieniowego tego typu, aby określić, jaki typ będzie wyglądać, gdy zostanie on wyświetlony w debugerze.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-104">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="4d9d1-105">Dodatkowo debuger wyświetla atrybuty, które udostępniają `Target` Właściwość, można stosować na poziomie zestawu przez użytkowników bez znajomości kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-105">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="4d9d1-106">Ten <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut określa sposób wyświetlania typu lub elementu członkowskiego w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-106">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="4d9d1-107">Ten <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybut określa, czy i w jaki sposób pole lub właściwość są wyświetlane w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-107">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="4d9d1-108"><xref:System.Diagnostics.DebuggerTypeProxyAttribute>Atrybut określa typ substytutu lub serwer proxy dla typu i zmienia sposób wyświetlania typu w oknach debugera.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-108">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="4d9d1-109">Podczas wyświetlania zmiennej, która ma serwer proxy lub typ zastępczy, serwer proxy znajduje się dla oryginalnego typu w oknie wyświetlania debugera.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-109">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="4d9d1-110">W oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-110">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="4d9d1-111">Prywatne elementy członkowskie nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-111">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="4d9d1-112">Korzystanie z DebuggerDisplayAttribute —</span><span class="sxs-lookup"><span data-stu-id="4d9d1-112">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="4d9d1-113"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A>Konstruktor ma jeden argument: ciąg, który ma być wyświetlany w kolumnie wartości dla wystąpień typu.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-113">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="4d9d1-114">Ten ciąg może zawierać nawiasy klamrowe ({i}).</span><span class="sxs-lookup"><span data-stu-id="4d9d1-114">This string can contain braces ({ and }).</span></span> <span data-ttu-id="4d9d1-115">Tekst w parze nawiasów klamrowych jest obliczany jako wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-115">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="4d9d1-116">Na przykład poniższy kod w języku C# powoduje, że wartość "Count = 4" będzie wyświetlana po wybraniu znaku plus (+), aby rozwinąć debuger wyświetlany dla wystąpienia `MyHashtable` .</span><span class="sxs-lookup"><span data-stu-id="4d9d1-116">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="4d9d1-117">Atrybuty zastosowane do właściwości, do których odwołuje się wyrażenie, nie są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-117">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="4d9d1-118">W przypadku kompilatora języka C# wyrażenie ogólne jest dozwolone, które ma tylko niejawny dostęp do tego odwołania dla bieżącego wystąpienia typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-118">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="4d9d1-119">Wyrażenie jest ograniczone; nie ma dostępu do aliasów, zmiennych lokalnych ani wskaźników.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-119">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="4d9d1-120">W kodzie C# można użyć wyrażenia ogólnego między nawiasy klamrowe, które mają niejawny dostęp do `this` wskaźnika dla bieżącego wystąpienia tylko typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-120">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="4d9d1-121">Na przykład jeśli obiekt języka C# został przesłonięty `ToString()` , debuger wywoła przesłonięcie i pokaże jego wynik zamiast standardowego, w `{<typeName>}.` związku z tym, jeśli został zastąpiony `ToString()` , nie trzeba używać <xref:System.Diagnostics.DebuggerDisplayAttribute> .</span><span class="sxs-lookup"><span data-stu-id="4d9d1-121">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="4d9d1-122">Jeśli używasz obu tych metod, <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut ma pierwszeństwo przed `ToString()` przesłonięciem.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-122">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="4d9d1-123">Korzystanie z DebuggerBrowsableAttribute</span><span class="sxs-lookup"><span data-stu-id="4d9d1-123">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="4d9d1-124">Zastosuj <xref:System.Diagnostics.DebuggerBrowsableAttribute> do pola lub właściwości, aby określić, w jaki sposób pole lub właściwość mają być wyświetlane w oknie debugera.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-124">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="4d9d1-125">Konstruktor dla tego atrybutu przyjmuje jedną z <xref:System.Diagnostics.DebuggerBrowsableState> wartości wyliczenia, która określa jeden z następujących stanów:</span><span class="sxs-lookup"><span data-stu-id="4d9d1-125">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="4d9d1-126"><xref:System.Diagnostics.DebuggerBrowsableState.Never>wskazuje, że element członkowski nie jest wyświetlany w oknie dane.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-126"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="4d9d1-127">Na przykład użycie tej wartości dla <xref:System.Diagnostics.DebuggerBrowsableAttribute> pola w polu usuwa pole z hierarchii; pole nie jest wyświetlane po rozwinięciu typu otaczającego przez kliknięcie znaku plus (+) dla wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-127">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="4d9d1-128"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>wskazuje, że element członkowski jest wyświetlany, ale nie jest domyślnie rozwinięty.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-128"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="4d9d1-129">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-129">This is the default behavior.</span></span>

- <span data-ttu-id="4d9d1-130"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>wskazuje, że sama składowa nie jest wyświetlana, ale jego obiekty składowe są wyświetlane, jeśli jest tablicą lub kolekcją.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-130"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
> <span data-ttu-id="4d9d1-131">Program <xref:System.Diagnostics.DebuggerBrowsableAttribute> nie jest obsługiwany przez Visual Basic w .NET Framework wersja 2,0.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-131">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="4d9d1-132">Poniższy przykład kodu pokazuje użycie elementu, <xref:System.Diagnostics.DebuggerBrowsableAttribute> Aby zapobiec wyświetlaniu właściwości, która nie jest wyświetlana w oknie debugowania dla klasy.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-132">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="4d9d1-133">Korzystanie z DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="4d9d1-133">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="4d9d1-134">Użyj <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutu, gdy trzeba znacząco i w sposób istotny zmienić widok debugowania typu, ale nie zmieniać samego typu.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-134">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="4d9d1-135">Ten <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybut służy do określania serwera proxy dla typu, co umożliwia deweloperom Dostosowywanie widoku dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-135">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="4d9d1-136">Ten atrybut, podobnie jak <xref:System.Diagnostics.DebuggerDisplayAttribute> , może być używany na poziomie zestawu, w tym przypadku <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> Właściwość określa typ, dla którego zostanie użyty serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-136">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="4d9d1-137">Zalecane użycie polega na tym, że ten atrybut określa prywatny Typ zagnieżdżony, który występuje w typie, do którego zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-137">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="4d9d1-138">Ewaluatora wyrażeń, które obsługują osoby przeglądające typy sprawdzają ten atrybut, gdy zostanie wyświetlony typ.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-138">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="4d9d1-139">Jeśli atrybut zostanie znaleziony, ewaluatora wyrażeń zastępuje typ wyświetlanego serwera proxy dla typu, do którego zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-139">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="4d9d1-140">Gdy <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest obecny, w oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-140">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="4d9d1-141">Prywatne elementy członkowskie nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-141">Private members are not displayed.</span></span> <span data-ttu-id="4d9d1-142">Zachowanie okna dane nie jest zmieniane przez widoki z rozszerzonymi atrybutami.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-142">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="4d9d1-143">Aby uniknąć niepotrzebnych kar z wydajnością, atrybuty wyświetlanego serwera proxy nie są przetwarzane do momentu, gdy obiekt zostanie rozwinięty, przez kliknięcie przez użytkownika kliknięcia znaku plusa (+) obok typu w oknie danych lub za pomocą aplikacji <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-143">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="4d9d1-144">Dlatego zaleca się, aby nie stosować atrybutów do typu wyświetlanego.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-144">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="4d9d1-145">Atrybuty mogą i powinny być stosowane w treści typu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-145">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="4d9d1-146">Poniższy przykład kodu pokazuje użycie, <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Aby określić typ, który ma być używany jako serwer proxy wyświetlania debugera.</span><span class="sxs-lookup"><span data-stu-id="4d9d1-146">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

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

## <a name="example"></a><span data-ttu-id="4d9d1-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d9d1-147">Example</span></span>

### <a name="description"></a><span data-ttu-id="4d9d1-148">Opis</span><span class="sxs-lookup"><span data-stu-id="4d9d1-148">Description</span></span>

<span data-ttu-id="4d9d1-149">Poniższy przykład kodu można wyświetlić w programie Visual Studio, aby zobaczyć wyniki zastosowania <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybutów, i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> .</span><span class="sxs-lookup"><span data-stu-id="4d9d1-149">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="4d9d1-150">Kod</span><span class="sxs-lookup"><span data-stu-id="4d9d1-150">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="4d9d1-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d9d1-151">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
