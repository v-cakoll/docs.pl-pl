---
title: -pathmap (Opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606628"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="636df-102">-pathmap (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="636df-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="636df-103">Opcja kompilatora **-pathmap** określa sposób mapowania ścieżek fizycznych na nazwy ścieżek źródłowych wyprowadzanych przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="636df-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="636df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="636df-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="636df-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="636df-105">Arguments</span></span>

 <span data-ttu-id="636df-106">`path1`Pełna ścieżka do plików źródłowych w bieżącym środowisku</span><span class="sxs-lookup"><span data-stu-id="636df-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="636df-107">`sourcePath1`Ścieżka źródłowa `path1` zastąpiona w dowolnych plikach wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="636df-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="636df-108">Aby określić wiele mapowanych ścieżek źródłowych, należy oddzielić każdy z przecinkiem.</span><span class="sxs-lookup"><span data-stu-id="636df-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="636df-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="636df-109">Remarks</span></span>

<span data-ttu-id="636df-110">Kompilator zapisuje ścieżkę źródłową w danych wyjściowych z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="636df-110">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="636df-111">Ścieżka źródłowa jest zastępowana <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> argumentem, gdy jest stosowany do parametru opcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="636df-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="636df-112">Ścieżka źródłowa jest osadzona w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="636df-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="636df-113">Ścieżka pliku PDB jest osadzona w pliku PE (przenośny plik wykonywalny).</span><span class="sxs-lookup"><span data-stu-id="636df-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="636df-114">Ta opcja mapuje każdą ścieżkę fizyczną na komputerze, na którym kompilator jest uruchamiany na odpowiednią ścieżkę, która powinna być zapisana w plikach wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="636df-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="636df-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="636df-115">Example</span></span>

<span data-ttu-id="636df-116">Skompiluj `t.cs` w katalogu **C:\\testy\\robocze** i mapuj ten katalog do **\publish** w danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="636df-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="636df-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="636df-117">See also</span></span>

- [<span data-ttu-id="636df-118">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="636df-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="636df-119">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="636df-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
