---
title: -elemencie pathmap (C# opcje kompilatora)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606628"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="c336a-102">-elemencie pathmap (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="c336a-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="c336a-103">Opcja kompilatora **-elemencie pathmap** określa sposób mapowania ścieżek fizycznych do nazw ścieżek źródłowych wyjściowych przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="c336a-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="c336a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c336a-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="c336a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c336a-105">Arguments</span></span>

 <span data-ttu-id="c336a-106">`path1`Pełna ścieżka do plików źródłowych w bieżącym środowisku</span><span class="sxs-lookup"><span data-stu-id="c336a-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="c336a-107">`sourcePath1`Ścieżka źródłowa zastępują dla `path1` plików wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c336a-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="c336a-108">Aby określić wiele mapowanych ścieżek źródłowych, rozdziel je przecinkami.</span><span class="sxs-lookup"><span data-stu-id="c336a-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="c336a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c336a-109">Remarks</span></span>

<span data-ttu-id="c336a-110">Kompilator zapisuje ścieżkę źródłową do danych wyjściowych z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="c336a-110">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="c336a-111">Ścieżka źródłowa jest zastępowana argumentem, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> gdy jest stosowany do opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="c336a-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="c336a-112">Ścieżka źródłowa jest osadzona w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="c336a-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="c336a-113">Ścieżka pliku PDB jest osadzona w pliku PE (przenośny plik wykonywalny).</span><span class="sxs-lookup"><span data-stu-id="c336a-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="c336a-114">Ta opcja mapuje każdą ścieżkę fizyczną na komputerze, na którym kompilator jest uruchamiany do odpowiedniej ścieżki, która powinna być zapisywana w plikach wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c336a-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="c336a-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="c336a-115">Example</span></span>

<span data-ttu-id="c336a-116">Kompiluj `t.cs` w katalogu **C:\\\\Work Tests** i Mapuj ten katalog na **\publish** w danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="c336a-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="c336a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c336a-117">See also</span></span>

- [<span data-ttu-id="c336a-118">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c336a-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c336a-119">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="c336a-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
