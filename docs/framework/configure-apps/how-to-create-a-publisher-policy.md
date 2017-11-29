---
title: 'Porady: tworzenie zasad wydawcy'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 430426e3662582bd904bc088a362e9d7ed331c11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="420b7-102">Porady: tworzenie zasad wydawcy</span><span class="sxs-lookup"><span data-stu-id="420b7-102">How to: Create a Publisher Policy</span></span>
<span data-ttu-id="420b7-103">Dostawców zestawy mogą stanu aplikacje powinny używać nowszej wersji zestawu przez dołączenie pliku zasad wydawcy w zestawie uaktualniony.</span><span class="sxs-lookup"><span data-stu-id="420b7-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="420b7-104">Plik zasad wydawcy określa przekierowanie zestawów i kod podstawowych ustawień i używa tego samego formatu co plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="420b7-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="420b7-105">Plik zasad wydawcy są kompilowane do zestawu i umieszczane w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="420b7-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="420b7-106">Istnieją trzy kroki związane z tworzeniem zasad wydawcy:</span><span class="sxs-lookup"><span data-stu-id="420b7-106">There are three steps involved in creating a publisher policy:</span></span>  
  
1.  <span data-ttu-id="420b7-107">Utwórz plik zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="420b7-107">Create a publisher policy file.</span></span>  
  
2.  <span data-ttu-id="420b7-108">Utwórz zestaw zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="420b7-108">Create a publisher policy assembly.</span></span>  
  
