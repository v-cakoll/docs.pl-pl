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
ms.openlocfilehash: a944cf87783c59c21bffc9c48a18237c9fe6cdec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295500"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="f2559-102">Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="f2559-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>
<span data-ttu-id="f2559-103">Istnieją dwa sposoby generowania podstawowego zestawu międzyoperacyjnego:</span><span class="sxs-lookup"><span data-stu-id="f2559-103">There are two ways to generate a primary interop assembly:</span></span>  
  
-   <span data-ttu-id="f2559-104">Za pomocą [wpisz Importer biblioteki (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) dostarczone przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2559-104">Using the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
     <span data-ttu-id="f2559-105">Najprostszy sposób do tworzenia podstawowych zestawów międzyoperacyjnych polega na użyciu [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="f2559-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="f2559-106">Tlbimp.exe zawiera następujące mechanizmy:</span><span class="sxs-lookup"><span data-stu-id="f2559-106">Tlbimp.exe provides the following safeguards:</span></span>  
  
    -   <span data-ttu-id="f2559-107">Sprawdza, czy inne zarejestrowanych podstawowych zestawach międzyoperacyjnych, przed utworzeniem nowego zestawy międzyoperacyjne dla żadnych odwołań do biblioteki typu zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="f2559-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>  
  
    -   <span data-ttu-id="f2559-108">Nie Emituj podstawowego zestawu międzyoperacyjnego, jeśli nie określisz kontenera lub nazwę pliku, aby zapewnić podstawowy zestaw międzyoperacyjny silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f2559-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>  
  
    -   <span data-ttu-id="f2559-109">Nie można wyemitować podstawowy zestaw międzyoperacyjny, jeśli pominięto odwołania do zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="f2559-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>  
  
    -   <span data-ttu-id="f2559-110">Nie Emituj podstawowy zestaw międzyoperacyjny, po dodaniu odwołania do zestawów zależnych, które nie są podstawowe zestawy międzyoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="f2559-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>  
  
-   <span data-ttu-id="f2559-111">Ręczne tworzenie podstawowych zestawów międzyoperacyjnych w kodzie źródłowym przy użyciu języka, który jest zgodny z Common Language Specification (CLS), takich jak C#.</span><span class="sxs-lookup"><span data-stu-id="f2559-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="f2559-112">Takie podejście jest przydatne, gdy biblioteki typów jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="f2559-112">This approach is useful when a type library is unavailable.</span></span>  
  
 <span data-ttu-id="f2559-113">Musisz mieć parę kluczy kryptograficznych, aby podpisać zestaw silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="f2559-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="f2559-114">Aby uzyskać więcej informacji, zobacz [tworzenia pary klucz](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="f2559-114">For details, see [Creating A Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="f2559-115">Aby wygenerować podstawowego zestawu międzyoperacyjnego przy użyciu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="f2559-115">To generate a primary interop assembly using Tlbimp.exe</span></span>  
  
1. <span data-ttu-id="f2559-116">W wierszu polecenia wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="f2559-116">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="f2559-117">**tlbimp** *tlbfile\*\*\*/primary/KeyFile:*\* *filename* **/out:** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="f2559-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>  
  
     <span data-ttu-id="f2559-118">W tym poleceniu *tlbfile* to plik biblioteki typów modelu COM, zawierającą *filename* to nazwa kontenera lub pliku, który zawiera pary kluczy i *assemblyname* jest Nazwa zestawu, aby zalogować się przy użyciu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f2559-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>  
  
 <span data-ttu-id="f2559-119">Podstawowe zestawy międzyoperacyjne może odwoływać się tylko inne podstawowe zestawy międzyoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="f2559-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="f2559-120">Jeśli zestaw odwołuje się do typów w bibliotece typów modelu COM innych firm, należy uzyskać podstawowy zestaw międzyoperacyjny od wydawcy przed wygenerowaniem Twojego podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f2559-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="f2559-121">Jeśli jesteś wydawcą, należy wygenerować podstawowego zestawu międzyoperacyjnego dla zależnej biblioteki typów przed wygenerowaniem odwołujący się podstawowy zestaw międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="f2559-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>  
  
 <span data-ttu-id="f2559-122">Zależne podstawowego zestawu międzyoperacyjnego z numerem wersji, która różni się od oryginalnej biblioteki typów nie jest stała się wykrywalna zainstalowany w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f2559-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="f2559-123">Należy zarejestrować zależne podstawowy zestaw międzyoperacyjny w rejestrze systemu Windows lub użyj **/reference** opcji, należy upewnić się, że Tlbimp.exe znajdzie zależnej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="f2559-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>  
  
 <span data-ttu-id="f2559-124">Można również opakować wielu wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="f2559-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="f2559-125">Aby uzyskać instrukcje, zobacz [jak: OPAKOWYWANIE wielu wersji bibliotek typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f2559-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2559-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2559-126">Example</span></span>  
 <span data-ttu-id="f2559-127">Następujący przykład importuje biblioteki typów COM `LibUtil.tlb` i podpisuje zestaw `LibUtil.dll` silną nazwą przy użyciu pliku klucza `CompanyA.snk`.</span><span class="sxs-lookup"><span data-stu-id="f2559-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="f2559-128">Pomijając nazwę określonej przestrzeni nazw, ten przykład generuje domyślny obszar nazw `LibUtil`.</span><span class="sxs-lookup"><span data-stu-id="f2559-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 <span data-ttu-id="f2559-129">Aby uzyskać bardziej opisową nazwę (przy użyciu *Nazwa_producenta*. *LibraryName* wskazówkami dotyczącymi nazewnictwa), poniższy przykład zastępuje domyślną nazwę pliku zestawu i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f2559-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 <span data-ttu-id="f2559-130">Następujący przykład importuje `MyLib.tlb`, która odwołuje się do `CompanyA.LibUtil.dll`, i podpisuje zestaw `CompanyB.MyLib.dll` silną nazwą przy użyciu pliku klucza `CompanyB.snk`.</span><span class="sxs-lookup"><span data-stu-id="f2559-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="f2559-131">Przestrzeń nazw, `CompanyB.MyLib`, przesłania domyślną nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f2559-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2559-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2559-132">See also</span></span>

- [<span data-ttu-id="f2559-133">Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="f2559-133">How to: Register Primary Interop Assemblies</span></span>](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
