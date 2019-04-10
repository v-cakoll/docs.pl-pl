---
title: Opóźnione podpisywanie zestawu
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc955ca892a8a0e5d15710b76a6a1c798ad4ecf5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334058"
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="1e0f5-102">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="1e0f5-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="1e0f5-103">Organizacja może mieć ściśle chronionej parę kluczy, że deweloperzy nie mają dostępu do codziennie.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="1e0f5-104">Klucz publiczny jest często dostępne, ale dostęp do klucza prywatnego jest ograniczony do tylko kilka osób.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="1e0f5-105">Podczas tworzenia zestawów o silnych nazwach, każdy zestaw ten zestaw docelowy o silnej nazwie odwołania zawiera token klucza publicznego, używać, aby zapewnić silnej nazwy zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="1e0f5-106">Wymaga to, czy klucz publiczny będą dostępne podczas procesu projektowania.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="1e0f5-107">Opóźnione lub częściowe podpisywanie w czasie kompilacji służy do rezerwowania miejsca w przenośny plik wykonywalny (PE) dla podpisu silnej nazwy, ale Odrocz rzeczywiste podpisywania do czasu na późniejszym etapie (zazwyczaj po prostu przed dostarczeniem zestawu).</span><span class="sxs-lookup"><span data-stu-id="1e0f5-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="1e0f5-108">Poniższe kroki przedstawiają procedurę opóźnione podpisywanie zestawu:</span><span class="sxs-lookup"><span data-stu-id="1e0f5-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1. <span data-ttu-id="1e0f5-109">Uzyskaj część z kluczem publicznym pary kluczy od organizacji, która będzie zajmować się ostateczną podpisywania.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="1e0f5-110">Zazwyczaj ten klucz jest w formie pliku .snk, które mogą być tworzone za pomocą [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) dostarczone przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e0f5-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
2. <span data-ttu-id="1e0f5-111">Dodawanie adnotacji do kodu źródłowego dla zestawu za pomocą dwóch atrybutów niestandardowych z <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="1e0f5-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute><span data-ttu-id="1e0f5-112">, która przekazuje nazwę pliku zawierającego klucz publiczny jako parametr do jej konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-112">, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute><span data-ttu-id="1e0f5-113">, co oznacza, że opóźnienie podpisywania jest używany przez przekazanie **true** jako parametr do jej konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-113">, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="1e0f5-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1e0f5-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3. <span data-ttu-id="1e0f5-115">Kompilator wstawia klucz publiczny do manifestu zestawu i rezerwuje miejsce w pliku PE podpisu pełnej silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="1e0f5-116">Rzeczywiste publicznego klucza musi być przechowywany, natomiast zestaw zaprojektowano tak, aby inne zestawy odwołujące się do tego zestawu można uzyskać klucz do przechowywania w odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4. <span data-ttu-id="1e0f5-117">Ponieważ zestaw nie ma podpisu prawidłową silną nazwę, należy wyłączyć weryfikację ten podpis.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="1e0f5-118">Można to zrobić za pomocą **— Vr** opcji narzędzie silnych nazw.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="1e0f5-119">Poniższy przykład powoduje wyłączenie weryfikacji dla zestawu o nazwie `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="1e0f5-120">Aby wyłączyć weryfikację na platformach gdzie nie można uruchomić narzędzie silnych nazw, takich jak mikroprocesory Advanced RISC Machine (ARM), należy użyć **— Vk** opcję, aby utworzyć plik rejestru.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="1e0f5-121">Importuj plik rejestru do rejestru na komputerze, w którym chcesz wyłączyć weryfikację.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="1e0f5-122">Poniższy przykład tworzy plik rejestru dla `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="1e0f5-123">Z oboma **— Vr** lub **— Vk** opcji, możesz opcjonalnie dołączyć plik .snk dla klucza podpisywania testów.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="1e0f5-124">Nie należy polegać na silne nazwy dla zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="1e0f5-125">Zapewniają one tylko unikatową tożsamość.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="1e0f5-126">Jeśli używasz opóźnione podpisywanie podczas programowania przy użyciu programu Visual Studio na komputerze 64-bitowym i kompilowania zestawu dla **dowolny Procesor**, może być konieczne zastosowanie **- Vr** opcji dwa razy.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="1e0f5-127">(W programie Visual Studio, **dowolny Procesor** jest wartością **platformę docelową** Tworzenie właściwości, podczas kompilowania z wiersza polecenia jest domyślna.) Aby uruchomić aplikację z poziomu wiersza polecenia lub Eksploratora plików, należy użyć 64-bitową wersję [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) do zastosowania **- Vr** opcji do zestawu.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="1e0f5-128">Aby załadować zestaw do programu Visual Studio w czasie projektowania (na przykład, jeśli zestaw zawiera składniki, które są używane przez inne zestawy w aplikacji), użyj wersji 32-bitowe narzędzie silnych nazw.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="1e0f5-129">Jest to spowodowane kompilator just-in-time (JIT) kompiluje zestaw 64-bitowego kodu macierzystego przy uruchamianiu z wiersza polecenia zestawu i 32-bitowego kodu natywnego, gdy zestaw jest ładowany do środowiska czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5. <span data-ttu-id="1e0f5-130">Później, zwykle po prostu przed wysyłką przesyłasz podpisywania urzędu dla rzeczywistego podpisywania silnymi nazwami przy użyciu zestawu dla Twojej organizacji **– R** opcji narzędzie silnych nazw.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="1e0f5-131">Poniższy przykład podpisuje zestaw o nazwie `myAssembly.dll` z silną nazwą przy użyciu `sgKey.snk` pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="1e0f5-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1e0f5-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e0f5-132">See also</span></span>

- [<span data-ttu-id="1e0f5-133">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="1e0f5-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="1e0f5-134">Instrukcje: Tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="1e0f5-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="1e0f5-135">Sn.exe (Narzędzie silnych nazw)</span><span class="sxs-lookup"><span data-stu-id="1e0f5-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="1e0f5-136">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="1e0f5-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
