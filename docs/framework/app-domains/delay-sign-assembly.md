---
title: "Opóźnione podpisywanie zestawu"
ms.date: 07/31/2017
ms.prod: .net-framework
ms.technology: dotnet-bcl
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce40f08b8b31ae3a4647e8919b4ea862fc03506f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="e04ec-102">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="e04ec-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="e04ec-103">Organizacja może mieć ściśle związany parę kluczy, że deweloperzy nie mają dostępu do codziennie.</span><span class="sxs-lookup"><span data-stu-id="e04ec-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="e04ec-104">Klucz publiczny często są dostępne, ale dostęp do klucza prywatnego jest ograniczony do tylko kilka osób.</span><span class="sxs-lookup"><span data-stu-id="e04ec-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="e04ec-105">Podczas tworzenia zestawy o silnych nazwach, każdego zestawu tego zestawu docelowego odwołania o silnych nazwach zawiera token klucza publicznego używać, aby zapewnić silnej nazwy zestawu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e04ec-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="e04ec-106">To wymaga klucza publicznego dostępne podczas procesu projektowania.</span><span class="sxs-lookup"><span data-stu-id="e04ec-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="e04ec-107">Umożliwia opóźnione lub częściowe podpisywanie w czasie kompilacji zarezerwowanego miejsca w przenośny plik wykonywalny (PE) dla podpisu silnej nazwy, ale mają być odroczone rzeczywiste podpisywania do czasu późniejszym etapie (zwykle tylko przed dostarczeniem zestawu).</span><span class="sxs-lookup"><span data-stu-id="e04ec-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="e04ec-108">Poniższe kroki wchodzą w skład procesu opóźnione podpisywanie zestawu:</span><span class="sxs-lookup"><span data-stu-id="e04ec-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1.  <span data-ttu-id="e04ec-109">Uzyskaj publicznej części klucza o pary kluczy z organizacji, który będzie do ostatecznego podpisywania.</span><span class="sxs-lookup"><span data-stu-id="e04ec-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="e04ec-110">Zazwyczaj ten klucz jest w formie pliku .snk —, które mogą być tworzone przy użyciu [narzędzie Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) dostarczonych przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e04ec-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
2.  <span data-ttu-id="e04ec-111">Dodawanie adnotacji kodu źródłowego dla zestawu z dwóch atrybutów niestandardowych z <xref:System.Reflection>:</span><span class="sxs-lookup"><span data-stu-id="e04ec-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    -   <span data-ttu-id="e04ec-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, która przekazuje nazwę pliku zawierającego klucz publiczny jako parametru dla jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e04ec-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    -   <span data-ttu-id="e04ec-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, co oznacza, że podpisywanie opóźnione jest używany przez przekazanie **true** jako parametru dla jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e04ec-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="e04ec-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e04ec-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  <span data-ttu-id="e04ec-115">Kompilator wstawia klucz publiczny w manifeście zestawu i rezerwuje miejsce w pliku PE pełnej silnego podpisu.</span><span class="sxs-lookup"><span data-stu-id="e04ec-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="e04ec-116">Klucz publiczny rzeczywistym musi być przechowywany podczas zestaw skonstruowano, dzięki czemu inne zestawy, które odwołują się do tego zestawu można uzyskać klucz do przechowywania w odwołaniu do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e04ec-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4.  <span data-ttu-id="e04ec-117">Ponieważ zestaw nie ma podpisu prawidłową silną nazwę, weryfikacja ten podpis musi być wyłączony.</span><span class="sxs-lookup"><span data-stu-id="e04ec-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="e04ec-118">Można to zrobić za pomocą **— Vr** opcji za pomocą narzędzia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e04ec-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="e04ec-119">Poniższy przykład powoduje wyłączenie weryfikacji dla zestawu o nazwie `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="e04ec-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="e04ec-120">Aby wyłączyć funkcję weryfikacji na platformach, której nie można uruchomić narzędzie Strong Name, takich jak mikroprocesorami Advanced RISC Machine (ARM), należy użyć **— Vk** opcję, aby utworzyć plik rejestru.</span><span class="sxs-lookup"><span data-stu-id="e04ec-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="e04ec-121">Importuj plik rejestru do rejestru na komputerze, w którym chcesz wyłączyć weryfikację.</span><span class="sxs-lookup"><span data-stu-id="e04ec-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="e04ec-122">Poniższy przykład tworzy plik rejestru dla `myAssembly.dll`.</span><span class="sxs-lookup"><span data-stu-id="e04ec-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="e04ec-123">Przy użyciu jednej **— Vr** lub **— Vk** opcji, można opcjonalnie dołączyć plik .snk — test klucza podpisywania.</span><span class="sxs-lookup"><span data-stu-id="e04ec-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="e04ec-124">Nie należy polegać na silnych nazw zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e04ec-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="e04ec-125">Udostępniają one tylko unikatową tożsamość.</span><span class="sxs-lookup"><span data-stu-id="e04ec-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="e04ec-126">Jeśli używasz opóźnione podpisywanie podczas tworzenia z programem Visual Studio na komputerze 64-bitowych, i kompilowania zestawu pod kątem **Any CPU**, może być konieczne zastosowanie **- Vr** opcji dwa razy.</span><span class="sxs-lookup"><span data-stu-id="e04ec-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="e04ec-127">(W programie Visual Studio, **Any CPU** jest wartością **platformy docelowej** kompilacji właściwości; podczas kompilowania z wiersza polecenia jest wartość domyślna.) Do uruchamiania aplikacji z poziomu wiersza polecenia lub w Eksploratorze plików, użyj wersji 64-bitowych [Sn.exe (narzędzie silnej nazwy)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) dotyczyć **- Vr** opcji do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e04ec-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="e04ec-128">Aby załadować zestawu do programu Visual Studio w czasie projektowania (np. zestaw zawiera składniki, które są używane przez innych zestawów w aplikacji), należy użyć 32-bitowej wersji narzędzia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e04ec-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="e04ec-129">Jest to spowodowane przy użyciu kompilatora just in time (JIT) kompiluje zestawu natywnego kodu 64-bitowego zestawu jest uruchamiany z wiersza polecenia i 32-bitowego kodu natywnego, gdy zestaw jest ładowany do środowiska czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="e04ec-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5.  <span data-ttu-id="e04ec-130">Później, zwykle po prostu przed wysyłką, przesyłania podpisywania urzędu do rzeczywistego silnej nazwy podpisywanie przy użyciu zestawu do organizacji **– R** opcji za pomocą narzędzia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e04ec-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="e04ec-131">Poniższy przykład podpisuje zestawu o nazwie `myAssembly.dll` z przy użyciu silnej nazwy `sgKey.snk` parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="e04ec-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e04ec-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e04ec-132">See Also</span></span>  
 [<span data-ttu-id="e04ec-133">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="e04ec-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="e04ec-134">Instrukcje: tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="e04ec-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="e04ec-135">Sn.exe (narzędzie silnych nazw)</span><span class="sxs-lookup"><span data-stu-id="e04ec-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="e04ec-136">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="e04ec-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
