---
title: -nostdlib (C# opcje kompilatora)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345078"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="8a364-102">-nostdlib (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="8a364-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="8a364-103">**-nostdlib** uniemożliwia Import biblioteki mscorlib. dll, która definiuje całą przestrzeń nazw System.</span><span class="sxs-lookup"><span data-stu-id="8a364-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a364-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a364-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="8a364-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a364-105">Remarks</span></span>

<span data-ttu-id="8a364-106">Użyj tej opcji, jeśli chcesz zdefiniować lub utworzyć własną przestrzeń nazw systemu i obiekty.</span><span class="sxs-lookup"><span data-stu-id="8a364-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="8a364-107">Jeśli nie określisz opcji **-nostdlib**, mscorlib. dll zostanie zaimportowany do programu (tak samo jak w przypadku określenia **-nostdlib-** ).</span><span class="sxs-lookup"><span data-stu-id="8a364-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="8a364-108">Określenie **-nostdlib** jest taka sama jak w przypadku określenia **-nostdlib +** .</span><span class="sxs-lookup"><span data-stu-id="8a364-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="8a364-109">Aby ustawić tę opcję kompilatora w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8a364-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="8a364-110">Poniższe instrukcje dotyczą tylko programu Visual Studio 2015 (i jego wcześniejszych wersji).</span><span class="sxs-lookup"><span data-stu-id="8a364-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="8a364-111">Właściwość kompilacja **nie odwołuje się do biblioteki mscorlib. dll** nie istnieje w nowszych wersjach programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a364-111">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="8a364-112">Otwórz stronę **Właściwości** dla projektu.</span><span class="sxs-lookup"><span data-stu-id="8a364-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="8a364-113">Kliknij stronę właściwości **kompilacji** .</span><span class="sxs-lookup"><span data-stu-id="8a364-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="8a364-114">Kliknij przycisk **Zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="8a364-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="8a364-115">Zmodyfikuj właściwość nie Odwołuj się do **biblioteki mscorlib. dll** .</span><span class="sxs-lookup"><span data-stu-id="8a364-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="8a364-116">Aby programowo ustawić tę opcję kompilatora</span><span class="sxs-lookup"><span data-stu-id="8a364-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="8a364-117">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="8a364-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a364-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a364-118">See also</span></span>

- [<span data-ttu-id="8a364-119">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="8a364-119">C# Compiler Options</span></span>](./index.md)
