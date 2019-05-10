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
ms.openlocfilehash: bd2f56f42bfe5ecce9357dbd2b483292d1736ec4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660464"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="07106-102">Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera</span><span class="sxs-lookup"><span data-stu-id="07106-102">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="07106-103">Atrybutów wyświetlania debugera umożliwia deweloperowi typu, który określa się oraz zrozumiał najlepiej zachowanie środowiska uruchomieniowego tego typu, można również określić, jakie tego typu będzie wyglądać po wyświetleniu go w debugerze.</span><span class="sxs-lookup"><span data-stu-id="07106-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="07106-104">Ponadto debuger wyświetlić atrybuty, które zapewniają `Target` właściwość może zostać zastosowana na poziomie zestawu przez użytkowników bez znajomości kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="07106-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="07106-105"><xref:System.Diagnostics.DebuggerDisplayAttribute> Atrybut kontroluje sposób wyświetlania typu lub elementu członkowskiego w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="07106-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="07106-106"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Atrybut określa, czy i jak pole lub właściwość jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="07106-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="07106-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut określa typu zastępczego lub serwera proxy dla typu i zmienia sposób typu jest wyświetlana w oknach debugera.</span><span class="sxs-lookup"><span data-stu-id="07106-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="07106-108">Po wyświetleniu zmiennej, która ma serwer proxy lub typu zastępczego oznacza serwera proxy oryginalnego typu w okna debugera.</span><span class="sxs-lookup"><span data-stu-id="07106-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="07106-109">W oknie zmiennych debugera zostaną wyświetlone tylko publiczne składowe typ serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="07106-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="07106-110">Prywatne elementy członkowskie nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="07106-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="07106-111">Za pomocą debuggerdisplayattribute —</span><span class="sxs-lookup"><span data-stu-id="07106-111">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="07106-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor ma jeden argument: ciąg, który ma być wyświetlana w kolumnie wartość dla wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="07106-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="07106-113">Ten ciąg może zawierać nawiasy klamrowe ({i}).</span><span class="sxs-lookup"><span data-stu-id="07106-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="07106-114">Tekst w parę nawiasów klamrowych jest oceniane jako wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="07106-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="07106-115">Na przykład, poniższy kod C# powoduje "liczba = 4" będzie wyświetlana po wybraniu znak plus (+), aby rozwinąć debugera dla wystąpienia `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="07106-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="07106-116">Atrybuty stosowane do właściwości, do którego odwołuje się wyrażenie nie są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="07106-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="07106-117">Dla kompilatora C# ogólnego wyrażenia jest dozwolone, który ma niejawne dostęp tylko do tego odwołania dla bieżącego wystąpienia typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="07106-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="07106-118">Wyrażenie jest ograniczona. Brak dostępu do aliasów, zmienne lokalne lub wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="07106-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="07106-119">W kodzie języka C#, można użyć wyrażenia ogólnych między nawiasy klamrowe, które ma niejawne dostęp do `this` wskaźnik dla bieżącego wystąpienia na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="07106-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="07106-120">Na przykład, jeśli obiekt C# została zastąpiona `ToString()`, debuger wywoła zastępowania i wyświetlić jego wynik zamiast standardowego `{<typeName>}.` Thus, jeśli zastępowano `ToString()`, nie trzeba używać <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="07106-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="07106-121">Jeśli używasz zarówno <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut ma pierwszeństwo przed `ToString()` zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="07106-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="07106-122">Za pomocą debuggerbrowsableattribute —</span><span class="sxs-lookup"><span data-stu-id="07106-122">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="07106-123">Zastosuj <xref:System.Diagnostics.DebuggerBrowsableAttribute> pola lub właściwości w celu określenia, jak pole lub właściwość ma być wyświetlana w oknie debugera.</span><span class="sxs-lookup"><span data-stu-id="07106-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="07106-124">Konstruktor dla tego atrybutu ma jedną z <xref:System.Diagnostics.DebuggerBrowsableState> wartości wyliczenia, które określa jedno z następujących stanów:</span><span class="sxs-lookup"><span data-stu-id="07106-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="07106-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> Wskazuje, że element członkowski nie jest wyświetlany w oknie dane.</span><span class="sxs-lookup"><span data-stu-id="07106-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="07106-126">Na przykład za pomocą tej wartości dla <xref:System.Diagnostics.DebuggerBrowsableAttribute> na pole usuwa pole z hierarchii; pole nie jest wyświetlane po rozwinięciu typ otaczający, klikając znak plus (+) dla wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="07106-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="07106-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> Wskazuje, że element członkowski jest wyświetlane, ale nie jest domyślnie rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="07106-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="07106-128">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="07106-128">This is the default behavior.</span></span>

