---
title: -nostdlib (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 70007c74efe9a41bdfc15e8fa7daf3c8fc0221ed
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506698"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="bb3e2-102">-nostdlib (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="bb3e2-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="bb3e2-103">**-nostdlib** zapobiega Importuj biblioteki mscorlib.dll, która określa całą przestrzeń nazw System.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb3e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb3e2-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="bb3e2-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb3e2-105">Remarks</span></span>

<span data-ttu-id="bb3e2-106">Użyj tej opcji, jeśli chcesz zdefiniować lub tworzyć własne systemową przestrzenią nazw i obiektów.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="bb3e2-107">Jeśli nie określisz **- nostdlib**, aby biblioteka mscorlib.dll są importowane do programu (taka sama jak określanie **- nostdlib —**).</span><span class="sxs-lookup"><span data-stu-id="bb3e2-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="bb3e2-108">Określanie **- nostdlib** jest taka sama jak określanie **- nostdlib +**.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="bb3e2-109">Aby ustawić tę opcję kompilatora w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb3e2-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="bb3e2-110">Poniższe instrukcje dotyczą programu Visual Studio 2015 (i wcześniejszych wersjach) tylko.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="bb3e2-111">**Nie odwołują się do biblioteki mscorlib.dll** właściwości kompilacji nie istnieje w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="bb3e2-112">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="bb3e2-113">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="bb3e2-114">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="bb3e2-115">Modyfikowanie **nie odwołują się do biblioteki mscorlib.dll** właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="bb3e2-116">Aby programowo ustawić tę opcję kompilatora</span><span class="sxs-lookup"><span data-stu-id="bb3e2-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="bb3e2-117">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb3e2-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb3e2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb3e2-118">See Also</span></span>

- [<span data-ttu-id="bb3e2-119">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="bb3e2-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
