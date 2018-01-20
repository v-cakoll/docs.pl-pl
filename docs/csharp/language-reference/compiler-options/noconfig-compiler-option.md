---
title: -noconfig (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1004f70547ca3a841c59338a1344235132af3fa7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="41abe-102">-noconfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="41abe-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="41abe-103">**- Noconfig** opcja informuje kompilator, aby nie kompilacji z pliku csc.rsp, który jest znajduje się w i załadowane z tym samym katalogu co plik csc.exe.</span><span class="sxs-lookup"><span data-stu-id="41abe-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41abe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41abe-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="41abe-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41abe-105">Remarks</span></span>  
 <span data-ttu-id="41abe-106">Pliku csc.rsp odwołuje się do wszystkich zestawów, które są dostarczane z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41abe-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="41abe-107">Rzeczywiste odwołań, które zawiera środowisko projektowe Visual Studio .NET są zależne od typu projektu.</span><span class="sxs-lookup"><span data-stu-id="41abe-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="41abe-108">Można zmodyfikować pliku csc.rsp i określ opcje kompilatora dodatkowe, które powinny być uwzględnione w każdej kompilacji z wiersza polecenia z csc.exe (z wyjątkiem **- noconfig** opcja).</span><span class="sxs-lookup"><span data-stu-id="41abe-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="41abe-109">Kompilator przetwarza opcje przekazane do **csc** ostatniego polecenia.</span><span class="sxs-lookup"><span data-stu-id="41abe-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="41abe-110">W związku z tym każda opcja, w wierszu polecenia zastępuje ustawienie opcji tego samego pliku csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="41abe-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="41abe-111">Jeśli nie chcesz kompilatora, aby wyszukać i użyj ustawień w pliku csc.rsp, określ **- noconfig**.</span><span class="sxs-lookup"><span data-stu-id="41abe-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="41abe-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="41abe-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41abe-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41abe-113">See Also</span></span>  
 [<span data-ttu-id="41abe-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="41abe-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="41abe-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="41abe-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
