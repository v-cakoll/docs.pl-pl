---
title: Odwołania do elementów zadeklarowanych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 18f9920891e35517efe7adcfd4c03e03ac771478
ms.sourcegitcommit: 875ecc3ab2437e299b1d50076bd9b878fa8c64de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43238540"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="ebff9-102">Odwołania do elementów zadeklarowanych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebff9-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="ebff9-103">Gdy kod odwołuje się do element zadeklarowany, kompilator Visual Basic pasuje do nazwy, w której można się odwołać do odpowiedniego zgłoszenia o takiej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ebff9-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="ebff9-104">Jeśli więcej niż jeden element jest zadeklarowana za pomocą tej samej nazwie, możesz kontrolować, które z tych elementów ma być przywoływane przez *kwalifikacji* jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="ebff9-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="ebff9-105">Kompilator podejmuje próbę dopasowania nazwy odwołania do deklaracji nazwy z *najwęższego zakresu*.</span><span class="sxs-lookup"><span data-stu-id="ebff9-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="ebff9-106">Oznacza to, rozpoczyna się od kodu, dzięki czemu odwołania i postępuje na zewnątrz do kolejnych poziomów zawierający elementy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="ebff9-107">Poniższy przykład pokazuje odwołania do dwóch zmiennych o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ebff9-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="ebff9-108">Przykład deklaruje dwie zmienne, każdy o nazwie `totalCount`, na różnych poziomach zakresu w module `container`.</span><span class="sxs-lookup"><span data-stu-id="ebff9-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="ebff9-109">Podczas procedury `showCount` Wyświetla `totalCount` bez kwalifikacji, kompilator Visual Basic jest rozpoznawana jako odwołanie do deklaracji z najwęższego zakresu, to znaczy lokalna deklaracja wewnątrz `showCount`.</span><span class="sxs-lookup"><span data-stu-id="ebff9-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="ebff9-110">Gdy kwalifikuje się `totalCount` za pomocą modułu zawierającego `container`, kompilator rozwiązuje odwołanie do deklaracji w szerszym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ebff9-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="ebff9-111">Kwalifikujące się nazwę elementu</span><span class="sxs-lookup"><span data-stu-id="ebff9-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="ebff9-112">Jeśli chcesz zastąpić ten proces wyszukiwania i określić, nazwa zadeklarowana w szerszym zakresie, należy najpierw *kwalifikowania* nazwą zawierającego element szerszy zakres.</span><span class="sxs-lookup"><span data-stu-id="ebff9-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="ebff9-113">W niektórych przypadkach może również być kwalifikuj element zawierający.</span><span class="sxs-lookup"><span data-stu-id="ebff9-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="ebff9-114">Kwalifikowanie oznacza nazwę poprzedzających je w instrukcji źródła informacje określające, w którym definiowany jest element docelowy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="ebff9-115">Informacja ta jest wywoływana *ciąg kwalifikacji*.</span><span class="sxs-lookup"><span data-stu-id="ebff9-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="ebff9-116">Może zawierać jeden lub więcej przestrzeni nazw i modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ebff9-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="ebff9-117">Ciąg kwalifikacji jednoznacznie określić modułu, klasy lub struktury zawierającej element docelowy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="ebff9-118">Kontener z kolei może znajdować się w innym elemencie zawierającego zazwyczaj przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="ebff9-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="ebff9-119">Może być konieczne obejmują kilka zawierający elementy w ciągu kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="ebff9-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="ebff9-120">Dostęp kwalifikowania nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="ebff9-120">To access a declared element by qualifying its name</span></span>  
  
