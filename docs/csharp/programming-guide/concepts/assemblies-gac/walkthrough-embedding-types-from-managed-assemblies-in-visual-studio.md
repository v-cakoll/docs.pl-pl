---
title: 'Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual StudioC#()'
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 5e6494f133128e3982aa07323d2c65b9fa5de47b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595797"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="d3049-102">Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual StudioC#()</span><span class="sxs-lookup"><span data-stu-id="d3049-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>

<span data-ttu-id="d3049-103">Jeśli osadzisz informacje o typie z zestawu o silnej nazwie zarządzanej, możesz luźno połączyć typy w aplikacji, aby osiągnąć niezależność wersji.</span><span class="sxs-lookup"><span data-stu-id="d3049-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="d3049-104">Oznacza to, że program można napisać tak, aby używał typów z wielu wersji biblioteki zarządzanej bez konieczności ponownego kompilowania dla każdej wersji.</span><span class="sxs-lookup"><span data-stu-id="d3049-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>

<span data-ttu-id="d3049-105">Osadzanie typów jest często używane z międzyoperacyjnym modelem COM, takim jak aplikacja, która korzysta z obiektów automatyzacji z Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="d3049-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="d3049-106">Osadzanie informacji o typie umożliwia tej samej kompilacji programu do pracy z różnymi wersjami Microsoft Office na różnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="d3049-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="d3049-107">Można jednak również używać osadzania typu z w pełni zarządzanym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="d3049-107">However, you can also use type embedding with a fully managed solution.</span></span>

<span data-ttu-id="d3049-108">Informacje o typie mogą być osadzone z zestawu o następujących cechach:</span><span class="sxs-lookup"><span data-stu-id="d3049-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>

- <span data-ttu-id="d3049-109">Zestaw uwidacznia co najmniej jeden interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="d3049-109">The assembly exposes at least one public interface.</span></span>

- <span data-ttu-id="d3049-110">Interfejsy osadzone mają adnotację z `ComImport` atrybutem `Guid` i atrybutem (i unikatowym identyfikatorem GUID).</span><span class="sxs-lookup"><span data-stu-id="d3049-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>

- <span data-ttu-id="d3049-111">Zestaw jest oznaczony `ImportedFromTypeLib` atrybutem `PrimaryInteropAssembly` lub atrybutem i atrybutem na poziomie `Guid` zestawu.</span><span class="sxs-lookup"><span data-stu-id="d3049-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="d3049-112">(Domyślnie szablony projektów wizualnych C# zawierają atrybut na poziomie `Guid` zestawu).</span><span class="sxs-lookup"><span data-stu-id="d3049-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>

<span data-ttu-id="d3049-113">Po określeniu interfejsów publicznych, które mogą być osadzone, można utworzyć klasy środowiska uruchomieniowego, które implementują te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="d3049-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="d3049-114">Program kliencki może następnie osadzić informacje o typie dla tych interfejsów w czasie projektowania, odwołując się do zestawu, który zawiera interfejsy publiczne, `Embed Interop Types` i ustawiając właściwość odwołania na `True`.</span><span class="sxs-lookup"><span data-stu-id="d3049-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="d3049-115">Jest to równoznaczne z użyciem kompilatora wiersza polecenia i odwołującego się do zestawu `/link` przy użyciu opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d3049-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="d3049-116">Następnie program kliencki może ładować wystąpienia obiektów środowiska uruchomieniowego, które zostały wpisane jako te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="d3049-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="d3049-117">Jeśli utworzysz nową wersję zestawu o silnej nazwie środowiska uruchomieniowego, program kliencki nie musi zostać ponownie skompilowany przy użyciu zaktualizowanego zestawu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d3049-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="d3049-118">Zamiast tego program kliencki nadal korzysta z niezależnej wersji zestawu środowiska uruchomieniowego, przy użyciu informacji o typie osadzonym dla interfejsów publicznych.</span><span class="sxs-lookup"><span data-stu-id="d3049-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="d3049-119">Ponieważ podstawową funkcją osadzania typu jest obsługa osadzania informacji o typie z zestawów międzyoperacyjnych modelu COM, podczas osadzania informacji o typie w w pełni zarządzanym rozwiązaniu obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="d3049-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>

- <span data-ttu-id="d3049-120">Osadzone są tylko atrybuty specyficzne dla międzyoperacyjnego modelu COM; inne atrybuty są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="d3049-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>

