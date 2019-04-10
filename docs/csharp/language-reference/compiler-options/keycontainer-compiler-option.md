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
ms.openlocfilehash: cf51bccc98f04c38149ec821b7064a4844d7e804
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302780"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="5e01d-102">-keycontainer (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="5e01d-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="5e01d-103">Określa nazwę kontenera kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="5e01d-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e01d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e01d-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="5e01d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5e01d-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="5e01d-106">Nazwa kontenera klucza silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5e01d-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e01d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e01d-107">Remarks</span></span>  
 <span data-ttu-id="5e01d-108">Gdy **- keycontainer** jest używana opcja, kompilator tworzy składnik, które można udostępnić.</span><span class="sxs-lookup"><span data-stu-id="5e01d-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="5e01d-109">Kompilator wstawia klucz publiczny z określonego kontenera do manifestu zestawu i podpisuje ostateczny zestaw przy użyciu klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="5e01d-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="5e01d-110">Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e01d-110">To generate a key file, type `sn -k file` at the command line.</span></span> `sn -i` <span data-ttu-id="5e01d-111">Instaluje parę kluczy w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="5e01d-111">installs the key pair into a container.</span></span> <span data-ttu-id="5e01d-112">Ta opcja nie jest obsługiwana, gdy kompilator jest uruchamiany w środowisku CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5e01d-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="5e01d-113">Aby podpisać zestaw, podczas tworzenia w środowisku CoreCLR, należy użyć [- keyfile](keyfile-compiler-option.md) opcji.</span><span class="sxs-lookup"><span data-stu-id="5e01d-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="5e01d-114">Jeśli kompilujesz z opcją [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), nazwę pliku klucza jest przechowywany w module i dołączone do zestawu podczas kompilowania tego modułu do zestawu z [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5e01d-114">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="5e01d-115">Można również określić tę opcję jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) w kodzie źródłowym dla każdego modułu języka intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5e01d-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="5e01d-116">Można również przekazać szyfrowania informacji do kompilatora przy użyciu [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5e01d-116">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="5e01d-117">Użyj [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Jeśli chcesz, aby klucz publiczny, dodać do manifestu zestawu, ale opóźnić podpisywanie zestawu, dopóki nie został przetestowany.</span><span class="sxs-lookup"><span data-stu-id="5e01d-117">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="5e01d-118">Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnienie podpisywania zestawu](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="5e01d-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5e01d-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5e01d-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5e01d-120">Ta opcja kompilatora nie jest dostępna w środowisku programowania Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e01d-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="5e01d-121">Programowego dostępu do tej opcji kompilatora z <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="5e01d-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e01d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e01d-122">See also</span></span>

- [<span data-ttu-id="5e01d-123">-Keyfile — opcja kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="5e01d-123">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="5e01d-124">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="5e01d-124">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="5e01d-125">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="5e01d-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
