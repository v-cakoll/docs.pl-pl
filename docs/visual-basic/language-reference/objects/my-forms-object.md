---
title: My.Forms — Obiekt
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 001f6fbfae2467ea0af5e98ca041b694d1e7b8f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372443"
---
# <a name="myforms-object"></a><span data-ttu-id="68cac-102">My.Forms — Obiekt</span><span class="sxs-lookup"><span data-stu-id="68cac-102">My.Forms Object</span></span>

<span data-ttu-id="68cac-103">Zawiera właściwości umożliwiające dostęp do wystąpienia każdego formularza systemu Windows zadeklarowanego w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="68cac-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>

## <a name="remarks"></a><span data-ttu-id="68cac-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68cac-104">Remarks</span></span>

<span data-ttu-id="68cac-105">`My.Forms`Obiekt zawiera wystąpienie każdego formularza w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="68cac-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="68cac-106">Nazwa właściwości jest taka sama jak nazwa formularza, do którego uzyskuje dostęp właściwość.</span><span class="sxs-lookup"><span data-stu-id="68cac-106">The name of the property is the same as the name of the form that the property accesses.</span></span>

<span data-ttu-id="68cac-107">Dostęp do formularzy dostarczonych przez obiekt można uzyskać `My.Forms` przy użyciu nazwy formularza bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="68cac-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="68cac-108">Ponieważ nazwa właściwości jest taka sama jak nazwa typu formularza, pozwala to na dostęp do formularza tak, jakby miał wystąpienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="68cac-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="68cac-109">Na przykład `My.Forms.Form1.Show` jest równoważne `Form1.Show` .</span><span class="sxs-lookup"><span data-stu-id="68cac-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>

<span data-ttu-id="68cac-110">`My.Forms`Obiekt uwidacznia tylko formularze skojarzone z bieżącym projektem.</span><span class="sxs-lookup"><span data-stu-id="68cac-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="68cac-111">Nie zapewnia dostępu do formularzy zadeklarowanych w przywoływanych bibliotekach DLL.</span><span class="sxs-lookup"><span data-stu-id="68cac-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="68cac-112">Aby uzyskać dostęp do formularza, który zapewnia Biblioteka DLL, należy użyć kwalifikowanej nazwy formularza, która jest zapisywana jako *nazwa_pliku_dll*. *FormatName*.</span><span class="sxs-lookup"><span data-stu-id="68cac-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>

<span data-ttu-id="68cac-113">Możesz użyć właściwości, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> Aby uzyskać kolekcję wszystkich otwartych formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="68cac-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>

<span data-ttu-id="68cac-114">Obiekt i jego właściwości są dostępne tylko dla aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="68cac-114">The object and its properties are available only for Windows applications.</span></span>

## <a name="properties"></a><span data-ttu-id="68cac-115">Właściwości</span><span class="sxs-lookup"><span data-stu-id="68cac-115">Properties</span></span>

<span data-ttu-id="68cac-116">Każda właściwość `My.Forms` obiektu zapewnia dostęp do wystąpienia formularza w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="68cac-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="68cac-117">Nazwa właściwości jest taka sama jak nazwa formularza, do którego uzyskuje dostęp właściwość, a typ właściwości jest taki sam jak typ formularza.</span><span class="sxs-lookup"><span data-stu-id="68cac-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>

> [!NOTE]
> <span data-ttu-id="68cac-118">W przypadku kolizji nazw nazwa właściwości do uzyskiwania dostępu do formularza to *RootNamespace*_*NamespaceName* \_ *FormName*.</span><span class="sxs-lookup"><span data-stu-id="68cac-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="68cac-119">Rozważmy na przykład dwa formularze o nazwie, `Form1.` Jeśli jeden z tych formularzy znajduje się w głównej przestrzeni nazw `WindowsApplication1` i w przestrzeni nazw `Namespace1` , możesz uzyskać dostęp do tego formularza `My.Forms.WindowsApplication1_Namespace1_Form1` .</span><span class="sxs-lookup"><span data-stu-id="68cac-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>

<span data-ttu-id="68cac-120">`My.Forms`Obiekt umożliwia dostęp do wystąpienia głównego formularza aplikacji, który został utworzony podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="68cac-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="68cac-121">W przypadku wszystkich innych formularzy `My.Forms` obiekt tworzy nowe wystąpienie formularza, gdy jest on dostępny i przechowuje je.</span><span class="sxs-lookup"><span data-stu-id="68cac-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="68cac-122">Kolejne próby uzyskania dostępu do tej właściwości zwracają to wystąpienie formularza.</span><span class="sxs-lookup"><span data-stu-id="68cac-122">Subsequent attempts to access that property return that instance of the form.</span></span>

