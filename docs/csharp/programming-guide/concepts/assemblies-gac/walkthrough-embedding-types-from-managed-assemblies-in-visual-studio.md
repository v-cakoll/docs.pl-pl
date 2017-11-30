---
title: "Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cbd95c71525a92714ab5758855964e323345b2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="46315-102">Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="46315-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="46315-103">Osadzenie informacji o typie z zarządzanego zestawu o silnej nazwie słabo można połączyć typów w aplikacji w celu osiągnięcia niezależność od wersji.</span><span class="sxs-lookup"><span data-stu-id="46315-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="46315-104">Oznacza to, że program mogą być zapisywane na użyć typów z wielu wersji biblioteki zarządzanej, bez konieczności ponownie skompilowana dla każdej wersji.</span><span class="sxs-lookup"><span data-stu-id="46315-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="46315-105">Osadzenie typu jest często używany pomocą modelu COM, takie jak aplikacji, która używa obiekty automatyzacji z witryny Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="46315-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="46315-106">Osadzanie informacji o typie włącza tę samą kompilację programu w różnych wersjach pakietu Microsoft Office na różnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="46315-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="46315-107">Jednak umożliwia także osadzanie z pełni zarządzane rozwiązanie typu.</span><span class="sxs-lookup"><span data-stu-id="46315-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="46315-108">Można ją osadzić informacji o typie z zestawu, który ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="46315-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="46315-109">Zestaw ujawnia co najmniej jeden interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="46315-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="46315-110">Osadzony interfejsy są opatrzoną `ComImport` atrybutu i `Guid` atrybutu (i unikatowy identyfikator GUID).</span><span class="sxs-lookup"><span data-stu-id="46315-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="46315-111">Zestaw jest oznaczony za pomocą `ImportedFromTypeLib` atrybutu lub `PrimaryInteropAssembly` atrybut i poziomu zestawu `Guid` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="46315-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="46315-112">(Domyślnie szablony projektów Visual C# obejmuje dane poziomu zestawu `Guid` atrybutu.)</span><span class="sxs-lookup"><span data-stu-id="46315-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="46315-113">Po określeniu interfejsów publicznych, które mogą być osadzone, można utworzyć klasy środowiska uruchomieniowego, które implementują te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="46315-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="46315-114">Program kliencki może następnie osadź informacji o typie dla tych interfejsów w czasie projektowania, umieszczając odwołanie do zestawu, który zawiera interfejsy publiczne i ustawienie `Embed Interop Types` właściwości odwołania do `True`.</span><span class="sxs-lookup"><span data-stu-id="46315-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="46315-115">Jest to równoważne przy użyciu kompilatora wiersza polecenia i odwołanie do zestawu przy użyciu `/link` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="46315-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="46315-116">Program kliencki może następnie załadowanie wystąpień obiektów czasu wykonywania typu te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="46315-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="46315-117">Jeśli tworzysz nową wersję używanemu zestawowi silną nazwą środowiska uruchomieniowego, program kliencki nie ma do ponownej kompilacji z zestawu zaktualizowane środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="46315-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="46315-118">Zamiast tego program kliencki będzie później nadal używać niezależnie od wersji zestawu środowiska wykonawczego jest dostępna, korzystając z informacji osadzonym typem interfejsów publicznych.</span><span class="sxs-lookup"><span data-stu-id="46315-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="46315-119">Ponieważ podstawowej funkcji typu osadzenia obsługuje osadzanie informacji o typie z zestawów międzyoperacyjnych COM, osadzenia informacji o typie w pełni zarządzane rozwiązanie obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="46315-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="46315-120">Tylko atrybuty specyficzne dla międzyoperacyjności z modelem COM są osadzone; inne atrybuty są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="46315-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="46315-121">Jeśli typem używa parametrów ogólnych i typ parametru ogólnego jest osadzonym typem, tego typu nie można użyć granicy zestawu.</span><span class="sxs-lookup"><span data-stu-id="46315-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="46315-122">Przekraczaniu granic zestawu przykładów wywoływanie metody z innego zestawu lub typu pochodnego od typu zdefiniowanej w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="46315-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="46315-123">Stałe nie są osadzone.</span><span class="sxs-lookup"><span data-stu-id="46315-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="46315-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Klasa nie obsługuje typu osadzonego jako klucza.</span><span class="sxs-lookup"><span data-stu-id="46315-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="46315-125">Można zaimplementować własne typu słownika do obsługi typu osadzonego jako klucza.</span><span class="sxs-lookup"><span data-stu-id="46315-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="46315-126">W tym przewodniku spowoduje wykonanie następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="46315-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="46315-127">Utwórz zestaw o silnej nazwie zawiera interfejs publiczny, który zawiera informacje o typie, który można ją osadzić.</span><span class="sxs-lookup"><span data-stu-id="46315-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="46315-128">Tworzenie zestawu o silnej nazwie środowiska uruchomieniowego, który implementuje ten interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="46315-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="46315-129">Utwórz program kliencki osadza informacje o typie z interfejsu publicznego, który tworzy wystąpienie klasy z zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="46315-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="46315-130">Zmodyfikuj i skompiluj ponownie zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="46315-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="46315-131">Uruchom program klienta, aby zobaczyć, że nowa wersja zestawu czasu wykonywania jest używana bez konieczności ponownego kompilowania programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="46315-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="46315-132">Tworzenie interfejsu</span><span class="sxs-lookup"><span data-stu-id="46315-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="46315-133">Aby utworzyć projekt interfejsu pełnienia roli równoważnika typu</span><span class="sxs-lookup"><span data-stu-id="46315-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="46315-134">W programie Visual Studio na **pliku** menu, wybierz **nowy** , a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="46315-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="46315-135">W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="46315-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="46315-136">Wybierz **biblioteki klas** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="46315-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="46315-137">W **nazwa** wpisz `TypeEquivalenceInterface`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="46315-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="46315-138">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="46315-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="46315-139">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.cs i kliknij przycisk **zmienić**.</span><span class="sxs-lookup"><span data-stu-id="46315-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="46315-140">Zmień nazwę pliku do `ISampleInterface.cs` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="46315-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="46315-141">Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="46315-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="46315-142">Ta klasa będzie reprezentować publiczny interfejs dla klasy.</span><span class="sxs-lookup"><span data-stu-id="46315-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="46315-143">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="46315-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="46315-144">Kliknij przycisk **kompilacji** kartę. Ustaw ścieżkę wyjściową do prawidłowej lokalizacji na komputerze deweloperskim takich jak `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="46315-144">Click the the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="46315-145">Ta lokalizacja będą również używane w kolejnym kroku w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="46315-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="46315-146">Podczas edycji nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji.</span><span class="sxs-lookup"><span data-stu-id="46315-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="46315-147">W **wybierz plik klucza o silnej nazwie** kliknij **< nowy... >**.</span><span class="sxs-lookup"><span data-stu-id="46315-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="46315-148">W **nazwę pliku klucza** wpisz `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="46315-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="46315-149">Wyczyść **ochrony pliku klucza przy użyciu hasła** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="46315-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="46315-150">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="46315-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="46315-151">Otwórz plik ISampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="46315-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="46315-152">Dodaj następujący kod do pliku klasy ISampleInterface utworzyć interfejsu ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="46315-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
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
  
