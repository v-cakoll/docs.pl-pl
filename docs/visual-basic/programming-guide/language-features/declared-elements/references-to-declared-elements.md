---
title: Odwołania do elementów zadeklarowanych
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: a6477a9f0abaf8eb9176f4f6ab2a920af6c8f500
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345303"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="3ae14-102">Odwołania do elementów zadeklarowanych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ae14-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="3ae14-103">Gdy kod odwołuje się do zadeklarowanego elementu, kompilator Visual Basic dopasowuje nazwę w odwołaniu do odpowiedniej deklaracji tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3ae14-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="3ae14-104">Jeśli jest zadeklarowany więcej niż jeden element o tej samej nazwie, można kontrolować, które z tych elementów mają być przywoływane przez *zakwalifikowanie* jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="3ae14-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="3ae14-105">Kompilator próbuje dopasować odwołanie do nazwy do deklaracji nazwy z *najwęższym zakresem*.</span><span class="sxs-lookup"><span data-stu-id="3ae14-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="3ae14-106">Oznacza to, że zaczyna się od kodu, który wprowadza odwołanie i działa na zewnątrz przez kolejne poziomy zawierające elementy.</span><span class="sxs-lookup"><span data-stu-id="3ae14-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="3ae14-107">Poniższy przykład przedstawia odwołania do dwóch zmiennych o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3ae14-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="3ae14-108">Przykład deklaruje dwie zmienne, z których każda o nazwie `totalCount`, na różnych poziomach zakresu w `container`modułu.</span><span class="sxs-lookup"><span data-stu-id="3ae14-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="3ae14-109">Gdy procedura `showCount` wyświetla `totalCount` bez kwalifikacji, kompilator Visual Basic rozpoznaje odwołanie do deklaracji z najwęższym zakresem, a mianowicie lokalną deklarację w `showCount`.</span><span class="sxs-lookup"><span data-stu-id="3ae14-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="3ae14-110">Gdy kwalifikuje `totalCount` z `container`modułu, kompilator rozpoznaje odwołanie do deklaracji z szerszym zakresem.</span><span class="sxs-lookup"><span data-stu-id="3ae14-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
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
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="3ae14-111">Kwalifikowanie nazwy elementu</span><span class="sxs-lookup"><span data-stu-id="3ae14-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="3ae14-112">Jeśli chcesz przesłonić ten proces wyszukiwania i określić nazwę zadeklarowaną w szerszym zakresie, musisz *zakwalifikować* nazwę z elementem zawierającym szerszy zakres.</span><span class="sxs-lookup"><span data-stu-id="3ae14-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="3ae14-113">W niektórych przypadkach może być również konieczne zakwalifikowanie elementu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="3ae14-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="3ae14-114">Kwalifikowanie nazwy oznacza poprzedzające ją w instrukcji źródłowej informacjami, które identyfikują, gdzie jest zdefiniowany element docelowy.</span><span class="sxs-lookup"><span data-stu-id="3ae14-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="3ae14-115">Te informacje są nazywane *ciągiem kwalifikacji*.</span><span class="sxs-lookup"><span data-stu-id="3ae14-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="3ae14-116">Może zawierać co najmniej jedną przestrzeń nazw oraz moduł, klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="3ae14-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="3ae14-117">Ciąg kwalifikacji powinien jednoznacznie określać moduł, klasę lub strukturę zawierające element docelowy.</span><span class="sxs-lookup"><span data-stu-id="3ae14-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="3ae14-118">Kontener może być umieszczony w innym elemencie zawierającym, zazwyczaj przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ae14-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="3ae14-119">Może być konieczne dołączenie do ciągu kwalifikacji kilku elementów zawierających elementy.</span><span class="sxs-lookup"><span data-stu-id="3ae14-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="3ae14-120">Aby uzyskać dostęp do zadeklarowanego elementu przez zakwalifikowanie jego nazwy</span><span class="sxs-lookup"><span data-stu-id="3ae14-120">To access a declared element by qualifying its name</span></span>  
  
1. <span data-ttu-id="3ae14-121">Określ lokalizację, w której element został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="3ae14-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="3ae14-122">Może to obejmować przestrzeń nazw, a nawet hierarchię przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ae14-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="3ae14-123">W przestrzeni nazw najniższego poziomu element musi być zawarty w module, klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="3ae14-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
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
  