<span data-ttu-id="68cac-123">Formularz można usunąć, przypisując `Nothing` do właściwości tego formularza.</span><span class="sxs-lookup"><span data-stu-id="68cac-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="68cac-124">Metoda ustawiająca właściwość wywołuje <xref:System.Windows.Forms.Form.Close%2A> metodę formularza, a następnie przypisuje `Nothing` do przechowywanej wartości.</span><span class="sxs-lookup"><span data-stu-id="68cac-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="68cac-125">Jeśli przypiszesz dowolną wartość inną niż `Nothing` Właściwość, Metoda ustawiająca zgłosi <xref:System.ArgumentException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="68cac-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="68cac-126">Można sprawdzić, czy właściwość `My.Forms` obiektu przechowuje wystąpienie formularza przy użyciu `Is` `IsNot` operatora OR.</span><span class="sxs-lookup"><span data-stu-id="68cac-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="68cac-127">Można użyć tych operatorów do sprawdzenia, czy wartość właściwości jest `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="68cac-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>

> [!NOTE]
> <span data-ttu-id="68cac-128">Zazwyczaj `Is` `IsNot` operator or musi odczytywać wartość właściwości w celu przeprowadzenia porównania.</span><span class="sxs-lookup"><span data-stu-id="68cac-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="68cac-129">Jeśli jednak właściwość jest obecnie przechowywana `Nothing` , Właściwość tworzy nowe wystąpienie formularza, a następnie zwraca to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="68cac-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="68cac-130">Jednak kompilator Visual Basic traktuje właściwości `My.Forms` obiektu inaczej i umożliwia `Is` `IsNot` operatorowi or sprawdzenie stanu właściwości bez zmiany jego wartości.</span><span class="sxs-lookup"><span data-stu-id="68cac-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>

## <a name="example"></a><span data-ttu-id="68cac-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="68cac-131">Example</span></span>

<span data-ttu-id="68cac-132">Ten przykład zmienia tytuł `SidebarMenu` formularza domyślnego.</span><span class="sxs-lookup"><span data-stu-id="68cac-132">This example changes the title of the default `SidebarMenu` form.</span></span>

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

<span data-ttu-id="68cac-133">Aby ten przykład działał, projekt musi mieć formularz o nazwie `SidebarMenu` .</span><span class="sxs-lookup"><span data-stu-id="68cac-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>

<span data-ttu-id="68cac-134">Ten kod będzie działał tylko w projekcie aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="68cac-134">This code will work only in a Windows Application project.</span></span>

## <a name="requirements"></a><span data-ttu-id="68cac-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68cac-135">Requirements</span></span>

### <a name="availability-by-project-type"></a><span data-ttu-id="68cac-136">Dostępność według typu projektu</span><span class="sxs-lookup"><span data-stu-id="68cac-136">Availability by Project Type</span></span>

|<span data-ttu-id="68cac-137">Project type (Typ projektu)</span><span class="sxs-lookup"><span data-stu-id="68cac-137">Project type</span></span>|<span data-ttu-id="68cac-138">Dostępne</span><span class="sxs-lookup"><span data-stu-id="68cac-138">Available</span></span>|
|---|---|
|<span data-ttu-id="68cac-139">Aplikacja systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68cac-139">Windows Application</span></span>|<span data-ttu-id="68cac-140">**Tak**</span><span class="sxs-lookup"><span data-stu-id="68cac-140">**Yes**</span></span>|
|<span data-ttu-id="68cac-141">Biblioteka klas</span><span class="sxs-lookup"><span data-stu-id="68cac-141">Class Library</span></span>|<span data-ttu-id="68cac-142">Nie</span><span class="sxs-lookup"><span data-stu-id="68cac-142">No</span></span>|
|<span data-ttu-id="68cac-143">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="68cac-143">Console Application</span></span>|<span data-ttu-id="68cac-144">Nie</span><span class="sxs-lookup"><span data-stu-id="68cac-144">No</span></span>|
|<span data-ttu-id="68cac-145">Biblioteka formantów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68cac-145">Windows Control Library</span></span>|<span data-ttu-id="68cac-146">Nie</span><span class="sxs-lookup"><span data-stu-id="68cac-146">No</span></span>|
|<span data-ttu-id="68cac-147">Biblioteka formantów sieci Web</span><span class="sxs-lookup"><span data-stu-id="68cac-147">Web Control Library</span></span>|<span data-ttu-id="68cac-148">Nie</span><span class="sxs-lookup"><span data-stu-id="68cac-148">No</span></span>|
|<span data-ttu-id="68cac-149">Usługa systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68cac-149">Windows Service</span></span>|<span data-ttu-id="68cac-150">Nie</span><span class="sxs-lookup"><span data-stu-id="68cac-150">No</span></span>|
|<span data-ttu-id="68cac-151">Witryna sieci Web</span><span class="sxs-lookup"><span data-stu-id="68cac-151">Web Site</span></span>|<span data-ttu-id="68cac-152">Nie</span><span class="sxs-lookup"><span data-stu-id="68cac-152">No</span></span>|

## <a name="see-also"></a><span data-ttu-id="68cac-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68cac-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="68cac-154">Obiekty</span><span class="sxs-lookup"><span data-stu-id="68cac-154">Objects</span></span>](index.md)
- [<span data-ttu-id="68cac-155">Is, operator</span><span class="sxs-lookup"><span data-stu-id="68cac-155">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="68cac-156">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="68cac-156">IsNot Operator</span></span>](../operators/isnot-operator.md)
- [<span data-ttu-id="68cac-157">Uzyskiwanie dostępu do formularzy aplikacji</span><span class="sxs-lookup"><span data-stu-id="68cac-157">Accessing Application Forms</span></span>](../../developing-apps/programming/accessing-application-forms.md)
