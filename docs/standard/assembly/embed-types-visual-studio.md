---
title: 'Przewodnik: Osadź typy z zestawów zarządzanych w programie Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1f32bd840efa97b62097a2d051c25d519785b381
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973272"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="ef4ac-102">Przewodnik: Osadź typy z zestawów zarządzanych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ef4ac-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="ef4ac-103">Jeśli osadzisz informacje o typie z zestawu o silnej nazwie zarządzanej, możesz luźno połączyć typy w aplikacji, aby osiągnąć niezależność wersji.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="ef4ac-104">Oznacza to, że program można napisać tak, aby używał typów z dowolnej wersji biblioteki zarządzanej bez konieczności ponownego kompilowania każdej nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="ef4ac-105">Osadzanie typów jest często używane z międzyoperacyjnym modelem COM, takim jak aplikacja, która korzysta z obiektów automatyzacji z Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="ef4ac-106">Osadzanie informacji o typie umożliwia tej samej kompilacji programu do pracy z różnymi wersjami Microsoft Office na różnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="ef4ac-107">Można jednak również użyć osadzania typu z w pełni zarządzanych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="ef4ac-108">Po określeniu interfejsów publicznych, które mogą być osadzone, należy utworzyć klasy środowiska uruchomieniowego, które implementują te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="ef4ac-109">Program kliencki może osadzić informacje o typie dla interfejsów w czasie projektowania, odwołując się do zestawu, który zawiera interfejsy publiczne i ustawiając `Embed Interop Types` Właściwość odwołania na. `True`</span><span class="sxs-lookup"><span data-stu-id="ef4ac-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="ef4ac-110">Następnie program kliencki może ładować wystąpienia obiektów środowiska uruchomieniowego, które zostały wpisane jako te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="ef4ac-111">Jest to równoznaczne z użyciem kompilatora wiersza polecenia i odwołującego się do zestawu `/link` przy użyciu opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-111">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> 

<span data-ttu-id="ef4ac-112">Jeśli utworzysz nową wersję zestawu o silnej nazwie środowiska uruchomieniowego, nie trzeba ponownie kompilować programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="ef4ac-113">Program kliencki nadal korzysta z niezależnej wersji zestawu środowiska uruchomieniowego, przy użyciu informacji o typie osadzonym dla interfejsów publicznych.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="ef4ac-114">W tym instruktażu zawarto następujące instrukcje:</span><span class="sxs-lookup"><span data-stu-id="ef4ac-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="ef4ac-115">Utwórz zestaw o silnej nazwie z interfejsem publicznym zawierającym informacje o typie, które mogą być osadzone.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="ef4ac-116">Utwórz zestaw o silnej nazwie środowiska uruchomieniowego, który implementuje interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="ef4ac-117">Utwórz program kliencki, który osadzi informacje o typie z interfejsu publicznego i tworzy wystąpienie klasy z zestawu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="ef4ac-118">Modyfikowanie i ponowne kompilowanie zestawu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="ef4ac-119">Uruchom program kliencki, aby zobaczyć, że używa nowej wersji zestawu środowiska uruchomieniowego bez konieczności ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="ef4ac-120">Warunki i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="ef4ac-120">Conditions and limitations</span></span>

<span data-ttu-id="ef4ac-121">Informacje o typie można osadzić z zestawu w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="ef4ac-121">You can embed type information from an assembly under the following conditions:</span></span> 

