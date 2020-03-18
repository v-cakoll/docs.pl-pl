---
title: 'Jak: Podpisywanie zestawu o silnej nazwie'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 9998e69e8bf1505bcfc7a9103e9d89616dad9633
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160316"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="f6034-102">Jak: Podpisywanie zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="f6034-102">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="f6034-103">Mimo że program .NET Core obsługuje zestawy o silnych nazwach, a wszystkie zestawy w bibliotece .NET Core są podpisane, większość zestawów innych firm nie wymaga silnych nazw.</span><span class="sxs-lookup"><span data-stu-id="f6034-103">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="f6034-104">Aby uzyskać więcej informacji, zobacz [Silne podpisywanie nazw](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) w usyjanie usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="f6034-104">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="f6034-105">Istnieje kilka metod podpisywania zestawu za pomocą silnej nazwy:</span><span class="sxs-lookup"><span data-stu-id="f6034-105">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="f6034-106">Za pomocą **karty Podpisywanie** w oknie dialogowym **Właściwości** projektu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f6034-106">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="f6034-107">Jest to najprostsza i najwygodniejsza metoda podpisywania zestawów za pomocą silnych nazw.</span><span class="sxs-lookup"><span data-stu-id="f6034-107">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="f6034-108">Za pomocą [konsolidatora zestawów (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) połączyć moduł kodu .NET Framework (plik *.netmodule)* z plikiem klucza.</span><span class="sxs-lookup"><span data-stu-id="f6034-108">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="f6034-109">Przy użyciu atrybutów zestawu w celu wstawienia informacji o silnej nazwie do kodu.</span><span class="sxs-lookup"><span data-stu-id="f6034-109">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="f6034-110">Można użyć atrybutu <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> lub atrybutu, w zależności od tego, gdzie znajduje się plik klucza do użycia.</span><span class="sxs-lookup"><span data-stu-id="f6034-110">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="f6034-111">Przy użyciu opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f6034-111">By using compiler options.</span></span>  
  
 <span data-ttu-id="f6034-112">Aby podpisać zestaw za pomocą silnej nazwy, trzeba mieć parę kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="f6034-112">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="f6034-113">Aby uzyskać więcej informacji na temat tworzenia pary kluczy, zobacz [Jak: Tworzenie pary kluczy publiczno-prywatnych](create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="f6034-113">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="f6034-114">Tworzenie i podpisywanie zestawu o silnej nazwie przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6034-114">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="f6034-115">W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, a następnie wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f6034-115">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="f6034-116">Wybierz kartę **Podpisywanie.**</span><span class="sxs-lookup"><span data-stu-id="f6034-116">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="f6034-117">Wybierz pole **Podpisz złożenie.**</span><span class="sxs-lookup"><span data-stu-id="f6034-117">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="f6034-118">W polu **Wybierz silną nazwę pliku klucza** wybierz pozycję **Przeglądaj**, a następnie przejdź do pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="f6034-118">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="f6034-119">Aby utworzyć nowy plik klucza, wybierz pozycję **Nowy** i wprowadź jego nazwę w oknie dialogowym **Tworzenie silnego klucza nazwy.**</span><span class="sxs-lookup"><span data-stu-id="f6034-119">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6034-120">Aby [opóźnić podpisanie zestawu,](delay-sign.md)wybierz plik klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="f6034-120">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="f6034-121">Tworzenie i podpisywanie złożenia o silnej nazwie przy użyciu konsolidatora złożenia</span><span class="sxs-lookup"><span data-stu-id="f6034-121">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="f6034-122">W [wierszu polecenia dewelopera dla programu Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f6034-122">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="f6034-123">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="f6034-123">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="f6034-124">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="f6034-124">Where:</span></span>  

- <span data-ttu-id="f6034-125">*AssemblyName* to nazwa zestawu silnie podpisanego *(pliku dll* lub *pliku exe),* który będzie emitować łącze zestawu.</span><span class="sxs-lookup"><span data-stu-id="f6034-125">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="f6034-126">*moduleName* to nazwa modułu kodu .NET Framework (pliku *.netmodule),* który zawiera jeden lub więcej typów.</span><span class="sxs-lookup"><span data-stu-id="f6034-126">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="f6034-127">Plik *.netmodule* można utworzyć, kompilując `/target:module` kod za pomocą przełącznika w języku C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f6034-127">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="f6034-128">*keyfileName* to nazwa kontenera lub pliku zawierającego parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="f6034-128">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="f6034-129">Konsolidator zestawów interpretuje ścieżkę względną w stosunku do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="f6034-129">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="f6034-130">Poniższy przykład podpisuje zestaw *MyAssembly.dll* o silnej nazwie przy użyciu pliku *klucza sgKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="f6034-130">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="f6034-131">Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [Łączenie złożenia](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="f6034-131">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="f6034-132">Podpisywanie zestawu o silnej nazwie przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="f6034-132">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="f6034-133">Dodaj <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybut do pliku kodu źródłowego i określ nazwę pliku lub kontenera, który zawiera parę kluczy do użycia podczas podpisywania zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f6034-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="f6034-134">Skompiluj w normalny sposób plik kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f6034-134">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="f6034-135">Kompilatory Języka C# i Visual Basic wydają ostrzeżenia kompilatora (odpowiednio CS1699 <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> i BC41008), gdy napotkają lub atrybut w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="f6034-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="f6034-136">Można zignorować te ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="f6034-136">You can ignore the warnings.</span></span>  

<span data-ttu-id="f6034-137">W poniższym <xref:System.Reflection.AssemblyKeyFileAttribute> przykładzie użyto atrybutu z plikiem klucza o nazwie *keyfile.snk*, który znajduje się w katalogu, w którym zestaw jest skompilowany.</span><span class="sxs-lookup"><span data-stu-id="f6034-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="f6034-138">Można również opóźnić podpisywanie zestawu podczas kompilowania pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f6034-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="f6034-139">Aby uzyskać więcej informacji, zobacz [Opóźnienie-sign zestawu](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="f6034-139">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="f6034-140">Podpisywanie zestawu o silnej nazwie przy użyciu kompilatora</span><span class="sxs-lookup"><span data-stu-id="f6034-140">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="f6034-141">Skompiluj plik kodu `/keyfile` źródłowego lub pliki z opcją `/delaysign` lub `/KEYFILE` `/DELAYSIGN` kompilatorem w językach C# i Visual Basic lub opcją lub konsolidatorem w języku C++.</span><span class="sxs-lookup"><span data-stu-id="f6034-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="f6034-142">Po nazwie opcji dodaj średnik, a następnie nazwę pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="f6034-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="f6034-143">W przypadku używania kompilatorów wiersza polecenia można skopiować plik klucza do katalogu, który zawiera pliki kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f6034-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="f6034-144">Aby uzyskać informacje na temat podpisywania opóźnienia, zobacz [Opóźnienie-sign zestawu](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="f6034-144">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="f6034-145">W poniższym przykładzie użyto kompilatora C# i podpisuje zestaw *UtilityLibrary.dll* o silnej nazwie przy użyciu pliku *klucza sgKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="f6034-145">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="f6034-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6034-146">See also</span></span>

- [<span data-ttu-id="f6034-147">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="f6034-147">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="f6034-148">Jak: Tworzenie pary kluczy publiczno-prywatnych</span><span class="sxs-lookup"><span data-stu-id="f6034-148">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="f6034-149">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="f6034-149">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="f6034-150">Podpisywanie zestawu z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="f6034-150">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="f6034-151">Zarządzanie podpisywaniem zestawu i manifestu</span><span class="sxs-lookup"><span data-stu-id="f6034-151">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="f6034-152">Strona podpisywania, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="f6034-152">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
