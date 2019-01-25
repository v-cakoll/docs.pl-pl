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
ms.openlocfilehash: cf87d8d2ac4531142288a8637f7fbeb9139382ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545832"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="84d18-102">-nostdlib (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="84d18-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="84d18-103">**-nostdlib** zapobiega Importuj biblioteki mscorlib.dll, która określa całą przestrzeń nazw System.</span><span class="sxs-lookup"><span data-stu-id="84d18-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="84d18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84d18-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="84d18-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84d18-105">Remarks</span></span>

<span data-ttu-id="84d18-106">Użyj tej opcji, jeśli chcesz zdefiniować lub tworzyć własne systemową przestrzenią nazw i obiektów.</span><span class="sxs-lookup"><span data-stu-id="84d18-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="84d18-107">Jeśli nie określisz **- nostdlib**, aby biblioteka mscorlib.dll są importowane do programu (taka sama jak określanie **- nostdlib —**).</span><span class="sxs-lookup"><span data-stu-id="84d18-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="84d18-108">Określanie **- nostdlib** jest taka sama jak określanie **- nostdlib +**.</span><span class="sxs-lookup"><span data-stu-id="84d18-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="84d18-109">Aby ustawić tę opcję kompilatora w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="84d18-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="84d18-110">Poniższe instrukcje dotyczą programu Visual Studio 2015 (i wcześniejszych wersjach) tylko.</span><span class="sxs-lookup"><span data-stu-id="84d18-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="84d18-111">**Nie odwołują się do biblioteki mscorlib.dll** właściwości kompilacji nie istnieje w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="84d18-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="84d18-112">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="84d18-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="84d18-113">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="84d18-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="84d18-114">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="84d18-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="84d18-115">Modyfikowanie **nie odwołują się do biblioteki mscorlib.dll** właściwości.</span><span class="sxs-lookup"><span data-stu-id="84d18-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="84d18-116">Aby programowo ustawić tę opcję kompilatora</span><span class="sxs-lookup"><span data-stu-id="84d18-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="84d18-117">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="84d18-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="84d18-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84d18-118">See also</span></span>

- [<span data-ttu-id="84d18-119">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="84d18-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
