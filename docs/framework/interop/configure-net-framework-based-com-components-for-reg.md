---
title: 'Poradnik: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework'
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: dedf5ab51ab5cf9befb5bd183968388406df4e5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181460"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="dba2b-102">Poradnik: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dba2b-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="dba2b-103">Aktywacja bez rejestracji dla składników opartych na platformie .NET Framework jest tylko nieco bardziej skomplikowana niż w przypadku składników COM.</span><span class="sxs-lookup"><span data-stu-id="dba2b-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="dba2b-104">Konfiguracja wymaga dwóch manifestów:</span><span class="sxs-lookup"><span data-stu-id="dba2b-104">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="dba2b-105">Aplikacje COM muszą mieć manifest aplikacji w stylu Win32, aby zidentyfikować składnik zarządzany.</span><span class="sxs-lookup"><span data-stu-id="dba2b-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="dba2b-106">Składniki oparte na platformie .NET Framework muszą mieć manifest składnika dla informacji aktywacji potrzebnych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dba2b-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="dba2b-107">W tym temacie opisano sposób skojarzenia manifestu aplikacji z aplikacją; skojarzyć manifest komponentu ze składnikiem; i osadź manifest komponentu w złożeniu.</span><span class="sxs-lookup"><span data-stu-id="dba2b-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="dba2b-108">Aby utworzyć manifest aplikacji</span><span class="sxs-lookup"><span data-stu-id="dba2b-108">To create an application manifest</span></span>  
  