- <span data-ttu-id="d3049-121">Jeśli typ korzysta z parametrów ogólnych, a typ parametru generycznego jest typem osadzonym, ten typ nie może być używany między granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="d3049-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="d3049-122">Przykłady przekroczenia granicy zestawu obejmują wywołanie metody z innego zestawu lub pochodny typ z typu zdefiniowanego w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="d3049-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>

- <span data-ttu-id="d3049-123">Stałe nie są osadzone.</span><span class="sxs-lookup"><span data-stu-id="d3049-123">Constants are not embedded.</span></span>

- <span data-ttu-id="d3049-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Klasa nie obsługuje osadzonego typu jako klucza.</span><span class="sxs-lookup"><span data-stu-id="d3049-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="d3049-125">Możesz zaimplementować własny typ słownika, aby obsługiwał typ osadzony jako klucz.</span><span class="sxs-lookup"><span data-stu-id="d3049-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>

<span data-ttu-id="d3049-126">W tym instruktażu wykonasz następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="d3049-126">In this walkthrough, you will do the following:</span></span>

- <span data-ttu-id="d3049-127">Utwórz zestaw o silnej nazwie z interfejsem publicznym zawierającym informacje o typie, które mogą być osadzone.</span><span class="sxs-lookup"><span data-stu-id="d3049-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>

- <span data-ttu-id="d3049-128">Utwórz zestaw o silnej nazwie środowiska uruchomieniowego, który implementuje ten interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="d3049-128">Create a strong-named runtime assembly that implements that public interface.</span></span>

- <span data-ttu-id="d3049-129">Utwórz program kliencki, który osadzi informacje o typie z interfejsu publicznego i tworzy wystąpienie klasy z zestawu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d3049-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>

- <span data-ttu-id="d3049-130">Modyfikowanie i ponowne kompilowanie zestawu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d3049-130">Modify and rebuild the runtime assembly.</span></span>

- <span data-ttu-id="d3049-131">Uruchom program kliencki, aby zobaczyć, że nowa wersja zestawu środowiska uruchomieniowego jest używana bez konieczności ponownego kompilowania programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="d3049-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a><span data-ttu-id="d3049-132">Tworzenie interfejsu</span><span class="sxs-lookup"><span data-stu-id="d3049-132">Creating an Interface</span></span>

#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="d3049-133">Aby utworzyć projekt interfejsu równoważności typu</span><span class="sxs-lookup"><span data-stu-id="d3049-133">To create the type equivalence interface project</span></span>

1. <span data-ttu-id="d3049-134">W programie Visual Studio w menu **plik** wybierz polecenie **Nowy** , a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="d3049-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>

2. <span data-ttu-id="d3049-135">W oknie dialogowym **Nowy projekt** w okienku **typy projektów** upewnij się, że wybrano opcję **Windows** .</span><span class="sxs-lookup"><span data-stu-id="d3049-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d3049-136">W okienku **Szablony** wybierz pozycję **Biblioteka klas** .</span><span class="sxs-lookup"><span data-stu-id="d3049-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="d3049-137">W polu **Nazwa** wpisz `TypeEquivalenceInterface`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3049-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="d3049-138">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="d3049-138">The new project is created.</span></span>

3. <span data-ttu-id="d3049-139">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik Class1.cs i kliknij polecenie **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="d3049-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="d3049-140">Zmień nazwę pliku na `ISampleInterface.cs` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="d3049-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="d3049-141">Zmiana nazwy pliku spowoduje również zmianę nazwy klasy na `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="d3049-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="d3049-142">Ta klasa będzie reprezentować interfejs publiczny dla klasy.</span><span class="sxs-lookup"><span data-stu-id="d3049-142">This class will represent the public interface for the class.</span></span>

4. <span data-ttu-id="d3049-143">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d3049-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="d3049-144">Kliknij kartę **kompilacja** . Skonfiguruj ścieżkę wyjściową do prawidłowej lokalizacji na komputerze deweloperskim, `C:\TypeEquivalenceSample`na przykład.</span><span class="sxs-lookup"><span data-stu-id="d3049-144">Click the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="d3049-145">Ta lokalizacja będzie również używana w kolejnym kroku w tym instruktażu.</span><span class="sxs-lookup"><span data-stu-id="d3049-145">This location will also be used in a later step in this walkthrough.</span></span>

5. <span data-ttu-id="d3049-146">Edytując właściwości projektu, kliknij kartę podpisywanie . Wybierz opcję **podpisz zestaw** .</span><span class="sxs-lookup"><span data-stu-id="d3049-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="d3049-147">Na liście **Wybierz plik klucza o silnej nazwie** kliknij pozycję  **\<nowy... >** .</span><span class="sxs-lookup"><span data-stu-id="d3049-147">In the **Choose a strong name key file** list, click **\<New...>**.</span></span> <span data-ttu-id="d3049-148">W polu **Nazwa pliku klucza** wpisz `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="d3049-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="d3049-149">Wyczyść pole wyboru **Chroń mój klucz plik hasłem** .</span><span class="sxs-lookup"><span data-stu-id="d3049-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="d3049-150">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3049-150">Click **OK**.</span></span>

