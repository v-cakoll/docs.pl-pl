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
ms.openlocfilehash: 113df1ad3fc3ac1e27ebfef572494c1f15a3dbb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733163"
---
# <a name="delay-sign-an-assembly"></a><span data-ttu-id="9cc3b-102">Podpisywanie zestawu z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="9cc3b-102">Delay-sign an assembly</span></span>

<span data-ttu-id="9cc3b-103">Organizacja może mieć ściśle strzeżoną parę kluczy, do których deweloperzy nie mogą uzyskać dostępu na co dzień.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-103">An organization can have a closely guarded key pair that developers can't access on a daily basis.</span></span> <span data-ttu-id="9cc3b-104">Klucz publiczny jest często dostępny, ale dostęp do klucza prywatnego jest ograniczony tylko do kilku osób.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="9cc3b-105">Podczas opracowywania zestawów o silnych nazwach, każdy zestaw, który odwołuje się do zestawu docelowego o silnej nazwie zawiera token klucza publicznego używanego do nadania zestawowi docelowemu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="9cc3b-106">Wymaga to, aby klucz publiczny był dostępny podczas procesu opracowywania.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-106">This requires that the public key be available during the development process.</span></span>

<span data-ttu-id="9cc3b-107">Można użyć opóźnionego lub częściowego podpisywania w czasie kompilacji, aby zarezerwować miejsce w przenośnym pliku wykonywalnym (PE) dla podpisu silnej nazwy, ale odroczyć rzeczywiste podpisywanie do jakiegoś późniejszego etapu, zwykle tuż przed wysyłką zestawu.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage, usually just before shipping the assembly.</span></span>

<span data-ttu-id="9cc3b-108">Aby opóźnić-sign zestawu:</span><span class="sxs-lookup"><span data-stu-id="9cc3b-108">To delay-sign an assembly:</span></span>

1. <span data-ttu-id="9cc3b-109">Pobierz część klucza publicznego pary kluczy od organizacji, która będzie wykonywać ostateczne podpisywanie.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-109">Get the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="9cc3b-110">Zazwyczaj ten klucz jest w postaci pliku *.snk,* który może być utworzony przy użyciu [narzędzia Silna nazwa (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) dostarczonego przez zestaw Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-110">Typically this key is in the form of an *.snk* file, which can be created using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) provided by the Windows SDK.</span></span>

2. <span data-ttu-id="9cc3b-111">Adnotuj kod źródłowy zestawu za <xref:System.Reflection>pomocą dwóch atrybutów niestandardowych z:</span><span class="sxs-lookup"><span data-stu-id="9cc3b-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>

   - <span data-ttu-id="9cc3b-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, który przekazuje nazwę pliku zawierającego klucz publiczny jako parametr do jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>

   - <span data-ttu-id="9cc3b-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, co wskazuje, że podpisywanie opóźnienia jest używany przez przekazywanie **true** jako parametr do jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span>

   <span data-ttu-id="9cc3b-114">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9cc3b-114">For example:</span></span>

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

3. <span data-ttu-id="9cc3b-115">Kompilator wstawia klucz publiczny do manifestu zestawu i rezerwuje miejsce w pliku PE dla pełnego podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="9cc3b-116">Prawdziwy klucz publiczny musi być przechowywany podczas złożenia jest zbudowany tak, aby inne zestawy, które odwołują się do tego zestawu można uzyskać klucz do przechowywania w ich odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>

