---
title: '@ (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d4dc8c81a9afd60add4c2a62be6804a0f6446124
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="-c-compiler-options"></a><span data-ttu-id="e1487-102">@ (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="e1487-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="e1487-103">@ — Opcja pozwala określić plik, który zawiera opcje kompilatora i plików kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="e1487-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1487-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1487-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1487-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e1487-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="e1487-106">Plik, który zawiera listę opcji kompilatora lub plików kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="e1487-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1487-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1487-107">Remarks</span></span>  
 <span data-ttu-id="e1487-108">Opcje kompilatora i plików kodu źródłowego zostanie przetworzony przez kompilator tak, jakby były one określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1487-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="e1487-109">Aby określić więcej niż jeden plik odpowiedzi w kompilacji, należy określić wiele opcji pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e1487-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="e1487-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e1487-110">For example:</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="e1487-111">W odpowiedzi na plik, wiele opcji kompilatora i plików kodu źródłowego może występować w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e1487-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="e1487-112">Specyfikacja opcji kompilatora pojedynczego musi znajdować się w jednym wierszu (nie może obejmować wiele wierszy).</span><span class="sxs-lookup"><span data-stu-id="e1487-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="e1487-113">Pliki odpowiedzi mogą mieć komentarze, które zaczynają się od symbolu #.</span><span class="sxs-lookup"><span data-stu-id="e1487-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="e1487-114">Określenie opcji kompilatora z pliku odpowiedzi jest podobnie jak wystawiania tych poleceń w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1487-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="e1487-115">Zobacz [tworzenie z wiersza polecenia](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="e1487-115">See [Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="e1487-116">Kompilator przetwarza opcji polecenia, ponieważ są one napotkał.</span><span class="sxs-lookup"><span data-stu-id="e1487-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="e1487-117">W związku z tym argumenty wiersza polecenia można zastąpić opcje wymienione wcześniej w plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e1487-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="e1487-118">Z drugiej strony Opcje w pliku odpowiedzi zastąpią opcje wymienione wcześniej w wierszu polecenia lub w innych plików odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e1487-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="e1487-119">C# zawiera pliku csc.rsp, który znajduje się w tym samym katalogu co plik csc.exe.</span><span class="sxs-lookup"><span data-stu-id="e1487-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="e1487-120">Zobacz [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Aby uzyskać więcej informacji na temat csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="e1487-120">See [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="e1487-121">Tej opcji kompilatora nie można ustawić w środowisku programowania Visual Studio i nie można go zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="e1487-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1487-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1487-122">Example</span></span>  
 <span data-ttu-id="e1487-123">Poniżej przedstawiono kilka wierszy z przykładowy plik odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="e1487-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
/target:exe /out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1487-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1487-124">See Also</span></span>  
 [<span data-ttu-id="e1487-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="e1487-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
