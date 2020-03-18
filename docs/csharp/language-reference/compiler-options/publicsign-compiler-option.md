---
title: -publicsign (Opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: de7d9c98b0f279b52bc93711c5b986a2b2e57215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61662533"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="b8454-102">-publicsign (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="b8454-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="b8454-103">Ta opcja powoduje, że kompilator zastosować klucz publiczny, ale faktycznie nie podpisuje zestawu.</span><span class="sxs-lookup"><span data-stu-id="b8454-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="b8454-104">Opcja **-publicsign** ustawia również nieco w zestawie, który informuje, że plik jest faktycznie podpisany.</span><span class="sxs-lookup"><span data-stu-id="b8454-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8454-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8454-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="b8454-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b8454-106">Arguments</span></span>

<span data-ttu-id="b8454-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="b8454-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8454-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8454-108">Remarks</span></span>

<span data-ttu-id="b8454-109">Opcja **-publicsign** wymaga użycia [pliku -keyfile](keyfile-compiler-option.md) lub [-keycontainer.](keycontainer-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="b8454-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="b8454-110">Opcje **pliku kluczy** lub **kontenera kluczy** określają klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="b8454-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="b8454-111">Opcje **-publicsign** i **-delaysign** wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="b8454-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="b8454-112">Czasami nazywany "fałszywy znak" lub "znak OSS", podpisywanie publiczne zawiera klucz publiczny w zestawie wyjściowym i ustawia flagę "signed", ale w rzeczywistości nie podpisuje zestawu kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="b8454-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="b8454-113">Jest to przydatne w przypadku projektów typu open source, w których ludzie chcą tworzyć zestawy, które są zgodne z wydanymi zestawami "w pełni podpisanymi", ale nie mają dostępu do klucza prywatnego używanego do podpisywania zestawów.</span><span class="sxs-lookup"><span data-stu-id="b8454-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="b8454-114">Ponieważ prawie nie konsumenci rzeczywiście trzeba sprawdzić, czy zestaw jest w pełni podpisany, te publicznie zbudowane zestawy są użyteczne w prawie każdym scenariuszu, w którym w pełni podpisany jeden będzie używany.</span><span class="sxs-lookup"><span data-stu-id="b8454-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b8454-115">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8454-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="b8454-116">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="b8454-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="b8454-117">Zmodyfikuj **tylko znak opóźnienia.**</span><span class="sxs-lookup"><span data-stu-id="b8454-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8454-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8454-118">See also</span></span>

- [<span data-ttu-id="b8454-119">C# Kompilator -delaysign opcja</span><span class="sxs-lookup"><span data-stu-id="b8454-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="b8454-120">C# Kompilator -keyfile opcja</span><span class="sxs-lookup"><span data-stu-id="b8454-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="b8454-121">Opcja Kompilator c# - keycontainer</span><span class="sxs-lookup"><span data-stu-id="b8454-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="b8454-122">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="b8454-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="b8454-123">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="b8454-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