7.  <span data-ttu-id="46315-153">Na **narzędzia** menu, kliknij przycisk **utworzyć identyfikatora Guid**.</span><span class="sxs-lookup"><span data-stu-id="46315-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="46315-154">W **utworzyć identyfikatora GUID** okno dialogowe, kliknij przycisk **Format rejestru** , a następnie kliknij przycisk **kopiowania**.</span><span class="sxs-lookup"><span data-stu-id="46315-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="46315-155">Kliknij przycisk **zakończenia**.</span><span class="sxs-lookup"><span data-stu-id="46315-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="46315-156">W `Guid` atrybutu, usuń przykładowe identyfikator GUID i Wklej skopiowany z identyfikatora GUID **utworzyć identyfikatora GUID** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="46315-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="46315-157">Usuń nawiasy klamrowe ({}) skopiowanych identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="46315-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="46315-158">W **Eksploratora rozwiązań**, rozwiń węzeł **właściwości** folderu.</span><span class="sxs-lookup"><span data-stu-id="46315-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="46315-159">Kliknij dwukrotnie plik AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="46315-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="46315-160">Dodaj następujący atrybut w pliku.</span><span class="sxs-lookup"><span data-stu-id="46315-160">Add the following attribute to the file.</span></span>  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     <span data-ttu-id="46315-161">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="46315-161">Save the file.</span></span>  
  
