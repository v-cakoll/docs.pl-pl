---
title: '@ (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 1884230f1779f9d425ef6e54cda6967c8e51d985
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602479"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="f5611-102">@ (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="f5611-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="f5611-103">Opcja @ pozwala określić plik, który zawiera opcje kompilatora i pliki kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="f5611-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5611-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5611-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5611-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f5611-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="f5611-106">Plik, który zawiera listę opcji kompilatora lub plików kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="f5611-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5611-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5611-107">Remarks</span></span>  
 <span data-ttu-id="f5611-108">Opcje kompilatora i pliki kodu źródłowego będą przetwarzane przez kompilator tak, jakby zostały określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f5611-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="f5611-109">Aby określić więcej niż jeden plik odpowiedzi w kompilacji, określ wiele opcji plików odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f5611-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="f5611-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f5611-110">For example:</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="f5611-111">W pliku odpowiedzi w jednym wierszu może znajdować się wiele opcji kompilatora i plików kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f5611-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="f5611-112">Jedna Specyfikacja opcji kompilatora musi znajdować się w jednym wierszu (nie może obejmować wielu wierszy).</span><span class="sxs-lookup"><span data-stu-id="f5611-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="f5611-113">Pliki odpowiedzi mogą mieć komentarze zaczynające się od znaku #.</span><span class="sxs-lookup"><span data-stu-id="f5611-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="f5611-114">Określanie opcji kompilatora z poziomu pliku odpowiedzi jest tak samo samo jak wydawanie tych poleceń w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f5611-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="f5611-115">Aby uzyskać więcej informacji, zobacz [Kompilowanie z wiersza polecenia](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) .</span><span class="sxs-lookup"><span data-stu-id="f5611-115">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="f5611-116">Kompilator przetwarza opcje polecenia w miarę ich napotkania.</span><span class="sxs-lookup"><span data-stu-id="f5611-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="f5611-117">W związku z tym argumenty wiersza polecenia mogą przesłonić wcześniej wymienione opcje w plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f5611-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="f5611-118">Z kolei opcje w pliku odpowiedzi zastępują opcje wymienione wcześniej w wierszu polecenia lub w innych plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f5611-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="f5611-119">C#udostępnia plik csc. rsp, który znajduje się w tym samym katalogu, co plik csc. exe.</span><span class="sxs-lookup"><span data-stu-id="f5611-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="f5611-120">Aby uzyskać więcej informacji na temat CSC. rsp, zobacz [-noconfig](./noconfig-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="f5611-120">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="f5611-121">Nie można ustawić tej opcji kompilatora w środowisku deweloperskim programu Visual Studio, ani programowo zmienić.</span><span class="sxs-lookup"><span data-stu-id="f5611-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5611-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5611-122">Example</span></span>  
 <span data-ttu-id="f5611-123">Poniżej przedstawiono kilka wierszy z przykładowego pliku odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="f5611-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5611-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5611-124">See also</span></span>

- [<span data-ttu-id="f5611-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="f5611-125">C# Compiler Options</span></span>](./index.md)
