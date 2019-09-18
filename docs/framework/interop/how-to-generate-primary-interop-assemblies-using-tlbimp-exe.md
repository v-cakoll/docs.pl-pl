---
title: 'Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac60fa96b7c9ce6991f89e8c6a37ff5da4a34a50
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051775"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="a6f80-102">Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="a6f80-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>

<span data-ttu-id="a6f80-103">Istnieją dwa sposoby generowania podstawowego zestawu międzyoperacyjnego:</span><span class="sxs-lookup"><span data-stu-id="a6f80-103">There are two ways to generate a primary interop assembly:</span></span>

- <span data-ttu-id="a6f80-104">Przy użyciu [importera biblioteki typów (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) dostarczonego przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="a6f80-104">Using the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) provided by the Windows SDK.</span></span>

  <span data-ttu-id="a6f80-105">Najbardziej prostym sposobem tworzenia podstawowych zestawów międzyoperacyjnych jest użycie [Tlbimp. exe (Importer biblioteki typów)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="a6f80-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="a6f80-106">Tlbimp. exe zapewnia następujące zabezpieczenia:</span><span class="sxs-lookup"><span data-stu-id="a6f80-106">Tlbimp.exe provides the following safeguards:</span></span>

  - <span data-ttu-id="a6f80-107">Sprawdza inne zarejestrowane podstawowe zestawy międzyoperacyjności przed utworzeniem nowych zestawów międzyoperacyjnych dla dowolnych odwołań do bibliotek typów zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="a6f80-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>

  - <span data-ttu-id="a6f80-108">Nie można wyemitować podstawowego zestawu międzyoperacyjnego, jeśli nie określisz kontenera lub nazwy pliku w celu uzyskania silnej nazwy podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a6f80-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>

  - <span data-ttu-id="a6f80-109">Nie można wyemitować podstawowego zestawu międzyoperacyjnego w przypadku pominięcia odwołań do zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="a6f80-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>

  - <span data-ttu-id="a6f80-110">Nie można wyemitować podstawowego zestawu międzyoperacyjnego w przypadku dodania odwołań do zestawów zależnych, które nie są zestawami podstawowych międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="a6f80-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>

- <span data-ttu-id="a6f80-111">Ręczne tworzenie podstawowych zestawów międzyoperacyjnych w kodzie źródłowym przy użyciu języka zgodnego z Common Language Specification (CLS), takiego jak C#.</span><span class="sxs-lookup"><span data-stu-id="a6f80-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="a6f80-112">Takie podejście jest przydatne, gdy biblioteka typów jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="a6f80-112">This approach is useful when a type library is unavailable.</span></span>

<span data-ttu-id="a6f80-113">Aby podpisać zestaw za pomocą silnej nazwy, musisz mieć parę kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="a6f80-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="a6f80-114">Aby uzyskać szczegółowe informacje, zobacz [Tworzenie pary kluczy](../../standard/assembly/create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="a6f80-114">For details, see [Creating A Key Pair](../../standard/assembly/create-public-private-key-pair.md).</span></span>

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="a6f80-115">Aby wygenerować podstawowy zestaw międzyoperacyjny przy użyciu programu Tlbimp. exe</span><span class="sxs-lookup"><span data-stu-id="a6f80-115">To generate a primary interop assembly using Tlbimp.exe</span></span>

1. <span data-ttu-id="a6f80-116">W wierszu polecenia wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="a6f80-116">At the command prompt, type:</span></span>

    <span data-ttu-id="a6f80-117">**Tlbimp** *tlbfile* **/Primary/keyfile:** *Nazwa pliku* **/out:** *AssemblyName*</span><span class="sxs-lookup"><span data-stu-id="a6f80-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>

    <span data-ttu-id="a6f80-118">W tym poleceniu *tlbfile* jest plikiem zawierającym bibliotekę typów com, *filename* jest nazwą kontenera lub pliku, który zawiera parę kluczy, a *AssemblyName* jest nazwą zestawu do podpisania silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="a6f80-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>

<span data-ttu-id="a6f80-119">Podstawowe zestawy międzyoperacyjności mogą odwoływać się tylko do innych podstawowych zestawów międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="a6f80-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="a6f80-120">Jeśli zestaw odwołuje się do typów z biblioteki typu COM innej firmy, należy uzyskać podstawowy zestaw międzyoperacyjny od wydawcy, aby można było wygenerować podstawowy zestaw międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="a6f80-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="a6f80-121">Jeśli jesteś wydawcą, musisz wygenerować podstawowy zestaw międzyoperacyjny dla zależnej biblioteki typów przed wygenerowaniem podstawowego zestawu międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="a6f80-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>

<span data-ttu-id="a6f80-122">Zależny podstawowy zestaw międzyoperacyjny z numerem wersji, który różni się od oryginalnej biblioteki typów, nie jest wykrywalny w przypadku instalacji w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a6f80-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="a6f80-123">Należy zarejestrować zależny podstawowy zestaw międzyoperacyjny w rejestrze systemu Windows lub użyć opcji **/Reference** , aby upewnić się, że Tlbimp. exe odnajdzie ZALEŻNĄ bibliotekę DLL.</span><span class="sxs-lookup"><span data-stu-id="a6f80-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>

<span data-ttu-id="a6f80-124">Możesz również otoczyć wiele wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="a6f80-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="a6f80-125">Aby uzyskać instrukcje, [zobacz How to: Zawiń wiele wersji bibliotek](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100))typów.</span><span class="sxs-lookup"><span data-stu-id="a6f80-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="a6f80-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6f80-126">Example</span></span>

<span data-ttu-id="a6f80-127">Poniższy przykład importuje bibliotekę `LibUtil.tlb` typów com i podpisuje zestaw `LibUtil.dll` za pomocą silnej nazwy przy użyciu pliku `CompanyA.snk`klucza.</span><span class="sxs-lookup"><span data-stu-id="a6f80-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="a6f80-128">Pomijając konkretną nazwę przestrzeni nazw, ten przykład tworzy domyślną przestrzeń nazw, `LibUtil`.</span><span class="sxs-lookup"><span data-stu-id="a6f80-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

<span data-ttu-id="a6f80-129">Aby uzyskać bardziej opisową nazwę (przy użyciu *NazwaDostawcy*. *LibraryName* nazewnictwo, w poniższym przykładzie zastępuje domyślną nazwę pliku zestawu i nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a6f80-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

<span data-ttu-id="a6f80-130">Poniższy przykład importuje `MyLib.tlb`, który odwołuje `CompanyA.LibUtil.dll`się i podpisuje `CompanyB.MyLib.dll` zestaw silną nazwą przy użyciu pliku `CompanyB.snk`klucza.</span><span class="sxs-lookup"><span data-stu-id="a6f80-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="a6f80-131">Przestrzeń nazw, `CompanyB.MyLib`zastępuje domyślną nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a6f80-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a><span data-ttu-id="a6f80-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6f80-132">See also</span></span>

- [<span data-ttu-id="a6f80-133">Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="a6f80-133">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)