- <span data-ttu-id="ef4ac-122">Zestaw uwidacznia co najmniej jeden interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="ef4ac-123">Interfejsy osadzone mają adnotacje z `ComImport` atrybutami i `Guid` atrybutami o unikatowych identyfikatorach GUID.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="ef4ac-124">Zestaw jest oznaczony `ImportedFromTypeLib` atrybutem `PrimaryInteropAssembly` lub atrybutem i atrybutem na poziomie `Guid` zestawu.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="ef4ac-125">Szablony projektu C# wizualizacji i Visual Basic zawierają domyślnie atrybut na poziomie `Guid` zestawu.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="ef4ac-126">Ponieważ podstawową funkcją osadzania typu jest obsługa zestawów międzyoperacyjnych COM, podczas osadzania informacji o typie w w pełni zarządzanym rozwiązaniu obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="ef4ac-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="ef4ac-127">Osadzone są tylko atrybuty charakterystyczne dla międzyoperacyjnych modelu COM.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="ef4ac-128">Inne atrybuty są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="ef4ac-129">Jeśli typ korzysta z parametrów ogólnych, a typ parametru generycznego jest typem osadzonym, ten typ nie może być używany między granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="ef4ac-130">Przykłady przekroczenia granicy zestawu obejmują wywołanie metody z innego zestawu lub pochodny typ z typu zdefiniowanego w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="ef4ac-131">Stałe nie są osadzone.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-131">Constants are not embedded.</span></span>
- <span data-ttu-id="ef4ac-132"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Klasa nie obsługuje osadzonego typu jako klucza.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="ef4ac-133">Możesz zaimplementować własny typ słownika, aby obsługiwał typ osadzony jako klucz.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="ef4ac-134">Tworzenie interfejsu</span><span class="sxs-lookup"><span data-stu-id="ef4ac-134">Create an interface</span></span>

<span data-ttu-id="ef4ac-135">Pierwszym krokiem jest utworzenie zestawu interfejsu równoważność typu.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-135">The first step is to create the type equivalence interface assembly.</span></span> 

1. <span data-ttu-id="ef4ac-136">W programie Visual Studio, wybierz **pliku** > **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="ef4ac-137">W oknie dialogowym **Utwórz nowy projekt** wpisz *Biblioteka klas* w polu **Wyszukaj szablony** .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="ef4ac-138">Wybierz z listy C# szablon lub **bibliotekę klas vb (.NET Framework)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-138">Select either the C# or VB **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="ef4ac-139">W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu**wpisz *TypeEquivalenceInterface*, a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="ef4ac-140">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-140">The new project is created.</span></span>
   
1. <span data-ttu-id="ef4ac-141">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Class1.cs* lub *Class1. vb* , wybierz polecenie **Zmień nazwę**, a następnie zmień nazwę pliku z *Class1* na *ISampleInterface*.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="ef4ac-142">Należy **odpowiedzieć na** monit, aby zmienić nazwę klasy na `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="ef4ac-143">Ta klasa reprezentuje interfejs publiczny dla klasy.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-143">This class represents the public interface for the class.</span></span>
   
1. <span data-ttu-id="ef4ac-144">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** , a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span> 
   
1. <span data-ttu-id="ef4ac-145">Wybierz opcję **Kompiluj** w lewym okienku ekranu **Właściwości** , a następnie ustaw **ścieżkę wyjściową** do lokalizacji na komputerze, na przykład *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="ef4ac-146">Ta sama lokalizacja jest używana w tym instruktażu.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-146">You use the same location throughout this walkthrough.</span></span> 
   
1. <span data-ttu-id="ef4ac-147">Wybierz pozycję Podpisz w lewym **okienku na ekranie** **Właściwości** , a następnie zaznacz pole wyboru **podpisywania zestawu** .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="ef4ac-148">Z listy rozwijanej **Wybierz plik klucza o silnej nazwie**, wybierz pozycję **Nowy**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span> 
   
1. <span data-ttu-id="ef4ac-149">W oknie dialogowym **Tworzenie klucza o silnej nazwie** w obszarze **Nazwa pliku klucza**wpisz polecenie *Key. snk*.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="ef4ac-150">Usuń zaznaczenie pola wyboru **Chroń mój klucz plik hasłem** , a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>
   
1. <span data-ttu-id="ef4ac-151">Otwórz plik klasy *ISampleInterface* w edytorze kodu i Zastąp jego zawartość następującym kodem, aby utworzyć `ISampleInterface` interfejs:</span><span class="sxs-lookup"><span data-stu-id="ef4ac-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>
   
   ```csharp
   using System;
   using System.Runtime.InteropServices;
   
   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```
   
   ```vb
   Imports System.Runtime.InteropServices
   
   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```
   
1. <span data-ttu-id="ef4ac-152">W menu **Narzędzia** wybierz pozycję **Utwórz identyfikator GUID**, a następnie w oknie dialogowym **Tworzenie identyfikatora GUID** wybierz pozycję **Format rejestru**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="ef4ac-153">Wybierz pozycję **Kopiuj**, a następnie wybierz pozycję **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-153">Select **Copy**, and then select **Exit**.</span></span>
   
1. <span data-ttu-id="ef4ac-154">W atrybucie kodu Zastąp przykładowy identyfikator GUID identyfikatorem, który został skopiowany, i Usuń nawiasy klamrowe ( **{}** ). `Guid`</span><span class="sxs-lookup"><span data-stu-id="ef4ac-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>
   
1. <span data-ttu-id="ef4ac-155">W **Eksplorator rozwiązań**rozwiń folder **Właściwości** i wybierz plik *AssemblyInfo.cs* lub *AssemblyInfo. vb* .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="ef4ac-156">W edytorze kodu Dodaj następujący atrybut do pliku:</span><span class="sxs-lookup"><span data-stu-id="ef4ac-156">In the code editor, add the following attribute to the file:</span></span>
   
   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```
   
   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```
   
1. <span data-ttu-id="ef4ac-157">Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="ef4ac-158">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="ef4ac-159">Plik DLL biblioteki klas jest kompilowany i zapisywany w określonej ścieżce danych wyjściowych kompilacji, na przykład *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="ef4ac-160">Tworzenie klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ef4ac-160">Create a runtime class</span></span>

<span data-ttu-id="ef4ac-161">Następnie Utwórz klasę środowiska uruchomieniowego typu równoważność.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="ef4ac-162">W programie Visual Studio, wybierz **pliku** > **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="ef4ac-163">W oknie dialogowym **Utwórz nowy projekt** wpisz *Biblioteka klas* w polu **Wyszukaj szablony** .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="ef4ac-164">Wybierz z listy C# szablon lub **bibliotekę klas vb (.NET Framework)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-164">Select either the C# or VB **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="ef4ac-165">W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu**wpisz *TypeEquivalenceRuntime*, a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="ef4ac-166">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-166">The new project is created.</span></span>
   
1. <span data-ttu-id="ef4ac-167">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *Class1.cs* lub *Class1. vb* , wybierz polecenie **Zmień nazwę**, a następnie zmień nazwę pliku z *Class1* na *SampleClass*.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="ef4ac-168">Należy **odpowiedzieć na** monit, aby zmienić nazwę klasy na `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="ef4ac-169">Ta klasa implementuje `ISampleInterface` interfejs.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-169">This class implements the `ISampleInterface` interface.</span></span>
   