6. <span data-ttu-id="d3049-151">Otwórz plik ISampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="d3049-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="d3049-152">Dodaj następujący kod do pliku klasy ISampleInterface, aby utworzyć interfejs ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="d3049-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>

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

7. <span data-ttu-id="d3049-153">W menu **Narzędzia** kliknij polecenie **Utwórz identyfikator GUID**.</span><span class="sxs-lookup"><span data-stu-id="d3049-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="d3049-154">W oknie dialogowym **Tworzenie identyfikatora GUID** kliknij przycisk **Format rejestru** , a następnie kliknij przycisk **Kopiuj**.</span><span class="sxs-lookup"><span data-stu-id="d3049-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="d3049-155">Kliknij przycisk **zakończenia**.</span><span class="sxs-lookup"><span data-stu-id="d3049-155">Click **Exit**.</span></span>

8. <span data-ttu-id="d3049-156">W atrybucie Usuń przykładowy identyfikator GUID i wklej identyfikator GUID, który został skopiowany z okna dialogowego **Tworzenie identyfikatora GUID.** `Guid`</span><span class="sxs-lookup"><span data-stu-id="d3049-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="d3049-157">Usuń nawiasy klamrowe{}() ze skopiowanego identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="d3049-157">Remove the braces ({}) from the copied GUID.</span></span>

9. <span data-ttu-id="d3049-158">W **Eksplorator rozwiązań**rozwiń folder **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="d3049-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="d3049-159">Kliknij dwukrotnie plik AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="d3049-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="d3049-160">Dodaj do pliku następujący atrybut.</span><span class="sxs-lookup"><span data-stu-id="d3049-160">Add the following attribute to the file.</span></span>

    ```csharp
    [assembly: ImportedFromTypeLib("")]
    ```

     <span data-ttu-id="d3049-161">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="d3049-161">Save the file.</span></span>

10. <span data-ttu-id="d3049-162">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="d3049-162">Save the project.</span></span>

11. <span data-ttu-id="d3049-163">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface i kliknij pozycję **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="d3049-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="d3049-164">Plik Library. dll został skompilowany i zapisany w określonej ścieżce danych wyjściowych kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3049-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-runtime-class"></a><span data-ttu-id="d3049-165">Tworzenie klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d3049-165">Creating a Runtime Class</span></span>

#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="d3049-166">Aby utworzyć projekt z równoważeniem typu w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="d3049-166">To create the type equivalence runtime project</span></span>

1. <span data-ttu-id="d3049-167">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d3049-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="d3049-168">W oknie dialogowym **Nowy projekt** w okienku **typy projektów** upewnij się, że wybrano opcję **Windows** .</span><span class="sxs-lookup"><span data-stu-id="d3049-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d3049-169">W okienku **Szablony** wybierz pozycję **Biblioteka klas** .</span><span class="sxs-lookup"><span data-stu-id="d3049-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="d3049-170">W polu **Nazwa** wpisz `TypeEquivalenceRuntime`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3049-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="d3049-171">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="d3049-171">The new project is created.</span></span>

