---
title: -pathmap (opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 36196ffea19cfde7ff5f830ea358d2bd83edf419
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472850"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="231bf-102">-pathmap (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="231bf-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="231bf-103">**- Pathmap** — opcja kompilatora określa sposób mapowania ścieżek fizycznych źródła ścieżkę nazwy w danych wyjściowych przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="231bf-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="231bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="231bf-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="231bf-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="231bf-105">Arguments</span></span>

 <span data-ttu-id="231bf-106">`path1` Pełna ścieżka do plików źródłowych w bieżącym środowisku</span><span class="sxs-lookup"><span data-stu-id="231bf-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="231bf-107">`sourcePath1` Ścieżka źródłowa podstawić `path1` w żadnych plików wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="231bf-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="231bf-108">Aby określić wiele ścieżek zamapowanych źródła, rozdzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="231bf-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="231bf-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="231bf-109">Remarks</span></span>

<span data-ttu-id="231bf-110">Kompilator zapisuje ścieżki źródłowej ścieżki do jego dane wyjściowe z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="231bf-110">The compiler writes the source path path into its output for the following reasons:</span></span>

1. <span data-ttu-id="231bf-111">Argument ścieżki źródłowej zostanie zastąpiony podczas <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> jest stosowany do parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="231bf-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="231bf-112">Ścieżka źródłowa jest osadzony w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="231bf-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="231bf-113">Ścieżka pliku PDB jest osadzony w pliku PE (przenośny plik wykonywalny).</span><span class="sxs-lookup"><span data-stu-id="231bf-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="231bf-114">Ta opcja mapuje każdej ścieżki fizycznej na komputerze, na którym jest uruchomiona przez kompilator do odpowiedniego ścieżki, w której mają być zapisywane w plikach wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="231bf-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="231bf-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="231bf-115">Example</span></span>

<span data-ttu-id="231bf-116">Kompiluj `t.cs` w katalogu **C:\\pracy\\testy** i mapowanie katalogowi na potrzeby **\publish** w danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="231bf-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="231bf-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="231bf-117">See also</span></span>

 [<span data-ttu-id="231bf-118">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="231bf-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="231bf-119">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="231bf-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