1. <span data-ttu-id="ef4ac-170">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="ef4ac-171">Wybierz opcję **Kompiluj** w lewym okienku ekranu **Właściwości** , a następnie ustaw **ścieżkę wyjściową** do tej samej lokalizacji, która została użyta dla projektu TypeEquivalenceInterface, na przykład *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>
   
1. <span data-ttu-id="ef4ac-172">Wybierz pozycję Podpisz w lewym **okienku na ekranie** **Właściwości** , a następnie zaznacz pole wyboru **podpisywania zestawu** .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="ef4ac-173">Z listy rozwijanej **Wybierz plik klucza o silnej nazwie**, wybierz pozycję **Nowy**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span> 
   
1. <span data-ttu-id="ef4ac-174">W oknie dialogowym **Tworzenie klucza o silnej nazwie** w obszarze **Nazwa pliku klucza**wpisz polecenie *Key. snk*.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="ef4ac-175">Usuń zaznaczenie pola wyboru **Chroń mój klucz plik hasłem** , a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>
   
1. <span data-ttu-id="ef4ac-176">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Dodaj** > **odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span> 
   
1. <span data-ttu-id="ef4ac-177">W oknie dialogowym **Menedżer odwołań** wybierz **Przeglądaj** i przejdź do folderu Ścieżka wyjściowa.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="ef4ac-178">Wybierz plik *TypeEquivalenceInterface. dll* , wybierz pozycję **Dodaj**, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>
   
1. <span data-ttu-id="ef4ac-179">W **Eksplorator rozwiązań**rozwiń folder **odwołania** i wybierz odwołanie **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="ef4ac-180">W okienku **Właściwości** Ustaw **określoną wersję** na **false** , jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>
   