3. <span data-ttu-id="d3049-172">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik Class1.cs i kliknij polecenie **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="d3049-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="d3049-173">Zmień nazwę pliku na `SampleClass.cs` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="d3049-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="d3049-174">Zmiana nazwy pliku zmienia również nazwę klasy na `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="d3049-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="d3049-175">Ta klasa będzie implementować `ISampleInterface` interfejs.</span><span class="sxs-lookup"><span data-stu-id="d3049-175">This class will implement the `ISampleInterface` interface.</span></span>

4. <span data-ttu-id="d3049-176">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d3049-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="d3049-177">Kliknij kartę **kompilacja** . Ustaw ścieżkę wyjściową do tej samej lokalizacji, która została użyta w projekcie TypeEquivalenceInterface, na `C:\TypeEquivalenceSample`przykład.</span><span class="sxs-lookup"><span data-stu-id="d3049-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

5. <span data-ttu-id="d3049-178">Edytując właściwości projektu, kliknij kartę podpisywanie . Wybierz opcję **podpisz zestaw** .</span><span class="sxs-lookup"><span data-stu-id="d3049-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="d3049-179">Na liście **Wybierz plik klucza o silnej nazwie** kliknij pozycję  **\<nowy... >** .</span><span class="sxs-lookup"><span data-stu-id="d3049-179">In the **Choose a strong name key file** list, click **\<New...>**.</span></span> <span data-ttu-id="d3049-180">W polu **Nazwa pliku klucza** wpisz `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="d3049-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="d3049-181">Wyczyść pole wyboru **Chroń mój klucz plik hasłem** .</span><span class="sxs-lookup"><span data-stu-id="d3049-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="d3049-182">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3049-182">Click **OK**.</span></span>

6. <span data-ttu-id="d3049-183">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d3049-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="d3049-184">Kliknij kartę **Przeglądaj** i przejdź do folderu Ścieżka wyjściowa.</span><span class="sxs-lookup"><span data-stu-id="d3049-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="d3049-185">Wybierz plik TypeEquivalenceInterface. dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3049-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>

7. <span data-ttu-id="d3049-186">W **Eksplorator rozwiązań**rozwiń folder **odwołania** .</span><span class="sxs-lookup"><span data-stu-id="d3049-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="d3049-187">Wybierz odwołanie TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="d3049-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="d3049-188">W okno Właściwości odwołania TypeEquivalenceInterface ustaw właściwość **określona wersja** na **false**.</span><span class="sxs-lookup"><span data-stu-id="d3049-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>

8. <span data-ttu-id="d3049-189">Dodaj następujący kod do pliku klasy SampleClass, aby utworzyć klasę SampleClass.</span><span class="sxs-lookup"><span data-stu-id="d3049-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>

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

9. <span data-ttu-id="d3049-190">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="d3049-190">Save the project.</span></span>

10. <span data-ttu-id="d3049-191">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime i kliknij pozycję **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="d3049-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="d3049-192">Plik Library. dll został skompilowany i zapisany w określonej ścieżce danych wyjściowych kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3049-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-client-project"></a><span data-ttu-id="d3049-193">Tworzenie projektu klienta</span><span class="sxs-lookup"><span data-stu-id="d3049-193">Creating a Client Project</span></span>

#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="d3049-194">Aby utworzyć projekt klienta równoważność typu</span><span class="sxs-lookup"><span data-stu-id="d3049-194">To create the type equivalence client project</span></span>

1. <span data-ttu-id="d3049-195">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d3049-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="d3049-196">W oknie dialogowym **Nowy projekt** w okienku **typy projektów** upewnij się, że wybrano opcję **Windows** .</span><span class="sxs-lookup"><span data-stu-id="d3049-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d3049-197">Wybierz pozycję **Aplikacja konsolowa** w okienku **Szablony** .</span><span class="sxs-lookup"><span data-stu-id="d3049-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="d3049-198">W polu **Nazwa** wpisz `TypeEquivalenceClient`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3049-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="d3049-199">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="d3049-199">The new project is created.</span></span>

3. <span data-ttu-id="d3049-200">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d3049-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="d3049-201">Kliknij kartę **kompilacja** . Ustaw ścieżkę wyjściową do tej samej lokalizacji, która została użyta w projekcie TypeEquivalenceInterface, na `C:\TypeEquivalenceSample`przykład.</span><span class="sxs-lookup"><span data-stu-id="d3049-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

4. <span data-ttu-id="d3049-202">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d3049-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="d3049-203">Kliknij kartę **Przeglądaj** i przejdź do folderu Ścieżka wyjściowa.</span><span class="sxs-lookup"><span data-stu-id="d3049-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="d3049-204">Wybierz plik TypeEquivalenceInterface. dll (nie TypeEquivalenceRuntime. dll), a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3049-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>

5. <span data-ttu-id="d3049-205">W **Eksplorator rozwiązań**rozwiń folder **odwołania** .</span><span class="sxs-lookup"><span data-stu-id="d3049-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="d3049-206">Wybierz odwołanie TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="d3049-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="d3049-207">W okno Właściwości odwołania TypeEquivalenceInterface ustaw właściwość **Osadź typy** współdziałania na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="d3049-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>

