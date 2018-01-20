---
title: "Porady: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dfbf3c2282e60ec45cb136f52fb115a8d769678
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="d11a0-102">Porady: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="d11a0-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>
<span data-ttu-id="d11a0-103">Istnieją dwa sposoby Generowanie podstawowego zestawu międzyoperacyjnego:</span><span class="sxs-lookup"><span data-stu-id="d11a0-103">There are two ways to generate a primary interop assembly:</span></span>  
  
-   <span data-ttu-id="d11a0-104">Przy użyciu [wpisz Importer biblioteki (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) dostarczonych przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d11a0-104">Using the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
     <span data-ttu-id="d11a0-105">Najbardziej oczywistym sposobem uzyskania podstawowe zestawy międzyoperacyjne jest użycie [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="d11a0-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="d11a0-106">Tlbimp.exe zapewnia następujące mechanizmy:</span><span class="sxs-lookup"><span data-stu-id="d11a0-106">Tlbimp.exe provides the following safeguards:</span></span>  
  
    -   <span data-ttu-id="d11a0-107">Sprawdza, czy inne zarejestrowane podstawowe zestawy międzyoperacyjne przed utworzeniem nowego zestawy międzyoperacyjne odwołań biblioteki typu zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="d11a0-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>  
  
    -   <span data-ttu-id="d11a0-108">Nie można wyemitować podstawowego zestawu międzyoperacyjnego, jeśli nie określisz kontener lub nazwę pliku, aby zapewnić podstawowy zestaw międzyoperacyjny silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d11a0-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>  
  
    -   <span data-ttu-id="d11a0-109">Nie można wyemitować podstawowego zestawu międzyoperacyjnego, jeśli pominięto odwołania do zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="d11a0-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>  
  
    -   <span data-ttu-id="d11a0-110">Nie można wyemitować podstawowy zestaw międzyoperacyjny dodania odwołania do zestawów zależnych, które nie są podstawowe zestawy międzyoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="d11a0-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>  
  
-   <span data-ttu-id="d11a0-111">Podstawowe zestawy międzyoperacyjne ręczne tworzenie w kodzie źródłowym przy użyciu języka, który jest zgodny z typowych Language Specification (ze specyfikacją CLS), takich jak C#.</span><span class="sxs-lookup"><span data-stu-id="d11a0-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="d11a0-112">Takie rozwiązanie jest przydatne, gdy biblioteka typów jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="d11a0-112">This approach is useful when a type library is unavailable.</span></span>  
  
 <span data-ttu-id="d11a0-113">Musi mieć pary kluczy kryptograficznych można podpisać zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="d11a0-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="d11a0-114">Aby uzyskać więcej informacji, zobacz [tworzenie pary klucz A](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="d11a0-114">For details, see [Creating A Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="d11a0-115">Aby wygenerować podstawowego zestawu międzyoperacyjnego przy użyciu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="d11a0-115">To generate a primary interop assembly using Tlbimp.exe</span></span>  
  
1.  <span data-ttu-id="d11a0-116">W wierszu polecenia wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="d11a0-116">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="d11a0-117">**tlbimp** *tlbfile***/primary/KeyFile:** *filename* **/out:** *assemblyname* </span><span class="sxs-lookup"><span data-stu-id="d11a0-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>  
  
     <span data-ttu-id="d11a0-118">W tym poleceniu *tlbfile* jest plik zawierający biblioteki typów COM *filename* to nazwa kontenera lub plik, który zawiera pary kluczy i *assemblyname* jest Nazwa logowania przy użyciu silnej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="d11a0-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>  
  
 <span data-ttu-id="d11a0-119">Podstawowe zestawy międzyoperacyjne może odwoływać się tylko inne podstawowe zestawy międzyoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="d11a0-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="d11a0-120">Jeśli Twoje zestawu odwołuje się do typów z biblioteki typów COM innych firm, należy uzyskać podstawowy zestaw międzyoperacyjny wydawcy przed wygenerowaniem Twojego podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d11a0-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="d11a0-121">Jeśli jesteś wydawcy, należy wygenerować podstawowy zestaw międzyoperacyjny dla biblioteki typów zależnych przed wygenerowaniem odwołaniem do podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d11a0-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>  
  
 <span data-ttu-id="d11a0-122">Zależne podstawowego zestawu międzyoperacyjnego z numerem wersji, która różni się od oryginalnej biblioteki typów nie jest wykrywalny, gdy zainstalowane w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d11a0-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="d11a0-123">Należy zarejestrować zależnych podstawowy zestaw międzyoperacyjny w rejestrze systemu Windows lub użyj **/reference** opcji, należy upewnić się, że Tlbimp.exe znajdzie zależnej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="d11a0-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>  
  
 <span data-ttu-id="d11a0-124">Można również zawijać wielu wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="d11a0-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="d11a0-125">Aby uzyskać instrukcje, zobacz [porady: zawijanie wielu wersji z biblioteki typów](http://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f).</span><span class="sxs-lookup"><span data-stu-id="d11a0-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](http://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d11a0-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="d11a0-126">Example</span></span>  
 <span data-ttu-id="d11a0-127">Poniższy przykład importuje Biblioteka typów COM `LibUtil.tlb` i podpisuje zestawu `LibUtil.dll` przy użyciu silnej nazwy przy użyciu pliku klucza `CompanyA.snk`.</span><span class="sxs-lookup"><span data-stu-id="d11a0-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="d11a0-128">Pomijając nazwę określonych przestrzeni nazw, w tym przykładzie tworzy domyślną przestrzeń nazw, `LibUtil`.</span><span class="sxs-lookup"><span data-stu-id="d11a0-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 <span data-ttu-id="d11a0-129">Dla nazwy opisowej (przy użyciu *Nazwa_producenta*. *LibraryName* nazewnictwa wytyczne), poniższy przykład przesłania domyślną nazwę pliku zestawu i nazwa przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d11a0-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 <span data-ttu-id="d11a0-130">Poniższy przykład importuje `MyLib.tlb`, które odwołania `CompanyA.LibUtil.dll`, i podpisuje zestawu `CompanyB.MyLib.dll` przy użyciu silnej nazwy przy użyciu pliku klucza `CompanyB.snk`.</span><span class="sxs-lookup"><span data-stu-id="d11a0-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="d11a0-131">Przestrzeń nazw, `CompanyB.MyLib`, zastępuje domyślną nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d11a0-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="d11a0-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d11a0-132">See Also</span></span>  
 [<span data-ttu-id="d11a0-133">Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="d11a0-133">How to: Register Primary Interop Assemblies</span></span>](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
