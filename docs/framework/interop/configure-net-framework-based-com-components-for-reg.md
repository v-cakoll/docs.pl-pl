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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9df1aa781bd54468d2273a335b3fda7d701854d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519411"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="c8372-102">Poradnik: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c8372-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="c8372-103">Aktywacji bez rejestracji dla składników opartych na programie .NET Framework jest tylko nieco bardziej skomplikowane niż jest dla składników COM.</span><span class="sxs-lookup"><span data-stu-id="c8372-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="c8372-104">Instalator wymaga dwóch manifesty:</span><span class="sxs-lookup"><span data-stu-id="c8372-104">The setup requires two manifests:</span></span>  
  
-   <span data-ttu-id="c8372-105">Aplikacje COM musi mieć Win32 stylu manifest aplikacji, aby zidentyfikować zarządzanego składnika.</span><span class="sxs-lookup"><span data-stu-id="c8372-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
-   <span data-ttu-id="c8372-106">Składniki .NET framework, musi mieć manifestu składnika, aby uzyskać informacje o aktywacji potrzebnych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c8372-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="c8372-107">W tym temacie opisano, jak skojarzyć manifest aplikacji za pomocą aplikacji; Kojarzenie manifestu składnika za pomocą składnika; i osadzanie manifestu składnika w zestawie.</span><span class="sxs-lookup"><span data-stu-id="c8372-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="c8372-108">Aby utworzyć manifest aplikacji</span><span class="sxs-lookup"><span data-stu-id="c8372-108">To create an application manifest</span></span>  
  
