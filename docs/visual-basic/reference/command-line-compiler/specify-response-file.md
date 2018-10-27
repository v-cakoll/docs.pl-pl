---
title: '@ (Określ plik odpowiedzi) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 54a4cee0b779c0784eec169a15ab1594c56cede9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194686"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="4f18f-102">@ (Określ plik odpowiedzi) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f18f-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="4f18f-103">Określa plik, który zawiera opcje kompilatora i pliki kodu źródłowego do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4f18f-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f18f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f18f-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="4f18f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4f18f-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="4f18f-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4f18f-106">Required.</span></span> <span data-ttu-id="4f18f-107">Plik, który zawiera listę opcji kompilatora lub pliki kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="4f18f-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="4f18f-108">Nazwę pliku należy ująć w znaki cudzysłowu ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="4f18f-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f18f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f18f-109">Remarks</span></span>  
 <span data-ttu-id="4f18f-110">Kompilator przetwarza opcje kompilatora i pliki kodu źródłowego, określone w pliku odpowiedzi, tak, jakby były one określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="4f18f-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="4f18f-111">Aby określić więcej niż jeden plik odpowiedzi w kompilacji, należy określić wiele opcji pliku odpowiedzi, takie jak następujące.</span><span class="sxs-lookup"><span data-stu-id="4f18f-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="4f18f-112">W odpowiedzi na plik, wiele opcji kompilatora i pliki kodu źródłowego może znajdować się w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="4f18f-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="4f18f-113">Specyfikacja pojedynczego opcję kompilatora musi znajdować się w jednym wierszu (nie może obejmować wiele wierszy).</span><span class="sxs-lookup"><span data-stu-id="4f18f-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="4f18f-114">Pliki odpowiedzi mogą mieć komentarze, które zaczynają się od `#` symboli.</span><span class="sxs-lookup"><span data-stu-id="4f18f-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="4f18f-115">Można połączyć opcje określone w wierszu polecenia za pomocą opcji określonych w co najmniej jeden plik odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4f18f-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="4f18f-116">Po ich napotkaniu, kompilator przetwarza opcje polecenia.</span><span class="sxs-lookup"><span data-stu-id="4f18f-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="4f18f-117">W związku z tym argumenty wiersza polecenia można zastąpić opcje wymienione wcześniej w plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4f18f-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="4f18f-118">Z drugiej strony Opcje w pliku odpowiedzi zastępują opcje wymienione wcześniej w wierszu polecenia lub w innych plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4f18f-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="4f18f-119">Soubor Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe zapewnia Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4f18f-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="4f18f-120">Soubor Vbc.rsp jest zawarte domyślnie, chyba że `-noconfig` jest używana opcja.</span><span class="sxs-lookup"><span data-stu-id="4f18f-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="4f18f-121">Aby uzyskać więcej informacji, zobacz [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="4f18f-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f18f-122">`@` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="4f18f-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f18f-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f18f-123">Example</span></span>  
 <span data-ttu-id="4f18f-124">Następujące wiersze pochodzą z przykładowego pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4f18f-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="4f18f-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f18f-125">Example</span></span>  
 <span data-ttu-id="4f18f-126">Poniższy przykład pokazuje sposób użycia `@` opcji z pliku odpowiedzi o nazwie `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="4f18f-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f18f-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f18f-127">See Also</span></span>  
 [<span data-ttu-id="4f18f-128">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f18f-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4f18f-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="4f18f-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="4f18f-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="4f18f-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
