---
title: 'Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 1f6176746b783d020c809fb0b5d55d741ce0148b
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245479"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="45777-102">Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45777-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="45777-103">W przypadku osadzenia informacji o typie z zarządzanego zestawu z silną nazwą, luźno połączyć typy w aplikacji, aby osiągnąć niezależność.</span><span class="sxs-lookup"><span data-stu-id="45777-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="45777-104">Oznacza to by używał typów z wielu wersji zarządzanej biblioteki bez konieczności ponownie skompilowana dla każdej wersji można napisać program.</span><span class="sxs-lookup"><span data-stu-id="45777-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="45777-105">Osadzenie typu jest często używany za pomocą modelu COM, takie jak aplikacja, która używa obiektów automatyzacji z Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="45777-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="45777-106">Osadzanie informacji o typie umożliwia tym samym kompilację programu do pracy z różnymi wersjami pakietu Microsoft Office na różnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="45777-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="45777-107">Jednak można również użyć osadzanie przy użyciu w pełni zarządzane rozwiązanie typu.</span><span class="sxs-lookup"><span data-stu-id="45777-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="45777-108">Informacje o typie mogą być osadzone z zestawu, który ma następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="45777-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="45777-109">Zestaw udostępnia co najmniej jeden interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="45777-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="45777-110">Osadzone interfejsy są oznaczony za pomocą `ComImport` atrybutu i `Guid` atrybutu (i unikatowy identyfikator GUID).</span><span class="sxs-lookup"><span data-stu-id="45777-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="45777-111">Zestaw jest oznaczony za pomocą `ImportedFromTypeLib` atrybutu lub `PrimaryInteropAssembly` atrybut i poziomie zestawu `Guid` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="45777-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="45777-112">(Domyślnie szablony projektów Visual Basic zawierają na poziomie zestawu `Guid` atrybutu.)</span><span class="sxs-lookup"><span data-stu-id="45777-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="45777-113">Po określeniu publicznych interfejsów, które mogą być osadzone, można utworzyć klasy środowiska wykonawczego, które implementują te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="45777-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="45777-114">Program kliencki następnie osadzić informacje o typie dla tych interfejsów w czasie projektowania, odwołując się do zestawu, który zawiera interfejsy publiczne i ustawienie `Embed Interop Types` właściwości odwołania do `True`.</span><span class="sxs-lookup"><span data-stu-id="45777-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="45777-115">Jest to równoważne do używania kompilatora wiersza polecenia i odwołanie do zestawu przy użyciu `/link` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="45777-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="45777-116">Program kliencki może następnie załadować wystąpień obiektów środowiska uruchomieniowego wpisanych w formie tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="45777-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="45777-117">Jeśli tworzysz nową wersję zestawu o silnej nazwie środowiska uruchomieniowego, program kliencki nie ma być ponownie kompilowane przy użyciu zestawu zaktualizowanego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="45777-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="45777-118">Zamiast tego program kliencki w dalszym ciągu używać niezależnie od wersji zestawu środowiska wykonawczego dostępnego, korzystając z informacji osadzonego typu interfejsów publicznych.</span><span class="sxs-lookup"><span data-stu-id="45777-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="45777-119">Ponieważ główna funkcja osadzania typu jest do obsługi, osadzanie informacji o typie z zestawów międzyoperacyjnych COM, gdy osadzanie informacji o typie w pełni zarządzane rozwiązanie obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="45777-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="45777-120">Tylko atrybuty specyficzne dla współdziałania z modelem COM są osadzone; inne atrybuty są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="45777-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="45777-121">Jeśli typ używa parametrów ogólnych, typ parametru ogólnego jest osadzonym typem tego typu nie można użyć granicy zestawu.</span><span class="sxs-lookup"><span data-stu-id="45777-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="45777-122">Przecinające się w granicach zestawu przykłady wywołanie metody z innego zestawu lub typem pochodząca z typu zdefiniowane w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="45777-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="45777-123">Stałe nie są osadzone.</span><span class="sxs-lookup"><span data-stu-id="45777-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="45777-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Klasa nie obsługuje osadzonego typu jako klucz.</span><span class="sxs-lookup"><span data-stu-id="45777-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="45777-125">Można zaimplementować swój własny typ słownika do obsługi osadzonego typu jako klucz.</span><span class="sxs-lookup"><span data-stu-id="45777-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="45777-126">W tym instruktażu wykonasz następujące:</span><span class="sxs-lookup"><span data-stu-id="45777-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="45777-127">Utwórz zestaw o silnej nazwie, która ma interfejs publiczny, który zawiera informacje o typie, który może zostać osadzony.</span><span class="sxs-lookup"><span data-stu-id="45777-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="45777-128">Utwórz zestaw o silnej nazwie środowiska uruchomieniowego, który implementuje ten interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="45777-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="45777-129">Utwórz program kliencki osadza informacje o typie z publicznego interfejsu, która tworzy wystąpienie klasy z zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="45777-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="45777-130">Zmodyfikuj i ponownie skompiluj zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="45777-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="45777-131">Uruchom program klienta, aby zobaczyć, że nowa wersja zestawu środowiska wykonawczego jest używana bez konieczności ponownego kompilowania programów klienckich.</span><span class="sxs-lookup"><span data-stu-id="45777-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="45777-132">Tworzenie interfejsu</span><span class="sxs-lookup"><span data-stu-id="45777-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="45777-133">Aby utworzyć projekt interfejsu równoważności typu</span><span class="sxs-lookup"><span data-stu-id="45777-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="45777-134">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="45777-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="45777-135">W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="45777-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="45777-136">Wybierz **biblioteki klas** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="45777-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="45777-137">W **nazwa** wpisz `TypeEquivalenceInterface`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="45777-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="45777-138">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="45777-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="45777-139">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.vb i kliknij przycisk **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="45777-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="45777-140">Zmień nazwę pliku do `ISampleInterface.vb` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="45777-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="45777-141">Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="45777-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="45777-142">Ta klasa będzie reprezentować publiczny interfejs dla klasy.</span><span class="sxs-lookup"><span data-stu-id="45777-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="45777-143">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="45777-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="45777-144">Kliknij przycisk **skompilować** kartę. Ustaw ścieżkę wyjściową do prawidłowej lokalizacji na komputerze deweloperskim, takich jak `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="45777-144">Click the **Compile** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="45777-145">Ta lokalizacja będzie używana również w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="45777-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="45777-146">Podczas edytowania nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji.</span><span class="sxs-lookup"><span data-stu-id="45777-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="45777-147">W **wybierz plik klucza o silnej nazwie** kliknij **< nowy … >**.</span><span class="sxs-lookup"><span data-stu-id="45777-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="45777-148">W **nazwę pliku klucza** wpisz `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="45777-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="45777-149">Wyczyść **Chroń mój plik klucza przy użyciu hasła** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="45777-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="45777-150">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="45777-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="45777-151">Otwórz plik ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="45777-151">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="45777-152">Dodaj następujący kod do pliku klasy ISampleInterface, aby utworzyć interfejs ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="45777-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  <span data-ttu-id="45777-153">Na **narzędzia** menu, kliknij przycisk **Utwórz Guid**.</span><span class="sxs-lookup"><span data-stu-id="45777-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="45777-154">W **Utwórz GUID** okno dialogowe, kliknij przycisk **Format rejestru** a następnie kliknij przycisk **kopiowania**.</span><span class="sxs-lookup"><span data-stu-id="45777-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="45777-155">Kliknij przycisk **zakończenia**.</span><span class="sxs-lookup"><span data-stu-id="45777-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="45777-156">W `Guid` atrybutu, usuwanie przykładowy identyfikator GUID i wkleić identyfikator GUID, który został skopiowany z **Utwórz GUID** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="45777-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="45777-157">Usuń nawiasy klamrowe ({}) ze skopiowanego identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="45777-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="45777-158">Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="45777-158">On the **Project** menu, click **Show All Files**.</span></span>  
  
10. <span data-ttu-id="45777-159">W **Eksploratora rozwiązań**, rozwiń węzeł **mój projekt** folderu.</span><span class="sxs-lookup"><span data-stu-id="45777-159">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="45777-160">Kliknij dwukrotnie AssemblyInfo.vb.</span><span class="sxs-lookup"><span data-stu-id="45777-160">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="45777-161">Dodaj następujący atrybut w pliku.</span><span class="sxs-lookup"><span data-stu-id="45777-161">Add the following attribute to the file.</span></span>  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     <span data-ttu-id="45777-162">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="45777-162">Save the file.</span></span>  
  
11. <span data-ttu-id="45777-163">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="45777-163">Save the project.</span></span>  
  
12. <span data-ttu-id="45777-164">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="45777-164">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="45777-165">Plik klasy biblioteki .dll jest kompilowany i zapisać ścieżkę wyjściową określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="45777-165">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="45777-166">Tworzenie klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="45777-166">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="45777-167">Aby utworzyć projekt środowiska uruchomieniowego równoważności typu</span><span class="sxs-lookup"><span data-stu-id="45777-167">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="45777-168">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="45777-168">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="45777-169">W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="45777-169">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="45777-170">Wybierz **biblioteki klas** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="45777-170">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="45777-171">W **nazwa** wpisz `TypeEquivalenceRuntime`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="45777-171">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="45777-172">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="45777-172">The new project is created.</span></span>  
  
3.  <span data-ttu-id="45777-173">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.vb i kliknij przycisk **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="45777-173">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="45777-174">Zmień nazwę pliku do `SampleClass.vb` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="45777-174">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="45777-175">Również zmienić nazwę pliku zmienia nazwę klasy, która ma `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="45777-175">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="45777-176">Ta klasa wdroży `ISampleInterface` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="45777-176">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="45777-177">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="45777-177">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="45777-178">Kliknij przycisk **skompilować** kartę. Ustaw ścieżkę wyjściową do tej samej lokalizacji, które są używane w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="45777-178">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="45777-179">Podczas edytowania nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji.</span><span class="sxs-lookup"><span data-stu-id="45777-179">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="45777-180">W **wybierz plik klucza o silnej nazwie** kliknij **< nowy … >**.</span><span class="sxs-lookup"><span data-stu-id="45777-180">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="45777-181">W **nazwę pliku klucza** wpisz `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="45777-181">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="45777-182">Wyczyść **Chroń mój plik klucza przy użyciu hasła** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="45777-182">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="45777-183">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="45777-183">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="45777-184">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="45777-184">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="45777-185">Kliknij przycisk **Przeglądaj** kartę, a następnie przejdź do folderu o podanej ścieżce danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="45777-185">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="45777-186">Wybierz plik TypeEquivalenceInterface.dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="45777-186">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="45777-187">Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="45777-187">On the **Project** menu, click **Show All Files**.</span></span>  
  
8.  <span data-ttu-id="45777-188">W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu.</span><span class="sxs-lookup"><span data-stu-id="45777-188">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="45777-189">Wybierz odwołanie TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="45777-189">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="45777-190">W oknie dialogowym właściwości odwołania TypeEquivalenceInterface ustaw **określonej wersji** właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="45777-190">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
9. <span data-ttu-id="45777-191">Dodaj następujący kod do pliku klasy SampleClass, aby utworzyć klasę SampleClass.</span><span class="sxs-lookup"><span data-stu-id="45777-191">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
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
  
10. <span data-ttu-id="45777-192">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="45777-192">Save the project.</span></span>  
  
11. <span data-ttu-id="45777-193">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="45777-193">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="45777-194">Plik klasy biblioteki .dll jest kompilowany i zapisać ścieżkę wyjściową określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="45777-194">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="45777-195">Tworzenie projektu klienta</span><span class="sxs-lookup"><span data-stu-id="45777-195">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="45777-196">Aby utworzyć projekt klienta równoważności typu</span><span class="sxs-lookup"><span data-stu-id="45777-196">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="45777-197">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="45777-197">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="45777-198">W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="45777-198">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="45777-199">Wybierz **aplikację Konsolową** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="45777-199">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="45777-200">W **nazwa** wpisz `TypeEquivalenceClient`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="45777-200">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="45777-201">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="45777-201">The new project is created.</span></span>  
  
3.  <span data-ttu-id="45777-202">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="45777-202">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="45777-203">Kliknij przycisk **skompilować** kartę. Ustaw ścieżkę wyjściową do tej samej lokalizacji, które są używane w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="45777-203">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="45777-204">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="45777-204">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="45777-205">Kliknij przycisk **Przeglądaj** kartę, a następnie przejdź do folderu o podanej ścieżce danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="45777-205">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="45777-206">Wybierz plik TypeEquivalenceInterface.dll (nie TypeEquivalenceRuntime.dll), a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="45777-206">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="45777-207">Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.</span><span class="sxs-lookup"><span data-stu-id="45777-207">On the **Project** menu, click **Show All Files**.</span></span>  
  
6.  <span data-ttu-id="45777-208">W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu.</span><span class="sxs-lookup"><span data-stu-id="45777-208">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="45777-209">Wybierz odwołanie TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="45777-209">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="45777-210">W oknie dialogowym właściwości odwołania TypeEquivalenceInterface ustaw **Osadź typy współdziałania** właściwości **True**.</span><span class="sxs-lookup"><span data-stu-id="45777-210">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
7.  <span data-ttu-id="45777-211">Dodaj następujący kod do pliku Module1.vb, aby utworzyć program klienta.</span><span class="sxs-lookup"><span data-stu-id="45777-211">Add the following code to the Module1.vb file to create the client program.</span></span>  
  
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
  
8.  <span data-ttu-id="45777-212">Naciśnij kombinację klawiszy CTRL + F5, aby skompilować i uruchomić program.</span><span class="sxs-lookup"><span data-stu-id="45777-212">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="45777-213">Modyfikowanie interfejsu</span><span class="sxs-lookup"><span data-stu-id="45777-213">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="45777-214">Aby zmodyfikować interfejs</span><span class="sxs-lookup"><span data-stu-id="45777-214">To modify the interface</span></span>  
  
1.  <span data-ttu-id="45777-215">W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="45777-215">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="45777-216">W **Otwórz projekt** okno dialogowe, kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="45777-216">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="45777-217">Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacje o zestawie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="45777-217">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="45777-218">Zmiana **wersji zestawu** i **wersja pliku** wartości `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="45777-218">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="45777-219">Otwórz plik ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="45777-219">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="45777-220">Dodaj następujący wiersz kodu do interfejsu ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="45777-220">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     <span data-ttu-id="45777-221">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="45777-221">Save the file.</span></span>  
  