1.  <span data-ttu-id="c8372-109">Za pomocą edytora XML, Utwórz (lub zmodyfikuj) należące do aplikacji modelu COM, który jest współdziałanie z co najmniej jednego składnika zarządzanego manifest aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8372-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2.  <span data-ttu-id="c8372-110">Wstaw następujący nagłówek standardowy na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="c8372-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="c8372-111">Aby uzyskać informacji na temat ich atrybuty i elementy manifestu, zobacz [manifesty aplikacji](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="c8372-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3.  <span data-ttu-id="c8372-112">Określ właściciela manifestu.</span><span class="sxs-lookup"><span data-stu-id="c8372-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="c8372-113">W poniższym przykładzie `myComApp` w wersji 1 jest właścicielem pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="c8372-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  <span data-ttu-id="c8372-114">Zidentyfikuj zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="c8372-114">Identify dependent assemblies.</span></span> <span data-ttu-id="c8372-115">W poniższym przykładzie `myComApp` zależy od `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="c8372-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5.  <span data-ttu-id="c8372-116">Zapisz i nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="c8372-116">Save and name the manifest file.</span></span> <span data-ttu-id="c8372-117">Nazwa manifest aplikacji jest nazwa zestawu pliku wykonywalnego, następuje rozszerzenie .manifest.</span><span class="sxs-lookup"><span data-stu-id="c8372-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="c8372-118">Na przykład nazwa pliku manifestu aplikacji dla myComApp.exe jest myComApp.exe.manifest.</span><span class="sxs-lookup"><span data-stu-id="c8372-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="c8372-119">W tym samym katalogu co aplikacji modelu COM, można zainstalować manifest aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8372-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="c8372-120">Alternatywnie można go dodać jako zasób do pliku .exe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8372-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="c8372-121">Aby uzyskać dodatkowe informacje, aby uzyskać więcej informacji, zobacz [informacje o zestawach Side-by-Side](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="c8372-121">For additional information, For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="c8372-122">Aby utworzyć manifest składnika</span><span class="sxs-lookup"><span data-stu-id="c8372-122">To create a component manifest</span></span>  
  
1.  <span data-ttu-id="c8372-123">Za pomocą edytora XML, Utwórz manifestu składnika, aby opisać zarządzanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8372-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2.  <span data-ttu-id="c8372-124">Wstaw następujący nagłówek standardowy na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="c8372-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  <span data-ttu-id="c8372-125">Określ właściciela pliku.</span><span class="sxs-lookup"><span data-stu-id="c8372-125">Identify the owner of the file.</span></span> <span data-ttu-id="c8372-126">`<assemblyIdentity>` Elementu `<dependentAssembly>` elementu w pliku manifestu aplikacji musi pasować do w manifeście składnika.</span><span class="sxs-lookup"><span data-stu-id="c8372-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="c8372-127">W poniższym przykładzie `myManagedComp` wersję 1.2.3.4 właścicielem pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="c8372-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
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
  
4.  <span data-ttu-id="c8372-128">Zidentyfikuj każdej klasy w zestawie.</span><span class="sxs-lookup"><span data-stu-id="c8372-128">Identify each class in the assembly.</span></span> <span data-ttu-id="c8372-129">Użyj `<clrClass>` element do unikatowego identyfikowania każdej klasy w zestawie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="c8372-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="c8372-130">Element, który jest podelementem z `<assembly>` elementu atrybutami opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c8372-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="c8372-131">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c8372-131">Attribute</span></span>|<span data-ttu-id="c8372-132">Opis</span><span class="sxs-lookup"><span data-stu-id="c8372-132">Description</span></span>|<span data-ttu-id="c8372-133">Wymagane</span><span class="sxs-lookup"><span data-stu-id="c8372-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="c8372-134">Identyfikator, który określa klasę do aktywacji.</span><span class="sxs-lookup"><span data-stu-id="c8372-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="c8372-135">Tak</span><span class="sxs-lookup"><span data-stu-id="c8372-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="c8372-136">Ciąg, który informuje użytkownika o informacje o składniku.</span><span class="sxs-lookup"><span data-stu-id="c8372-136">A string that informs the user about the component.</span></span> <span data-ttu-id="c8372-137">Pusty ciąg jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="c8372-137">An empty string is the default.</span></span>|<span data-ttu-id="c8372-138">Nie</span><span class="sxs-lookup"><span data-stu-id="c8372-138">No</span></span>|  
    |`name`|<span data-ttu-id="c8372-139">Ciąg, który reprezentuje klasy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="c8372-139">A string that represents the managed class.</span></span>|<span data-ttu-id="c8372-140">Tak</span><span class="sxs-lookup"><span data-stu-id="c8372-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="c8372-141">Identyfikator, który ma być używany do aktywacji z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="c8372-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="c8372-142">Nie</span><span class="sxs-lookup"><span data-stu-id="c8372-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="c8372-143">Model wątkowości COM.</span><span class="sxs-lookup"><span data-stu-id="c8372-143">The COM threading model.</span></span> <span data-ttu-id="c8372-144">"Both" jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="c8372-144">"Both" is the default value.</span></span>|<span data-ttu-id="c8372-145">Nie</span><span class="sxs-lookup"><span data-stu-id="c8372-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="c8372-146">Wersja wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) do użycia.</span><span class="sxs-lookup"><span data-stu-id="c8372-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="c8372-147">Jeśli nie określisz tego atrybutu, a środowisko CLR nie jest już załadowany, składnik jest ładowany z najnowsza wersja zainstalowanego środowiska CLR przed CLR w wersji 4.</span><span class="sxs-lookup"><span data-stu-id="c8372-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="c8372-148">Jeśli określisz v1.0.3705, v1.1.4322 lub v2.0.50727 wersję automatycznie przenosi do przodu do najnowszej zainstalowanej wersji środowiska CLR przed CLR w wersji 4 (zazwyczaj v2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="c8372-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="c8372-149">Jeśli inna wersja środowiska CLR jest już załadowany, określonej wersji, może zostać załadowany side-by-side w procesie jest ładowany określonej wersji; w przeciwnym razie załadowane środowisko CLR jest używany.</span><span class="sxs-lookup"><span data-stu-id="c8372-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="c8372-150">Może to spowodować awarię obciążenia.</span><span class="sxs-lookup"><span data-stu-id="c8372-150">This might cause a load failure.</span></span>|<span data-ttu-id="c8372-151">Nie</span><span class="sxs-lookup"><span data-stu-id="c8372-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="c8372-152">Identyfikator biblioteki typów, zawierający informacje o typie o klasie.</span><span class="sxs-lookup"><span data-stu-id="c8372-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="c8372-153">Nie</span><span class="sxs-lookup"><span data-stu-id="c8372-153">No</span></span>|  
  
     <span data-ttu-id="c8372-154">Wszystkie tagi atrybutów jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="c8372-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="c8372-155">Możesz uzyskać CLSID ProgID, Modele wątkowości i wersji środowiska uruchomieniowego, wyświetlając wyeksportowanej biblioteki typów dla zestawu z ObjectViewer OLE/COM (Oleview.exe).</span><span class="sxs-lookup"><span data-stu-id="c8372-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="c8372-156">Następujące manifestu składnika identyfikuje dwóch klas `testClass1` i `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="c8372-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
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
  