6. <span data-ttu-id="d3049-208">Dodaj następujący kod do pliku Program.cs, aby utworzyć program kliencki.</span><span class="sxs-lookup"><span data-stu-id="d3049-208">Add the following code to the Program.cs file to create the client program.</span></span>

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

7. <span data-ttu-id="d3049-209">Naciśnij kombinację klawiszy CTRL + F5, aby skompilować i uruchomić program.</span><span class="sxs-lookup"><span data-stu-id="d3049-209">Press CTRL+F5 to build and run the program.</span></span>

## <a name="modifying-the-interface"></a><span data-ttu-id="d3049-210">Modyfikowanie interfejsu</span><span class="sxs-lookup"><span data-stu-id="d3049-210">Modifying the Interface</span></span>

#### <a name="to-modify-the-interface"></a><span data-ttu-id="d3049-211">Aby zmodyfikować interfejs</span><span class="sxs-lookup"><span data-stu-id="d3049-211">To modify the interface</span></span>

1. <span data-ttu-id="d3049-212">W programie Visual Studio w menu **plik** wskaż polecenie **Otwórz**, a następnie kliknij pozycję **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="d3049-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="d3049-213">W oknie dialogowym **Otwórz projekt** kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d3049-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="d3049-214">Kliknij kartę **aplikacja** . Kliknij przycisk **Informacje o zestawie** .</span><span class="sxs-lookup"><span data-stu-id="d3049-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="d3049-215">Zmień **wersję zestawu** i wartość **wersji pliku** na `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="d3049-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="d3049-216">Otwórz plik SampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="d3049-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="d3049-217">Dodaj następujący wiersz kodu do interfejsu ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="d3049-217">Add the following line of code to the ISampleInterface interface.</span></span>

    ```csharp
    DateTime GetDate();
    ```

    <span data-ttu-id="d3049-218">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="d3049-218">Save the file.</span></span>

4. <span data-ttu-id="d3049-219">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="d3049-219">Save the project.</span></span>

5. <span data-ttu-id="d3049-220">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface i kliknij pozycję **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="d3049-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="d3049-221">Nowa wersja pliku dll biblioteki klas została skompilowana i zapisana w określonej ścieżce danych wyjściowych kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3049-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="modifying-the-runtime-class"></a><span data-ttu-id="d3049-222">Modyfikowanie klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d3049-222">Modifying the Runtime Class</span></span>

#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="d3049-223">Aby zmodyfikować klasę środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d3049-223">To modify the runtime class</span></span>

1. <span data-ttu-id="d3049-224">W programie Visual Studio w menu **plik** wskaż polecenie **Otwórz**, a następnie kliknij pozycję **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="d3049-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="d3049-225">W oknie dialogowym **Otwórz projekt** kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d3049-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="d3049-226">Kliknij kartę **aplikacja** . Kliknij przycisk **Informacje o zestawie** .</span><span class="sxs-lookup"><span data-stu-id="d3049-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="d3049-227">Zmień **wersję zestawu** i wartość **wersji pliku** na `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="d3049-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="d3049-228">Otwórz plik SampleClass.cs.</span><span class="sxs-lookup"><span data-stu-id="d3049-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="d3049-229">Dodaj następujące wiersze kodu do klasy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="d3049-229">Add the following lines of code to the SampleClass class.</span></span>

    ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
    ```

    <span data-ttu-id="d3049-230">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="d3049-230">Save the file.</span></span>

4. <span data-ttu-id="d3049-231">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="d3049-231">Save the project.</span></span>

5. <span data-ttu-id="d3049-232">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime i kliknij pozycję **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="d3049-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="d3049-233">Zaktualizowana wersja pliku dll biblioteki klas została skompilowana i zapisana w wcześniej określonej ścieżce danych wyjściowych kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3049-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

6. <span data-ttu-id="d3049-234">W Eksploratorze plików otwórz folder Ścieżka wyjściowa (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3049-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="d3049-235">Kliknij dwukrotnie plik TypeEquivalenceClient. exe, aby uruchomić program.</span><span class="sxs-lookup"><span data-stu-id="d3049-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="d3049-236">Program będzie odzwierciedlał nową wersję zestawu TypeEquivalenceRuntime bez ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="d3049-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3049-237">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3049-237">See also</span></span>

- [<span data-ttu-id="d3049-238">/Link (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="d3049-238">/link (C# Compiler Options)</span></span>](../../../language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="d3049-239">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d3049-239">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="d3049-240">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="d3049-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="d3049-241">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="d3049-241">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
