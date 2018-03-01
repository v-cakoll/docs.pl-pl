---
title: "@ (Określ plik odpowiedzi) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ced258713983ded06fa70cb65d56071b41cdc75b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="9a3a2-102">@ (Określ plik odpowiedzi) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a3a2-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="9a3a2-103">Określa plik, który zawiera opcje kompilatora i skompilować plików kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a3a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a3a2-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a3a2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9a3a2-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="9a3a2-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-106">Required.</span></span> <span data-ttu-id="9a3a2-107">Plik, który zawiera listę opcji kompilatora lub plików kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="9a3a2-108">Nazwę pliku należy ująć w cudzysłów ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a3a2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a3a2-109">Remarks</span></span>  
 <span data-ttu-id="9a3a2-110">Kompilator przetwarza opcje kompilatora i określone w pliku odpowiedzi, tak jakby były one określone w wierszu polecenia plików kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="9a3a2-111">Aby określić więcej niż jeden plik odpowiedzi w kompilacji, należy określić wiele opcji pliku odpowiedzi, takie jak.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="9a3a2-112">W odpowiedzi na plik, wiele opcji kompilatora i plików kodu źródłowego może występować w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="9a3a2-113">Specyfikacja opcji kompilatora pojedyncza musi znajdować się w jednym wierszu (nie może obejmować wiele wierszy).</span><span class="sxs-lookup"><span data-stu-id="9a3a2-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="9a3a2-114">Pliki odpowiedzi mogą mieć komentarze, które zaczynają się od `#` symbolu.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="9a3a2-115">Możesz łączyć opcje określone w wierszu polecenia z opcjami w co najmniej jeden plik odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="9a3a2-116">Kompilator przetwarza opcji polecenia, po ich napotkaniu.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="9a3a2-117">W związku z tym argumenty wiersza polecenia można zastąpić opcje wymienione wcześniej w plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="9a3a2-118">Z drugiej strony Opcje w pliku odpowiedzi musi zostać zastąpiona opcje wymienione wcześniej w wierszu polecenia lub w innych plików odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="9a3a2-119">Visual Basic zapewnia pliku Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="9a3a2-120">Pliku Vbc.rsp znajduje się domyślnie, chyba że `/noconfig` jest używana opcja.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-120">The Vbc.rsp file is included by default, unless the `/noconfig` option is used.</span></span> <span data-ttu-id="9a3a2-121">Aby uzyskać więcej informacji, zobacz [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="9a3a2-121">For more information, see [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a3a2-122">`@` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a3a2-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a3a2-123">Example</span></span>  
 <span data-ttu-id="9a3a2-124">Następujące wiersze są z przykładowy plik odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-124">The following lines are from a sample response file.</span></span>  
  
```  
# build the first output file  
/target:exe   
/out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="9a3a2-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a3a2-125">Example</span></span>  
 <span data-ttu-id="9a3a2-126">W poniższym przykładzie pokazano sposób użycia `@` opcji przy użyciu pliku odpowiedzi o nazwie `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="9a3a2-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```  
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a3a2-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a3a2-127">See Also</span></span>  
 [<span data-ttu-id="9a3a2-128">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a3a2-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9a3a2-129">/ noconfig</span><span class="sxs-lookup"><span data-stu-id="9a3a2-129">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="9a3a2-130">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="9a3a2-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
