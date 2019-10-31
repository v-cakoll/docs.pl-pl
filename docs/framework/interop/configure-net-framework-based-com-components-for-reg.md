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
ms.openlocfilehash: 61f5f0f3ec9a4386fa12e7511b4a518f2b56a21c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123664"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="9d3aa-102">Poradnik: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d3aa-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="9d3aa-103">Aktywacja bez rejestracji dla składników opartych na .NET Framework jest nieco bardziej skomplikowana niż w przypadku składników modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="9d3aa-104">Instalator wymaga dwóch manifestów:</span><span class="sxs-lookup"><span data-stu-id="9d3aa-104">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="9d3aa-105">Aplikacje COM muszą mieć manifest aplikacji w stylu Win32, aby zidentyfikować składnik zarządzany.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="9d3aa-106">Składniki oparte na .NET Framework muszą mieć manifest składnika dla informacji o aktywacji wymaganych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="9d3aa-107">W tym temacie opisano sposób kojarzenia manifestu aplikacji z aplikacją; Skojarz manifest składnika ze składnikiem; i osadzić Manifest składnika w zestawie.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="9d3aa-108">Aby utworzyć manifest aplikacji</span><span class="sxs-lookup"><span data-stu-id="9d3aa-108">To create an application manifest</span></span>  
  