5.  <span data-ttu-id="c8372-157">Zapisz i nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="c8372-157">Save and name the manifest file.</span></span> <span data-ttu-id="c8372-158">Nazwa manifestu składnika jest nazwa biblioteki zestawu, a po nim rozszerzenie .manifest.</span><span class="sxs-lookup"><span data-stu-id="c8372-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="c8372-159">Na przykład myManagedComp.dll jest myManagedComp.manifest.</span><span class="sxs-lookup"><span data-stu-id="c8372-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="c8372-160">Manifestu składnika należy osadzić jako zasób w zestawie.</span><span class="sxs-lookup"><span data-stu-id="c8372-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="c8372-161">Osadzanie manifestu składnika w zestaw zarządzany</span><span class="sxs-lookup"><span data-stu-id="c8372-161">To embed a component manifest in a managed assembly</span></span>  
  
1.  <span data-ttu-id="c8372-162">Utwórz skrypt zasobu, który zawiera następującą instrukcję:</span><span class="sxs-lookup"><span data-stu-id="c8372-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="c8372-163">W niniejszych zasadach `myManagedComp.manifest` nazywa się manifestu składnika osadzona.</span><span class="sxs-lookup"><span data-stu-id="c8372-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="c8372-164">W tym przykładzie jest nazwa pliku skryptu `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="c8372-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2.  <span data-ttu-id="c8372-165">Kompiluj skrypt z użyciem Microsoft Windows Resource Compiler (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="c8372-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="c8372-166">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c8372-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="c8372-167">Tworzy RC.exe `myresource.res` pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="c8372-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3.  <span data-ttu-id="c8372-168">Ponownie skompiluj plik źródłowy zestawu i określ plik zasobów przy użyciu **/win32res** opcji:</span><span class="sxs-lookup"><span data-stu-id="c8372-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     <span data-ttu-id="c8372-169">Ponownie `myresource.res` to nazwa pliku zasobu zawierającego osadzonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="c8372-169">Again, `myresource.res` is the name of the resource file containing embedded resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8372-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8372-170">See Also</span></span>  
 [<span data-ttu-id="c8372-171">Współdziałanie z COM bez rejestrowania</span><span class="sxs-lookup"><span data-stu-id="c8372-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
 <span data-ttu-id="c8372-172">[Wymagania dotyczące współdziałania z modelem COM bez rejestrowania](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100)))</span><span class="sxs-lookup"><span data-stu-id="c8372-172">[Requirements for Registration-Free COM Interop](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100)))</span></span>  
 <span data-ttu-id="c8372-173">[Konfigurowanie aktywacji bez rejestracji składników COM](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100)))</span><span class="sxs-lookup"><span data-stu-id="c8372-173">[Configuring COM Components for Registration-Free Activation](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100)))</span></span>  
 [<span data-ttu-id="c8372-174">Współdziałanie aktywacji. NET składników: Przewodnik</span><span class="sxs-lookup"><span data-stu-id="c8372-174">Registration-Free Activation of .NET-Based Components: A Walkthrough</span></span>](https://msdn.microsoft.com/library/ms973915.aspx)