2. <span data-ttu-id="3ae14-124">Określ ścieżkę kwalifikacyjną na podstawie lokalizacji elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3ae14-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="3ae14-125">Zacznij od przestrzeni nazw najwyższego poziomu, Kontynuuj do przestrzeni nazw najniższego poziomu i kończyć się modułem, klasą lub strukturą zawierającą element docelowy.</span><span class="sxs-lookup"><span data-stu-id="3ae14-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="3ae14-126">Każdy element w ścieżce musi zawierać element, który następuje po nim.</span><span class="sxs-lookup"><span data-stu-id="3ae14-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="3ae14-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="3ae14-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3. <span data-ttu-id="3ae14-128">Przygotuj ciąg kwalifikacji dla elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3ae14-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="3ae14-129">Umieść kropkę (`.`) po każdym elemencie w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="3ae14-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="3ae14-130">Aplikacja musi mieć dostęp do każdego elementu w ciągu kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="3ae14-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. <span data-ttu-id="3ae14-131">Napisz wyrażenie lub instrukcję przypisania odwołującą się do elementu docelowego w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="3ae14-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. <span data-ttu-id="3ae14-132">Poprzedź nazwę elementu docelowego ciągiem kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="3ae14-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="3ae14-133">Nazwa powinna natychmiast podążać za kropką (`.`), która następuje po module, klasie lub strukturze zawierającej element.</span><span class="sxs-lookup"><span data-stu-id="3ae14-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. <span data-ttu-id="3ae14-134">Kompilator używa ciągu kwalifikacji do znalezienia jasnej, jednoznacznej deklaracji, do której może być zgodny z odwołaniem do elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3ae14-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="3ae14-135">Może być również konieczne zakwalifikowanie odwołania do nazwy, jeśli aplikacja ma dostęp do więcej niż jednego elementu programistycznego, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="3ae14-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="3ae14-136">Na przykład przestrzenie nazw <xref:System.Windows.Forms> i <xref:System.Web.UI.WebControls> zawierają klasy `Label` (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> i <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="3ae14-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="3ae14-137">Jeśli aplikacja używa obu, lub jeśli definiuje własną klasę `Label`, należy rozróżnić różne obiekty `Label`.</span><span class="sxs-lookup"><span data-stu-id="3ae14-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="3ae14-138">Uwzględnij przestrzeń nazw lub zaimportuj alias w deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3ae14-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="3ae14-139">Poniższy przykład używa aliasu importu.</span><span class="sxs-lookup"><span data-stu-id="3ae14-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="3ae14-140">Elementy członkowskie innych zawierających elementy</span><span class="sxs-lookup"><span data-stu-id="3ae14-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="3ae14-141">W przypadku korzystania z nieudostępnionej składowej innej klasy lub struktury, należy najpierw zakwalifikować nazwę składowej ze zmienną lub wyrażeniem, które wskazuje na wystąpienie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="3ae14-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="3ae14-142">W poniższym przykładzie `demoClass` jest wystąpieniem klasy o nazwie `class1`.</span><span class="sxs-lookup"><span data-stu-id="3ae14-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="3ae14-143">Nie można użyć samej nazwy klasy do kwalifikowania elementu członkowskiego, który nie jest [udostępniany](../../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="3ae14-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="3ae14-144">Najpierw należy utworzyć wystąpienie w zmiennej obiektu (w tym przypadku `demoClass`), a następnie odwołać się do niego przy użyciu nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3ae14-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="3ae14-145">Jeśli klasa lub struktura ma `Shared` składową, można kwalifikować tę składową przy użyciu nazwy klasy lub struktury lub ze zmienną lub wyrażeniem, które wskazuje na wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="3ae14-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="3ae14-146">Moduł nie ma żadnych oddzielnych wystąpień, a wszystkie jego elementy członkowskie są domyślnie `Shared`.</span><span class="sxs-lookup"><span data-stu-id="3ae14-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="3ae14-147">W związku z tym należy zakwalifikować element członkowski modułu przy użyciu nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="3ae14-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="3ae14-148">Poniższy przykład przedstawia kwalifikowane odwołania do procedur składowych modułu.</span><span class="sxs-lookup"><span data-stu-id="3ae14-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="3ae14-149">Przykład deklaruje dwie `Sub` procedury, zarówno nazwane `perform`, w różnych modułach w projekcie.</span><span class="sxs-lookup"><span data-stu-id="3ae14-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="3ae14-150">Każdą z nich można określić bez kwalifikacji w ramach własnego modułu, ale musi być kwalifikowana, jeśli istnieje odwołanie z dowolnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="3ae14-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="3ae14-151">Ponieważ ostateczne odwołanie w `module3` nie kwalifikuje się `perform`, kompilator nie może rozpoznać tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="3ae14-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
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
  
## <a name="references-to-projects"></a><span data-ttu-id="3ae14-152">Odwołania do projektów</span><span class="sxs-lookup"><span data-stu-id="3ae14-152">References to Projects</span></span>  
 <span data-ttu-id="3ae14-153">Aby użyć elementów [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) zdefiniowanych w innym projekcie, należy najpierw ustawić *odwołanie* do zestawu lub biblioteki typów tego projektu.</span><span class="sxs-lookup"><span data-stu-id="3ae14-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="3ae14-154">Aby ustawić odwołanie, kliknij opcję **Dodaj odwołanie** w menu **projekt** lub użyj opcji kompilatora wiersza polecenia [-Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) .</span><span class="sxs-lookup"><span data-stu-id="3ae14-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [-reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="3ae14-155">Na przykład można użyć modelu obiektów XML .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ae14-155">For example, you can use the XML object model of the .NET Framework.</span></span> <span data-ttu-id="3ae14-156">Jeśli ustawisz odwołanie do przestrzeni nazw <xref:System.Xml>, możesz zadeklarować i użyć dowolnej z jej klas, takich jak <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3ae14-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="3ae14-157">Poniższy przykład używa <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3ae14-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="3ae14-158">Importowanie zawierających elementy</span><span class="sxs-lookup"><span data-stu-id="3ae14-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="3ae14-159">Aby *zaimportować* przestrzenie nazw zawierające moduły lub klasy, które mają być używane, można użyć [instrukcji Imports (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) .</span><span class="sxs-lookup"><span data-stu-id="3ae14-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="3ae14-160">Dzięki temu można odwołać się do elementów zdefiniowanych w importowanym obszarze nazw bez w pełni kwalifikujących się nazw.</span><span class="sxs-lookup"><span data-stu-id="3ae14-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="3ae14-161">Poniższy przykład zapisuje ponownie poprzedni przykład, aby zaimportować przestrzeń nazw <xref:System.Xml>.</span><span class="sxs-lookup"><span data-stu-id="3ae14-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="3ae14-162">Ponadto instrukcja `Imports` może definiować *alias importu* dla każdej zaimportowanej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ae14-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="3ae14-163">Może to spowodować, że kod źródłowy jest krótszy i łatwiejszy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="3ae14-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="3ae14-164">Poniższy przykład zapisuje ponownie poprzedni przykład, aby użyć `xD` jako aliasu dla <xref:System.Xml> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ae14-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="3ae14-165">Instrukcja `Imports` nie sprawia, że elementy z innych projektów są dostępne dla Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3ae14-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="3ae14-166">Oznacza to, że nie ma miejsca na ustawienie odwołania.</span><span class="sxs-lookup"><span data-stu-id="3ae14-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="3ae14-167">Importowanie przestrzeni nazw powoduje jedynie usunięcie wymagania, aby kwalifikować się do nazw zdefiniowanych w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ae14-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="3ae14-168">Można również użyć instrukcji `Imports`, aby zaimportować moduły, klasy, struktury i wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3ae14-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="3ae14-169">Następnie można użyć elementów członkowskich takich zaimportowanych elementów bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="3ae14-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="3ae14-170">Należy jednak zawsze kwalifikować nieudostępniane elementy członkowskie klas i struktur z zmienną lub wyrażeniem, które oblicza wystąpienie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="3ae14-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="3ae14-171">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="3ae14-171">Naming Guidelines</span></span>  
 <span data-ttu-id="3ae14-172">Po zdefiniowaniu co najmniej dwóch elementów programistycznych, które mają taką samą nazwę, *niejednoznaczność* może wynikać z tego, kiedy kompilator próbuje rozpoznać odwołanie do tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3ae14-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="3ae14-173">Jeśli więcej niż jedna definicja znajduje się w zakresie lub jeśli żadna definicja nie należy do zakresu, odwołanie jest nierozwiązywalny.</span><span class="sxs-lookup"><span data-stu-id="3ae14-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="3ae14-174">Aby zapoznać się z przykładem, zobacz sekcję dotyczącą przykładowego odwołania na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="3ae14-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="3ae14-175">Można uniknąć niejednoznaczności nazwy, dając wszystkie elementy unikatowymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="3ae14-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="3ae14-176">Następnie można utworzyć odwołanie do dowolnego elementu bez konieczności kwalifikowania jego nazwy z przestrzenią nazw, modułem lub klasą.</span><span class="sxs-lookup"><span data-stu-id="3ae14-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="3ae14-177">Zmniejszamy również szanse przypadkowego odwołującego się do niewłaściwego elementu.</span><span class="sxs-lookup"><span data-stu-id="3ae14-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="3ae14-178">Zasłanianie</span><span class="sxs-lookup"><span data-stu-id="3ae14-178">Shadowing</span></span>  
 <span data-ttu-id="3ae14-179">Gdy dwa elementy programistyczne współdzielą tę samą nazwę, jeden z nich może ukryć lub *Zacień*, drugi.</span><span class="sxs-lookup"><span data-stu-id="3ae14-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="3ae14-180">Element z cieniem nie jest dostępny dla celów referencyjnych. Zamiast tego, gdy kod używa zasłoniętej nazwy elementu, kompilator Visual Basic rozpoznaje ją jako element przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="3ae14-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="3ae14-181">Aby uzyskać bardziej szczegółowe wyjaśnienie z przykładami, zobacz [przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="3ae14-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae14-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ae14-182">See also</span></span>

- [<span data-ttu-id="3ae14-183">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="3ae14-183">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="3ae14-184">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="3ae14-184">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="3ae14-185">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="3ae14-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="3ae14-186">Zmienne</span><span class="sxs-lookup"><span data-stu-id="3ae14-186">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="3ae14-187">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="3ae14-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="3ae14-188">Operator New</span><span class="sxs-lookup"><span data-stu-id="3ae14-188">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="3ae14-189">Public</span><span class="sxs-lookup"><span data-stu-id="3ae14-189">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
