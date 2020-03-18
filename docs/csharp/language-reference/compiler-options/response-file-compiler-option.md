---
title: '@ (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: d8e5c0ec148754c3e4cebfa32ad9f44a0bb0119e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70202908"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="aadf6-102">@ (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="aadf6-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="aadf6-103">Opcja @ umożliwia określenie pliku zawierającego opcje kompilatora i pliki kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="aadf6-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aadf6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aadf6-104">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="aadf6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="aadf6-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="aadf6-106">Plik, który zawiera listę opcji kompilatora lub plików kodu źródłowego do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="aadf6-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aadf6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aadf6-107">Remarks</span></span>  
 <span data-ttu-id="aadf6-108">Opcje kompilatora i pliki kodu źródłowego będą przetwarzane przez kompilator tak, jakby zostały określone w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="aadf6-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="aadf6-109">Aby określić więcej niż jeden plik odpowiedzi w kompilacji, określ wiele opcji pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="aadf6-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="aadf6-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="aadf6-110">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="aadf6-111">W pliku odpowiedzi wiele opcji kompilatora i plików kodu źródłowego może pojawić się w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="aadf6-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="aadf6-112">Specyfikacja opcji pojedynczego kompilatora musi pojawić się w jednym wierszu (nie może zawierać wielu wierszy).</span><span class="sxs-lookup"><span data-stu-id="aadf6-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="aadf6-113">Pliki odpowiedzi mogą mieć komentarze, które zaczynają się od symbolu #.</span><span class="sxs-lookup"><span data-stu-id="aadf6-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="aadf6-114">Określanie opcji kompilatora z pliku odpowiedzi jest jak wydawanie tych poleceń w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="aadf6-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="aadf6-115">Aby uzyskać więcej informacji, zobacz [Tworzenie z wiersza polecenia.](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)</span><span class="sxs-lookup"><span data-stu-id="aadf6-115">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="aadf6-116">Kompilator przetwarza opcje polecenia, ponieważ są one napotkane.</span><span class="sxs-lookup"><span data-stu-id="aadf6-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="aadf6-117">W związku z tym argumenty wiersza polecenia można zastąpić wcześniej wymienionych opcji w plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="aadf6-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="aadf6-118">Z drugiej strony opcje w pliku odpowiedzi zastąpią opcje wymienione wcześniej w wierszu polecenia lub w innych plikach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="aadf6-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="aadf6-119">C# udostępnia plik csc.rsp, który znajduje się w tym samym katalogu co plik csc.exe.</span><span class="sxs-lookup"><span data-stu-id="aadf6-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="aadf6-120">Zobacz [-noconfig](./noconfig-compiler-option.md) aby uzyskać więcej informacji na temat csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="aadf6-120">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="aadf6-121">Nie można ustawić tej opcji kompilatora w środowisku programistycznym programu Visual Studio ani nie można jej programowo zmienić.</span><span class="sxs-lookup"><span data-stu-id="aadf6-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aadf6-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="aadf6-122">Example</span></span>  
 <span data-ttu-id="aadf6-123">Poniżej przedstawiono kilka wierszy z przykładowego pliku odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="aadf6-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="aadf6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aadf6-124">See also</span></span>

- [<span data-ttu-id="aadf6-125">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="aadf6-125">C# Compiler Options</span></span>](./index.md)
