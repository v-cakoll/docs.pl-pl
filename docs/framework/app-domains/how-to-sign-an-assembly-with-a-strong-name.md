---
title: 'Instrukcje: Podpisywanie zestawu silną nazwą'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b109ec82d139e3b3eb321c90d5f41dd1eae216f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927932"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="e644a-102">Instrukcje: Podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="e644a-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="e644a-103">Istnieje kilka metod podpisywania zestawu za pomocą silnej nazwy:</span><span class="sxs-lookup"><span data-stu-id="e644a-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="e644a-104">Za pomocą karty podpisywanie w oknie dialogowym **Właściwości** projektu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e644a-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="e644a-105">Jest to najprostsza i najwygodniejsza metoda podpisywania zestawów za pomocą silnych nazw.</span><span class="sxs-lookup"><span data-stu-id="e644a-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="e644a-106">Za pomocą [konsolidatora zestawu (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) do łączenia modułu kodu .NET Framework (plik. module) z plikiem klucza.</span><span class="sxs-lookup"><span data-stu-id="e644a-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
- <span data-ttu-id="e644a-107">Przy użyciu atrybutów zestawu w celu wstawienia informacji o silnej nazwie do kodu.</span><span class="sxs-lookup"><span data-stu-id="e644a-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="e644a-108">Możesz użyć <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> albo atrybutu, w zależności od tego, gdzie znajduje się plik klucza, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="e644a-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="e644a-109">Przy użyciu opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e644a-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="e644a-110">Aby podpisać zestaw za pomocą silnej nazwy, trzeba mieć parę kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="e644a-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="e644a-111">Aby uzyskać więcej informacji na temat tworzenia pary kluczy, [zobacz How to: Utwórz parę](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)kluczy publiczny-prywatny.</span><span class="sxs-lookup"><span data-stu-id="e644a-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="e644a-112">Aby utworzyć i podpisać zestaw za pomocą silnej nazwą przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e644a-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="e644a-113">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e644a-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="e644a-114">Wybierz kartę podpisywanie.</span><span class="sxs-lookup"><span data-stu-id="e644a-114">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="e644a-115">Zaznacz pole **podpisz zestaw** .</span><span class="sxs-lookup"><span data-stu-id="e644a-115">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="e644a-116">W polu **Wybierz plik klucza o silnej nazwie** wybierz  **\<Przeglądaj... >** , a następnie przejdź do pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="e644a-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="e644a-117">Aby utworzyć nowy plik klucza, wybierz  **\<pozycję Nowy... >** i wprowadź jej nazwę w oknie dialogowym **Tworzenie klucza silnej nazwy** .</span><span class="sxs-lookup"><span data-stu-id="e644a-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e644a-118">Aby opóźnić [podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md), wybierz plik klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="e644a-118">In order to [delay sign an assembly](../../../docs/framework/app-domains/delay-sign-assembly.md), choose a public key file.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="e644a-119">Aby utworzyć i podpisać zestaw za pomocą silnej nazwy przy użyciu programu Assembly Linker</span><span class="sxs-lookup"><span data-stu-id="e644a-119">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
- <span data-ttu-id="e644a-120">W [wiersz polecenia dla deweloperów dla programu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md)wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e644a-120">At the [Developer Command Prompt for Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="e644a-121">**Al** **/out:** \<AssemblyNameModuleName> > **/KeyFile**:filename\< *\<* ></span><span class="sxs-lookup"><span data-stu-id="e644a-121">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="e644a-122">gdzie:</span><span class="sxs-lookup"><span data-stu-id="e644a-122">where:</span></span>  
  
     <span data-ttu-id="e644a-123">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="e644a-123">*assemblyName*</span></span>  
     <span data-ttu-id="e644a-124">Nazwa zestawu podpisanego za pomocą silnej nazwy (plik dll lub exe), który zostanie wyemitowany przez program Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="e644a-124">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="e644a-125">*moduleName*</span><span class="sxs-lookup"><span data-stu-id="e644a-125">*moduleName*</span></span>  
     <span data-ttu-id="e644a-126">Nazwa modułu kodu programu .NET Framework (plik netmodule) zawierającego co najmniej jeden typ.</span><span class="sxs-lookup"><span data-stu-id="e644a-126">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="e644a-127">Można utworzyć plik. module, kompilując kod z `/target:module` przełącznikiem w C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e644a-127">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="e644a-128">*keyfileName*</span><span class="sxs-lookup"><span data-stu-id="e644a-128">*keyfileName*</span></span>  
     <span data-ttu-id="e644a-129">Nazwa kontenera lub pliku zawierającego parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="e644a-129">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="e644a-130">Program Assembly Linker interpretuje ścieżkę względną w odniesieniu do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="e644a-130">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="e644a-131">Poniższy przykład podpisuje zestaw `MyAssembly.dll` silną nazwą przy użyciu pliku `sgKey.snk`klucza.</span><span class="sxs-lookup"><span data-stu-id="e644a-131">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="e644a-132">Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [konsolidator zestawu](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="e644a-132">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="e644a-133">Aby podpisać zestaw za pomocą silnej nazwy przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="e644a-133">To sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="e644a-134">Dodaj atrybut <xref:System.Reflection.AssemblyKeyNameAttribute> or do pliku kodu źródłowego i określ nazwę pliku lub kontenera, który zawiera parę kluczy do użycia podczas podpisywania zestawu o silnej nazwie. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e644a-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2. <span data-ttu-id="e644a-135">Skompiluj w normalny sposób plik kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e644a-135">Compile the source code file normally.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e644a-136">Kompilatory C# i Visual Basic nie generują ostrzeżeń kompilatora (odpowiednio CS1699 i BC41008), gdy napotkają <xref:System.Reflection.AssemblyKeyFileAttribute> atrybut <xref:System.Reflection.AssemblyKeyNameAttribute> lub w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="e644a-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="e644a-137">Można zignorować te ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="e644a-137">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="e644a-138">W poniższym przykładzie jest używany <xref:System.Reflection.AssemblyKeyFileAttribute> atrybut z plikiem klucza o nazwie `keyfile.snk`, który znajduje się w katalogu, w którym skompilowano zestaw.</span><span class="sxs-lookup"><span data-stu-id="e644a-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="e644a-139">Można również opóźnić podpisywanie zestawu podczas kompilowania pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e644a-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="e644a-140">Aby uzyskać więcej informacji, zobacz [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="e644a-140">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="e644a-141">Aby podpisać zestaw za pomocą silnej nazwy przy użyciu kompilatora</span><span class="sxs-lookup"><span data-stu-id="e644a-141">To sign an assembly with a strong name by using the compiler</span></span>  
  
- <span data-ttu-id="e644a-142">Kompiluj plik lub `/keyfile` pliki kodu źródłowego z opcją kompilatora lub `/delaysign` w C# Visual Basic `/KEYFILE` `/DELAYSIGN` lub opcję konsolidatora w. C++</span><span class="sxs-lookup"><span data-stu-id="e644a-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="e644a-143">Po nazwie opcji dodaj średnik, a następnie nazwę pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="e644a-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="e644a-144">W przypadku używania kompilatorów wiersza polecenia można skopiować plik klucza do katalogu, który zawiera pliki kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e644a-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="e644a-145">Aby uzyskać informacje o opóźnieniu podpisywania, zobacz [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="e644a-145">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="e644a-146">W poniższym przykładzie użyto C# kompilatora i podpisuje zestaw `UtilityLibrary.dll` silną nazwą przy użyciu pliku `sgKey.snk`klucza.</span><span class="sxs-lookup"><span data-stu-id="e644a-146">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e644a-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e644a-147">See also</span></span>

- [<span data-ttu-id="e644a-148">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="e644a-148">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="e644a-149">Instrukcje: Tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="e644a-149">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="e644a-150">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="e644a-150">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="e644a-151">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="e644a-151">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [<span data-ttu-id="e644a-152">Zarządzanie podpisywaniem zestawu i manifestu</span><span class="sxs-lookup"><span data-stu-id="e644a-152">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="e644a-153">Strona podpisywania, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="e644a-153">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
