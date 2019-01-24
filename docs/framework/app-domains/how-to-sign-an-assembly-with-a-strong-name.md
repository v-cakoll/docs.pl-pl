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
ms.openlocfilehash: 963923951b3f3c288506cf339cd8a15f27792af3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599221"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="48f87-102">Instrukcje: Podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="48f87-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="48f87-103">Istnieje kilka metod podpisywania zestawu za pomocą silnej nazwy:</span><span class="sxs-lookup"><span data-stu-id="48f87-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="48f87-104">Za pomocą **podpisywanie** kartę w projekcie **właściwości** okno dialogowe w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="48f87-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="48f87-105">Jest to najprostsza i najwygodniejsza metoda podpisywania zestawów za pomocą silnych nazw.</span><span class="sxs-lookup"><span data-stu-id="48f87-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
-   <span data-ttu-id="48f87-106">Za pomocą [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) połączyć moduł kodu programu .NET Framework (plik netmodule) z plikiem klucza.</span><span class="sxs-lookup"><span data-stu-id="48f87-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
-   <span data-ttu-id="48f87-107">Przy użyciu atrybutów zestawu w celu wstawienia informacji o silnej nazwie do kodu.</span><span class="sxs-lookup"><span data-stu-id="48f87-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="48f87-108">Można użyć dowolnego <xref:System.Reflection.AssemblyKeyFileAttribute> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybut, w zależności od tego, w którym znajduje się plik klucza do użycia.</span><span class="sxs-lookup"><span data-stu-id="48f87-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
-   <span data-ttu-id="48f87-109">Przy użyciu opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="48f87-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="48f87-110">Aby podpisać zestaw za pomocą silnej nazwy, trzeba mieć parę kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="48f87-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="48f87-111">Aby uzyskać więcej informacji o tworzeniu pary kluczy, zobacz [jak: Tworzenie pary kluczy publiczny prywatny](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="48f87-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="48f87-112">Aby utworzyć i podpisać zestaw za pomocą silnej nazwą przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="48f87-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="48f87-113">W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="48f87-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="48f87-114">Wybierz **podpisywanie** kartę.</span><span class="sxs-lookup"><span data-stu-id="48f87-114">Choose the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="48f87-115">Wybierz **Podpisz zestaw** pole.</span><span class="sxs-lookup"><span data-stu-id="48f87-115">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="48f87-116">W **wybierz plik klucza o silnej nazwie** wybierz  **\<Przeglądaj … >**, a następnie przejdź do pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="48f87-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="48f87-117">Aby utworzyć nowy plik klucza, wybierz  **\<nowy... >** i wprowadź jego nazwę w **Utwórz klucz silnej nazwy** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="48f87-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="48f87-118">Aby utworzyć i podpisać zestaw za pomocą silnej nazwy przy użyciu programu Assembly Linker</span><span class="sxs-lookup"><span data-stu-id="48f87-118">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
-   <span data-ttu-id="48f87-119">W [wiersz polecenia programisty dla programu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="48f87-119">At the [Developer Command Prompt for Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="48f87-120">**Al** **/out:**\<*assemblyName*> *\<Nazwa_modułu >* **/KeyFile:** \<  *keyfileName*></span><span class="sxs-lookup"><span data-stu-id="48f87-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="48f87-121">gdzie:</span><span class="sxs-lookup"><span data-stu-id="48f87-121">where:</span></span>  
  
     <span data-ttu-id="48f87-122">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="48f87-122">*assemblyName*</span></span>  
     <span data-ttu-id="48f87-123">Nazwa zestawu podpisanego za pomocą silnej nazwy (plik dll lub exe), który zostanie wyemitowany przez program Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="48f87-123">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="48f87-124">*moduleName*</span><span class="sxs-lookup"><span data-stu-id="48f87-124">*moduleName*</span></span>  
     <span data-ttu-id="48f87-125">Nazwa modułu kodu programu .NET Framework (plik netmodule) zawierającego co najmniej jeden typ.</span><span class="sxs-lookup"><span data-stu-id="48f87-125">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="48f87-126">Plik netmodule można utworzyć, kompilując kod z `/target:module` przełącznika w języku C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="48f87-126">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="48f87-127">*keyfileName*</span><span class="sxs-lookup"><span data-stu-id="48f87-127">*keyfileName*</span></span>  
     <span data-ttu-id="48f87-128">Nazwa kontenera lub pliku zawierającego parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="48f87-128">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="48f87-129">Program Assembly Linker interpretuje ścieżkę względną w odniesieniu do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="48f87-129">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="48f87-130">Poniższy przykład podpisuje zestaw `MyAssembly.dll` za pomocą silnej nazwy przy użyciu pliku klucza `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="48f87-130">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="48f87-131">Aby uzyskać więcej informacji o tym narzędziu, zobacz [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="48f87-131">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="48f87-132">Aby podpisać zestaw za pomocą silnej nazwy przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="48f87-132">To sign an assembly with a strong name by using attributes</span></span>  
  
1.  <span data-ttu-id="48f87-133">Dodaj <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybutu do pliku kodu źródłowego i określ nazwę pliku lub kontener, który zawiera pary kluczy do użycia podczas podpisywania zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="48f87-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2.  <span data-ttu-id="48f87-134">Skompiluj w normalny sposób plik kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="48f87-134">Compile the source code file normally.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48f87-135">Kompilatory C# i Visual Basic generuje ostrzeżeń kompilatora (odpowiednio CS1699 i BC41008, odpowiednio) gdy napotkają <xref:System.Reflection.AssemblyKeyFileAttribute> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybutu w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="48f87-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="48f87-136">Można zignorować te ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="48f87-136">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="48f87-137">W poniższym przykładzie użyto <xref:System.Reflection.AssemblyKeyFileAttribute> atrybutu z plikiem klucza o nazwie `keyfile.snk`, który znajduje się w katalogu, w którym jest kompilowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="48f87-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="48f87-138">Można również opóźnić podpisywanie zestawu podczas kompilowania pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="48f87-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="48f87-139">Aby uzyskać więcej informacji, zobacz [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="48f87-139">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="48f87-140">Aby podpisać zestaw za pomocą silnej nazwy przy użyciu kompilatora</span><span class="sxs-lookup"><span data-stu-id="48f87-140">To sign an assembly with a strong name by using the compiler</span></span>  
  
-   <span data-ttu-id="48f87-141">Kompiluj z pliku kodu źródłowego lub plików za pomocą `/keyfile` lub `/delaysign` — opcja kompilatora w języku C# i Visual Basic lub `/KEYFILE` lub `/DELAYSIGN` — opcja konsolidatora w języku C++.</span><span class="sxs-lookup"><span data-stu-id="48f87-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="48f87-142">Po nazwie opcji dodaj średnik, a następnie nazwę pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="48f87-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="48f87-143">W przypadku używania kompilatorów wiersza polecenia można skopiować plik klucza do katalogu, który zawiera pliki kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="48f87-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="48f87-144">Aby uzyskać informacje na temat opóźnionego podpisywania, zobacz [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="48f87-144">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="48f87-145">Poniższy przykład używa kompilatora C# i podpisuje zestaw `UtilityLibrary.dll` za pomocą silnej nazwy przy użyciu pliku klucza `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="48f87-145">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="48f87-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48f87-146">See also</span></span>
- [<span data-ttu-id="48f87-147">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="48f87-147">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="48f87-148">Instrukcje: Tworzenie pary kluczy publiczny prywatny</span><span class="sxs-lookup"><span data-stu-id="48f87-148">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="48f87-149">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="48f87-149">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="48f87-150">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="48f87-150">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [<span data-ttu-id="48f87-151">Zarządzanie podpisywaniem zestawu i manifestu</span><span class="sxs-lookup"><span data-stu-id="48f87-151">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="48f87-152">Strona podpisywania, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="48f87-152">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
