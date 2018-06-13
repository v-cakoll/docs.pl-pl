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
ms.openlocfilehash: 2efa8cfb2b196d6f5a26354161e42c1f376e43b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389542"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="8fdb8-102">Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera</span><span class="sxs-lookup"><span data-stu-id="8fdb8-102">Enhancing Debugging with the Debugger Display Attributes</span></span>
<span data-ttu-id="8fdb8-103">Zezwalaj na wyświetlanie atrybutów debugera dewelopera typu, który określa i najlepiej rozumie zachowania w czasie wykonywania tego typu, można również określić, jakie tego typu będą wyglądać po wyświetleniu go w debugerze.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="8fdb8-104">Ponadto debuger wyświetlić atrybuty, które zapewniają `Target` właściwości można zastosować na poziomie zestawu przez użytkowników bez wiedzy o kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="8fdb8-105"><xref:System.Diagnostics.DebuggerDisplayAttribute> Atrybut kontroluje sposób wyświetlania typu lub elementu członkowskiego w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="8fdb8-106"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Atrybut określa, czy i jak pole lub właściwość jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="8fdb8-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut określa typu zastępczego lub serwer proxy dla typu i zmienia sposób typ jest wyświetlana w oknach debugera.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="8fdb8-108">Po wyświetleniu zmiennej, która jest serwer proxy lub typu zastępczego serwera proxy dla oryginalnego typu w okna debugera oznacza **.**</span><span class="sxs-lookup"><span data-stu-id="8fdb8-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window **.**</span></span> <span data-ttu-id="8fdb8-109">Wpisz windowdisplays zmiennych debugera tylko publiczne elementy członkowskie serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-109">The debugger variable windowdisplays only the public members of the proxy type.</span></span> <span data-ttu-id="8fdb8-110">Prywatne elementy członkowskie nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="8fdb8-111">Przy użyciu debuggerdisplayattribute —</span><span class="sxs-lookup"><span data-stu-id="8fdb8-111">Using the DebuggerDisplayAttribute</span></span>  
 <span data-ttu-id="8fdb8-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor ma jeden argument: ciąg mają być wyświetlane w kolumnie wartość dla wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="8fdb8-113">Ten ciąg może zawierać nawiasy klamrowe ({i}).</span><span class="sxs-lookup"><span data-stu-id="8fdb8-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="8fdb8-114">Tekst w parę nawiasów klamrowych jest szacowana jako wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="8fdb8-115">Na przykład następujący kod C# spowoduje "Count = 4" do wyświetlenia, gdy zaznaczona jest znak plus (+), aby rozwinąć debugera dla wystąpienia `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  
  
```csharp
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```
  
 <span data-ttu-id="8fdb8-116">Atrybuty stosowane do właściwości, do którego odwołuje się wyrażenie, które nie zostały przetworzone.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="8fdb8-117">Dla kompilatora C# ogólne wyrażenia jest dozwolone, który ma niejawne dostęp tylko do tego odwołania dla bieżącego wystąpienia typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="8fdb8-118">Wyrażenie jest ograniczona. Brak dostępu do aliasy, zmienne lokalne lub wskaźniki nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="8fdb8-119">W kodzie języka C#, można użyć ogólne wyrażenia w nawiasach klamrowych, które ma niejawny dostęp do `this` wskaźnika dla bieżącego wystąpienia tylko typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>  
  
 <span data-ttu-id="8fdb8-120">Na przykład, jeśli obiekt C# została zastąpiona `ToString()`, debuger wywoła zastąpienie i wyświetlić jej wynik, zamiast standardowego `{<typeName>}.` związku z tym, jeśli ma być zastąpiona `ToString()`, nie trzeba używać <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="8fdb8-121">Jeśli używasz zarówno <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut ma pierwszeństwo przed `ToString()` zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>  
  
## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="8fdb8-122">Przy użyciu debuggerbrowsableattribute —</span><span class="sxs-lookup"><span data-stu-id="8fdb8-122">Using the DebuggerBrowsableAttribute</span></span>  
 <span data-ttu-id="8fdb8-123">Zastosuj <xref:System.Diagnostics.DebuggerBrowsableAttribute> pola lub właściwości w celu określenia, jak pola lub właściwości ma być wyświetlany w oknie debugera.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="8fdb8-124">Konstruktor dla tego atrybutu przyjmuje jeden z <xref:System.Diagnostics.DebuggerBrowsableState> wartości wyliczenia, które określa jeden z następujących stanów:</span><span class="sxs-lookup"><span data-stu-id="8fdb8-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>  
  
