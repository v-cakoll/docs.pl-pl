---
title: -keycontainer (Opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: fead2d4296cfa6fb0195cb4b43f6448c0fc7e6a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970147"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="3eb9d-102">-keycontainer (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="3eb9d-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="3eb9d-103">Określa nazwę kontenera kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="3eb9d-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb9d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3eb9d-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="3eb9d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3eb9d-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="3eb9d-106">Nazwa kontenera kluczy silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3eb9d-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eb9d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3eb9d-107">Remarks</span></span>  
 <span data-ttu-id="3eb9d-108">Gdy używana jest opcja **-keycontainer,** kompilator tworzy składnik sharable.</span><span class="sxs-lookup"><span data-stu-id="3eb9d-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="3eb9d-109">Kompilator wstawia klucz publiczny z określonego kontenera do manifestu zestawu i podpisuje końcowy zestaw kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="3eb9d-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="3eb9d-110">Aby wygenerować plik `sn -k file` klucza, wpisz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="3eb9d-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="3eb9d-111">`sn -i`instaluje parę kluczy w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="3eb9d-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="3eb9d-112">Ta opcja nie jest obsługiwana, gdy kompilator działa na coreclr.</span><span class="sxs-lookup"><span data-stu-id="3eb9d-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="3eb9d-113">Aby podpisać zestaw podczas budowania na coreclr, należy użyć opcji [-keyfile.](keyfile-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="3eb9d-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="3eb9d-114">Jeśli skompilować z [-target:module](./target-module-compiler-option.md), nazwa pliku klucza jest utrzymywana w module i włączone do zestawu podczas kompilowania tego modułu do zestawu z [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3eb9d-114">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="3eb9d-115">Tę opcję można również określić jako<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>atrybut niestandardowy ( ) w kodzie źródłowym dla dowolnego modułu języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="3eb9d-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="3eb9d-116">Można również przekazać informacje szyfrowania do kompilatora z [-keyfile](./keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3eb9d-116">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="3eb9d-117">Użyj [-delaysign,](./delaysign-compiler-option.md) jeśli klucz publiczny ma zostać dodany do manifestu zestawu, ale chcesz opóźnić podpisanie zestawu, dopóki nie zostanie przetestowany.</span><span class="sxs-lookup"><span data-stu-id="3eb9d-117">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="3eb9d-118">Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../standard/assembly/create-use-strong-named.md) i [Opóźnianie podpisywania zestawu](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="3eb9d-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3eb9d-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3eb9d-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3eb9d-120">Ta opcja kompilatora nie jest dostępna w środowisku programistycznym programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3eb9d-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="3eb9d-121">Można programowo uzyskać dostęp do <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>tej opcji kompilatora z .</span><span class="sxs-lookup"><span data-stu-id="3eb9d-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb9d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3eb9d-122">See also</span></span>

- [<span data-ttu-id="3eb9d-123">C# Kompilator -keyfile opcja</span><span class="sxs-lookup"><span data-stu-id="3eb9d-123">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="3eb9d-124">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="3eb9d-124">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="3eb9d-125">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="3eb9d-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
