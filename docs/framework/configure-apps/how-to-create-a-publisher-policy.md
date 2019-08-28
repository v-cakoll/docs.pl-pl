---
title: 'Instrukcje: Tworzenie zasad wydawcy'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 16d11147af7b54d492c099269a48a92ce83bc05d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043997"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="ead4d-102">Instrukcje: Tworzenie zasad wydawcy</span><span class="sxs-lookup"><span data-stu-id="ead4d-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="ead4d-103">Dostawcy zestawów mogą określać, że aplikacje powinny korzystać z nowszej wersji zestawu, dołączając plik zasad wydawcy z uaktualnionym zestawem.</span><span class="sxs-lookup"><span data-stu-id="ead4d-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="ead4d-104">Plik zasad wydawcy określa przekierowania zestawu i ustawienia podstawowe kodu, a także używa tego samego formatu co plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ead4d-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="ead4d-105">Plik zasad wydawcy jest kompilowany do zestawu i umieszczany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ead4d-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="ead4d-106">Tworzenie zasad wydawcy obejmuje trzy kroki:</span><span class="sxs-lookup"><span data-stu-id="ead4d-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="ead4d-107">Utwórz plik zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="ead4d-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="ead4d-108">Utwórz zestaw zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="ead4d-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="ead4d-109">Dodaj zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ead4d-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="ead4d-110">Schemat zasad wydawcy został opisany w temacie [przekierowywanie wersji zestawu](redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="ead4d-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="ead4d-111">Poniższy przykład pokazuje plik zasad wydawcy, który przekierowuje jedną wersję programu `myAssembly` do innej.</span><span class="sxs-lookup"><span data-stu-id="ead4d-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="ead4d-112">Aby dowiedzieć się, jak określić bazę kodu, zobacz [Określanie lokalizacji zestawu](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="ead4d-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="ead4d-113">Tworzenie zestawu zasad wydawcy</span><span class="sxs-lookup"><span data-stu-id="ead4d-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="ead4d-114">Użyj [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md) , aby utworzyć zestaw zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="ead4d-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="ead4d-115">Aby utworzyć zestaw zasad wydawcy</span><span class="sxs-lookup"><span data-stu-id="ead4d-115">To create a publisher policy assembly</span></span>

1. <span data-ttu-id="ead4d-116">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ead4d-116">Type the following command at the command prompt:</span></span>

    <span data-ttu-id="ead4d-117">**Al/link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="ead4d-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>

    <span data-ttu-id="ead4d-118">W tym poleceniu:</span><span class="sxs-lookup"><span data-stu-id="ead4d-118">In this command:</span></span>

    - <span data-ttu-id="ead4d-119">Argument *publisherPolicyFile* jest nazwą pliku zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="ead4d-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>

    - <span data-ttu-id="ead4d-120">Argument *publisherPolicyAssemblyFile* jest nazwą zestawu zasad wydawcy, który jest wynikiem tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ead4d-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="ead4d-121">Nazwa pliku zestawu musi być zgodna z formatem:</span><span class="sxs-lookup"><span data-stu-id="ead4d-121">The assembly file name must follow the format:</span></span>

      <span data-ttu-id="ead4d-122">**policy.**</span><span class="sxs-lookup"><span data-stu-id="ead4d-122">**policy.**</span></span> <span data-ttu-id="ead4d-123">*majorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="ead4d-123">*majorNumber* **.**</span></span> <span data-ttu-id="ead4d-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="ead4d-124">*minorNumber* **.**</span></span> <span data-ttu-id="ead4d-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="ead4d-125">*mainAssemblyName* **.dll**</span></span>

    - <span data-ttu-id="ead4d-126">Argument *keyPairFile* jest nazwą pliku zawierającego parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="ead4d-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="ead4d-127">Należy podpisać zestaw i zestaw zasad wydawcy z tą samą parą kluczy.</span><span class="sxs-lookup"><span data-stu-id="ead4d-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

    - <span data-ttu-id="ead4d-128">Argument *processorArchitecture* identyfikuje platformę objętą przez zestaw specyficzny dla procesora.</span><span class="sxs-lookup"><span data-stu-id="ead4d-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>

      > [!NOTE]
      > <span data-ttu-id="ead4d-129">Możliwość kierowania określonej architektury procesora jest nowa w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="ead4d-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>

    <span data-ttu-id="ead4d-130">Następujące polecenie tworzy zestaw zasad wydawcy o `policy.1.0.myAssembly` nazwie z pliku zasad wydawcy o nazwie `pub.config`, przypisuje silną nazwę do zestawu przy użyciu pary kluczy w `sgKey.snk` pliku i określa, że zestaw jest przeznaczony dla architektury x86 Architektura procesora.</span><span class="sxs-lookup"><span data-stu-id="ead4d-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

    ```
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
    ```

    <span data-ttu-id="ead4d-131">Zestaw zasad wydawcy musi być zgodny z architekturą procesora zestawu, którego dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ead4d-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="ead4d-132">W takim przypadku, jeśli zestaw ma <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> <xref:System.Reflection.ProcessorArchitecture.MSIL>wartość, zestaw zasad wydawcy dla tego zestawu musi być utworzony przy użyciu `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="ead4d-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="ead4d-133">Należy podać osobny zestaw zasad wydawcy dla każdego zestawu specyficznego dla procesora.</span><span class="sxs-lookup"><span data-stu-id="ead4d-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

    <span data-ttu-id="ead4d-134">Wynikiem tej reguły jest zmiana architektury procesora dla zestawu, dlatego należy zmienić składnik główny lub pomocniczy numeru wersji, aby można było dostarczyć nowy zestaw zasad wydawcy z poprawną architekturą procesora.</span><span class="sxs-lookup"><span data-stu-id="ead4d-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="ead4d-135">Stary zestaw zasad wydawcy nie może obtworzyć zestawu, gdy zestaw ma inną architekturę procesora.</span><span class="sxs-lookup"><span data-stu-id="ead4d-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

    <span data-ttu-id="ead4d-136">Inna konsekwencja polega na tym, że konsolidator w wersji 2,0 nie może zostać użyty do utworzenia zestawu zasad wydawcy dla zestawu skompilowanego przy użyciu wcześniejszych wersji .NET Framework, ponieważ zawsze określa architekturę procesora.</span><span class="sxs-lookup"><span data-stu-id="ead4d-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="ead4d-137">Dodawanie zestawu zasad wydawcy do globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="ead4d-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="ead4d-138">Użyj [Narzędzia globalnej pamięci podręcznej zestawów (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) , aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ead4d-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="ead4d-139">Aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="ead4d-139">To add the publisher policy assembly to the global assembly cache</span></span>

1. <span data-ttu-id="ead4d-140">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ead4d-140">Type the following command at the command prompt:</span></span>

    <span data-ttu-id="ead4d-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span><span class="sxs-lookup"><span data-stu-id="ead4d-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>

    <span data-ttu-id="ead4d-142">Następujące polecenie dodaje `policy.1.0.myAssembly.dll` do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ead4d-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

    ```
    gacutil /i policy.1.0.myAssembly.dll
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="ead4d-143">Zestawu zasad wydawcy nie można dodać do globalnej pamięci podręcznej zestawów, chyba że oryginalny plik zasad wydawcy znajduje się w tym samym katalogu, w którym znajduje się zestaw.</span><span class="sxs-lookup"><span data-stu-id="ead4d-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="ead4d-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ead4d-144">See also</span></span>

- [<span data-ttu-id="ead4d-145">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="ead4d-145">Programming with Assemblies</span></span>](../app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="ead4d-146">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ead4d-146">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ead4d-147">Konfigurowanie aplikacji przy użyciu plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ead4d-147">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="ead4d-148">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ead4d-148">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="ead4d-149">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ead4d-149">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="ead4d-150">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="ead4d-150">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
