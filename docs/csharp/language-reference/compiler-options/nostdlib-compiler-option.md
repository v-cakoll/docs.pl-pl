---
title: -nostdlib (Opcje kompilatora C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345078"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="283a5-102">-nostdlib (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="283a5-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="283a5-103">**-nostdlib** zapobiega importowi pliku mscorlib.dll, który definiuje cały obszar nazw systemowy.</span><span class="sxs-lookup"><span data-stu-id="283a5-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="283a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="283a5-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="283a5-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="283a5-105">Remarks</span></span>

<span data-ttu-id="283a5-106">Użyj tej opcji, jeśli chcesz zdefiniować lub utworzyć własny obszar nazw i obiektów systemowych.</span><span class="sxs-lookup"><span data-stu-id="283a5-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="283a5-107">Jeśli nie określisz **-nostdlib,** plik mscorlib.dll zostanie zaimportowany do programu (tak samo jak określenie **-nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="283a5-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="283a5-108">Określanie **-nostdlib** jest takie samo jak określenie **-nostdlib+**.</span><span class="sxs-lookup"><span data-stu-id="283a5-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="283a5-109">Aby ustawić tę opcję kompilatora w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="283a5-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="283a5-110">Poniższe instrukcje dotyczą tylko programu Visual Studio 2015 (i wcześniejszych wersji).</span><span class="sxs-lookup"><span data-stu-id="283a5-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="283a5-111">Właściwość **kompilacji pliku Mscorlib.dll** nie istnieje w nowszych wersjach programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="283a5-111">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="283a5-112">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="283a5-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="283a5-113">Kliknij stronę **Tworzenie** właściwości.</span><span class="sxs-lookup"><span data-stu-id="283a5-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="283a5-114">Kliknij przycisk **Zaawansowane.**</span><span class="sxs-lookup"><span data-stu-id="283a5-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="283a5-115">Zmodyfikuj właściwość **Docorlib.dll.**</span><span class="sxs-lookup"><span data-stu-id="283a5-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="283a5-116">Aby programowo ustawić tę opcję kompilatora</span><span class="sxs-lookup"><span data-stu-id="283a5-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="283a5-117">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="283a5-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="283a5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="283a5-118">See also</span></span>

- [<span data-ttu-id="283a5-119">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="283a5-119">C# Compiler Options</span></span>](./index.md)