- <span data-ttu-id="07106-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> Wskazuje, że ten element członkowski nie jest wyświetlana, ale obiekty składowe są wyświetlane w przypadku tablicy lub kolekcji.</span><span class="sxs-lookup"><span data-stu-id="07106-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
>  <span data-ttu-id="07106-130"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Nie jest obsługiwana przez program Visual Basic w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="07106-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="07106-131">Poniższy przykład kodu pokazuje użycie <xref:System.Diagnostics.DebuggerBrowsableAttribute> zapobiegające właściwość postępując znajdujących się w oknie Debugowanie dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="07106-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="07106-132">Za pomocą DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="07106-132">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="07106-133">Użyj <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutu, gdy trzeba znacznie i całkowicie zmienić widok debugowania typu, ale nie zmienianie samego typu.</span><span class="sxs-lookup"><span data-stu-id="07106-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="07106-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut jest używany do określenia wyświetlania serwera proxy dla typu, co zatem programistą, aby dostosować widok dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="07106-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="07106-135">Ten atrybut, takie jak <xref:System.Diagnostics.DebuggerDisplayAttribute>, może służyć na poziomie zestawu, w którym to przypadku <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> właściwość określa typ, dla której będzie używany serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="07106-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="07106-136">Zalecane użycie jest, że ten atrybut określa prywatnej typu zagnieżdżonego, występujący w przypadku typu jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="07106-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="07106-137">Ewaluatora wyrażeń, aby obsługuje typ osoby przeglądające sprawdza dla tego atrybutu, gdy typem jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="07106-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="07106-138">Jeśli ten atrybut zostanie znaleziony, Ewaluator wyrażeń zastępuje wyświetlaną typ serwera proxy dla typu, który jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="07106-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="07106-139">Gdy <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest obecny, w oknie zmiennych debugera, zostaną wyświetlone tylko publiczne składowe typ serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="07106-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="07106-140">Prywatne elementy członkowskie nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="07106-140">Private members are not displayed.</span></span> <span data-ttu-id="07106-141">Zachowanie okna danych nie jest zmieniany przy użyciu funkcji widoków rozszerzonych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="07106-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="07106-142">Aby uniknąć spadku wydajności niepotrzebne, atrybutów wyświetlania serwera proxy nie zostały przetworzone, dopóki obiekt jest rozwinięta, przez użytkownika, klikając znak plus (+) obok typu w oknie danych lub przez zastosowanie <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="07106-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="07106-143">W związku z tym zaleca się, że żadne atrybuty można zastosować do typu ekranu.</span><span class="sxs-lookup"><span data-stu-id="07106-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="07106-144">Atrybuty można i powinny być stosowane w ramach organu typ wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="07106-144">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="07106-145">Poniższy przykład kodu pokazuje użycie <xref:System.Diagnostics.DebuggerTypeProxyAttribute> do określania typu ma być używany jako serwer proxy wyświetlania debugera.</span><span class="sxs-lookup"><span data-stu-id="07106-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

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

## <a name="example"></a><span data-ttu-id="07106-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="07106-146">Example</span></span>

### <a name="description"></a><span data-ttu-id="07106-147">Opis</span><span class="sxs-lookup"><span data-stu-id="07106-147">Description</span></span>

<span data-ttu-id="07106-148">Poniższy przykład kodu mogą być wyświetlane w programie Visual Studio, aby zobaczyć wyniki zastosowania <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="07106-148">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="07106-149">Kod</span><span class="sxs-lookup"><span data-stu-id="07106-149">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="07106-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07106-150">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>