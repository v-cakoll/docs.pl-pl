---
title: 'Instruktaż: Osadzanie typów z zestawów zarządzanych w programie Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338558"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="9c11d-102">Instruktaż: Osadzanie typów z zestawów zarządzanych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c11d-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="9c11d-103">Jeśli osadzasz informacje o typie z zestawu zarządzanego o silnej nazwie, można luźno pokilku typów w aplikacji, aby osiągnąć niezależność wersji.</span><span class="sxs-lookup"><span data-stu-id="9c11d-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="9c11d-104">Oznacza to, że program może być napisany do używania typów z dowolnej wersji biblioteki zarządzanej bez konieczności ponownego kompilowania dla każdej nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="9c11d-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="9c11d-105">Osadzanie typów jest często używane z współdziałaniacom COM, na przykład aplikacja, która używa obiektów automatyzacji z pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="9c11d-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="9c11d-106">Osadzanie informacji o typie umożliwia tej samej kompilacji programu do pracy z różnymi wersjami pakietu Microsoft Office na różnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="9c11d-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="9c11d-107">Można jednak również użyć osadzania typów z w pełni zarządzanymi rozwiązaniami.</span><span class="sxs-lookup"><span data-stu-id="9c11d-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="9c11d-108">Po określeniu interfejsów publicznych, które mogą być osadzone, należy utworzyć klasy czasu wykonywania, które implementują te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="9c11d-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="9c11d-109">Program kliencki może osadzić informacje o typie interfejsów w czasie projektowania, `Embed Interop Types` odwołując się `True`do zestawu, który zawiera interfejsy publiczne i ustawiając właściwość odwołania do .</span><span class="sxs-lookup"><span data-stu-id="9c11d-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="9c11d-110">Program kliencki może następnie załadować wystąpienia obiektów czasu wykonywania wpisanych jako te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="9c11d-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="9c11d-111">Jest to równoważne użyciu kompilatora wiersza polecenia i odwoływaniu się do zestawu przy użyciu [opcji kompilatora -link](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="9c11d-111">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="9c11d-112">Jeśli utworzysz nową wersję zestawu uruchomieniowego o silnej nazwie, program klienta nie musi być ponownie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="9c11d-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="9c11d-113">Program kliencki nadal używa niezależnie od wersji zestawu wykonywania jest dostępna dla niego, przy użyciu informacji o typie osadzonym dla interfejsów publicznych.</span><span class="sxs-lookup"><span data-stu-id="9c11d-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="9c11d-114">W tym instruktacie:</span><span class="sxs-lookup"><span data-stu-id="9c11d-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="9c11d-115">Utwórz zestaw o silnej nazwie z interfejsem publicznym zawierającym informacje o typie, które mogą być osadzone.</span><span class="sxs-lookup"><span data-stu-id="9c11d-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="9c11d-116">Tworzenie zestawu wykonywania o silnej nazwie, który implementuje interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="9c11d-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="9c11d-117">Utwórz program kliencki, który osadza informacje o typie z interfejsu publicznego i tworzy wystąpienie klasy z zestawu czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9c11d-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="9c11d-118">Modyfikowanie i przebudowywanie zestawu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9c11d-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="9c11d-119">Uruchom program kliencki, aby zobaczyć, że używa nowej wersji zestawu runtime bez konieczności ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="9c11d-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="9c11d-120">Warunki i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9c11d-120">Conditions and limitations</span></span>

