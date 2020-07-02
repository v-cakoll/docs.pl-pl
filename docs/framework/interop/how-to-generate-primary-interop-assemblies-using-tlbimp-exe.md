---
title: 'Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe'
description: Dowiedz się, jak generować podstawowe zestawy międzyoperacyjności przy użyciu importera biblioteki typów (Tlbimp.exe), który jest dostarczany przez Windows SDK.
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
ms.openlocfilehash: 779b4863b6f1513f3566d4ab31660d88cda1039b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619133"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="41ddb-103">Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="41ddb-103">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>

<span data-ttu-id="41ddb-104">Istnieją dwa sposoby generowania podstawowego zestawu międzyoperacyjnego:</span><span class="sxs-lookup"><span data-stu-id="41ddb-104">There are two ways to generate a primary interop assembly:</span></span>

- <span data-ttu-id="41ddb-105">Przy użyciu [importera biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) dostarczonego przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="41ddb-105">Using the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) provided by the Windows SDK.</span></span>

  <span data-ttu-id="41ddb-106">Najbardziej prostym sposobem tworzenia podstawowych zestawów międzyoperacyjnych jest użycie [Tlbimp.exe (Importer biblioteki typów)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="41ddb-106">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="41ddb-107">Tlbimp.exe zapewnia następujące zabezpieczenia:</span><span class="sxs-lookup"><span data-stu-id="41ddb-107">Tlbimp.exe provides the following safeguards:</span></span>

  - <span data-ttu-id="41ddb-108">Sprawdza inne zarejestrowane podstawowe zestawy międzyoperacyjności przed utworzeniem nowych zestawów międzyoperacyjnych dla dowolnych odwołań do bibliotek typów zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="41ddb-108">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>

  - <span data-ttu-id="41ddb-109">Nie można wyemitować podstawowego zestawu międzyoperacyjnego, jeśli nie określisz kontenera lub nazwy pliku w celu uzyskania silnej nazwy podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="41ddb-109">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>

  - <span data-ttu-id="41ddb-110">Nie można wyemitować podstawowego zestawu międzyoperacyjnego w przypadku pominięcia odwołań do zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="41ddb-110">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>

  - <span data-ttu-id="41ddb-111">Nie można wyemitować podstawowego zestawu międzyoperacyjnego w przypadku dodania odwołań do zestawów zależnych, które nie są zestawami podstawowych międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="41ddb-111">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>

- <span data-ttu-id="41ddb-112">Ręczne tworzenie podstawowych zestawów międzyoperacyjnych w kodzie źródłowym przy użyciu języka zgodnego z Common Language Specification (CLS), takiego jak C#.</span><span class="sxs-lookup"><span data-stu-id="41ddb-112">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="41ddb-113">Takie podejście jest przydatne, gdy biblioteka typów jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="41ddb-113">This approach is useful when a type library is unavailable.</span></span>

<span data-ttu-id="41ddb-114">Aby podpisać zestaw za pomocą silnej nazwy, musisz mieć parę kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="41ddb-114">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="41ddb-115">Aby uzyskać szczegółowe informacje, zobacz [Tworzenie pary kluczy](../../standard/assembly/create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="41ddb-115">For details, see [Creating A Key Pair](../../standard/assembly/create-public-private-key-pair.md).</span></span>

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="41ddb-116">Aby wygenerować podstawowy zestaw międzyoperacyjny przy użyciu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="41ddb-116">To generate a primary interop assembly using Tlbimp.exe</span></span>

1. <span data-ttu-id="41ddb-117">W wierszu polecenia wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="41ddb-117">At the command prompt, type:</span></span>

    <span data-ttu-id="41ddb-118">**Tlbimp** *tlbfile*  **/Primary/keyfile:** *filename* **/out:** *AssemblyName*</span><span class="sxs-lookup"><span data-stu-id="41ddb-118">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>

    <span data-ttu-id="41ddb-119">W tym poleceniu *tlbfile* jest plikiem zawierającym bibliotekę typów com, *filename* jest nazwą kontenera lub pliku, który zawiera parę kluczy, a *AssemblyName* jest nazwą zestawu do podpisania silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="41ddb-119">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>

<span data-ttu-id="41ddb-120">Podstawowe zestawy międzyoperacyjności mogą odwoływać się tylko do innych podstawowych zestawów międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="41ddb-120">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="41ddb-121">Jeśli zestaw odwołuje się do typów z biblioteki typu COM innej firmy, należy uzyskać podstawowy zestaw międzyoperacyjny od wydawcy, aby można było wygenerować podstawowy zestaw międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="41ddb-121">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="41ddb-122">Jeśli jesteś wydawcą, musisz wygenerować podstawowy zestaw międzyoperacyjny dla zależnej biblioteki typów przed wygenerowaniem podstawowego zestawu międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="41ddb-122">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>

<span data-ttu-id="41ddb-123">Zależny podstawowy zestaw międzyoperacyjny z numerem wersji, który różni się od oryginalnej biblioteki typów, nie jest wykrywalny w przypadku instalacji w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="41ddb-123">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="41ddb-124">Musisz zarejestrować zależny podstawowy zestaw międzyoperacyjny w rejestrze systemu Windows lub użyć opcji **/Reference** , aby upewnić się, że Tlbimp.exe odnajdzie ZALEŻNĄ bibliotekę DLL.</span><span class="sxs-lookup"><span data-stu-id="41ddb-124">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>

<span data-ttu-id="41ddb-125">Możesz również otoczyć wiele wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="41ddb-125">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="41ddb-126">Aby uzyskać instrukcje, zobacz [How to: Otocz wiele wersji bibliotek typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="41ddb-126">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="41ddb-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="41ddb-127">Example</span></span>

<span data-ttu-id="41ddb-128">Poniższy przykład importuje bibliotekę typów COM `LibUtil.tlb` i podpisuje zestaw `LibUtil.dll` za pomocą silnej nazwy przy użyciu pliku klucza `CompanyA.snk` .</span><span class="sxs-lookup"><span data-stu-id="41ddb-128">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="41ddb-129">Pomijając konkretną nazwę przestrzeni nazw, ten przykład tworzy domyślną przestrzeń nazw, `LibUtil` .</span><span class="sxs-lookup"><span data-stu-id="41ddb-129">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

<span data-ttu-id="41ddb-130">Aby uzyskać bardziej opisową nazwę (przy użyciu *NazwaDostawcy*.\* LibraryName\* nazewnictwo, w poniższym przykładzie zastępuje domyślną nazwę pliku zestawu i nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="41ddb-130">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

<span data-ttu-id="41ddb-131">Poniższy przykład importuje `MyLib.tlb` , który odwołuje się `CompanyA.LibUtil.dll` i podpisuje zestaw `CompanyB.MyLib.dll` silną nazwą przy użyciu pliku klucza `CompanyB.snk` .</span><span class="sxs-lookup"><span data-stu-id="41ddb-131">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="41ddb-132">Przestrzeń nazw, `CompanyB.MyLib` zastępuje domyślną nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="41ddb-132">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a><span data-ttu-id="41ddb-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41ddb-133">See also</span></span>

- [<span data-ttu-id="41ddb-134">Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="41ddb-134">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)
