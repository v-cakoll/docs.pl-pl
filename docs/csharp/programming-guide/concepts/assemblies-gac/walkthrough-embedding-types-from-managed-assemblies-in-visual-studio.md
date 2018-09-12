---
title: 'Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 1900c62d1ebaf611f141f8f1bdf95f8d11f82140
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44510171"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="2acae-102">Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="2acae-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="2acae-103">W przypadku osadzenia informacji o typie z zarządzanego zestawu z silną nazwą, luźno połączyć typy w aplikacji, aby osiągnąć niezależność.</span><span class="sxs-lookup"><span data-stu-id="2acae-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="2acae-104">Oznacza to by używał typów z wielu wersji zarządzanej biblioteki bez konieczności ponownie skompilowana dla każdej wersji można napisać program.</span><span class="sxs-lookup"><span data-stu-id="2acae-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="2acae-105">Osadzenie typu jest często używany za pomocą modelu COM, takie jak aplikacja, która używa obiektów automatyzacji z Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="2acae-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="2acae-106">Osadzanie informacji o typie umożliwia tym samym kompilację programu do pracy z różnymi wersjami pakietu Microsoft Office na różnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="2acae-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="2acae-107">Jednak można również użyć osadzanie przy użyciu w pełni zarządzane rozwiązanie typu.</span><span class="sxs-lookup"><span data-stu-id="2acae-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="2acae-108">Informacje o typie mogą być osadzone z zestawu, który ma następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="2acae-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="2acae-109">Zestaw udostępnia co najmniej jeden interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="2acae-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="2acae-110">Osadzone interfejsy są oznaczony za pomocą `ComImport` atrybutu i `Guid` atrybutu (i unikatowy identyfikator GUID).</span><span class="sxs-lookup"><span data-stu-id="2acae-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="2acae-111">Zestaw jest oznaczony za pomocą `ImportedFromTypeLib` atrybutu lub `PrimaryInteropAssembly` atrybut i poziomie zestawu `Guid` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2acae-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="2acae-112">(Domyślnie szablony projektu Visual C# zawiera poziomie zestawu `Guid` atrybutu.)</span><span class="sxs-lookup"><span data-stu-id="2acae-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="2acae-113">Po określeniu publicznych interfejsów, które mogą być osadzone, można utworzyć klasy środowiska wykonawczego, które implementują te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="2acae-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="2acae-114">Program kliencki następnie osadzić informacje o typie dla tych interfejsów w czasie projektowania, odwołując się do zestawu, który zawiera interfejsy publiczne i ustawienie `Embed Interop Types` właściwości odwołania do `True`.</span><span class="sxs-lookup"><span data-stu-id="2acae-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="2acae-115">Jest to równoważne do używania kompilatora wiersza polecenia i odwołanie do zestawu przy użyciu `/link` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2acae-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="2acae-116">Program kliencki może następnie załadować wystąpień obiektów środowiska uruchomieniowego wpisanych w formie tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2acae-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="2acae-117">Jeśli tworzysz nową wersję zestawu o silnej nazwie środowiska uruchomieniowego, program kliencki nie ma być ponownie kompilowane przy użyciu zestawu zaktualizowanego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="2acae-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="2acae-118">Zamiast tego program kliencki w dalszym ciągu używać niezależnie od wersji zestawu środowiska wykonawczego dostępnego, korzystając z informacji osadzonego typu interfejsów publicznych.</span><span class="sxs-lookup"><span data-stu-id="2acae-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="2acae-119">Ponieważ główna funkcja osadzania typu jest do obsługi, osadzanie informacji o typie z zestawów międzyoperacyjnych COM, gdy osadzanie informacji o typie w pełni zarządzane rozwiązanie obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="2acae-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="2acae-120">Tylko atrybuty specyficzne dla współdziałania z modelem COM są osadzone; inne atrybuty są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="2acae-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="2acae-121">Jeśli typ używa parametrów ogólnych, typ parametru ogólnego jest osadzonym typem tego typu nie można użyć granicy zestawu.</span><span class="sxs-lookup"><span data-stu-id="2acae-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="2acae-122">Przecinające się w granicach zestawu przykłady wywołanie metody z innego zestawu lub typem pochodząca z typu zdefiniowane w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="2acae-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="2acae-123">Stałe nie są osadzone.</span><span class="sxs-lookup"><span data-stu-id="2acae-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="2acae-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Klasa nie obsługuje osadzonego typu jako klucz.</span><span class="sxs-lookup"><span data-stu-id="2acae-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="2acae-125">Można zaimplementować swój własny typ słownika do obsługi osadzonego typu jako klucz.</span><span class="sxs-lookup"><span data-stu-id="2acae-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="2acae-126">W tym instruktażu wykonasz następujące:</span><span class="sxs-lookup"><span data-stu-id="2acae-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="2acae-127">Utwórz zestaw o silnej nazwie, która ma interfejs publiczny, który zawiera informacje o typie, który może zostać osadzony.</span><span class="sxs-lookup"><span data-stu-id="2acae-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="2acae-128">Utwórz zestaw o silnej nazwie środowiska uruchomieniowego, który implementuje ten interfejs publiczny.</span><span class="sxs-lookup"><span data-stu-id="2acae-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="2acae-129">Utwórz program kliencki osadza informacje o typie z publicznego interfejsu, która tworzy wystąpienie klasy z zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="2acae-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="2acae-130">Zmodyfikuj i ponownie skompiluj zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="2acae-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="2acae-131">Uruchom program klienta, aby zobaczyć, że nowa wersja zestawu środowiska wykonawczego jest używana bez konieczności ponownego kompilowania programów klienckich.</span><span class="sxs-lookup"><span data-stu-id="2acae-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="2acae-132">Tworzenie interfejsu</span><span class="sxs-lookup"><span data-stu-id="2acae-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="2acae-133">Aby utworzyć projekt interfejsu równoważności typu</span><span class="sxs-lookup"><span data-stu-id="2acae-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="2acae-134">W programie Visual Studio na **pliku** menu, wybierz **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="2acae-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="2acae-135">W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="2acae-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="2acae-136">Wybierz **biblioteki klas** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="2acae-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="2acae-137">W **nazwa** wpisz `TypeEquivalenceInterface`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2acae-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="2acae-138">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="2acae-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="2acae-139">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.cs i kliknij przycisk **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="2acae-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="2acae-140">Zmień nazwę pliku do `ISampleInterface.cs` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="2acae-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="2acae-141">Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="2acae-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="2acae-142">Ta klasa będzie reprezentować publiczny interfejs dla klasy.</span><span class="sxs-lookup"><span data-stu-id="2acae-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="2acae-143">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2acae-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="2acae-144">Kliknij przycisk **kompilacji** kartę. Ustaw ścieżkę wyjściową do prawidłowej lokalizacji na komputerze deweloperskim, takich jak `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="2acae-144">Click the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="2acae-145">Ta lokalizacja będzie używana również w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="2acae-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="2acae-146">Podczas edytowania nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji.</span><span class="sxs-lookup"><span data-stu-id="2acae-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="2acae-147">W **wybierz plik klucza o silnej nazwie** kliknij **< nowy … >**.</span><span class="sxs-lookup"><span data-stu-id="2acae-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="2acae-148">W **nazwę pliku klucza** wpisz `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="2acae-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="2acae-149">Wyczyść **Chroń mój plik klucza przy użyciu hasła** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="2acae-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="2acae-150">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2acae-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="2acae-151">Otwórz plik ISampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="2acae-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="2acae-152">Dodaj następujący kod do pliku klasy ISampleInterface, aby utworzyć interfejs ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="2acae-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
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
  
7.  <span data-ttu-id="2acae-153">Na **narzędzia** menu, kliknij przycisk **Utwórz Guid**.</span><span class="sxs-lookup"><span data-stu-id="2acae-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="2acae-154">W **Utwórz GUID** okno dialogowe, kliknij przycisk **Format rejestru** a następnie kliknij przycisk **kopiowania**.</span><span class="sxs-lookup"><span data-stu-id="2acae-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="2acae-155">Kliknij przycisk **zakończenia**.</span><span class="sxs-lookup"><span data-stu-id="2acae-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="2acae-156">W `Guid` atrybutu, usuwanie przykładowy identyfikator GUID i wkleić identyfikator GUID, który został skopiowany z **Utwórz GUID** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="2acae-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="2acae-157">Usuń nawiasy klamrowe ({}) ze skopiowanego identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="2acae-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="2acae-158">W **Eksploratora rozwiązań**, rozwiń węzeł **właściwości** folderu.</span><span class="sxs-lookup"><span data-stu-id="2acae-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="2acae-159">Kliknij dwukrotnie plik AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="2acae-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="2acae-160">Dodaj następujący atrybut w pliku.</span><span class="sxs-lookup"><span data-stu-id="2acae-160">Add the following attribute to the file.</span></span>  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     <span data-ttu-id="2acae-161">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="2acae-161">Save the file.</span></span>  
  
10. <span data-ttu-id="2acae-162">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="2acae-162">Save the project.</span></span>  
  
11. <span data-ttu-id="2acae-163">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="2acae-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="2acae-164">Plik klasy biblioteki .dll jest kompilowany i zapisać ścieżkę wyjściową określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="2acae-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="2acae-165">Tworzenie klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2acae-165">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="2acae-166">Aby utworzyć projekt środowiska uruchomieniowego równoważności typu</span><span class="sxs-lookup"><span data-stu-id="2acae-166">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="2acae-167">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="2acae-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="2acae-168">W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="2acae-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="2acae-169">Wybierz **biblioteki klas** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="2acae-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="2acae-170">W **nazwa** wpisz `TypeEquivalenceRuntime`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2acae-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="2acae-171">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="2acae-171">The new project is created.</span></span>  
  
3.  <span data-ttu-id="2acae-172">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Class1.cs i kliknij przycisk **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="2acae-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="2acae-173">Zmień nazwę pliku do `SampleClass.cs` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="2acae-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="2acae-174">Również zmienić nazwę pliku zmienia nazwę klasy, która ma `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="2acae-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="2acae-175">Ta klasa wdroży `ISampleInterface` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2acae-175">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="2acae-176">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2acae-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="2acae-177">Kliknij przycisk **kompilacji** kartę. Ustaw ścieżkę wyjściową do tej samej lokalizacji, które są używane w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="2acae-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="2acae-178">Podczas edytowania nadal właściwości projektu, kliknij przycisk **podpisywanie** kartę. Wybierz **Podpisz zestaw** opcji.</span><span class="sxs-lookup"><span data-stu-id="2acae-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="2acae-179">W **wybierz plik klucza o silnej nazwie** kliknij **< nowy … >**.</span><span class="sxs-lookup"><span data-stu-id="2acae-179">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="2acae-180">W **nazwę pliku klucza** wpisz `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="2acae-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="2acae-181">Wyczyść **Chroń mój plik klucza przy użyciu hasła** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="2acae-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="2acae-182">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2acae-182">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="2acae-183">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="2acae-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="2acae-184">Kliknij przycisk **Przeglądaj** kartę, a następnie przejdź do folderu o podanej ścieżce danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2acae-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="2acae-185">Wybierz plik TypeEquivalenceInterface.dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2acae-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="2acae-186">W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu.</span><span class="sxs-lookup"><span data-stu-id="2acae-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="2acae-187">Wybierz odwołanie TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="2acae-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="2acae-188">W oknie dialogowym właściwości odwołania TypeEquivalenceInterface ustaw **określonej wersji** właściwości **False**.</span><span class="sxs-lookup"><span data-stu-id="2acae-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
8.  <span data-ttu-id="2acae-189">Dodaj następujący kod do pliku klasy SampleClass, aby utworzyć klasę SampleClass.</span><span class="sxs-lookup"><span data-stu-id="2acae-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
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
  
9. <span data-ttu-id="2acae-190">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="2acae-190">Save the project.</span></span>  
  
10. <span data-ttu-id="2acae-191">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="2acae-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="2acae-192">Plik klasy biblioteki .dll jest kompilowany i zapisać ścieżkę wyjściową określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="2acae-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="2acae-193">Tworzenie projektu klienta</span><span class="sxs-lookup"><span data-stu-id="2acae-193">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="2acae-194">Aby utworzyć projekt klienta równoważności typu</span><span class="sxs-lookup"><span data-stu-id="2acae-194">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="2acae-195">W programie Visual Studio na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="2acae-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="2acae-196">W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="2acae-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="2acae-197">Wybierz **aplikację Konsolową** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="2acae-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="2acae-198">W **nazwa** wpisz `TypeEquivalenceClient`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2acae-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="2acae-199">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="2acae-199">The new project is created.</span></span>  
  
3.  <span data-ttu-id="2acae-200">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2acae-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="2acae-201">Kliknij przycisk **kompilacji** kartę. Ustaw ścieżkę wyjściową do tej samej lokalizacji, które są używane w projekcie TypeEquivalenceInterface, na przykład `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="2acae-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="2acae-202">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceClient, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="2acae-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="2acae-203">Kliknij przycisk **Przeglądaj** kartę, a następnie przejdź do folderu o podanej ścieżce danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2acae-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="2acae-204">Wybierz plik TypeEquivalenceInterface.dll (nie TypeEquivalenceRuntime.dll), a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2acae-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="2acae-205">W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** folderu.</span><span class="sxs-lookup"><span data-stu-id="2acae-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="2acae-206">Wybierz odwołanie TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="2acae-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="2acae-207">W oknie dialogowym właściwości odwołania TypeEquivalenceInterface ustaw **Osadź typy współdziałania** właściwości **True**.</span><span class="sxs-lookup"><span data-stu-id="2acae-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
6.  <span data-ttu-id="2acae-208">Dodaj następujący kod do pliku Program.cs, aby utworzyć program kliencki.</span><span class="sxs-lookup"><span data-stu-id="2acae-208">Add the following code to the Program.cs file to create the client program.</span></span>  
  
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
  
7.  <span data-ttu-id="2acae-209">Naciśnij kombinację klawiszy CTRL + F5, aby skompilować i uruchomić program.</span><span class="sxs-lookup"><span data-stu-id="2acae-209">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="2acae-210">Modyfikowanie interfejsu</span><span class="sxs-lookup"><span data-stu-id="2acae-210">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="2acae-211">Aby zmodyfikować interfejs</span><span class="sxs-lookup"><span data-stu-id="2acae-211">To modify the interface</span></span>  
  
1.  <span data-ttu-id="2acae-212">W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="2acae-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="2acae-213">W **Otwórz projekt** okno dialogowe, kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2acae-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="2acae-214">Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacje o zestawie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="2acae-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="2acae-215">Zmiana **wersji zestawu** i **wersja pliku** wartości `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="2acae-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="2acae-216">Otwórz plik SampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="2acae-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="2acae-217">Dodaj następujący wiersz kodu do interfejsu ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="2acae-217">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     <span data-ttu-id="2acae-218">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="2acae-218">Save the file.</span></span>  
  
4.  <span data-ttu-id="2acae-219">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="2acae-219">Save the project.</span></span>  
  
5.  <span data-ttu-id="2acae-220">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceInterface, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="2acae-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="2acae-221">Nową wersję pliku klasy biblioteki .dll jest kompilowany i zapisać w ścieżce wyjściowej określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="2acae-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="2acae-222">Modyfikowanie klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2acae-222">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="2acae-223">Aby zmodyfikować klasy środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2acae-223">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="2acae-224">W programie Visual Studio na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="2acae-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="2acae-225">W **Otwórz projekt** okna dialogowego pole, kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime i kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2acae-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="2acae-226">Kliknij przycisk **aplikacji** kartę. Kliknij przycisk **informacje o zestawie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="2acae-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="2acae-227">Zmiana **wersji zestawu** i **wersja pliku** wartości `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="2acae-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="2acae-228">Otwórz plik SampleClass.cs.</span><span class="sxs-lookup"><span data-stu-id="2acae-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="2acae-229">Dodaj następujące wiersze kodu do klasy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="2acae-229">Add the following lines of code to the SampleClass class.</span></span>  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     <span data-ttu-id="2acae-230">Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="2acae-230">Save the file.</span></span>  
  
4.  <span data-ttu-id="2acae-231">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="2acae-231">Save the project.</span></span>  
  
5.  <span data-ttu-id="2acae-232">Kliknij prawym przyciskiem myszy projekt TypeEquivalenceRuntime, a następnie kliknij przycisk **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="2acae-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="2acae-233">Zaktualizowaną wersję pliku klasy biblioteki .dll jest kompilowany i zapisać w ścieżce wyjściowej wcześniej określonej kompilacji (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="2acae-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="2acae-234">W Eksploratorze plików otwórz folder wyjściowy ścieżki (na przykład C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="2acae-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="2acae-235">Kliknij dwukrotnie TypeEquivalenceClient.exe do uruchomienia programu.</span><span class="sxs-lookup"><span data-stu-id="2acae-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="2acae-236">Program będzie odzwierciedlać nową wersję zestawu TypeEquivalenceRuntime bez konieczności został ponownie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="2acae-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2acae-237">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2acae-237">See Also</span></span>

- [<span data-ttu-id="2acae-238">/ Link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="2acae-238">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
- [<span data-ttu-id="2acae-239">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2acae-239">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2acae-240">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="2acae-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
- [<span data-ttu-id="2acae-241">Zestawy i Globalna pamięć podręczna zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="2acae-241">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
