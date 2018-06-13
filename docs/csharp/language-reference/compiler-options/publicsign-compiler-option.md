---
title: -publicsign (opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: ec25f9c1f2ef943db41bcfa20c8efd1d05866acd
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472853"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="d8d39-102">-publicsign (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d8d39-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="d8d39-103">Ta opcja powoduje, że kompilator zastosowanie klucza publicznego, ale faktycznie nie podpisać zestawu.</span><span class="sxs-lookup"><span data-stu-id="d8d39-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="d8d39-104">**- Publicsign** również ustawia bit w zestawie środowiska uruchomieniowego informuje, że plik został podpisany faktycznie.</span><span class="sxs-lookup"><span data-stu-id="d8d39-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8d39-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8d39-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="d8d39-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d8d39-106">Arguments</span></span>

<span data-ttu-id="d8d39-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="d8d39-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8d39-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8d39-108">Remarks</span></span>

<span data-ttu-id="d8d39-109">**- Publicsign** opcja wymaga użycia [- keyfile](keyfile-compiler-option.md) lub [- keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d8d39-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="d8d39-110">**Keyfile** lub **keycontainer** opcje określić klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="d8d39-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="d8d39-111">**- Publicsign** i **- delaysign** wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="d8d39-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="d8d39-112">Czasami nazywany "fałszywych znaku" lub "OSS znaku", publiczne podpisywanie zawiera klucz publiczny w zestawie danych wyjściowych i ustawia flagę "podpisem", ale faktycznie nie Podpisz zestaw z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="d8d39-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="d8d39-113">Jest to przydatne dla projektów typu open source, której chcesz utworzyć zestawy, które są zgodne z wydaną zestawy "podpisany całkowicie", ale nie mają dostępu do klucza prywatnego, używany do podpisywania zestawy osób.</span><span class="sxs-lookup"><span data-stu-id="d8d39-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="d8d39-114">Ponieważ prawie żadnych użytkowników faktycznie należy sprawdzić, czy zestaw jest niecałkowicie podpisany, publicznie skompilowane zestawy są użyteczny w niemal każdego scenariusz, gdzie będzie używane to całkowicie podpisane.</span><span class="sxs-lookup"><span data-stu-id="d8d39-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d8d39-115">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d8d39-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="d8d39-116">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="d8d39-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="d8d39-117">Modyfikowanie **opóźnienie tylko znak** właściwości.</span><span class="sxs-lookup"><span data-stu-id="d8d39-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8d39-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8d39-118">See Also</span></span>
 [<span data-ttu-id="d8d39-119">-Delaysign — opcja kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d8d39-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)  
 [<span data-ttu-id="d8d39-120">-Keyfile — opcja kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d8d39-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)  
 [<span data-ttu-id="d8d39-121">-Keycontainer — opcja kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d8d39-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)  
 [<span data-ttu-id="d8d39-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d8d39-122">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="d8d39-123">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d8d39-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