<span data-ttu-id="9c11d-121">Informacje o typie można osadzać z zestawu w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="9c11d-121">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="9c11d-122">Zestaw udostępnia co najmniej jeden interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="9c11d-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="9c11d-123">Interfejsy osadzone są oanotowane `ComImport` `Guid` atrybutami i atrybutami za pomocą unikatowych identyfikatorów GUID.</span><span class="sxs-lookup"><span data-stu-id="9c11d-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="9c11d-124">Zestaw jest oanotowany `ImportedFromTypeLib` atrybutem `PrimaryInteropAssembly` lub atrybutem i `Guid` atrybutem na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c11d-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="9c11d-125">Szablony projektów Visual C# i Visual Basic `Guid` domyślnie zawierają atrybut na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c11d-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="9c11d-126">Ponieważ podstawową funkcją osadzania typu jest obsługa zestawów współdziałania COM, podczas osadzania informacji o typie w pełni zarządzanym rozwiązaniu obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="9c11d-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="9c11d-127">Osadzone są tylko atrybuty specyficzne dla współoperacji COM.</span><span class="sxs-lookup"><span data-stu-id="9c11d-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="9c11d-128">Inne atrybuty są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9c11d-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="9c11d-129">Jeśli typ używa parametrów ogólnych, a typ parametru ogólnego jest typem osadzonym, tego typu nie można użyć na granicy zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c11d-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="9c11d-130">Przykłady przekraczania granicy złożenia obejmują wywołanie metody z innego zestawu lub wyprowadzenie typu z typu zdefiniowanego w innym złożeniu.</span><span class="sxs-lookup"><span data-stu-id="9c11d-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="9c11d-131">Stałe nie są osadzone.</span><span class="sxs-lookup"><span data-stu-id="9c11d-131">Constants are not embedded.</span></span>
- <span data-ttu-id="9c11d-132">Klasa <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> nie obsługuje typu osadzonego jako klucz.</span><span class="sxs-lookup"><span data-stu-id="9c11d-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="9c11d-133">Można zaimplementować własny typ słownika do obsługi typu osadzonego jako klucz.</span><span class="sxs-lookup"><span data-stu-id="9c11d-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="9c11d-134">Tworzenie interfejsu</span><span class="sxs-lookup"><span data-stu-id="9c11d-134">Create an interface</span></span>

<span data-ttu-id="9c11d-135">Pierwszym krokiem jest utworzenie zestawu interfejsu równoważności typu.</span><span class="sxs-lookup"><span data-stu-id="9c11d-135">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="9c11d-136">W programie Visual Studio wybierz **pozycję Plik** > **nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="9c11d-137">W oknie **dialogowym Tworzenie nowego projektu** wpisz *bibliotekę klas* w polu **Wyszukaj szablony.**</span><span class="sxs-lookup"><span data-stu-id="9c11d-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="9c11d-138">Wybierz z listy szablon C# lub Visual Basic **Class Library (.NET Framework),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-138">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="9c11d-139">W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu** *wpisz typeEquivalenceInterface*, a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="9c11d-140">Zostanie utworzony nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="9c11d-140">The new project is created.</span></span>

1. <span data-ttu-id="9c11d-141">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *Class1.cs* lub *Class1.vb,* wybierz polecenie **Zmień nazwę**i zmień nazwę pliku z *Class1* na *ISampleInterface*.</span><span class="sxs-lookup"><span data-stu-id="9c11d-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="9c11d-142">Odpowiedz **tak** na monit, `ISampleInterface`aby również zmienić nazwę klasy na .</span><span class="sxs-lookup"><span data-stu-id="9c11d-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="9c11d-143">Ta klasa reprezentuje interfejs publiczny dla klasy.</span><span class="sxs-lookup"><span data-stu-id="9c11d-143">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="9c11d-144">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface,** a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="9c11d-145">Wybierz **pozycję Konfiguruj** w lewym okienku ekranu **Właściwości** i ustaw **ścieżkę output** na lokalizację na komputerze, na przykład *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="9c11d-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="9c11d-146">W tym instruktacie jest używana ta sama lokalizacja.</span><span class="sxs-lookup"><span data-stu-id="9c11d-146">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="9c11d-147">Wybierz **pozycję Podpisywanie** w lewym okienku ekranu **Właściwości,** a następnie zaznacz pole wyboru **Podpisz złożenie.**</span><span class="sxs-lookup"><span data-stu-id="9c11d-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="9c11d-148">W rozwijanym polu **Wybierz plik klucza o silnej nazwie**wybierz pozycję **Nowy**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="9c11d-149">W oknie dialogowym **Tworzenie silnego klucza nazwy** w obszarze **Nazwa pliku klucza**wpisz polecenie *key.snk*.</span><span class="sxs-lookup"><span data-stu-id="9c11d-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="9c11d-150">Usuń zaznaczenie pola wyboru **Chroń mój plik klucza hasłem,** a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="9c11d-151">Otwórz plik klasy *ISampleInterface* w edytorze kodu i zastąp `ISampleInterface` jego zawartość następującym kodem, aby utworzyć interfejs:</span><span class="sxs-lookup"><span data-stu-id="9c11d-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

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

