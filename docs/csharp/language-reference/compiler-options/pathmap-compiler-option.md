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
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425787"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="49633-102">-elemencie pathmap (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="49633-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="49633-103">**- Elemencie pathmap** — opcja kompilatora określa sposób mapowania ścieżek fizycznych na dane wyjściowe nazwy ścieżki źródłowej przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="49633-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="49633-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49633-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="49633-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="49633-105">Arguments</span></span>

 <span data-ttu-id="49633-106">`path1` Pełna ścieżka do plików źródłowych w bieżącym środowisku</span><span class="sxs-lookup"><span data-stu-id="49633-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="49633-107">`sourcePath1` Ścieżka źródłowa zamieniony na `path1` w żadnych plików wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49633-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="49633-108">Aby określić wiele ścieżek zamapowanego źródła, rozdzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="49633-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="49633-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49633-109">Remarks</span></span>

<span data-ttu-id="49633-110">Kompilator zapisuje ścieżki źródłowej w ścieżce do jego dane wyjściowe z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="49633-110">The compiler writes the source path path into its output for the following reasons:</span></span>

1. <span data-ttu-id="49633-111">Ścieżka źródłowa zostanie zastąpiony argument podczas <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> jest stosowany do opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="49633-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="49633-112">Ścieżka źródłowa jest osadzony w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="49633-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="49633-113">Ścieżka do pliku PDB jest osadzony w pliku PE (przenośny plik wykonywalny).</span><span class="sxs-lookup"><span data-stu-id="49633-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="49633-114">Ta opcja mapuje każdej ścieżki fizycznej na komputerze, na którym jest uruchamiany kompilator do odpowiedniej ścieżki, w której powinny być zapisywane w plikach wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="49633-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="49633-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="49633-115">Example</span></span>

<span data-ttu-id="49633-116">Skompilować `t.cs` w katalogu **C:\\pracy\\testy** i zamapuj katalogowi na potrzeby **\publish** w danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="49633-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="49633-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49633-117">See also</span></span>

- [<span data-ttu-id="49633-118">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="49633-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="49633-119">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="49633-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