1. <span data-ttu-id="ef4ac-181">Otwórz plik klasy *SampleClass* w edytorze kodu i Zastąp jego zawartość następującym kodem, aby utworzyć `SampleClass` klasę:</span><span class="sxs-lookup"><span data-stu-id="ef4ac-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using TypeEquivalenceInterface;
   
   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }
   
           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```
   
   ```vb
   Imports TypeEquivalenceInterface
   
   Public Class SampleClass
       Implements ISampleInterface
   
       Private p_UserInput As String
       Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
           Get
               Return p_UserInput
           End Get
       End Property
   
       Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
           Console.WriteLine("Please enter a value:")
           p_UserInput = Console.ReadLine()
       End Sub
   End Class
   ```
   
1. <span data-ttu-id="ef4ac-182">Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="ef4ac-183">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="ef4ac-184">Plik DLL biblioteki klas zostanie skompilowany i zapisany w określonej ścieżce danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="ef4ac-185">Tworzenie projektu klienta</span><span class="sxs-lookup"><span data-stu-id="ef4ac-185">Create a client project</span></span>

<span data-ttu-id="ef4ac-186">Na koniec Utwórz program kliencki typu równoważność, który odwołuje się do zestawu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="ef4ac-187">W programie Visual Studio, wybierz **pliku** > **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="ef4ac-188">W oknie dialogowym **Utwórz nowy projekt** wpisz *Console* w polu **Wyszukaj szablony** .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="ef4ac-189">Wybierz z listy C# szablon lub **aplikację konsolową vb (.NET Framework)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-189">Select either the C# or VB **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="ef4ac-190">W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu**wpisz *TypeEquivalenceClient*, a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="ef4ac-191">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-191">The new project is created.</span></span>
   
1. <span data-ttu-id="ef4ac-192">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceClient** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="ef4ac-193">Wybierz opcję **Kompiluj** w lewym okienku ekranu **Właściwości** , a następnie ustaw **ścieżkę wyjściową** do tej samej lokalizacji, która została użyta dla projektu TypeEquivalenceInterface, na przykład *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>
   
1. <span data-ttu-id="ef4ac-194">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceClient** i wybierz polecenie **Dodaj** > **odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span> 
   
1. <span data-ttu-id="ef4ac-195">W oknie dialogowym **Menedżer odwołań** , jeśli plik **TypeEquivalenceInterface. dll** jest już wymieniony, zaznacz go.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="ef4ac-196">W przeciwnym razie wybierz pozycję **Przeglądaj**, przejdź do folderu Ścieżka wyjściowa, wybierz plik *TypeEquivalenceInterface. dll* (nie *TypeEquivalenceRuntime. dll*), a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="ef4ac-197">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-197">Select **OK**.</span></span>
   
1. <span data-ttu-id="ef4ac-198">W **Eksplorator rozwiązań**rozwiń folder **odwołania** i wybierz odwołanie **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="ef4ac-199">W okienku **Właściwości** ustaw opcję **Osadź typy międzyoperacyjności** na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>
   
1. <span data-ttu-id="ef4ac-200">Otwórz plik *program.cs* lub *Module1. vb* w edytorze kodu i Zastąp jego zawartość następującym kodem, aby utworzyć program kliencki:</span><span class="sxs-lookup"><span data-stu-id="ef4ac-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using TypeEquivalenceInterface;
   using System.Reflection;
   
   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```
   
   ```vb
   Imports TypeEquivalenceInterface
   Imports System.Reflection
   
   Module Module1
   
       Sub Main()
           Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
           Dim sampleClass As ISampleInterface = CType( _
               sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
           sampleClass.GetUserInput()
           Console.WriteLine(sampleClass.UserInput)
           Console.WriteLine(sampleAssembly.GetName().Version)
           Console.ReadLine()
       End Sub
   
   End Module
   ```
   
1. <span data-ttu-id="ef4ac-201">Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="ef4ac-202">Naciśnij klawisz **Ctrl**+**F5** , aby skompilować i uruchomić program.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="ef4ac-203">Zwróć uwagę, że dane wyjściowe konsoli zwracają zestaw w wersji **1.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span> 
   
## <a name="modify-the-interface"></a><span data-ttu-id="ef4ac-204">Modyfikowanie interfejsu</span><span class="sxs-lookup"><span data-stu-id="ef4ac-204">Modify the interface</span></span>

<span data-ttu-id="ef4ac-205">Teraz zmodyfikuj zestaw interfejsów i zmień jego wersję.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-205">Now, modify the interface assembly, and change its version.</span></span> 