4.  <span data-ttu-id="45777-222">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="45777-222">Save the project.</span></span>  
  
5.  <span data-ttu-id="45777-223">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="45777-223">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="45777-224">Nową wersję pliku klasy biblioteki .dll jest kompilowany i zapisać w ścieżce wyjściowej określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="45777-224">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="45777-225">Modyfikowanie klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="45777-225">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="45777-226">Aby zmodyfikować klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="45777-226">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="45777-227">W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="45777-227">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="45777-228">W **Otwórz projekt** okna dialogowego pole, kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime i kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="45777-228">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="45777-229">Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacje o zestawie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="45777-229">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="45777-230">Zmiana **wersji zestawu** i **wersja pliku** wartości `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="45777-230">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="45777-231">Otwórz SampleClass.vbfile.</span><span class="sxs-lookup"><span data-stu-id="45777-231">Open the SampleClass.vbfile.</span></span> <span data-ttu-id="45777-232">Dodaj następujące wiersze kodu do klasy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="45777-232">Add the following lines of code to the SampleClass class.</span></span>  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  <span data-ttu-id="45777-233">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="45777-233">Save the project.</span></span>  
  
5.  <span data-ttu-id="45777-234">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="45777-234">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="45777-235">Zaktualizowaną wersję pliku klasy biblioteki .dll jest kompilowany i zapisać w ścieżce wyjściowej wcześniej określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="45777-235">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="45777-236">W Eksploratorze plików otwórz folder wyjściowy ścieżki (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="45777-236">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="45777-237">Kliknij dwukrotnie TypeEquivalenceClient.exe do uruchomienia programu.</span><span class="sxs-lookup"><span data-stu-id="45777-237">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="45777-238">Program będzie odzwierciedlać nową wersję zestawu TypeEquivalenceRuntime bez konieczności został ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="45777-238">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45777-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45777-239">See Also</span></span>  
 [<span data-ttu-id="45777-240">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45777-240">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="45777-241">Pojęcia związane z programowaniem</span><span class="sxs-lookup"><span data-stu-id="45777-241">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="45777-242">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="45777-242">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="45777-243">Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45777-243">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