10. <span data-ttu-id="46315-162">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="46315-162">Save the project.</span></span>  
  
11. <span data-ttu-id="46315-163">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="46315-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="46315-164">Plik klasy biblioteki DLL są kompilowane i zapisane w ścieżce wyjściowej określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="46315-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="46315-165">Tworzenie klasy środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="46315-165">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="46315-166">Aby utworzyć projekt środowiska uruchomieniowego pełnienia roli równoważnika typu</span><span class="sxs-lookup"><span data-stu-id="46315-166">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="46315-167">W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="46315-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="46315-168">W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="46315-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="46315-169">Wybierz **biblioteki klas** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="46315-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="46315-170">W **nazwa** wpisz `TypeEquivalenceRuntime`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="46315-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="46315-171">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="46315-171">The new project is created.</span></span>  
  
3.  <span data-ttu-id="46315-172">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.cs i kliknij przycisk **zmienić**.</span><span class="sxs-lookup"><span data-stu-id="46315-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="46315-173">Zmień nazwę pliku do `SampleClass.cs` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="46315-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="46315-174">Zmiana nazwy pliku również zmienia nazwę klasy, która ma `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="46315-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="46315-175">Ta klasa będzie implementowany `ISampleInterface` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="46315-175">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="46315-176">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="46315-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="46315-177">Kliknij przycisk **kompilacji** kartę. Ustaw ścieżkę danych wyjściowych do tej samej lokalizacji, używany w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="46315-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="46315-178">Podczas edycji nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji.</span><span class="sxs-lookup"><span data-stu-id="46315-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="46315-179">W **wybierz plik klucza o silnej nazwie** kliknij **< nowy... >**.</span><span class="sxs-lookup"><span data-stu-id="46315-179">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="46315-180">W **nazwę pliku klucza** wpisz `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="46315-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="46315-181">Wyczyść **ochrony pliku klucza przy użyciu hasła** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="46315-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="46315-182">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="46315-182">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="46315-183">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="46315-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="46315-184">Kliknij przycisk **Przeglądaj** karcie i przejdź do folderu o podanej ścieżce danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="46315-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="46315-185">Wybierz plik TypeEquivalenceInterface.dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="46315-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="46315-186">W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu.</span><span class="sxs-lookup"><span data-stu-id="46315-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="46315-187">Wybierz odwołanie TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="46315-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="46315-188">W oknie właściwości odwołania TypeEquivalenceInterface ustawić **określonej wersji** właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="46315-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
8.  <span data-ttu-id="46315-189">Dodaj następujący kod do pliku klasy SampleClass, aby utworzyć klasę SampleClass.</span><span class="sxs-lookup"><span data-stu-id="46315-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
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
    )  
    ```  
  
9. <span data-ttu-id="46315-190">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="46315-190">Save the project.</span></span>  
  
10. <span data-ttu-id="46315-191">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="46315-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="46315-192">Plik klasy biblioteki DLL są kompilowane i zapisane w ścieżce wyjściowej określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="46315-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="46315-193">Tworzenie projektu klienta</span><span class="sxs-lookup"><span data-stu-id="46315-193">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="46315-194">Aby utworzyć projekt klienta pełnienia roli równoważnika typu</span><span class="sxs-lookup"><span data-stu-id="46315-194">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="46315-195">W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="46315-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="46315-196">W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="46315-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="46315-197">Wybierz **aplikacji konsoli** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="46315-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="46315-198">W **nazwa** wpisz `TypeEquivalenceClient`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="46315-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="46315-199">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="46315-199">The new project is created.</span></span>  
  
3.  <span data-ttu-id="46315-200">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="46315-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="46315-201">Kliknij przycisk **kompilacji** kartę. Ustaw ścieżkę danych wyjściowych do tej samej lokalizacji, używany w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="46315-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="46315-202">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="46315-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="46315-203">Kliknij przycisk **Przeglądaj** karcie i przejdź do folderu o podanej ścieżce danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="46315-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="46315-204">Wybierz plik TypeEquivalenceInterface.dll (nie TypeEquivalenceRuntime.dll), a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="46315-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="46315-205">W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu.</span><span class="sxs-lookup"><span data-stu-id="46315-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="46315-206">Wybierz odwołanie TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="46315-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="46315-207">W oknie właściwości odwołania TypeEquivalenceInterface ustawić **Osadź typy międzyoperacyjne** właściwości **True**.</span><span class="sxs-lookup"><span data-stu-id="46315-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
6.  <span data-ttu-id="46315-208">Dodaj następujący kod do pliku Program.cs, aby utworzyć program klienta.</span><span class="sxs-lookup"><span data-stu-id="46315-208">Add the following code to the Program.cs file to create the client program.</span></span>  
  
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
  
7.  <span data-ttu-id="46315-209">Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić program.</span><span class="sxs-lookup"><span data-stu-id="46315-209">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="46315-210">Modyfikowanie interfejsu</span><span class="sxs-lookup"><span data-stu-id="46315-210">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="46315-211">Aby zmodyfikować interfejs</span><span class="sxs-lookup"><span data-stu-id="46315-211">To modify the interface</span></span>  
  
1.  <span data-ttu-id="46315-212">W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projektu/rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="46315-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="46315-213">W **Otwórz projekt** okno dialogowe, kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="46315-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="46315-214">Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacji o zestawie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="46315-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="46315-215">Zmień **wersja zestawu** i **wersja pliku** wartości do `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="46315-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="46315-216">Otwórz plik SampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="46315-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="46315-217">Dodaj następujący wiersz kodu do interfejsu ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="46315-217">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     <span data-ttu-id="46315-218">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="46315-218">Save the file.</span></span>  
  