1. <span data-ttu-id="9d3aa-109">Za pomocą edytora XML Utwórz (lub zmodyfikuj) manifest aplikacji należący do aplikacji COM, która współdziała z co najmniej jednym zarządzanym składnikiem.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="9d3aa-110">Wstaw następujący standardowy nagłówek na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="9d3aa-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="9d3aa-111">Aby uzyskać informacje na temat elementów manifestu i ich atrybutów, zobacz [manifesty aplikacji](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="9d3aa-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="9d3aa-112">Zidentyfikuj właściciela manifestu.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="9d3aa-113">W poniższym przykładzie `myComApp` wersja 1 jest właścicielem pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4. <span data-ttu-id="9d3aa-114">Zidentyfikuj zestawy zależne.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-114">Identify dependent assemblies.</span></span> <span data-ttu-id="9d3aa-115">W poniższym przykładzie `myComApp` zależy od `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5. <span data-ttu-id="9d3aa-116">Zapisz plik manifestu i nadaj mu nazwę.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-116">Save and name the manifest file.</span></span> <span data-ttu-id="9d3aa-117">Nazwa manifestu aplikacji jest nazwą pliku wykonywalnego zestawu, po którym następuje rozszerzenie. manifest.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="9d3aa-118">Na przykład nazwa pliku manifestu aplikacji dla myComApp. exe to myComApp. exe. manifest.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="9d3aa-119">Manifest aplikacji można zainstalować w tym samym katalogu, w którym znajduje się aplikacja COM.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="9d3aa-120">Alternatywnie możesz dodać go jako zasób do pliku. exe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="9d3aa-121">Aby uzyskać dodatkowe informacje, zobacz [Informacje o zestawach Side-by-Side](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="9d3aa-121">For additional information, For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="9d3aa-122">Aby utworzyć manifest składnika</span><span class="sxs-lookup"><span data-stu-id="9d3aa-122">To create a component manifest</span></span>  
  
1. <span data-ttu-id="9d3aa-123">Za pomocą edytora XML Utwórz manifest składnika, aby opisać zarządzany zestaw.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="9d3aa-124">Wstaw następujący standardowy nagłówek na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="9d3aa-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3. <span data-ttu-id="9d3aa-125">Zidentyfikuj właściciela pliku.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-125">Identify the owner of the file.</span></span> <span data-ttu-id="9d3aa-126">Element `<assemblyIdentity>` elementu `<dependentAssembly>` w pliku manifestu aplikacji musi być zgodny z plikiem w manifeście składnika.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="9d3aa-127">W poniższym przykładzie `myManagedComp` wersja 1.2.3.4 jest właścicielem pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
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
  
4. <span data-ttu-id="9d3aa-128">Zidentyfikuj każdą klasę w zestawie.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-128">Identify each class in the assembly.</span></span> <span data-ttu-id="9d3aa-129">Użyj elementu `<clrClass>`, aby jednoznacznie zidentyfikować każdą klasę w zarządzanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="9d3aa-130">Element, który jest podelementem elementu `<assembly>`, ma atrybuty opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="9d3aa-131">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9d3aa-131">Attribute</span></span>|<span data-ttu-id="9d3aa-132">Opis</span><span class="sxs-lookup"><span data-stu-id="9d3aa-132">Description</span></span>|<span data-ttu-id="9d3aa-133">Wymagane</span><span class="sxs-lookup"><span data-stu-id="9d3aa-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="9d3aa-134">Identyfikator określający klasę, która ma zostać aktywowana.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="9d3aa-135">Tak</span><span class="sxs-lookup"><span data-stu-id="9d3aa-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="9d3aa-136">Ciąg, który informuje użytkownika o składniku.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-136">A string that informs the user about the component.</span></span> <span data-ttu-id="9d3aa-137">Pusty ciąg jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-137">An empty string is the default.</span></span>|<span data-ttu-id="9d3aa-138">Nie</span><span class="sxs-lookup"><span data-stu-id="9d3aa-138">No</span></span>|  
    |`name`|<span data-ttu-id="9d3aa-139">Ciąg, który reprezentuje klasę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-139">A string that represents the managed class.</span></span>|<span data-ttu-id="9d3aa-140">Tak</span><span class="sxs-lookup"><span data-stu-id="9d3aa-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="9d3aa-141">Identyfikator, który ma być używany w przypadku aktywacji z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="9d3aa-142">Nie</span><span class="sxs-lookup"><span data-stu-id="9d3aa-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="9d3aa-143">Model wątkowości COM.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-143">The COM threading model.</span></span> <span data-ttu-id="9d3aa-144">Wartość domyślna to "Both".</span><span class="sxs-lookup"><span data-stu-id="9d3aa-144">"Both" is the default value.</span></span>|<span data-ttu-id="9d3aa-145">Nie</span><span class="sxs-lookup"><span data-stu-id="9d3aa-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="9d3aa-146">Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do użycia.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="9d3aa-147">Jeśli nie określisz tego atrybutu, a środowisko CLR nie jest już załadowane, składnik zostanie załadowany z najnowszym zainstalowanym środowiskiem CLR przed środowiskiem CLR w wersji 4.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="9d3aa-148">W przypadku określenia v 1.0.3705, v 1.1.4322 lub v 2.0.50727 wersja zostanie automatycznie przesunięta do najnowszej zainstalowanej wersji środowiska CLR przed środowiskiem CLR w wersji 4 (zazwyczaj 2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="9d3aa-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="9d3aa-149">Jeśli inna wersja środowiska CLR jest już załadowana i określona wersja może zostać załadowana równolegle, określona wersja zostanie załadowana. w przeciwnym razie zostanie użyte załadowane środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="9d3aa-150">Może to spowodować niepowodzenie ładowania.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-150">This might cause a load failure.</span></span>|<span data-ttu-id="9d3aa-151">Nie</span><span class="sxs-lookup"><span data-stu-id="9d3aa-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="9d3aa-152">Identyfikator biblioteki typów, który zawiera informacje o typie klasy.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="9d3aa-153">Nie</span><span class="sxs-lookup"><span data-stu-id="9d3aa-153">No</span></span>|  
  
     <span data-ttu-id="9d3aa-154">We wszystkich tagach atrybutów jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="9d3aa-155">Możesz uzyskać identyfikatory CLSID, ProgID, modele wątkowości i wersję środowiska uruchomieniowego, wyświetlając eksportowaną bibliotekę typów dla zestawu za pomocą OLE/COM ObjectViewer (OleView. exe).</span><span class="sxs-lookup"><span data-stu-id="9d3aa-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="9d3aa-156">Następujący manifest składnika identyfikuje dwie klasy `testClass1` i `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
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
  
5. <span data-ttu-id="9d3aa-157">Zapisz plik manifestu i nadaj mu nazwę.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-157">Save and name the manifest file.</span></span> <span data-ttu-id="9d3aa-158">Nazwa manifestu składnika jest nazwą biblioteki zestawu, po której następuje rozszerzenie. manifest.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="9d3aa-159">Na przykład myManagedComp. dll to myManagedComp. manifest.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="9d3aa-160">Manifest składnika należy osadzić jako zasób w zestawie.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="9d3aa-161">Aby osadzić Manifest składnika w zarządzanym zestawie</span><span class="sxs-lookup"><span data-stu-id="9d3aa-161">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="9d3aa-162">Utwórz skrypt zasobów zawierający następującą instrukcję:</span><span class="sxs-lookup"><span data-stu-id="9d3aa-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="9d3aa-163">W tej instrukcji `myManagedComp.manifest` jest nazwą manifestu składnika, który jest osadzony.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="9d3aa-164">W tym przykładzie nazwa pliku skryptu jest `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="9d3aa-165">Skompiluj skrypt przy użyciu kompilatora zasobów systemu Microsoft Windows (RC. exe).</span><span class="sxs-lookup"><span data-stu-id="9d3aa-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="9d3aa-166">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9d3aa-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="9d3aa-167">RC. exe tworzy plik zasobów `myresource.res`.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="9d3aa-168">Skompiluj ponownie plik źródłowy zestawu i określ plik zasobów przy użyciu opcji **/win32res** :</span><span class="sxs-lookup"><span data-stu-id="9d3aa-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="9d3aa-169">`myresource.res` to nazwa pliku zasobów zawierającego osadzone zasoby.</span><span class="sxs-lookup"><span data-stu-id="9d3aa-169">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d3aa-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d3aa-170">See also</span></span>

- [<span data-ttu-id="9d3aa-171">Współdziałanie z COM bez rejestrowania</span><span class="sxs-lookup"><span data-stu-id="9d3aa-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="9d3aa-172">[Wymagania dotyczące międzyoperacyjności modelu COM bez rejestracji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d3aa-172">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="9d3aa-173">[Konfigurowanie składników COM do aktywacji bez rejestracji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9d3aa-173">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="9d3aa-174">[Aktywacja bez rejestracji. Składniki oparte na sieci: Przewodnik](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="9d3aa-174">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
