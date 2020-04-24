---
title: '@ (określenie pliku odpowiedzi)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: c578495bbba0efee79f02da284c7feffb8c12fab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348548"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="857ad-102">@ (Określ plik odpowiedzi) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857ad-102">@ (Specify Response File) (Visual Basic)</span></span>

<span data-ttu-id="857ad-103">Określa plik, który zawiera opcje kompilatora i pliki kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="857ad-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>

## <a name="syntax"></a><span data-ttu-id="857ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="857ad-104">Syntax</span></span>

```console
@response_file
```

## <a name="arguments"></a><span data-ttu-id="857ad-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="857ad-105">Arguments</span></span>

`response_file`  
<span data-ttu-id="857ad-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="857ad-106">Required.</span></span> <span data-ttu-id="857ad-107">Plik, który zawiera listę opcji kompilatora lub plików kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="857ad-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="857ad-108">Nazwa pliku należy ująć w cudzysłów (""), jeśli zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="857ad-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>

## <a name="remarks"></a><span data-ttu-id="857ad-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="857ad-109">Remarks</span></span>

<span data-ttu-id="857ad-110">Kompilator przetwarza opcje kompilatora i pliki kodu źródłowego określone w pliku odpowiedzi, tak jakby zostały określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="857ad-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>

<span data-ttu-id="857ad-111">Aby określić więcej niż jeden plik odpowiedzi w kompilacji, określ wiele opcji pliku odpowiedzi, takich jak poniższe.</span><span class="sxs-lookup"><span data-stu-id="857ad-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>

```console
@file1.rsp @file2.rsp
```

<span data-ttu-id="857ad-112">W pliku odpowiedzi w jednym wierszu mogą znajdować się wiele opcji kompilatora i plików kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="857ad-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="857ad-113">Pojedyncza Specyfikacja kompilatora-Option musi znajdować się w jednym wierszu (nie może obejmować wielu wierszy).</span><span class="sxs-lookup"><span data-stu-id="857ad-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="857ad-114">Pliki odpowiedzi mogą mieć komentarze zaczynające się od `#` symbolu.</span><span class="sxs-lookup"><span data-stu-id="857ad-114">Response files can have comments that begin with the `#` symbol.</span></span>

<span data-ttu-id="857ad-115">Opcje określone w wierszu polecenia można połączyć z opcjami określonymi w jednym lub kilku plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="857ad-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="857ad-116">Kompilator przetwarza opcje polecenia w miarę ich występowania.</span><span class="sxs-lookup"><span data-stu-id="857ad-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="857ad-117">W związku z tym argumenty wiersza polecenia mogą przesłonić wcześniej wymienione opcje w plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="857ad-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="857ad-118">Z kolei opcje w pliku odpowiedzi opcje przesłaniają się wcześniej w wierszu polecenia lub w innych plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="857ad-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>

<span data-ttu-id="857ad-119">Visual Basic udostępnia plik VBC. rsp, który znajduje się w tym samym katalogu, co plik VBC. exe.</span><span class="sxs-lookup"><span data-stu-id="857ad-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="857ad-120">Plik VBC. rsp jest uwzględniany domyślnie, jeśli `-noconfig` opcja jest używana.</span><span class="sxs-lookup"><span data-stu-id="857ad-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="857ad-121">Aby uzyskać więcej informacji, zobacz [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="857ad-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>

> [!NOTE]
> <span data-ttu-id="857ad-122">`@` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="857ad-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="857ad-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="857ad-123">Example</span></span>

<span data-ttu-id="857ad-124">Poniższe wiersze pochodzą z przykładowego pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="857ad-124">The following lines are from a sample response file.</span></span>

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a><span data-ttu-id="857ad-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="857ad-125">Example</span></span>

<span data-ttu-id="857ad-126">W poniższym przykładzie pokazano, jak użyć `@` opcji z plikiem odpowiedzi o nazwie. `File1.rsp`</span><span class="sxs-lookup"><span data-stu-id="857ad-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>

```console
vbc @file1.rsp
```

## <a name="see-also"></a><span data-ttu-id="857ad-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="857ad-127">See also</span></span>

- [<span data-ttu-id="857ad-128">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="857ad-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="857ad-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="857ad-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="857ad-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="857ad-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
