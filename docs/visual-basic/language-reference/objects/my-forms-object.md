---
title: My.Forms — obiekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: d15765b7673f321d4362ceea0adb73959a7e7726
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360482"
---
# <a name="myforms-object"></a><span data-ttu-id="6cf59-102">My.Forms — Obiekt</span><span class="sxs-lookup"><span data-stu-id="6cf59-102">My.Forms Object</span></span>
<span data-ttu-id="6cf59-103">Udostępnia właściwości do uzyskiwania dostępu do wystąpienia każdego formularza Windows zadeklarowana w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="6cf59-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cf59-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cf59-104">Remarks</span></span>  
 <span data-ttu-id="6cf59-105">`My.Forms` Obiekt zawiera wystąpienie każdego formularza w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="6cf59-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="6cf59-106">Nazwa właściwości jest taka sama jak nazwa formularza, który uzyskuje dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="6cf59-106">The name of the property is the same as the name of the form that the property accesses.</span></span>   
  
 <span data-ttu-id="6cf59-107">Możesz uzyskać dostęp przypominają zwykłe formularze `My.Forms` obiektu przy użyciu nazwy formularza, bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="6cf59-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="6cf59-108">Nazwa właściwości jest taka sama jak nazwa typu formularza, to umożliwia dostęp do formularza tak, jakby był domyślnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6cf59-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="6cf59-109">Na przykład `My.Forms.Form1.Show` jest odpowiednikiem `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="6cf59-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="6cf59-110">`My.Forms` Obiekt udostępnia tylko formularze, które są skojarzone z bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="6cf59-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="6cf59-111">Go nie zapewnia dostępu do formularzy zadeklarowane w przywoływanych bibliotekach DLL.</span><span class="sxs-lookup"><span data-stu-id="6cf59-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="6cf59-112">Aby uzyskać dostęp do formularza, który zawiera biblioteki DLL, należy użyć kwalifikowana nazwa formularza zapisywane jako *Nazwa_pliku_dll*. *Nazwa_formularza*.</span><span class="sxs-lookup"><span data-stu-id="6cf59-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="6cf59-113">Możesz użyć <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> właściwości do pobrania zbiór wszystkich aplikacji, otwartych formularzy.</span><span class="sxs-lookup"><span data-stu-id="6cf59-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="6cf59-114">Obiekt i jego właściwości są dostępne tylko dla aplikacji Windows.</span><span class="sxs-lookup"><span data-stu-id="6cf59-114">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6cf59-115">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6cf59-115">Properties</span></span>  
 <span data-ttu-id="6cf59-116">Każda właściwość `My.Forms` obiekt umożliwia dostęp do wystąpienia do formularza w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="6cf59-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="6cf59-117">Nazwa właściwości jest taka sama jak nazwa formularza, który uzyskuje dostęp do właściwości, a typ właściwości jest taka sama jak typ formularza.</span><span class="sxs-lookup"><span data-stu-id="6cf59-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cf59-118">W przypadku kolizji nazw, nazwę właściwości, aby przejść do formularza jest *RootNamespace*_*Namespace*\_*Nazwa_formularza*.</span><span class="sxs-lookup"><span data-stu-id="6cf59-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="6cf59-119">Na przykład, należy wziąć pod uwagę dwie formy o nazwie `Form1.`jednej z poniższych metod czy w głównej przestrzeni nazw `WindowsApplication1` w przestrzeni nazw `Namespace1`, dostęp do formularza przy użyciu `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="6cf59-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="6cf59-120">`My.Forms` Obiekt umożliwia dostęp do wystąpienia aplikacji formularza głównego, który został utworzony podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="6cf59-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="6cf59-121">Dla wszystkich innych form `My.Forms` obiektu tworzy nowe wystąpienie formularza, jeśli jest dostępny i zapisuje go.</span><span class="sxs-lookup"><span data-stu-id="6cf59-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="6cf59-122">Kolejne próby dostępu do tej właściwości zwracają tego wystąpienia formularza.</span><span class="sxs-lookup"><span data-stu-id="6cf59-122">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="6cf59-123">Można dysponować formularza, przypisując `Nothing` do właściwości dla formularza.</span><span class="sxs-lookup"><span data-stu-id="6cf59-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="6cf59-124">Wywołania metody ustawiającej właściwość <xref:System.Windows.Forms.Form.Close%2A> metody formularza, a następnie przypisuje `Nothing` do przechowywanej wartości.</span><span class="sxs-lookup"><span data-stu-id="6cf59-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="6cf59-125">Jeśli przypiszesz dowolnej wartości innych niż `Nothing` dla właściwości, metody ustawiającej zgłasza <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6cf59-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="6cf59-126">Możesz sprawdzić, czy właściwość `My.Forms` obiekt przechowuje wystąpienia formularza za pomocą `Is` lub `IsNot` operatora.</span><span class="sxs-lookup"><span data-stu-id="6cf59-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="6cf59-127">Aby sprawdzić, czy wartość właściwości można używać tych operatorów `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="6cf59-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cf59-128">Zazwyczaj `Is` lub `IsNot` operator ma zostać odczytana wartość właściwości, które ma wykonać porównanie.</span><span class="sxs-lookup"><span data-stu-id="6cf59-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="6cf59-129">Jednakże jeśli właściwość jest obecnie przechowuje `Nothing`, właściwość tworzy nowe wystąpienie formularza, a następnie zwraca tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6cf59-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="6cf59-130">Jednak kompilator języka Visual Basic traktuje właściwości `My.Forms` obiektu inaczej i umożliwia `Is` lub `IsNot` operatora, aby sprawdzić stan właściwości bez zmieniania jego wartości.</span><span class="sxs-lookup"><span data-stu-id="6cf59-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cf59-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="6cf59-131">Example</span></span>  
 <span data-ttu-id="6cf59-132">Ten przykład umożliwia zmianę tytuł domyślnego `SidebarMenu` formularza.</span><span class="sxs-lookup"><span data-stu-id="6cf59-132">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="6cf59-133">W tym przykładzie do pracy, projekt musi mieć formularz o nazwie `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="6cf59-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>  
  
 <span data-ttu-id="6cf59-134">Ten kod będzie działać tylko w projekcie aplikacji Windows.</span><span class="sxs-lookup"><span data-stu-id="6cf59-134">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cf59-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6cf59-135">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="6cf59-136">Dostępność według typu projektu</span><span class="sxs-lookup"><span data-stu-id="6cf59-136">Availability by Project Type</span></span>  
  
|<span data-ttu-id="6cf59-137">Typ projektu</span><span class="sxs-lookup"><span data-stu-id="6cf59-137">Project type</span></span>|<span data-ttu-id="6cf59-138">Dostępne</span><span class="sxs-lookup"><span data-stu-id="6cf59-138">Available</span></span>|  
|---|---|  
|<span data-ttu-id="6cf59-139">Aplikacja Windows</span><span class="sxs-lookup"><span data-stu-id="6cf59-139">Windows Application</span></span>|<span data-ttu-id="6cf59-140">**Tak**</span><span class="sxs-lookup"><span data-stu-id="6cf59-140">**Yes**</span></span>|  
|<span data-ttu-id="6cf59-141">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="6cf59-141">Class Library</span></span>|<span data-ttu-id="6cf59-142">Nie</span><span class="sxs-lookup"><span data-stu-id="6cf59-142">No</span></span>|  
|<span data-ttu-id="6cf59-143">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="6cf59-143">Console Application</span></span>|<span data-ttu-id="6cf59-144">Nie</span><span class="sxs-lookup"><span data-stu-id="6cf59-144">No</span></span>|  
|<span data-ttu-id="6cf59-145">Biblioteka formantów Windows</span><span class="sxs-lookup"><span data-stu-id="6cf59-145">Windows Control Library</span></span>|<span data-ttu-id="6cf59-146">Nie</span><span class="sxs-lookup"><span data-stu-id="6cf59-146">No</span></span>|  
|<span data-ttu-id="6cf59-147">Biblioteka formantów sieci Web</span><span class="sxs-lookup"><span data-stu-id="6cf59-147">Web Control Library</span></span>|<span data-ttu-id="6cf59-148">Nie</span><span class="sxs-lookup"><span data-stu-id="6cf59-148">No</span></span>|  
|<span data-ttu-id="6cf59-149">Usługa systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6cf59-149">Windows Service</span></span>|<span data-ttu-id="6cf59-150">Nie</span><span class="sxs-lookup"><span data-stu-id="6cf59-150">No</span></span>|  
|<span data-ttu-id="6cf59-151">Witryna sieci Web</span><span class="sxs-lookup"><span data-stu-id="6cf59-151">Web Site</span></span>|<span data-ttu-id="6cf59-152">Nie</span><span class="sxs-lookup"><span data-stu-id="6cf59-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6cf59-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cf59-153">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="6cf59-154">Obiekty</span><span class="sxs-lookup"><span data-stu-id="6cf59-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="6cf59-155">Is, operator</span><span class="sxs-lookup"><span data-stu-id="6cf59-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="6cf59-156">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="6cf59-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="6cf59-157">Uzyskiwanie dostępu do formularzy aplikacji</span><span class="sxs-lookup"><span data-stu-id="6cf59-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
