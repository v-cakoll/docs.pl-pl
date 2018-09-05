---
title: -elemencie pathmap (opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 277ab8e094f28fd5e3cbba4de12e742bb9614730
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559046"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="d1bbd-102">-elemencie pathmap (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d1bbd-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="d1bbd-103">**- Elemencie pathmap** — opcja kompilatora określa sposób mapowania ścieżek fizycznych na dane wyjściowe nazwy ścieżki źródłowej przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1bbd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1bbd-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="d1bbd-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d1bbd-105">Arguments</span></span>

 <span data-ttu-id="d1bbd-106">`path1` Pełna ścieżka do plików źródłowych w bieżącym środowisku</span><span class="sxs-lookup"><span data-stu-id="d1bbd-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="d1bbd-107">`sourcePath1` Ścieżka źródłowa zamieniony na `path1` w żadnych plików wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="d1bbd-108">Aby określić wiele ścieżek zamapowanego źródła, rozdzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1bbd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1bbd-109">Remarks</span></span>

<span data-ttu-id="d1bbd-110">Kompilator zapisuje ścieżki źródłowej w ścieżce do jego dane wyjściowe z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="d1bbd-110">The compiler writes the source path path into its output for the following reasons:</span></span>

1. <span data-ttu-id="d1bbd-111">Ścieżka źródłowa zostanie zastąpiony argument podczas <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> jest stosowany do opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="d1bbd-112">Ścieżka źródłowa jest osadzony w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="d1bbd-113">Ścieżka do pliku PDB jest osadzony w pliku PE (przenośny plik wykonywalny).</span><span class="sxs-lookup"><span data-stu-id="d1bbd-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="d1bbd-114">Ta opcja mapuje każdej ścieżki fizycznej na komputerze, na którym jest uruchamiany kompilator do odpowiedniej ścieżki, w której powinny być zapisywane w plikach wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d1bbd-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="d1bbd-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1bbd-115">Example</span></span>

<span data-ttu-id="d1bbd-116">Skompilować `t.cs` w katalogu **C:\\pracy\\testy** i zamapuj katalogowi na potrzeby **\publish** w danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="d1bbd-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="d1bbd-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1bbd-117">See also</span></span>

- [<span data-ttu-id="d1bbd-118">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d1bbd-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="d1bbd-119">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d1bbd-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