4. <span data-ttu-id="9cc3b-117">Ponieważ zestaw nie ma prawidłowego podpisu silnej nazwy, weryfikacja tego podpisu musi być wyłączona.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="9cc3b-118">Możesz to zrobić za pomocą opcji **-Vr** za pomocą narzędzia Silna nazwa.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>

     <span data-ttu-id="9cc3b-119">Poniższy przykład wyłącza weryfikację dla zestawu o nazwie *myAssembly.dll*.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-119">The following example turns off verification for an assembly called *myAssembly.dll*.</span></span>

   ```console
   sn –Vr myAssembly.dll
   ```

   <span data-ttu-id="9cc3b-120">Aby wyłączyć weryfikację na platformach, na których nie można uruchomić narzędzia Silna nazwa, takiego jak mikroprocesory ARM (Advanced RISC Machine), użyj opcji **–Vk,** aby utworzyć plik rejestru.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="9cc3b-121">Zaimportuj plik rejestru do rejestru na komputerze, na którym chcesz wyłączyć weryfikację.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="9cc3b-122">Poniższy przykład tworzy plik `myAssembly.dll`rejestru dla .</span><span class="sxs-lookup"><span data-stu-id="9cc3b-122">The following example creates a registry file for `myAssembly.dll`.</span></span>

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   <span data-ttu-id="9cc3b-123">Za pomocą opcji **–Vr** lub **–Vk** można opcjonalnie dołączyć plik *.snk* do podpisywania klucza testowego.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-123">With either the **–Vr** or **–Vk** option, you can optionally include an *.snk* file for test key signing.</span></span>

   > [!WARNING]
   > <span data-ttu-id="9cc3b-124">Nie należy polegać na silne nazwy dla bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="9cc3b-125">Zapewniają one tylko unikatową tożsamość.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-125">They provide a unique identity only.</span></span>

   > [!NOTE]
   > <span data-ttu-id="9cc3b-126">Jeśli używasz podpisywania opóźnienia podczas tworzenia programu Visual Studio na komputerze 64-bitowym i skompilować zestaw dla **dowolnego procesora CPU,** może być trzeba zastosować opcję **-Vr** dwa razy.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="9cc3b-127">(W programie Visual Studio **dowolny procesor CPU** jest wartością właściwości kompilacji **docelowej platformy;** podczas kompilowania z wiersza polecenia jest to wartość domyślna). Aby uruchomić aplikację z wiersza polecenia lub z Eksploratora plików, użyj 64-bitowej wersji [narzędzia Sn.exe (Silna nazwa),](../../framework/tools/sn-exe-strong-name-tool.md) aby zastosować opcję **-Vr** do zestawu.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="9cc3b-128">Aby załadować zestaw do programu Visual Studio w czasie projektowania (na przykład jeśli zestaw zawiera składniki, które są używane przez inne zestawy w aplikacji), należy użyć 32-bitowej wersji narzędzia o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="9cc3b-129">Dzieje się tak, ponieważ kompilator just-in-time (JIT) kompiluje zestaw do 64-bitowego kodu macierzystego, gdy zestaw jest uruchamiany z wiersza polecenia, oraz do 32-bitowego kodu macierzystego po załadowaniu zestawu do środowiska czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>

5. <span data-ttu-id="9cc3b-130">Później, zwykle tuż przed wysyłką, przesyłasz zestaw do urzędu podpisywania organizacji w celu podpisania rzeczywistej silnej nazwy za pomocą opcji **–R** za pomocą narzędzia Silna nazwa.</span><span class="sxs-lookup"><span data-stu-id="9cc3b-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>

   <span data-ttu-id="9cc3b-131">Poniższy przykład podpisuje zestaw o nazwie *myAssembly.dll* o silnej nazwie przy użyciu pary *kluczy sgKey.snk.*</span><span class="sxs-lookup"><span data-stu-id="9cc3b-131">The following example signs an assembly called *myAssembly.dll* with a strong name using the *sgKey.snk* key pair.</span></span>

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a><span data-ttu-id="9cc3b-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cc3b-132">See also</span></span>

- [<span data-ttu-id="9cc3b-133">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="9cc3b-133">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="9cc3b-134">Jak: Tworzenie pary kluczy publiczno-prywatnych</span><span class="sxs-lookup"><span data-stu-id="9cc3b-134">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="9cc3b-135">Sn.exe (narzędzie Silna nazwa)</span><span class="sxs-lookup"><span data-stu-id="9cc3b-135">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