1.  <span data-ttu-id="ebff9-121">Określ lokalizację, w którym zdefiniowano element.</span><span class="sxs-lookup"><span data-stu-id="ebff9-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="ebff9-122">Może to obejmować przestrzeni nazw lub nawet hierarchię przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ebff9-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="ebff9-123">W obszarze nazw najniższy poziom elementu muszą być zawarte w module, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ebff9-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  <span data-ttu-id="ebff9-124">Określ ścieżkę kwalifikacji, na podstawie lokalizacji elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ebff9-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="ebff9-125">Uruchom z przestrzenią nazw najwyższego poziomu, przejdź do obszaru nazw najniższy poziom, a kończyć się znakiem modułu, klasy lub struktury zawierającej element docelowy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="ebff9-126">Każdy element w ścieżce musi zawierać element, który po nim następuje.</span><span class="sxs-lookup"><span data-stu-id="ebff9-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="ebff9-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="ebff9-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3.  <span data-ttu-id="ebff9-128">Przygotowanie ciągu kwalifikacji do elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ebff9-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="ebff9-129">Umieść okres (`.`) po każdego elementu w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="ebff9-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="ebff9-130">Aplikacja musi mieć dostęp do każdego elementu w ciągu kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="ebff9-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  <span data-ttu-id="ebff9-131">Napisz wyrażenie lub instrukcję przypisania odwołujące się do elementu docelowego w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="ebff9-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  <span data-ttu-id="ebff9-132">Poprzedź nazwę elementu docelowego przy użyciu parametrów kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="ebff9-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="ebff9-133">Nazwę należy natychmiast po kropce (`.`) następujący modułu, klasy lub struktury, który zawiera element.</span><span class="sxs-lookup"><span data-stu-id="ebff9-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="ebff9-134">Kompilator używa ciągu kwalifikacji, aby znaleźć Wyczyść, jednoznaczną deklaracji, do którego może odnosić odwołanie do elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ebff9-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="ebff9-135">Może być również konieczne kwalifikują się odwołania do nazwy, jeśli aplikacja ma dostęp do więcej niż jeden element programowania, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="ebff9-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="ebff9-136">Na przykład <xref:System.Windows.Forms> i <xref:System.Web.UI.WebControls> przestrzenie nazw obu zawierają `Label` klasy (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> i <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="ebff9-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="ebff9-137">Jeśli aplikacja korzysta z obu lub definiuje swój własny `Label` klasy, należy odróżnić poszczególne `Label` obiektów.</span><span class="sxs-lookup"><span data-stu-id="ebff9-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="ebff9-138">Uwzględnij aliasu przestrzeni nazw lub importu w deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ebff9-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="ebff9-139">W poniższym przykładzie użyto aliasu importu.</span><span class="sxs-lookup"><span data-stu-id="ebff9-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="ebff9-140">Inne elementy zawierające elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ebff9-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="ebff9-141">Gdy używasz nieudostępnionych członkiem innej klasy lub struktury, należy najpierw kwalifikujesz się do nazwy elementu członkowskiego za pomocą zmiennej lub wyrażenia, który wskazuje na wystąpienie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ebff9-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="ebff9-142">W poniższym przykładzie `demoClass` jest wystąpieniem klasy o nazwie `class1`.</span><span class="sxs-lookup"><span data-stu-id="ebff9-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="ebff9-143">Sama nazwa klasy nie można użyć, aby zakwalifikować się elementu członkowskiego, który nie jest [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="ebff9-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="ebff9-144">Należy najpierw utworzyć wystąpienia w zmiennej obiektu (w tym przypadku `demoClass`), a następnie Odwołaj przez nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ebff9-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="ebff9-145">Jeśli klasa lub struktura ma `Shared` elementu członkowskiego, może kwalifikujesz się do tego elementu członkowskiego o nazwie klasy lub struktury lub za pomocą zmiennej lub wyrażenia, który wskazuje na wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="ebff9-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="ebff9-146">Moduł nie ma wszelkie osobnych wystąpień, a jej elementy członkowskie są `Shared` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="ebff9-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="ebff9-147">W związku z tym kwalifikujesz się do członka modułu z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="ebff9-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="ebff9-148">Poniższy przykład pokazuje kwalifikowanego odwołania do procedur element członkowski modułu.</span><span class="sxs-lookup"><span data-stu-id="ebff9-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="ebff9-149">Przykład deklaruje dwie `Sub` procedur, o nazwie `perform`, w różnych modułach w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ebff9-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="ebff9-150">Każdy z nich mogą zostać określone bez kwalifikacji w ramach własnego modułu, ale musi być kwalifikowana, jeśli przywoływane z dowolnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="ebff9-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="ebff9-151">Ponieważ końcowe odwoływać w `module3` nie kwalifikuje się `perform`, kompilator nie można rozpoznać tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="ebff9-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="ebff9-152">Odwołania do projektów</span><span class="sxs-lookup"><span data-stu-id="ebff9-152">References to Projects</span></span>  
 <span data-ttu-id="ebff9-153">Do użycia [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) elementy zdefiniowane w innym projekcie, należy najpierw ustawić *odwołania* do tego projektu zestawu lub biblioteka typów.</span><span class="sxs-lookup"><span data-stu-id="ebff9-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="ebff9-154">Aby ustawić odwołanie, kliknij **Dodaj odwołanie** na **projektu** menu lub użyj [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebff9-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="ebff9-155">Na przykład, można użyć modelu obiektów XML z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ebff9-155">For example, you can use the XML object model of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="ebff9-156">Jeśli odwołanie jest ustawiona na <xref:System.Xml> przestrzeni nazw, można zadeklarować i użyć dowolnego z jego klas, takie jak <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="ebff9-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="ebff9-157">W poniższym przykładzie użyto <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="ebff9-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="ebff9-158">Importowanie zawierający elementy</span><span class="sxs-lookup"><span data-stu-id="ebff9-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="ebff9-159">Możesz użyć [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do *zaimportować* przestrzenie nazw, które zawierają moduły lub klasy, które chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="ebff9-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="ebff9-160">Dzięki temu można odwoływać się do elementów zdefiniowanych w importowanych przestrzeni nazw bez w pełni kwalifikowania ich nazwy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="ebff9-161">Poniższy przykład ponownie zapisuje poprzedniego przykładu, aby zaimportować <xref:System.Xml> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ebff9-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="ebff9-162">Ponadto `Imports` instrukcji można zdefiniować *zaimportować alias* dla każdej importowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ebff9-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="ebff9-163">Dzięki temu może być krótsze i bardziej czytelny kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="ebff9-164">Poniższy przykład ponownie zapisuje poprzedniego przykładu, aby użyć `xD` jako alias <xref:System.Xml> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ebff9-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="ebff9-165">`Imports` Instrukcji nie udostępnia elementy z innych projektów do swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebff9-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="ebff9-166">Oznacza to, że nie przyjmuje miejsce odwołanie do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="ebff9-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="ebff9-167">Importowanie przestrzeni nazw, po prostu usuwa wymaganie, aby kwalifikowania nazwy zdefiniowane w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ebff9-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="ebff9-168">Można również użyć `Imports` instrukcję, aby zaimportować moduły, klasy, struktury i wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ebff9-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="ebff9-169">Następnie można użyć elementów członkowskich takich zaimportowane elementy bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="ebff9-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="ebff9-170">Jednak zawsze musi kwalifikować nieudostępnionych członków klasy i struktury za pomocą zmiennej lub wyrażenia, które ocenia do wystąpienia klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ebff9-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="ebff9-171">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="ebff9-171">Naming Guidelines</span></span>  
 <span data-ttu-id="ebff9-172">Po zdefiniowaniu dwóch lub więcej elementów programowania, które mają taką samą nazwę *nazwę niejednoznaczności* może spowodować, gdy kompilator próbuje rozpoznać odwołania do tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="ebff9-173">Jeśli więcej niż jedną definicję znajduje się w zakresie lub Brak definicji znajduje się w zakresie, odwołanie jest nierozwiązywalny.</span><span class="sxs-lookup"><span data-stu-id="ebff9-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="ebff9-174">Aby uzyskać przykład zobacz "Przykład kwalifikowana" na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="ebff9-175">Aby uniknąć niejednoznaczności, należy zapewniając wszystkie swoje elementy unikatowe nazwy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="ebff9-176">Następnie można tworzyć odwołania do dowolnego elementu bez potrzeby kwalifikowania nazwy przestrzeni nazw, modułu lub klasy.</span><span class="sxs-lookup"><span data-stu-id="ebff9-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="ebff9-177">Możesz też zmniejszyć prawdopodobieństwo przypadkowego odwołujące się do niewłaściwej elementu.</span><span class="sxs-lookup"><span data-stu-id="ebff9-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="ebff9-178">Przesłanianie</span><span class="sxs-lookup"><span data-stu-id="ebff9-178">Shadowing</span></span>  
 <span data-ttu-id="ebff9-179">Gdy dwa elementy programowania mają taką samą nazwę, jeden z nich można ukryć, lub *w tle*, jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="ebff9-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="ebff9-180">Tekst z cieniem element nie jest dostępne do użytku; Zamiast tego po kodzie używa nazwy elementu zasłonięte, kompilator Visual Basic jest rozpoznawany jako jego przesłaniania elementu.</span><span class="sxs-lookup"><span data-stu-id="ebff9-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="ebff9-181">Aby uzyskać bardziej szczegółowy opis wraz z przykładami, zobacz [przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="ebff9-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebff9-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebff9-182">See Also</span></span>  
 [<span data-ttu-id="ebff9-183">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="ebff9-183">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="ebff9-184">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="ebff9-184">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="ebff9-185">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ebff9-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="ebff9-186">Zmienne</span><span class="sxs-lookup"><span data-stu-id="ebff9-186">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="ebff9-187">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="ebff9-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="ebff9-188">Operator New</span><span class="sxs-lookup"><span data-stu-id="ebff9-188">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="ebff9-189">Public</span><span class="sxs-lookup"><span data-stu-id="ebff9-189">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