1. <span data-ttu-id="9c11d-152">W menu **Narzędzia** wybierz polecenie **Utwórz guid**, a w oknie dialogowym **Tworzenie identyfikatora GUID** wybierz pozycję **Format rejestru**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="9c11d-153">Wybierz **pozycję Kopiuj**, a następnie wybierz pozycję **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-153">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="9c11d-154">W `Guid` atrybucie kodu zastąp przykładowy identyfikator GUID skopiowanym identyfikatorem GUID i usuń nawiasy klamrowe (**{ }**).</span><span class="sxs-lookup"><span data-stu-id="9c11d-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="9c11d-155">W **Eksploratorze rozwiązań**rozwiń folder **Właściwości** i wybierz *plik AssemblyInfo.cs* lub *AssemblyInfo.vb.*</span><span class="sxs-lookup"><span data-stu-id="9c11d-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="9c11d-156">W edytorze kodu dodaj następujący atrybut do pliku:</span><span class="sxs-lookup"><span data-stu-id="9c11d-156">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="9c11d-157">Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="9c11d-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="9c11d-158">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Zbuduj**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="9c11d-159">Plik DLL biblioteki klas jest kompilowany i zapisywany do określonej ścieżki wyjściowej kompilacji, na przykład *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="9c11d-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="9c11d-160">Tworzenie klasy czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="9c11d-160">Create a runtime class</span></span>

<span data-ttu-id="9c11d-161">Następnie utwórz klasę wykonywania równoważności typu.</span><span class="sxs-lookup"><span data-stu-id="9c11d-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="9c11d-162">W programie Visual Studio wybierz **pozycję Plik** > **nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="9c11d-163">W oknie **dialogowym Tworzenie nowego projektu** wpisz *bibliotekę klas* w polu **Wyszukaj szablony.**</span><span class="sxs-lookup"><span data-stu-id="9c11d-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="9c11d-164">Wybierz z listy szablon C# lub Visual Basic **Class Library (.NET Framework),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-164">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="9c11d-165">W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu** *wpisz typeEquivalenceRuntime*, a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="9c11d-166">Zostanie utworzony nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="9c11d-166">The new project is created.</span></span>

