---
title: Podpisywanie zestawu z opóźnieniem
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 75c86c49f4d471452a7e8f56856d5437e84df307
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084345"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="17c0d-102">Podpisywanie zestawu z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="17c0d-102">Delay-sign an assembly</span></span>

<span data-ttu-id="17c0d-103">Organizacja może mieć dokładnie chronioną parę kluczy, której deweloperzy nie mogą uzyskać codziennie.</span><span class="sxs-lookup"><span data-stu-id="17c0d-103">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="17c0d-104">Klucz publiczny jest często dostępny, ale dostęp do klucza prywatnego jest ograniczony tylko do kilku osób.</span><span class="sxs-lookup"><span data-stu-id="17c0d-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="17c0d-105">Podczas tworzenia zestawów o silnych nazwach każdy zestaw, który odwołuje się do zestawu o silnej nazwie, zawiera token klucza publicznego, który jest używany do nadawania silnej nazwy zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="17c0d-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="17c0d-106">Wymaga to, aby klucz publiczny był dostępny podczas procesu tworzenia.</span><span class="sxs-lookup"><span data-stu-id="17c0d-106">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="17c0d-107">Możesz użyć opóźnionego lub częściowego podpisywania w czasie kompilacji, aby zarezerwować miejsce w przenośnym pliku wykonywalnym (PE) dla sygnatury silnej nazwy, ale odroczyć rzeczywiste podpisywanie do późniejszego etapu, zazwyczaj przed wysyłką zestawu.</span><span class="sxs-lookup"><span data-stu-id="17c0d-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="17c0d-108">Aby podpisać zestaw z opóźnieniem:</span><span class="sxs-lookup"><span data-stu-id="17c0d-108">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="17c0d-109">Pobierz część klucza publicznego pary kluczy z organizacji, która będzie podpisywać ostateczne.</span><span class="sxs-lookup"><span data-stu-id="17c0d-109">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="17c0d-110">Zazwyczaj ten klucz jest w formie pliku *. snk* , który można utworzyć za pomocą [Narzędzia silnej nazwy (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md) dostarczonego przez Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="17c0d-110">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="17c0d-111">Dodaj adnotację do kodu źródłowego dla zestawu z dwoma atrybutami niestandardowymi z <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="17c0d-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="17c0d-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, który przekazuje nazwę pliku zawierającego klucz publiczny jako parametr do jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="17c0d-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="17c0d-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, która wskazuje, że podpisywanie opóźnień jest używane przez przekazanie jako parametru do jego konstruktora **wartości true** .</span><span class="sxs-lookup"><span data-stu-id="17c0d-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="17c0d-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="17c0d-114">For example:</span></span>

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. <span data-ttu-id="17c0d-115">Kompilator wstawia klucz publiczny do manifestu zestawu i rezerwuje miejsce w pliku PE w celu uzyskania pełnej sygnatury silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="17c0d-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="17c0d-116">Prawdziwy klucz publiczny musi być przechowywany podczas tworzenia zestawu, tak aby inne zestawy odwołujące się do tego zestawu mogły uzyskać klucz do przechowywania we własnym odwołaniu do zestawu.</span><span class="sxs-lookup"><span data-stu-id="17c0d-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="17c0d-117">Ponieważ zestaw nie ma prawidłowego podpisu silnej nazwy, weryfikacja tej sygnatury musi być wyłączona.</span><span class="sxs-lookup"><span data-stu-id="17c0d-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="17c0d-118">Można to zrobić za pomocą opcji **– VR** za pomocą narzędzia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="17c0d-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="17c0d-119">Poniższy przykład wyłącza weryfikację dla zestawu o nazwie Moja *Assembly. dll*.</span><span class="sxs-lookup"><span data-stu-id="17c0d-119">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="17c0d-120">Aby wyłączyć weryfikację na platformach, w których nie można uruchomić narzędzia silnej nazwy, na przykład mikroprocesorów Advanced RISC Machine (ARM), użyj opcji **– VK** , aby utworzyć plik rejestru.</span><span class="sxs-lookup"><span data-stu-id="17c0d-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="17c0d-121">Zaimportuj plik rejestru do rejestru na komputerze, na którym chcesz wyłączyć weryfikację.</span><span class="sxs-lookup"><span data-stu-id="17c0d-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="17c0d-122">Poniższy przykład tworzy plik rejestru dla `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="17c0d-122">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="17c0d-123">Za pomocą opcji **– VR** lub **– VK** można opcjonalnie dołączyć plik *. snk* do podpisywania klucza testowego.</span><span class="sxs-lookup"><span data-stu-id="17c0d-123">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="17c0d-124">Nie należy polegać na silnych nazwach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="17c0d-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="17c0d-125">Zapewniają one tylko unikatową tożsamość.</span><span class="sxs-lookup"><span data-stu-id="17c0d-125">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="17c0d-126">Jeśli używasz opóźnienia podpisywania podczas opracowywania w programie Visual Studio na komputerze 64-bitowym i kompilujesz zestaw dla **dowolnego procesora**, może być konieczne dwukrotne zastosowanie opcji **-VR** .</span><span class="sxs-lookup"><span data-stu-id="17c0d-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="17c0d-127">(W programie Visual Studio **każdy procesor CPU** jest wartością właściwości kompilacji **docelowej platformy** ; podczas kompilowania z wiersza polecenia jest to wartość domyślna). Aby uruchomić aplikację z poziomu wiersza polecenia lub Eksploratora plików, użyj 64-bitowej wersji [SN. exe (Narzędzie silnej nazwy)](../../framework/tools/sn-exe-strong-name-tool.md) , aby zastosować opcję **-VR** do zestawu.</span><span class="sxs-lookup"><span data-stu-id="17c0d-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="17c0d-128">Aby załadować zestaw do programu Visual Studio w czasie projektowania (na przykład jeśli zestaw zawiera składniki, które są używane przez inne zestawy w aplikacji), użyj 32-bitowej wersji narzędzia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="17c0d-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="17c0d-129">Dzieje się tak, ponieważ kompilator just-in-Time (JIT) kompiluje zestaw do 64-bitowego kodu natywnego, gdy zestaw jest uruchamiany z wiersza polecenia i do 32-bitowy kod natywny, gdy zestaw jest ładowany do środowiska czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="17c0d-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="17c0d-130">Później, zazwyczaj tuż przed wysyłką, przesyłasz zestaw do urzędu podpisywania w organizacji w celu zapewnienia rzeczywistego podpisywania silnej nazwy przy użyciu opcji **– R** z narzędziem silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="17c0d-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="17c0d-131">Poniższy przykład podpisuje zestaw o nazwie *plik. dll* o silnej nazwie przy użyciu pary kluczy *sgKey. snk* .</span><span class="sxs-lookup"><span data-stu-id="17c0d-131">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="17c0d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17c0d-132">See also</span></span>

- [<span data-ttu-id="17c0d-133">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="17c0d-133">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="17c0d-134">Instrukcje: Tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="17c0d-134">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="17c0d-135">SN. exe (Narzędzie silnej nazwy)</span><span class="sxs-lookup"><span data-stu-id="17c0d-135">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="17c0d-136">Program z zestawami</span><span class="sxs-lookup"><span data-stu-id="17c0d-136">Program with assemblies</span></span>](program.md)
