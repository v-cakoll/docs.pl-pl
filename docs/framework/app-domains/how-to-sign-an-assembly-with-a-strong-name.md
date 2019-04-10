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
ms.openlocfilehash: 5580b6d8af7319397ad7eb6416941c2be0dcdb76
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303436"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="3467f-102">Instrukcje: Podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="3467f-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="3467f-103">Istnieje kilka metod podpisywania zestawu za pomocą silnej nazwy:</span><span class="sxs-lookup"><span data-stu-id="3467f-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="3467f-104">Za pomocą **podpisywanie** kartę w projekcie **właściwości** okno dialogowe w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3467f-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="3467f-105">Jest to najprostsza i najwygodniejsza metoda podpisywania zestawów za pomocą silnych nazw.</span><span class="sxs-lookup"><span data-stu-id="3467f-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
-   <span data-ttu-id="3467f-106">Za pomocą [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) połączyć moduł kodu programu .NET Framework (plik netmodule) z plikiem klucza.</span><span class="sxs-lookup"><span data-stu-id="3467f-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
-   <span data-ttu-id="3467f-107">Przy użyciu atrybutów zestawu w celu wstawienia informacji o silnej nazwie do kodu.</span><span class="sxs-lookup"><span data-stu-id="3467f-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="3467f-108">Można użyć dowolnego <xref:System.Reflection.AssemblyKeyFileAttribute> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybut, w zależności od tego, w którym znajduje się plik klucza do użycia.</span><span class="sxs-lookup"><span data-stu-id="3467f-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
-   <span data-ttu-id="3467f-109">Przy użyciu opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="3467f-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="3467f-110">Aby podpisać zestaw za pomocą silnej nazwy, trzeba mieć parę kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="3467f-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="3467f-111">Aby uzyskać więcej informacji o tworzeniu pary kluczy, zobacz [jak: Tworzenie pary kluczy publiczny prywatny](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="3467f-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="3467f-112">Aby utworzyć i podpisać zestaw za pomocą silnej nazwą przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3467f-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="3467f-113">W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="3467f-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="3467f-114">Wybierz **podpisywanie** kartę.</span><span class="sxs-lookup"><span data-stu-id="3467f-114">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="3467f-115">Wybierz **Podpisz zestaw** pole.</span><span class="sxs-lookup"><span data-stu-id="3467f-115">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="3467f-116">W **wybierz plik klucza o silnej nazwie** wybierz  **\<Przeglądaj … >**, a następnie przejdź do pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="3467f-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="3467f-117">Aby utworzyć nowy plik klucza, wybierz  **\<nowy... >** i wprowadź jego nazwę w **Utwórz klucz silnej nazwy** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="3467f-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3467f-118">W celu [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md), wybierz plik klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="3467f-118">In order to [delay sign an assembly](../../../docs/framework/app-domains/delay-sign-assembly.md), choose a public key file.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="3467f-119">Aby utworzyć i podpisać zestaw za pomocą silnej nazwy przy użyciu programu Assembly Linker</span><span class="sxs-lookup"><span data-stu-id="3467f-119">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
-   <span data-ttu-id="3467f-120">W [wiersz polecenia programisty dla programu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="3467f-120">At the [Developer Command Prompt for Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="3467f-121">**Al** **/out:**\<*assemblyName*> *\<Nazwa_modułu >* **/KeyFile:** \<  *keyfileName*></span><span class="sxs-lookup"><span data-stu-id="3467f-121">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="3467f-122">gdzie:</span><span class="sxs-lookup"><span data-stu-id="3467f-122">where:</span></span>  
  
     *<span data-ttu-id="3467f-123">nazwaZestawu</span><span class="sxs-lookup"><span data-stu-id="3467f-123">assemblyName</span></span>*  
     <span data-ttu-id="3467f-124">Nazwa zestawu podpisanego za pomocą silnej nazwy (plik dll lub exe), który zostanie wyemitowany przez program Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="3467f-124">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     *<span data-ttu-id="3467f-125">{1&gt;nazwaModułu&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3467f-125">moduleName</span></span>*  
     <span data-ttu-id="3467f-126">Nazwa modułu kodu programu .NET Framework (plik netmodule) zawierającego co najmniej jeden typ.</span><span class="sxs-lookup"><span data-stu-id="3467f-126">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="3467f-127">Plik netmodule można utworzyć, kompilując kod z `/target:module` przełącznika w języku C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3467f-127">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     *<span data-ttu-id="3467f-128">{1&gt;nazwaPlikuKlucza&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3467f-128">keyfileName</span></span>*  
     <span data-ttu-id="3467f-129">Nazwa kontenera lub pliku zawierającego parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="3467f-129">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="3467f-130">Program Assembly Linker interpretuje ścieżkę względną w odniesieniu do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="3467f-130">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="3467f-131">Poniższy przykład podpisuje zestaw `MyAssembly.dll` za pomocą silnej nazwy przy użyciu pliku klucza `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="3467f-131">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="3467f-132">Aby uzyskać więcej informacji o tym narzędziu, zobacz [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="3467f-132">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="3467f-133">Aby podpisać zestaw za pomocą silnej nazwy przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="3467f-133">To sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="3467f-134">Dodaj <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybutu do pliku kodu źródłowego i określ nazwę pliku lub kontener, który zawiera pary kluczy do użycia podczas podpisywania zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3467f-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2. <span data-ttu-id="3467f-135">Skompiluj w normalny sposób plik kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3467f-135">Compile the source code file normally.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3467f-136">Kompilatory C# i Visual Basic generuje ostrzeżeń kompilatora (odpowiednio CS1699 i BC41008, odpowiednio) gdy napotkają <xref:System.Reflection.AssemblyKeyFileAttribute> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybutu w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="3467f-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="3467f-137">Można zignorować te ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="3467f-137">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="3467f-138">W poniższym przykładzie użyto <xref:System.Reflection.AssemblyKeyFileAttribute> atrybutu z plikiem klucza o nazwie `keyfile.snk`, który znajduje się w katalogu, w którym jest kompilowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="3467f-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="3467f-139">Można również opóźnić podpisywanie zestawu podczas kompilowania pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3467f-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="3467f-140">Aby uzyskać więcej informacji, zobacz [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="3467f-140">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="3467f-141">Aby podpisać zestaw za pomocą silnej nazwy przy użyciu kompilatora</span><span class="sxs-lookup"><span data-stu-id="3467f-141">To sign an assembly with a strong name by using the compiler</span></span>  
  
-   <span data-ttu-id="3467f-142">Kompiluj z pliku kodu źródłowego lub plików za pomocą `/keyfile` lub `/delaysign` — opcja kompilatora w języku C# i Visual Basic lub `/KEYFILE` lub `/DELAYSIGN` — opcja konsolidatora w języku C++.</span><span class="sxs-lookup"><span data-stu-id="3467f-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="3467f-143">Po nazwie opcji dodaj średnik, a następnie nazwę pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="3467f-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="3467f-144">W przypadku używania kompilatorów wiersza polecenia można skopiować plik klucza do katalogu, który zawiera pliki kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3467f-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="3467f-145">Aby uzyskać informacje na temat opóźnionego podpisywania, zobacz [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="3467f-145">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="3467f-146">Poniższy przykład używa kompilatora C# i podpisuje zestaw `UtilityLibrary.dll` za pomocą silnej nazwy przy użyciu pliku klucza `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="3467f-146">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3467f-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3467f-147">See also</span></span>

- [<span data-ttu-id="3467f-148">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="3467f-148">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="3467f-149">Instrukcje: Tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="3467f-149">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="3467f-150">Al.exe (Konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="3467f-150">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="3467f-151">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="3467f-151">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [<span data-ttu-id="3467f-152">Zarządzanie zestawem i podpisywanie manifestu</span><span class="sxs-lookup"><span data-stu-id="3467f-152">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="3467f-153">Strona podpisywania, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="3467f-153">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
