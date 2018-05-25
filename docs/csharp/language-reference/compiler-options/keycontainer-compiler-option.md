---
title: -keycontainer (opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 5a7b378cad7a1df9249fcbefa28bb9aa9a6a3da4
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="a4afd-102">-keycontainer (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a4afd-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="a4afd-103">Określa nazwę kontenera kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="a4afd-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4afd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4afd-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="a4afd-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a4afd-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="a4afd-106">Nazwa kontenera klucza silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a4afd-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4afd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4afd-107">Remarks</span></span>  
 <span data-ttu-id="a4afd-108">Gdy **- keycontainer** jest używana opcja, kompilator tworzy zabezpieczać składnika.</span><span class="sxs-lookup"><span data-stu-id="a4afd-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="a4afd-109">Kompilator wstawia klucza publicznego z kontenera określonej w manifeście zestawu i podpisuje zestawie końcowym z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="a4afd-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="a4afd-110">Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="a4afd-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="a4afd-111">`sn -i` Instaluje pary kluczy do kontenera.</span><span class="sxs-lookup"><span data-stu-id="a4afd-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="a4afd-112">Ta opcja nie jest obsługiwana, gdy kompilator uruchamia środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="a4afd-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="a4afd-113">Aby podpisać zestaw podczas kompilowania na środowisko CoreCLR, należy użyć [- keyfile](keyfile-compiler-option.md) opcji.</span><span class="sxs-lookup"><span data-stu-id="a4afd-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="a4afd-114">Jeśli kompilacji z [-docelowych: moduł](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), nazwa pliku klucza jest przechowywana w module i wbudowanej w zestawie podczas kompilowania tego modułu do zestawu z [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a4afd-114">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="a4afd-115">Tę opcję można również określić jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) w kodzie źródłowym dla każdy moduł język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4afd-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="a4afd-116">Można również przekazać do kompilatora z informacjami szyfrowania [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a4afd-116">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="a4afd-117">Użyj [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Jeśli klucz publiczny dodane do manifestu zestawu, ale opóźnić podpisywania zestawu, dopóki nie był testowany.</span><span class="sxs-lookup"><span data-stu-id="a4afd-117">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="a4afd-118">Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="a4afd-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a4afd-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a4afd-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="a4afd-120">Ta opcja kompilatora nie jest dostępna w środowisku programowania Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4afd-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="a4afd-121">Programowo dostęp do tej opcji kompilatora z <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4afd-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4afd-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4afd-122">See Also</span></span>  
 <span data-ttu-id="a4afd-123">[-Keyfile — opcja kompilatora C#](keyfile-compiler-option.md) [opcje kompilatora C#](index.md)</span><span class="sxs-lookup"><span data-stu-id="a4afd-123">[C# Compiler -keyfile option](keyfile-compiler-option.md) [C# Compiler Options](index.md)</span></span>  
 [<span data-ttu-id="a4afd-124">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a4afd-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
