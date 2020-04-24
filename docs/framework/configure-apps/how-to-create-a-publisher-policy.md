---
title: 'Porady: tworzenie zasad wydawcy'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646059"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="e4c55-102">Porady: tworzenie zasad wydawcy</span><span class="sxs-lookup"><span data-stu-id="e4c55-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="e4c55-103">Dostawcy zestawów można stwierdzić, że aplikacje powinny używać nowszej wersji zestawu, dołączając plik zasad wydawcy z uaktualnionego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e4c55-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="e4c55-104">Plik zasad wydawcy określa przekierowanie zestawu i ustawienia podstawowe kodu i używa tego samego formatu co plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4c55-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="e4c55-105">Plik zasad wydawcy jest kompilowany do zestawu i umieszczany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="e4c55-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="e4c55-106">Tworzenie zasad wydawcy jest trzy kroki:</span><span class="sxs-lookup"><span data-stu-id="e4c55-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="e4c55-107">Tworzenie pliku zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="e4c55-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="e4c55-108">Tworzenie zestawu zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="e4c55-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="e4c55-109">Dodaj zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="e4c55-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="e4c55-110">Schemat zasad wydawcy jest opisany w [przekierowywaniu wersji zestawu](redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="e4c55-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="e4c55-111">W poniższym przykładzie przedstawiono plik zasad `myAssembly` wydawcy, który przekierowuje jedną wersję do innej.</span><span class="sxs-lookup"><span data-stu-id="e4c55-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="e4c55-112">Aby dowiedzieć się, jak określić podstawę kodu, zobacz [Określanie lokalizacji zestawu](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="e4c55-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="e4c55-113">Tworzenie zestawu zasad wydawcy</span><span class="sxs-lookup"><span data-stu-id="e4c55-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="e4c55-114">Użyj [zestawu łączącego zestawu (Al.exe),](../tools/al-exe-assembly-linker.md) aby utworzyć zestaw zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="e4c55-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="e4c55-115">Aby utworzyć zestaw zasad wydawcy</span><span class="sxs-lookup"><span data-stu-id="e4c55-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="e4c55-116">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e4c55-116">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="e4c55-117">W tym poleceniu:</span><span class="sxs-lookup"><span data-stu-id="e4c55-117">In this command:</span></span>

- <span data-ttu-id="e4c55-118">Argument `publisherPolicyFile` jest nazwą pliku zasad wydawcy.</span><span class="sxs-lookup"><span data-stu-id="e4c55-118">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="e4c55-119">Argument `publisherPolicyAssemblyFile` jest nazwą zestawu zasad wydawcy, który wynika z tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e4c55-119">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="e4c55-120">Nazwa pliku złożenia musi być zgodna z formatem:</span><span class="sxs-lookup"><span data-stu-id="e4c55-120">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="e4c55-121">'policy.majorNumber.minorNumber.mainAssemblyName.dll'</span><span class="sxs-lookup"><span data-stu-id="e4c55-121">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="e4c55-122">Argument `keyPairFile` jest nazwą pliku zawierającego parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="e4c55-122">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="e4c55-123">Należy podpisać zestaw zasad zestawu i wydawcy z tą samą parą kluczy.</span><span class="sxs-lookup"><span data-stu-id="e4c55-123">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="e4c55-124">Argument `processorArchitecture` identyfikuje platformę, na podstawie których ma odpowiadać zestaw specyficzny dla procesora.</span><span class="sxs-lookup"><span data-stu-id="e4c55-124">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e4c55-125">Możliwość kierowania na architekturę określonego procesora jest dostępna począwszy od programu .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="e4c55-125">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="e4c55-126">Możliwość kierowania na architekturę określonego procesora jest dostępna począwszy od programu .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="e4c55-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="e4c55-127">Następujące polecenie tworzy zestaw zasad `policy.1.0.myAssembly` wydawcy wywoływany `pub.config`z pliku zasad wydawcy o nazwie , `sgKey.snk` przypisuje silną nazwę do zestawu przy użyciu pary kluczy w pliku i określa, że zestaw jest przeznaczony dla architektury procesora x86.</span><span class="sxs-lookup"><span data-stu-id="e4c55-127">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="e4c55-128">Zestaw zasad wydawcy musi być zgodny z architekturą procesora zestawu, który ma zastosowanie do.</span><span class="sxs-lookup"><span data-stu-id="e4c55-128">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="e4c55-129">W związku z tym <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> jeśli <xref:System.Reflection.ProcessorArchitecture.MSIL>zestaw ma wartość , zestaw zasad `/platform:anycpu`wydawcy dla tego zestawu musi być utworzony za pomocą .</span><span class="sxs-lookup"><span data-stu-id="e4c55-129">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="e4c55-130">Należy podać oddzielny zestaw zasad wydawcy dla każdego zestawu specyficznego dla procesora.</span><span class="sxs-lookup"><span data-stu-id="e4c55-130">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="e4c55-131">Konsekwencją tej reguły jest to, że aby zmienić architekturę procesora dla zestawu, należy zmienić główny lub pomocniczy składnik numeru wersji, aby można było dostarczyć nowy zestaw zasad wydawcy z właściwą architekturą procesora.</span><span class="sxs-lookup"><span data-stu-id="e4c55-131">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="e4c55-132">Stary zestaw zasad wydawcy nie może obsługiwać zestawu, gdy zestaw ma inną architekturę procesora.</span><span class="sxs-lookup"><span data-stu-id="e4c55-132">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="e4c55-133">Inną konsekwencją jest to, że konsolidator wersji 2.0 nie może służyć do tworzenia zestawu zasad wydawcy dla zestawu skompilowanego przy użyciu wcześniejszych wersji programu .NET Framework, ponieważ zawsze określa architekturę procesora.</span><span class="sxs-lookup"><span data-stu-id="e4c55-133">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="e4c55-134">Dodawanie zestawu zasad wydawcy do globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="e4c55-134">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="e4c55-135">Użyj [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe),](../tools/gacutil-exe-gac-tool.md) aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="e4c55-135">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="e4c55-136">Aby dodać zestaw zasad wydawcy do globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="e4c55-136">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="e4c55-137">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e4c55-137">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="e4c55-138">Następujące polecenie `policy.1.0.myAssembly.dll` dodaje do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="e4c55-138">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="e4c55-139">Zestawu zasad wydawcy nie można dodać do globalnej pamięci podręcznej zestawów, chyba że oryginalny plik zasad wydawcy określony w `/link` argumie znajduje się w tym samym katalogu co zestaw.</span><span class="sxs-lookup"><span data-stu-id="e4c55-139">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4c55-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4c55-140">See also</span></span>

- [<span data-ttu-id="e4c55-141">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="e4c55-141">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="e4c55-142">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e4c55-142">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="e4c55-143">Konfigurowanie aplikacji za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e4c55-143">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="e4c55-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e4c55-144">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="e4c55-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e4c55-145">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="e4c55-146">Przekierowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="e4c55-146">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