3.  <span data-ttu-id="420b7-109">Dodaj zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="420b7-109">Add the publisher policy assembly to the global assembly cache.</span></span>  
  
 <span data-ttu-id="420b7-110">Schemat dla zasad wydawcy jest opisany w [przekierowywanie wersji zestawu](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="420b7-110">The schema for publisher policy is described in [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span></span> <span data-ttu-id="420b7-111">W poniższym przykładzie przedstawiono wydawcy pliku zasad, który przekierowuje jednej wersji `myAssembly` na inny.</span><span class="sxs-lookup"><span data-stu-id="420b7-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="420b7-112">Aby dowiedzieć się, jak określać ścieżki bazowej kodu, zobacz [Określanie lokalizacji zestawu](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="420b7-112">To learn how to specify a code base, see [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  
  
## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="420b7-113">Tworzenie zestaw zasad wydawcy</span><span class="sxs-lookup"><span data-stu-id="420b7-113">Creating the Publisher Policy Assembly</span></span>  
 <span data-ttu-id="420b7-114">Użyj [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) można utworzyć zestaw zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="420b7-114">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>  
  
#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="420b7-115">Aby utworzyć zestaw zasad wydawcy</span><span class="sxs-lookup"><span data-stu-id="420b7-115">To create a publisher policy assembly</span></span>  
  
1.  <span data-ttu-id="420b7-116">Wpisz następujące polecenie w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="420b7-116">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="420b7-117">**Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/KeyFile:**  *keyPairFile* **/platform:** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="420b7-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>  
  
     <span data-ttu-id="420b7-118">W tym poleceniu:</span><span class="sxs-lookup"><span data-stu-id="420b7-118">In this command:</span></span>  
  
    -   <span data-ttu-id="420b7-119">*PublisherPolicyFile* argument jest nazwą pliku zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="420b7-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>  
  
    -   <span data-ttu-id="420b7-120">*PublisherPolicyAssemblyFile* argument jest nazwą zestaw zasad wydawcy, która wynika z tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="420b7-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="420b7-121">Nazwa pliku zestawu musi mieć format:</span><span class="sxs-lookup"><span data-stu-id="420b7-121">The assembly file name must follow the format:</span></span>  
  
         <span data-ttu-id="420b7-122">**zasady.**</span><span class="sxs-lookup"><span data-stu-id="420b7-122">**policy.**</span></span> <span data-ttu-id="420b7-123">*majorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="420b7-123">*majorNumber* **.**</span></span> <span data-ttu-id="420b7-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="420b7-124">*minorNumber* **.**</span></span> <span data-ttu-id="420b7-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="420b7-125">*mainAssemblyName* **.dll**</span></span>  
  
    -   <span data-ttu-id="420b7-126">*KeyPairFile* argument jest nazwą pliku zawierającego pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="420b7-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="420b7-127">Musisz zalogować się zestaw i zestaw zasad wydawcy z tej samej pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="420b7-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>  
  
    -   <span data-ttu-id="420b7-128">*ProcessorArchitecture* argument identyfikuje platformy docelowej zestawu specyficznych dla procesora.</span><span class="sxs-lookup"><span data-stu-id="420b7-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="420b7-129">Możliwość architekturę procesora w określonym celem jest nowa w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="420b7-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>  
  
     <span data-ttu-id="420b7-130">Poniższe polecenie tworzy zestaw zasad wydawcy o nazwie `policy.1.0.myAssembly` z pliku zasad wydawcy o nazwie `pub.config`, przypisuje silnej nazwy zestawu przy użyciu pary kluczy w `sgKey.snk` pliku i określa, że zestaw jest przeznaczony dla x86 architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="420b7-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     <span data-ttu-id="420b7-131">Zestaw zasad wydawcy musi odpowiadać architekturze procesora stosowanym do zestawu.</span><span class="sxs-lookup"><span data-stu-id="420b7-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="420b7-132">W związku z tym jeśli ma używanemu zestawowi <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> wartość <xref:System.Reflection.ProcessorArchitecture.MSIL>, zestaw zasad wydawcy dla tego zestawu musi zostać utworzona z `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="420b7-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="420b7-133">Należy podać osobny zestaw zasad wydawcy dla każdego zestawu specyficznych dla procesora.</span><span class="sxs-lookup"><span data-stu-id="420b7-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>  
  
     <span data-ttu-id="420b7-134">Konsekwencji tej zasady jest, że aby można było zmienić architektury procesora dla zestawu, należy zmienić mniejszym lub składnik numeru wersji tak, aby można dostarczyć nowy zestaw zasad wydawcy o poprawnej architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="420b7-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="420b7-135">Stary zestaw zasad wydawcy nie może zrealizować używanego zestawu z zestawu ma inny procesor.</span><span class="sxs-lookup"><span data-stu-id="420b7-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>  
  
     <span data-ttu-id="420b7-136">Inny konsekwencją jest, że konsolidator w wersji 2.0 nie może służyć do tworzenia zestaw zasad wydawcy dla zestawu skompilowanego za pomocą wcześniejszych wersji programu .NET Framework, ponieważ określa ona zawsze architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="420b7-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="420b7-137">Dodawanie zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="420b7-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>  
 <span data-ttu-id="420b7-138">Użyj [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) można dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="420b7-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="420b7-139">Aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="420b7-139">To add the publisher policy assembly to the global assembly cache</span></span>  
  
1.  <span data-ttu-id="420b7-140">Wpisz następujące polecenie w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="420b7-140">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="420b7-141">**gacutil /i***publisherPolicyAssemblyFile* </span><span class="sxs-lookup"><span data-stu-id="420b7-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>  
  
     <span data-ttu-id="420b7-142">Następujące polecenie dodaje `policy.1.0.myAssembly.dll` do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="420b7-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="420b7-143">Nie można dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów, chyba że oryginalnego pliku zasad wydawcy znajduje się w tym samym katalogu co zestaw.</span><span class="sxs-lookup"><span data-stu-id="420b7-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="420b7-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="420b7-144">See Also</span></span>  
 [<span data-ttu-id="420b7-145">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="420b7-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="420b7-146">Jak lokalizuje zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="420b7-146">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="420b7-147">Konfigurowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="420b7-147">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="420b7-148">Konfigurowanie aplikacji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="420b7-148">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [<span data-ttu-id="420b7-149">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="420b7-149">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="420b7-150">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="420b7-150">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="420b7-151">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="420b7-151">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
