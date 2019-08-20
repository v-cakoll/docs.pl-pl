---
title: -nostdlib (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 486539d7abdc3e65847a0bc0e228b1b20a2b2c37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602690"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="ca94a-102">-nostdlib (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="ca94a-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="ca94a-103">**-nostdlib** uniemożliwia Import biblioteki mscorlib. dll, która definiuje całą przestrzeń nazw System.</span><span class="sxs-lookup"><span data-stu-id="ca94a-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca94a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca94a-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="ca94a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca94a-105">Remarks</span></span>

<span data-ttu-id="ca94a-106">Użyj tej opcji, jeśli chcesz zdefiniować lub utworzyć własną przestrzeń nazw systemu i obiekty.</span><span class="sxs-lookup"><span data-stu-id="ca94a-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="ca94a-107">Jeśli nie określisz opcji **-nostdlib**, mscorlib. dll zostanie zaimportowany do programu (tak samo jak w przypadku określenia **-nostdlib-** ).</span><span class="sxs-lookup"><span data-stu-id="ca94a-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="ca94a-108">Określenie **-nostdlib** jest taka sama jak w przypadku określenia **-nostdlib +** .</span><span class="sxs-lookup"><span data-stu-id="ca94a-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="ca94a-109">Aby ustawić tę opcję kompilatora w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca94a-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="ca94a-110">Poniższe instrukcje dotyczą tylko programu Visual Studio 2015 (i jego wcześniejszych wersji).</span><span class="sxs-lookup"><span data-stu-id="ca94a-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="ca94a-111">W programie Visual Studio 2017 nie istnieje właściwość Build programu **mscorlib. dll** .</span><span class="sxs-lookup"><span data-stu-id="ca94a-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="ca94a-112">Otwórz stronę **Właściwości** dla projektu.</span><span class="sxs-lookup"><span data-stu-id="ca94a-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="ca94a-113">Kliknij stronę właściwości **kompilacji** .</span><span class="sxs-lookup"><span data-stu-id="ca94a-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="ca94a-114">Kliknij przycisk **Zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="ca94a-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="ca94a-115">Zmodyfikuj właściwość nie Odwołuj się do **biblioteki mscorlib. dll** .</span><span class="sxs-lookup"><span data-stu-id="ca94a-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="ca94a-116">Aby programowo ustawić tę opcję kompilatora</span><span class="sxs-lookup"><span data-stu-id="ca94a-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="ca94a-117">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="ca94a-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca94a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca94a-118">See also</span></span>

- [<span data-ttu-id="ca94a-119">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="ca94a-119">C# Compiler Options</span></span>](./index.md)