1. <span data-ttu-id="9c11d-167">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem *myszy* plik Class1.cs lub *Class1.vb,* wybierz polecenie **Zmień nazwę**i zmień nazwę pliku z *Class1* na *SampleClass*.</span><span class="sxs-lookup"><span data-stu-id="9c11d-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="9c11d-168">Odpowiedz **tak** na monit, `SampleClass`aby również zmienić nazwę klasy na .</span><span class="sxs-lookup"><span data-stu-id="9c11d-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="9c11d-169">Ta klasa implementuje `ISampleInterface` interfejs.</span><span class="sxs-lookup"><span data-stu-id="9c11d-169">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="9c11d-170">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="9c11d-171">Wybierz **pozycję Konfiguruj** w lewym okienku ekranu **Właściwości,** a następnie ustaw **ścieżkę output** w tej samej lokalizacji, która została użyta dla projektu TypeEquivalenceInterface, na przykład *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="9c11d-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="9c11d-172">Wybierz **pozycję Podpisywanie** w lewym okienku ekranu **Właściwości,** a następnie zaznacz pole wyboru **Podpisz złożenie.**</span><span class="sxs-lookup"><span data-stu-id="9c11d-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="9c11d-173">W rozwijanym polu **Wybierz plik klucza o silnej nazwie**wybierz pozycję **Nowy**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="9c11d-174">W oknie dialogowym **Tworzenie silnego klucza nazwy** w obszarze **Nazwa pliku klucza**wpisz polecenie *key.snk*.</span><span class="sxs-lookup"><span data-stu-id="9c11d-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="9c11d-175">Usuń zaznaczenie pola wyboru **Chroń mój plik klucza hasłem,** a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="9c11d-176">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Dodaj** > **odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="9c11d-177">W oknie dialogowym **Menedżer odwołań** wybierz pozycję **Przeglądaj** i przejdź do folderu ścieżki wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="9c11d-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="9c11d-178">Wybierz plik *TypeEquivalenceInterface.dll,* wybierz pozycję **Dodaj**, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="9c11d-179">W **Eksploratorze rozwiązań**rozwiń folder **Odwołania** i wybierz odwołanie **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="9c11d-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="9c11d-180">W okienku Właściwości ustaw **określoną wersję** na **Fałsz,** jeśli jeszcze nie jest. **Properties**</span><span class="sxs-lookup"><span data-stu-id="9c11d-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="9c11d-181">Otwórz plik klasy *SampleClass* w edytorze kodu i zastąp `SampleClass` jego zawartość następującym kodem, aby utworzyć klasę:</span><span class="sxs-lookup"><span data-stu-id="9c11d-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

   ```csharp
   using System;
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

1. <span data-ttu-id="9c11d-182">Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="9c11d-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="9c11d-183">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Kompilacja**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="9c11d-184">Plik DLL biblioteki klas jest kompilowany i zapisywany do określonej ścieżki wyjściowej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c11d-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="9c11d-185">Tworzenie projektu klienta</span><span class="sxs-lookup"><span data-stu-id="9c11d-185">Create a client project</span></span>

<span data-ttu-id="9c11d-186">Na koniec utwórz program klienta równoważności typów, który odwołuje się do zestawu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9c11d-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="9c11d-187">W programie Visual Studio wybierz **pozycję Plik** > **nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="9c11d-188">W oknie **dialogowym Tworzenie nowego projektu** wpisz *konsolę* w polu **Wyszukaj szablony.**</span><span class="sxs-lookup"><span data-stu-id="9c11d-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="9c11d-189">Wybierz z listy szablon C# lub Visual **Basic Console App (.NET Framework),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-189">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="9c11d-190">W oknie dialogowym **Konfigurowanie nowego projektu** w obszarze **Nazwa projektu** *wpisz typ Typ RównoważnościKlient*, a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="9c11d-191">Zostanie utworzony nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="9c11d-191">The new project is created.</span></span>

1. <span data-ttu-id="9c11d-192">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceClient** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="9c11d-193">Wybierz **pozycję Konfiguruj** w lewym okienku ekranu **Właściwości,** a następnie ustaw **ścieżkę output** w tej samej lokalizacji, która została użyta dla projektu TypeEquivalenceInterface, na przykład *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="9c11d-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="9c11d-194">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceClient** i wybierz polecenie **Dodaj** > **odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="9c11d-195">Jeśli w oknie dialogowym **Menedżer odwołań,** jeśli plik **TypeEquivalenceInterface.dll** jest już wymieniony, wybierz go.</span><span class="sxs-lookup"><span data-stu-id="9c11d-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="9c11d-196">Jeśli nie, wybierz pozycję **Przeglądaj**, przejdź do folderu ścieżki wyjściowej, wybierz plik *TypeEquivalenceInterface.dll* (nie *typeEquivalenceRuntime.dll)* i wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="9c11d-197">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-197">Select **OK**.</span></span>

1. <span data-ttu-id="9c11d-198">W **Eksploratorze rozwiązań**rozwiń folder **Odwołania** i wybierz odwołanie **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="9c11d-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="9c11d-199">W okienku **Właściwości** ustaw **osadzanie typów pooperacji** na **Wartość True**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="9c11d-200">Otwórz *plik Program.cs* lub *Module1.vb* w edytorze kodu i zastąp jego zawartość następującym kodem, aby utworzyć program kliencki:</span><span class="sxs-lookup"><span data-stu-id="9c11d-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

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
   Imports System.Reflection
   Imports TypeEquivalenceInterface

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

1. <span data-ttu-id="9c11d-201">Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="9c11d-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="9c11d-202">Naciśnij **klawisz Ctrl**+**F5,** aby zbudować i uruchomić program.</span><span class="sxs-lookup"><span data-stu-id="9c11d-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="9c11d-203">Należy zauważyć, że wyjście konsoli zwraca zestaw w wersji **1.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="9c11d-204">Modyfikowanie interfejsu</span><span class="sxs-lookup"><span data-stu-id="9c11d-204">Modify the interface</span></span>

<span data-ttu-id="9c11d-205">Teraz zmodyfikuj zestaw interfejsu i zmień jego wersję.</span><span class="sxs-lookup"><span data-stu-id="9c11d-205">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="9c11d-206">W programie Visual Studio wybierz pozycję Otwórz**Open** > **projekt/rozwiązanie** **File** > pliku i otwórz projekt **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="9c11d-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="9c11d-207">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="9c11d-208">Wybierz **pozycję Aplikacja** w lewym okienku ekranu **Właściwości,** a następnie wybierz pozycję Informacje o **złożeniu**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="9c11d-209">W oknie dialogowym **Informacje o złożeniu** zmień wartości **wersja zestawu** i wersję **pliku** na *2.0.0.0*, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="9c11d-210">Otwórz *plik SampleInterface.cs* lub *SampleInterface.vb* i dodaj następujący `ISampleInterface` wiersz kodu do interfejsu:</span><span class="sxs-lookup"><span data-stu-id="9c11d-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="9c11d-211">Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="9c11d-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="9c11d-212">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceInterface** i wybierz polecenie **Zbuduj**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="9c11d-213">Nowa wersja pliku DLL biblioteki klas jest kompilowana i zapisywana w ścieżce wyjściowej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c11d-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="9c11d-214">Modyfikowanie klasy czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="9c11d-214">Modify the runtime class</span></span>

<span data-ttu-id="9c11d-215">Zmodyfikuj również klasę czasu wykonywania i zaktualizuj jej wersję.</span><span class="sxs-lookup"><span data-stu-id="9c11d-215">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="9c11d-216">W programie Visual Studio wybierz pozycję Otwórz**Open** > **projekt/rozwiązanie** **File** > pliku i otwórz projekt **TypeEquivalenceRuntime.**</span><span class="sxs-lookup"><span data-stu-id="9c11d-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="9c11d-217">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz **polecenie Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="9c11d-218">Wybierz **pozycję Aplikacja** w lewym okienku ekranu **Właściwości,** a następnie wybierz pozycję Informacje o **złożeniu**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="9c11d-219">W oknie dialogowym **Informacje o złożeniu** zmień wartości **wersja zestawu** i wersję **pliku** na *2.0.0.0*, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="9c11d-220">Otwórz *plik SampleClass.cs* lub *SampleClass.vb* i dodaj `SampleClass` następujący kod do klasy:</span><span class="sxs-lookup"><span data-stu-id="9c11d-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="9c11d-221">Wybierz **pozycję Zapisz wszystko** > **Save All** lub naciśnij **klawisz Etui Ctrl**+**Shift**+**S,** aby zapisać pliki i projekt.</span><span class="sxs-lookup"><span data-stu-id="9c11d-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="9c11d-222">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **TypeEquivalenceRuntime** i wybierz polecenie **Kompilacja**.</span><span class="sxs-lookup"><span data-stu-id="9c11d-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="9c11d-223">Nowa wersja pliku DLL biblioteki klas jest kompilowana i zapisywana w ścieżce wyjściowej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c11d-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="9c11d-224">Uruchamianie zaktualizowanego programu klienta</span><span class="sxs-lookup"><span data-stu-id="9c11d-224">Run the updated client program</span></span>

<span data-ttu-id="9c11d-225">Przejdź do lokalizacji folderu wyjściowego kompilacji i uruchom *program TypeEquivalenceClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="9c11d-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="9c11d-226">Należy zauważyć, że dane wyjściowe konsoli `TypeEquivalenceRuntime` odzwierciedla teraz nową wersję zestawu, *2.0.0.0*, bez ponownej kompilacji programu.</span><span class="sxs-lookup"><span data-stu-id="9c11d-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c11d-227">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c11d-227">See also</span></span>

- [<span data-ttu-id="9c11d-228">-link (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="9c11d-228">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="9c11d-229">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c11d-229">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="9c11d-230">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9c11d-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9c11d-231">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c11d-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="9c11d-232">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="9c11d-232">Assemblies in .NET</span></span>](index.md)