-   <span data-ttu-id="8fdb8-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> Wskazuje, że element członkowski nie jest wyświetlany w oknie dane.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="8fdb8-126">Na przykład za pomocą tej wartości dla <xref:System.Diagnostics.DebuggerBrowsableAttribute> na pole usuwa pole z hierarchii; pole nie jest wyświetlany po rozwinięciu typu otaczającego, klikając znak plus (+) dla wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>  
  
-   <span data-ttu-id="8fdb8-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> Wskazuje, że element członkowski jest wyświetlane, ale nie jest domyślnie rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="8fdb8-128">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-128">This is the default behavior.</span></span>  
  
-   <span data-ttu-id="8fdb8-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> Wskazuje, że ten element członkowski nie jest widoczne, ale obiekty składowe są wyświetlane, gdy jest tablicą lub kolekcją.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fdb8-130"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Nie jest obsługiwana przez program Visual Basic w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="8fdb8-131">W poniższym przykładzie pokazano sposób użycia <xref:System.Diagnostics.DebuggerBrowsableAttribute> zapobiegające właściwości po znajdujących się w oknie debugowania dla klasy.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>  
  
```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="8fdb8-132">Przy użyciu DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="8fdb8-132">Using the DebuggerTypeProxy</span></span>  
 <span data-ttu-id="8fdb8-133">Użyj <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutu, gdy trzeba znacznie i całkowicie zmienić widok debugowania typu, lecz nie zmieniać samego typu.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="8fdb8-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut służy do określania wyświetlania serwera proxy dla typu, dzięki czemu Deweloper dostosować widok dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="8fdb8-135">Ten atrybut tak samo, jak <xref:System.Diagnostics.DebuggerDisplayAttribute>, można na poziomie zestawu, w którym to przypadku <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> właściwość określa typ, dla którego będzie można używać serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="8fdb8-136">Zalecane użycie jest, że ten atrybut określa prywatnej typu zagnieżdżonego w typie, do którego zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="8fdb8-137">Ewaluatora wyrażeń, aby obsługuje typ przeglądarki sprawdza dla tego atrybutu, gdy typem jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="8fdb8-138">Jeśli ten atrybut zostanie znaleziony, ewaluatora wyrażenia zastępuje wyświetlania typ serwera proxy dla ten atrybut jest stosowany do typu.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>  
  
 <span data-ttu-id="8fdb8-139">Gdy <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest obecny, okno zmiennych debugera zawiera tylko publiczne elementy członkowskie typu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="8fdb8-140">Prywatne elementy członkowskie nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-140">Private members are not displayed.</span></span> <span data-ttu-id="8fdb8-141">Zachowanie okna danych nie ulega zmianie przez rozszerzony atrybut widoki.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>  
  
 <span data-ttu-id="8fdb8-142">Aby uniknąć kar za niepotrzebne wydajności, atrybutów wyświetlania serwera proxy nie są przetwarzane aż obiekt jest rozwinięty przez użytkownika, klikając znak plus (+) obok typu w oknie danych lub poprzez zastosowanie <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="8fdb8-143">W związku z tym zaleca się, że atrybuty nie można zastosować do typu ekranu.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="8fdb8-144">Atrybuty można i powinny być stosowane w treści typu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-144">Attributes can and should be applied within the body of the display type.</span></span>  
  
 <span data-ttu-id="8fdb8-145">W poniższym przykładzie pokazano sposób użycia <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Aby określić typ ma być używany jako serwer proxy wyświetlania debugera.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="8fdb8-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="8fdb8-146">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8fdb8-147">Opis</span><span class="sxs-lookup"><span data-stu-id="8fdb8-147">Description</span></span>  
 <span data-ttu-id="8fdb8-148">Poniższy przykład kodu można wyświetlać w [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] aby zobaczyć wyniki zastosowania <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="8fdb8-148">The following code example can be viewed in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8fdb8-149">Kod</span><span class="sxs-lookup"><span data-stu-id="8fdb8-149">Code</span></span>  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8fdb8-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fdb8-150">See Also</span></span>  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