1. <span data-ttu-id="dba2b-109">Za pomocą edytora XML utwórz (lub zmodyfikuj) manifest aplikacji należący do aplikacji COM, który współpracuje z co najmniej jednym składnikiem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="dba2b-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="dba2b-110">Wstaw następujący standardowy nagłówek na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="dba2b-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="dba2b-111">Aby uzyskać informacje o elementach manifestu i ich [atrybutach,](/windows/desktop/SbsCs/application-manifests)zobacz Manifesty aplikacji .</span><span class="sxs-lookup"><span data-stu-id="dba2b-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="dba2b-112">Zidentyfikuj właściciela manifestu.</span><span class="sxs-lookup"><span data-stu-id="dba2b-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="dba2b-113">W poniższym `myComApp` przykładzie wersja 1 jest właścicielem pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="dba2b-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />  
    ```  
  
4. <span data-ttu-id="dba2b-114">Identyfikowanie zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="dba2b-114">Identify dependent assemblies.</span></span> <span data-ttu-id="dba2b-115">W poniższym `myComApp` przykładzie `myManagedComp`zależy od .</span><span class="sxs-lookup"><span data-stu-id="dba2b-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="x86"
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myManagedComp"
                        version="6.0.0.0"
                        processorArchitecture="X86"
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="dba2b-116">Zapisz i nazwij plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="dba2b-116">Save and name the manifest file.</span></span> <span data-ttu-id="dba2b-117">Nazwa manifestu aplikacji jest nazwą pliku wykonywalnego zestawu, po którym następuje rozszerzenie .manifest.</span><span class="sxs-lookup"><span data-stu-id="dba2b-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="dba2b-118">Na przykład nazwa pliku manifestu aplikacji dla myComApp.exe to myComApp.exe.manifest.</span><span class="sxs-lookup"><span data-stu-id="dba2b-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="dba2b-119">Manifest aplikacji można zainstalować w tym samym katalogu co aplikacja COM.</span><span class="sxs-lookup"><span data-stu-id="dba2b-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="dba2b-120">Alternatywnie można dodać go jako zasób do pliku .exe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dba2b-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="dba2b-121">Aby uzyskać dodatkowe informacje, Aby uzyskać więcej informacji, zobacz [Informacje o złożeniach obok siebie](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="dba2b-121">For additional information, For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="dba2b-122">Aby utworzyć manifest komponentu</span><span class="sxs-lookup"><span data-stu-id="dba2b-122">To create a component manifest</span></span>  
  
1. <span data-ttu-id="dba2b-123">Za pomocą edytora XML utwórz manifest składnika, aby opisać zarządzany zestaw.</span><span class="sxs-lookup"><span data-stu-id="dba2b-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="dba2b-124">Wstaw następujący standardowy nagłówek na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="dba2b-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. <span data-ttu-id="dba2b-125">Zidentyfikuj właściciela pliku.</span><span class="sxs-lookup"><span data-stu-id="dba2b-125">Identify the owner of the file.</span></span> <span data-ttu-id="dba2b-126">Element `<assemblyIdentity>` `<dependentAssembly>` elementu w pliku manifestu aplikacji musi być zgodny z elementem manifestu składnika.</span><span class="sxs-lookup"><span data-stu-id="dba2b-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="dba2b-127">W poniższym `myManagedComp` przykładzie wersja 1.2.3.4 jest właścicielem pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="dba2b-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4. <span data-ttu-id="dba2b-128">Zidentyfikuj każdą klasę w zestawie.</span><span class="sxs-lookup"><span data-stu-id="dba2b-128">Identify each class in the assembly.</span></span> <span data-ttu-id="dba2b-129">Użyj `<clrClass>` elementu, aby jednoznacznie zidentyfikować każdą klasę w zestawie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="dba2b-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="dba2b-130">Element, który jest podśrodkiem `<assembly>` elementu, ma atrybuty opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="dba2b-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="dba2b-131">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dba2b-131">Attribute</span></span>|<span data-ttu-id="dba2b-132">Opis</span><span class="sxs-lookup"><span data-stu-id="dba2b-132">Description</span></span>|<span data-ttu-id="dba2b-133">Wymagany</span><span class="sxs-lookup"><span data-stu-id="dba2b-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="dba2b-134">Identyfikator, który określa klasę, która ma zostać aktywowana.</span><span class="sxs-lookup"><span data-stu-id="dba2b-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="dba2b-135">Tak</span><span class="sxs-lookup"><span data-stu-id="dba2b-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="dba2b-136">Ciąg, który informuje użytkownika o składniku.</span><span class="sxs-lookup"><span data-stu-id="dba2b-136">A string that informs the user about the component.</span></span> <span data-ttu-id="dba2b-137">Pusty ciąg jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="dba2b-137">An empty string is the default.</span></span>|<span data-ttu-id="dba2b-138">Nie</span><span class="sxs-lookup"><span data-stu-id="dba2b-138">No</span></span>|  
    |`name`|<span data-ttu-id="dba2b-139">Ciąg reprezentujący klasę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="dba2b-139">A string that represents the managed class.</span></span>|<span data-ttu-id="dba2b-140">Tak</span><span class="sxs-lookup"><span data-stu-id="dba2b-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="dba2b-141">Identyfikator, który ma być używany do aktywacji z późnym użyciem.</span><span class="sxs-lookup"><span data-stu-id="dba2b-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="dba2b-142">Nie</span><span class="sxs-lookup"><span data-stu-id="dba2b-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="dba2b-143">Model gwintowania COM.</span><span class="sxs-lookup"><span data-stu-id="dba2b-143">The COM threading model.</span></span> <span data-ttu-id="dba2b-144">"Oba" jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="dba2b-144">"Both" is the default value.</span></span>|<span data-ttu-id="dba2b-145">Nie</span><span class="sxs-lookup"><span data-stu-id="dba2b-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="dba2b-146">Określa wersję wspólnego środowiska wykonawczego języka (CLR) do użycia.</span><span class="sxs-lookup"><span data-stu-id="dba2b-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="dba2b-147">Jeśli ten atrybut nie zostanie określony, a program CLR nie jest jeszcze załadowany, składnik jest ładowany z najnowszym zainstalowanym programem CLR przed programem CLR w wersji 4.</span><span class="sxs-lookup"><span data-stu-id="dba2b-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="dba2b-148">Jeśli określisz v1.0.3705, v1.1.4322 lub v2.0.50727, wersja automatycznie przekieruje do najnowszej zainstalowanej wersji CLR przed CLR w wersji 4 (zwykle v2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="dba2b-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="dba2b-149">Jeśli inna wersja CLR jest już załadowany i określoną wersję można załadować obok siebie w procesie, określona wersja jest ładowany; w przeciwnym razie używany jest załadowany clr.</span><span class="sxs-lookup"><span data-stu-id="dba2b-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="dba2b-150">Może to spowodować awarię obciążenia.</span><span class="sxs-lookup"><span data-stu-id="dba2b-150">This might cause a load failure.</span></span>|<span data-ttu-id="dba2b-151">Nie</span><span class="sxs-lookup"><span data-stu-id="dba2b-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="dba2b-152">Identyfikator biblioteki typów zawierający informacje o typie klasy.</span><span class="sxs-lookup"><span data-stu-id="dba2b-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="dba2b-153">Nie</span><span class="sxs-lookup"><span data-stu-id="dba2b-153">No</span></span>|  
  
     <span data-ttu-id="dba2b-154">We wszystkich tagach atrybutów rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="dba2b-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="dba2b-155">Można uzyskać clsids, progids, modele wątków i wersji środowiska wykonawczego, wyświetlając eksportowane biblioteki typów dla zestawu z OLE/COM ObjectViewer (Oleview.exe).</span><span class="sxs-lookup"><span data-stu-id="dba2b-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="dba2b-156">Poniższy manifest składnika identyfikuje `testClass1` `testClass2`dwie klasy i .</span><span class="sxs-lookup"><span data-stu-id="dba2b-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="dba2b-157">Zapisz i nazwij plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="dba2b-157">Save and name the manifest file.</span></span> <span data-ttu-id="dba2b-158">Nazwa manifestu składnika jest nazwą biblioteki zestawu, po której następuje rozszerzenie manifestu.</span><span class="sxs-lookup"><span data-stu-id="dba2b-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="dba2b-159">Na przykład myManagedComp.dll jest myManagedComp.manifest.</span><span class="sxs-lookup"><span data-stu-id="dba2b-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="dba2b-160">Manifest komponentu należy osadzić jako zasób w złożeniu.</span><span class="sxs-lookup"><span data-stu-id="dba2b-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="dba2b-161">Aby osadzić manifest komponentu w zestawie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="dba2b-161">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="dba2b-162">Utwórz skrypt zasobu zawierający następującą instrukcję:</span><span class="sxs-lookup"><span data-stu-id="dba2b-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="dba2b-163">W tej `myManagedComp.manifest` instrukcji jest nazwa manifestu składnika są osadzone.</span><span class="sxs-lookup"><span data-stu-id="dba2b-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="dba2b-164">W tym przykładzie nazwa `myresource.rc`pliku skryptu to .</span><span class="sxs-lookup"><span data-stu-id="dba2b-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="dba2b-165">Skompiluj skrypt przy użyciu kompilatora zasobów systemu Microsoft Windows (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="dba2b-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="dba2b-166">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="dba2b-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="dba2b-167">Program Rc.exe `myresource.res` tworzy plik zasobu.</span><span class="sxs-lookup"><span data-stu-id="dba2b-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="dba2b-168">Skompiluj ponownie plik źródłowy zestawu i określ plik zasobu za pomocą opcji **/win32res:**</span><span class="sxs-lookup"><span data-stu-id="dba2b-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="dba2b-169">Ponownie, `myresource.res` jest nazwa pliku zasobów zawierającego zasoby osadzone.</span><span class="sxs-lookup"><span data-stu-id="dba2b-169">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba2b-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dba2b-170">See also</span></span>

- [<span data-ttu-id="dba2b-171">Współdziałanie z COM bez rejestrowania</span><span class="sxs-lookup"><span data-stu-id="dba2b-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="dba2b-172">[Wymagania dotyczące rejestracji-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dba2b-172">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="dba2b-173">[Konfigurowanie składników COM do aktywacji bez rejestracji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dba2b-173">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="dba2b-174">[Rejestracja-Free Aktywacja . Składniki oparte na sieci: przewodnik](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="dba2b-174">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