1. <span data-ttu-id="ef4ac-206">W programie Visual Studio wybierz pozycję **plik** > **Otwórz** > **projekt/rozwiązanie**, a następnie otwórz projekt **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>
   
1. <span data-ttu-id="ef4ac-207">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="ef4ac-208">Wybierz pozycję **aplikacja** w lewym okienku ekranu **Właściwości** , a następnie wybierz pozycję **Informacje o zestawie**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span> 
   
1. <span data-ttu-id="ef4ac-209">W oknie dialogowym **Informacje o zestawie** Zmień **wersję zestawu** i wartość **wersji pliku** na *2.0.0.0*, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>
   
1. <span data-ttu-id="ef4ac-210">Otwórz plik *SampleInterface.cs* lub *SampleInterface. vb* i Dodaj następujący wiersz `ISampleInterface` kodu do interfejsu:</span><span class="sxs-lookup"><span data-stu-id="ef4ac-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>
   
   ```csharp
   DateTime GetDate();
   ```
   
   ```vb
   Function GetDate() As Date
   ```
   
1. <span data-ttu-id="ef4ac-211">Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="ef4ac-212">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="ef4ac-213">Nowa wersja pliku DLL biblioteki klas jest kompilowana i zapisywana w ścieżce danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="ef4ac-214">Modyfikowanie klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ef4ac-214">Modify the runtime class</span></span>

<span data-ttu-id="ef4ac-215">Należy również zmodyfikować klasę środowiska uruchomieniowego i zaktualizować jej wersję.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-215">Also modify the runtime class and update its version.</span></span> 

1. <span data-ttu-id="ef4ac-216">W programie Visual Studio wybierz pozycję **plik** > **Otwórz** > **projekt/rozwiązanie**, a następnie otwórz projekt **TypeEquivalenceRuntime** .</span><span class="sxs-lookup"><span data-stu-id="ef4ac-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>
   
1. <span data-ttu-id="ef4ac-217">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="ef4ac-218">Wybierz pozycję **aplikacja** w lewym okienku ekranu **Właściwości** , a następnie wybierz pozycję **Informacje o zestawie**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span> 
   
1. <span data-ttu-id="ef4ac-219">W oknie dialogowym **Informacje o zestawie** Zmień **wersję zestawu** i wartość **wersji pliku** na *2.0.0.0*, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>
   
1. <span data-ttu-id="ef4ac-220">Otwórz plik *SampleClass.cs* lub *SampleClass. vb* i Dodaj następujący `SampleClass` kod do klasy:</span><span class="sxs-lookup"><span data-stu-id="ef4ac-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>
   
   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```
   
   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```
   
1. <span data-ttu-id="ef4ac-221">Wybierz pozycję **plik** > **Zapisz wszystko** lub naciśnij **klawisze CTRL**+**SHIFT**+**S** , aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="ef4ac-222">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="ef4ac-223">Nowa wersja pliku DLL biblioteki klas jest kompilowana i zapisywana w ścieżce danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="ef4ac-224">Uruchom zaktualizowany program kliencki</span><span class="sxs-lookup"><span data-stu-id="ef4ac-224">Run the updated client program</span></span> 

<span data-ttu-id="ef4ac-225">Przejdź do lokalizacji folderu danych wyjściowych kompilacji i uruchom *TypeEquivalenceClient. exe*.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="ef4ac-226">Zwróć uwagę, że dane wyjściowe konsoli teraz odzwierciedlają nową wersję `TypeEquivalenceRuntime` zestawu, *2.0.0.0*, bez ponownej kompilacji programu.</span><span class="sxs-lookup"><span data-stu-id="ef4ac-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef4ac-227">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef4ac-227">See also</span></span>

- [<span data-ttu-id="ef4ac-228">/Link (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="ef4ac-228">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="ef4ac-229">/Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef4ac-229">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="ef4ac-230">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="ef4ac-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ef4ac-231">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef4ac-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="ef4ac-232">Program z zestawami</span><span class="sxs-lookup"><span data-stu-id="ef4ac-232">Program with assemblies</span></span>](program.md)
- [<span data-ttu-id="ef4ac-233">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="ef4ac-233">Assemblies in .NET</span></span>](index.md)