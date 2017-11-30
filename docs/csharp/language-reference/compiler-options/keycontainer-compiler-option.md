---
title: -keycontainer (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0292ff38b1d03f5960a20858fbb9c42a6aff1f43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="keycontainer-c-compiler-options"></a><span data-ttu-id="7dbe0-102">/keycontainer (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="7dbe0-102">/keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="7dbe0-103">Określa nazwę kontenera kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="7dbe0-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dbe0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7dbe0-104">Syntax</span></span>  
  
```console  
/keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="7dbe0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7dbe0-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="7dbe0-106">Nazwa kontenera klucza silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="7dbe0-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dbe0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7dbe0-107">Remarks</span></span>  
 <span data-ttu-id="7dbe0-108">Gdy **/KeyContainer** jest używana opcja, kompilator tworzy składnik zabezpieczać wstawianie klucza publicznego z kontenera określonej w manifeście zestawu i podpisywania z kluczem prywatnym zestawie końcowym.</span><span class="sxs-lookup"><span data-stu-id="7dbe0-108">When the **/keycontainer** option is used, the compiler creates a sharable component by inserting a public key from the specified container into the assembly manifest and signing the final assembly with the private key.</span></span> <span data-ttu-id="7dbe0-109">Aby wygenerować plik klucza, wpisz sn -k `file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="7dbe0-109">To generate a key file, type sn -k `file` at the command line.</span></span> <span data-ttu-id="7dbe0-110">SN -i instaluje pary kluczy do kontenera.</span><span class="sxs-lookup"><span data-stu-id="7dbe0-110">sn -i installs the key pair into a container.</span></span>  
  
 <span data-ttu-id="7dbe0-111">Jeśli kompilacji z [/target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), nazwa pliku klucza jest przechowywana w module i wbudowanej w zestawie podczas kompilowania tego modułu do zestawu z [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7dbe0-111">If you compile with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="7dbe0-112">Tę opcję można również określić jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) w kodzie źródłowym dla każdy moduł język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7dbe0-112">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="7dbe0-113">Można również przekazać do kompilatora z informacjami szyfrowania [/KeyFile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7dbe0-113">You can also pass your encryption information to the compiler with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="7dbe0-114">Użyj [/DelaySign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Jeśli klucz publiczny dodane do manifestu zestawu, ale opóźnić podpisywania zestawu, dopóki nie był testowany.</span><span class="sxs-lookup"><span data-stu-id="7dbe0-114">Use [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="7dbe0-115">Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="7dbe0-115">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7dbe0-116">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7dbe0-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="7dbe0-117">Ta opcja kompilatora nie jest dostępna w środowisku programowania Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7dbe0-117">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="7dbe0-118">Programowo dostęp do tej opcji kompilatora z <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="7dbe0-118">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dbe0-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7dbe0-119">See Also</span></span>  
 [<span data-ttu-id="7dbe0-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="7dbe0-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="7dbe0-121">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="7dbe0-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
