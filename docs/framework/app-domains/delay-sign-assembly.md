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
ms.openlocfilehash: 17034eb5dcb48ae43b8e0cd0bd0f49d0b0920a8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921610"
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="537d8-102">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="537d8-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="537d8-103">Organizacja może mieć dokładnie chronioną parę kluczy, do której deweloperzy nie mają dostępu codziennie.</span><span class="sxs-lookup"><span data-stu-id="537d8-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="537d8-104">Klucz publiczny jest często dostępny, ale dostęp do klucza prywatnego jest ograniczony tylko do kilku osób.</span><span class="sxs-lookup"><span data-stu-id="537d8-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="537d8-105">Podczas tworzenia zestawów o silnych nazwach każdy zestaw, który odwołuje się do zestawu o silnej nazwie, zawiera token klucza publicznego, który jest używany do nadawania silnej nazwy zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="537d8-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="537d8-106">Wymaga to, aby klucz publiczny był dostępny podczas procesu tworzenia.</span><span class="sxs-lookup"><span data-stu-id="537d8-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="537d8-107">Możesz użyć opóźnionego lub częściowego podpisywania w czasie kompilacji, aby zarezerwować miejsce w przenośnym pliku wykonywalnym (PE) dla sygnatury silnej nazwy, ale odroczyć rzeczywiste podpisywanie do pewnego późniejszego etapu (zazwyczaj przed wysyłką zestawu).</span><span class="sxs-lookup"><span data-stu-id="537d8-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="537d8-108">Poniższe kroki przedstawiają proces opóźnienia podpisywania zestawu:</span><span class="sxs-lookup"><span data-stu-id="537d8-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1. <span data-ttu-id="537d8-109">Uzyskaj część klucza publicznego pary kluczy od organizacji, która będzie podpisywać ostateczne.</span><span class="sxs-lookup"><span data-stu-id="537d8-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="537d8-110">Zazwyczaj ten klucz jest w formie pliku. snk, który można utworzyć za pomocą [Narzędzia silnej nazwy (SN. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) dostarczonego przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="537d8-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>  
  
2. <span data-ttu-id="537d8-111">Dodaj adnotację do kodu źródłowego dla zestawu z dwoma atrybutami niestandardowymi z <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="537d8-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    - <span data-ttu-id="537d8-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, który przekazuje nazwę pliku zawierającego klucz publiczny jako parametr do jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="537d8-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    - <span data-ttu-id="537d8-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, co oznacza, że jest używane podpisywanie opóźnień, przekazując **wartość true** jako parametr do jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="537d8-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="537d8-114">Przykład:</span><span class="sxs-lookup"><span data-stu-id="537d8-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3. <span data-ttu-id="537d8-115">Kompilator wstawia klucz publiczny do manifestu zestawu i rezerwuje miejsce w pliku PE w celu uzyskania pełnej sygnatury silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="537d8-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="537d8-116">Prawdziwy klucz publiczny musi być przechowywany podczas tworzenia zestawu, tak aby inne zestawy odwołujące się do tego zestawu mogły uzyskać klucz do przechowywania we własnym odwołaniu do zestawu.</span><span class="sxs-lookup"><span data-stu-id="537d8-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4. <span data-ttu-id="537d8-117">Ponieważ zestaw nie ma prawidłowego podpisu silnej nazwy, weryfikacja tej sygnatury musi być wyłączona.</span><span class="sxs-lookup"><span data-stu-id="537d8-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="537d8-118">Można to zrobić za pomocą opcji **– VR** za pomocą narzędzia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="537d8-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="537d8-119">Poniższy przykład wyłącza weryfikację dla zestawu o nazwie `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="537d8-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="537d8-120">Aby wyłączyć weryfikację na platformach, w których nie można uruchomić narzędzia silnej nazwy, na przykład mikroprocesorów Advanced RISC Machine (ARM), użyj opcji **– VK** , aby utworzyć plik rejestru.</span><span class="sxs-lookup"><span data-stu-id="537d8-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="537d8-121">Zaimportuj plik rejestru do rejestru na komputerze, na którym chcesz wyłączyć weryfikację.</span><span class="sxs-lookup"><span data-stu-id="537d8-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="537d8-122">Poniższy przykład tworzy plik rejestru dla `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="537d8-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="537d8-123">Za pomocą opcji **– VR** lub **– VK** można opcjonalnie dołączyć plik. snk do podpisywania klucza testowego.</span><span class="sxs-lookup"><span data-stu-id="537d8-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="537d8-124">Nie należy polegać na silnych nazwach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="537d8-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="537d8-125">Zapewniają one tylko unikatową tożsamość.</span><span class="sxs-lookup"><span data-stu-id="537d8-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    > <span data-ttu-id="537d8-126">Jeśli używasz opóźnienia podpisywania podczas opracowywania w programie Visual Studio na komputerze 64-bitowym i kompilujesz zestaw dla **dowolnego procesora**, może być konieczne dwukrotne zastosowanie opcji **-VR** .</span><span class="sxs-lookup"><span data-stu-id="537d8-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="537d8-127">(W programie Visual Studio **każdy procesor CPU** jest wartością właściwości kompilacji **docelowej platformy** ; podczas kompilowania z wiersza polecenia jest to wartość domyślna). Aby uruchomić aplikację z poziomu wiersza polecenia lub Eksploratora plików, użyj 64-bitowej wersji [SN. exe (Narzędzie silnej nazwy)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) , aby zastosować opcję **-VR** do zestawu.</span><span class="sxs-lookup"><span data-stu-id="537d8-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="537d8-128">Aby załadować zestaw do programu Visual Studio w czasie projektowania (na przykład jeśli zestaw zawiera składniki, które są używane przez inne zestawy w aplikacji), użyj 32-bitowej wersji narzędzia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="537d8-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="537d8-129">Dzieje się tak, ponieważ kompilator just-in-Time (JIT) kompiluje zestaw do 64-bitowego kodu natywnego, gdy zestaw jest uruchamiany z wiersza polecenia i do 32-bitowy kod natywny, gdy zestaw jest ładowany do środowiska czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="537d8-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5. <span data-ttu-id="537d8-130">Później, zazwyczaj tuż przed wysyłką, przesyłasz zestaw do urzędu podpisywania w organizacji w celu zapewnienia rzeczywistego podpisywania silnej nazwy przy użyciu opcji **– R** z narzędziem silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="537d8-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="537d8-131">Poniższy przykład podpisuje zestaw `myAssembly.dll` o silnej nazwie `sgKey.snk` przy użyciu pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="537d8-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="537d8-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="537d8-132">See also</span></span>

- [<span data-ttu-id="537d8-133">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="537d8-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="537d8-134">Instrukcje: Tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="537d8-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="537d8-135">Sn.exe (narzędzie silnych nazw)</span><span class="sxs-lookup"><span data-stu-id="537d8-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="537d8-136">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="537d8-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