4.  <span data-ttu-id="46315-219">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="46315-219">Save the project.</span></span>  
  
5.  <span data-ttu-id="46315-220">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="46315-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="46315-221">Nowa wersja pliku klasy biblioteki DLL są kompilowane i zapisać w ścieżce wyjściowej określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="46315-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="46315-222">Modyfikowanie klasy środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="46315-222">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="46315-223">Aby zmodyfikować klasy środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="46315-223">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="46315-224">W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projektu/rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="46315-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="46315-225">W **Otwórz projekt** okno dialogowe, kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime i kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="46315-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="46315-226">Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacji o zestawie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="46315-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="46315-227">Zmień **wersja zestawu** i **wersja pliku** wartości do `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="46315-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="46315-228">Otwórz plik SampleClass.cs.</span><span class="sxs-lookup"><span data-stu-id="46315-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="46315-229">Dodaj następujące wiersze kodu do klasy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="46315-229">Add the following lines of code to the SampleClass class.</span></span>  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     <span data-ttu-id="46315-230">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="46315-230">Save the file.</span></span>  
  
4.  <span data-ttu-id="46315-231">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="46315-231">Save the project.</span></span>  
  
5.  <span data-ttu-id="46315-232">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="46315-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="46315-233">Zaktualizowaną wersję pliku klasy biblioteki DLL są kompilowane i zapisać w ścieżce wyjściowej wcześniej określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="46315-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="46315-234">W Eksploratorze plików otwórz folder wyjściowy ścieżki (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="46315-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="46315-235">Kliknij dwukrotnie TypeEquivalenceClient.exe do uruchomienia programu.</span><span class="sxs-lookup"><span data-stu-id="46315-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="46315-236">Program będzie odzwierciedlać nową wersję zestawu TypeEquivalenceRuntime bez konieczności została ponownie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="46315-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46315-237">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46315-237">See Also</span></span>  
 [<span data-ttu-id="46315-238">/ Link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="46315-238">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="46315-239">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="46315-239">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46315-240">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="46315-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="46315-241">Zestawy i Globalna pamięć podręczna zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="46315-241">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
