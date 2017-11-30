---
title: "My.Forms — Obiekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5aa7af1f07a29660335d968c1ecc17be5f8beec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="myforms-object"></a><span data-ttu-id="99813-102">My.Forms — Obiekt</span><span class="sxs-lookup"><span data-stu-id="99813-102">My.Forms Object</span></span>
<span data-ttu-id="99813-103">Dostarcza właściwości, aby uzyskać dostęp do wystąpienia każdego formularza systemu Windows zadeklarowana w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="99813-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99813-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99813-104">Remarks</span></span>  
 <span data-ttu-id="99813-105">`My.Forms` Obiektu zawiera wystąpienie każdego formularza w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="99813-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="99813-106">Nazwa właściwości jest taka sama jak nazwa formularza, który uzyskuje dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="99813-106">The name of the property is the same as the name of the form that the property accesses.</span></span> <span data-ttu-id="99813-107">Uzyskać informacji o dodawaniu formularzy do projektu, zobacz [porady: dodawanie formularzy systemu Windows z projektem](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="99813-107">For information about adding forms to a project, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="99813-108">Dostęp można uzyskać formularzy dostarczonych przez `My.Forms` obiektu przy użyciu nazwy w postaci bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="99813-108">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="99813-109">Nazwa właściwości jest taka sama jak nazwa typu formularza, to umożliwia dostęp do formularza tak, jakby zawierał wystąpienia domyślnego.</span><span class="sxs-lookup"><span data-stu-id="99813-109">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="99813-110">Na przykład `My.Forms.Form1.Show` jest odpowiednikiem `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="99813-110">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="99813-111">`My.Forms` Obiekt ujawnia tylko do formularzy, które są skojarzone z bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="99813-111">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="99813-112">Nie ma dostępu do formularzy zadeklarowany w przywoływane biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="99813-112">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="99813-113">Aby uzyskać dostęp do formularza, który udostępnia bibliotekę DLL, należy użyć nazwa kwalifikowana w postaci zapisywane jako *DllName*. *Nazwa formularza*.</span><span class="sxs-lookup"><span data-stu-id="99813-113">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="99813-114">Można użyć <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> właściwości do pobrania kolekcja formularzy otwartych wszystkich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99813-114">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="99813-115">Obiekt i jego właściwości są dostępne tylko dla aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="99813-115">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="99813-116">Właściwości</span><span class="sxs-lookup"><span data-stu-id="99813-116">Properties</span></span>  
 <span data-ttu-id="99813-117">Każda właściwość `My.Forms` obiektu zapewnia dostęp do wystąpienia formularza w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="99813-117">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="99813-118">Nazwa właściwości jest taka sama jak nazwa formularza, który uzyskuje dostęp do właściwości, a typ właściwości jest taki sam jak typ formularza.</span><span class="sxs-lookup"><span data-stu-id="99813-118">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99813-119">W przypadku kolizję nazw, nazwę właściwości, aby przejść do formularza jest *RootNamespace*_*Namespace*\_*nazwa formularza*.</span><span class="sxs-lookup"><span data-stu-id="99813-119">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="99813-120">Rozważmy na przykład dwie formy o nazwie `Form1.`Jeśli jeden z nich jest w głównej przestrzeni nazw `WindowsApplication1` i w przestrzeni nazw `Namespace1`, czy dostęp do tego formularza za pomocą `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="99813-120">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="99813-121">`My.Forms` Obiekt zapewnia dostęp do wystąpienia aplikacji formularz główny, który został utworzony podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="99813-121">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="99813-122">Dla wszystkich innych formularzy `My.Forms` obiektu tworzy nowe wystąpienie formularza, gdy jest dostępny i zapisuje go.</span><span class="sxs-lookup"><span data-stu-id="99813-122">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="99813-123">Kolejne próby dostęp do tej właściwości zwrócenie tego wystąpienia formularza.</span><span class="sxs-lookup"><span data-stu-id="99813-123">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="99813-124">Można zlikwidować formularza, przypisując `Nothing` do właściwości dla tego formularza.</span><span class="sxs-lookup"><span data-stu-id="99813-124">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="99813-125">Wywołania metody ustawiającej właściwość <xref:System.Windows.Forms.Form.Close%2A> metody formularza, a następnie przypisuje `Nothing` przechowywanej wartości.</span><span class="sxs-lookup"><span data-stu-id="99813-125">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="99813-126">Po przypisaniu wartości inne niż `Nothing` do właściwości metody ustawiającej zgłasza <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="99813-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="99813-127">Można sprawdzić, czy właściwość `My.Forms` obiekt przechowuje wystąpienia formularza za pomocą `Is` lub `IsNot` operatora.</span><span class="sxs-lookup"><span data-stu-id="99813-127">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="99813-128">Te operatory można użyć do sprawdzenia, czy wartość właściwości jest `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="99813-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99813-129">Zazwyczaj `Is` lub `IsNot` operator ma odczytać wartości właściwości do porównania.</span><span class="sxs-lookup"><span data-stu-id="99813-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="99813-130">Jednak jeśli właściwość obecnie przechowuje `Nothing`, właściwość tworzy nowe wystąpienie formularza, a następnie zwraca tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="99813-130">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="99813-131">Jednak kompilator Visual Basic traktuje właściwości `My.Forms` obiektu inaczej i umożliwia `Is` lub `IsNot` operatora, aby sprawdzić stan właściwości bez zmiany jego wartość.</span><span class="sxs-lookup"><span data-stu-id="99813-131">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99813-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="99813-132">Example</span></span>  
 <span data-ttu-id="99813-133">Ten przykład umożliwia zmianę nazwy domyślnej `SidebarMenu` formularza.</span><span class="sxs-lookup"><span data-stu-id="99813-133">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="99813-134">Na przykład do pracy projektu musi mieć formularza o nazwie `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="99813-134">For this example to work, your project must have a form named `SidebarMenu`.</span></span> <span data-ttu-id="99813-135">Aby uzyskać więcej informacji, zobacz [porady: dodawanie formularzy systemu Windows z projektem](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="99813-135">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="99813-136">Ten kod będzie działać tylko w projekcie aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="99813-136">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99813-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99813-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="99813-138">Dostępność według typu projektu</span><span class="sxs-lookup"><span data-stu-id="99813-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="99813-139">Typ projektu</span><span class="sxs-lookup"><span data-stu-id="99813-139">Project type</span></span>|<span data-ttu-id="99813-140">Dostępne</span><span class="sxs-lookup"><span data-stu-id="99813-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="99813-141">Aplikacja systemu Windows</span><span class="sxs-lookup"><span data-stu-id="99813-141">Windows Application</span></span>|<span data-ttu-id="99813-142">**Tak**</span><span class="sxs-lookup"><span data-stu-id="99813-142">**Yes**</span></span>|  
|<span data-ttu-id="99813-143">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="99813-143">Class Library</span></span>|<span data-ttu-id="99813-144">Nie</span><span class="sxs-lookup"><span data-stu-id="99813-144">No</span></span>|  
|<span data-ttu-id="99813-145">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="99813-145">Console Application</span></span>|<span data-ttu-id="99813-146">Nie</span><span class="sxs-lookup"><span data-stu-id="99813-146">No</span></span>|  
|<span data-ttu-id="99813-147">Biblioteka formantów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="99813-147">Windows Control Library</span></span>|<span data-ttu-id="99813-148">Nie</span><span class="sxs-lookup"><span data-stu-id="99813-148">No</span></span>|  
|<span data-ttu-id="99813-149">Biblioteka formantów sieci Web</span><span class="sxs-lookup"><span data-stu-id="99813-149">Web Control Library</span></span>|<span data-ttu-id="99813-150">Nie</span><span class="sxs-lookup"><span data-stu-id="99813-150">No</span></span>|  
|<span data-ttu-id="99813-151">Usługa systemu Windows</span><span class="sxs-lookup"><span data-stu-id="99813-151">Windows Service</span></span>|<span data-ttu-id="99813-152">Nie</span><span class="sxs-lookup"><span data-stu-id="99813-152">No</span></span>|  
|<span data-ttu-id="99813-153">Witryna sieci Web</span><span class="sxs-lookup"><span data-stu-id="99813-153">Web Site</span></span>|<span data-ttu-id="99813-154">Nie</span><span class="sxs-lookup"><span data-stu-id="99813-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99813-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99813-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="99813-156">Obiekty</span><span class="sxs-lookup"><span data-stu-id="99813-156">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="99813-157">Porady: dodawanie formularzy systemu Windows do projektu</span><span class="sxs-lookup"><span data-stu-id="99813-157">How to: Add Windows Forms to a Project</span></span>](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)  
 [<span data-ttu-id="99813-158">Is — Operator</span><span class="sxs-lookup"><span data-stu-id="99813-158">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="99813-159">IsNot — Operator</span><span class="sxs-lookup"><span data-stu-id="99813-159">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="99813-160">Uzyskiwanie dostępu do formularzy aplikacji</span><span class="sxs-lookup"><span data-stu-id="99813-160">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
