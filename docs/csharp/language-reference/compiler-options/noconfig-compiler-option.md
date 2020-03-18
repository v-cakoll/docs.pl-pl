---
title: -noconfig (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 2d6d0c52be2306292224d7831f8818c6f865f2f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602741"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="245b1-102">-noconfig (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="245b1-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="245b1-103">Opcja **-noconfig** informuje kompilator, aby nie kompilował z plikiem csc.rsp, który znajduje się i ładował z tego samego katalogu co plik csc.exe.</span><span class="sxs-lookup"><span data-stu-id="245b1-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="245b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="245b1-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="245b1-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="245b1-105">Remarks</span></span>  
 <span data-ttu-id="245b1-106">Plik csc.rsp odwołuje się do wszystkich zestawów dostarczanych z platformą .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="245b1-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="245b1-107">Rzeczywiste odwołania, które zawiera środowisko programistyczne programu Visual Studio .NET, zależą od typu projektu.</span><span class="sxs-lookup"><span data-stu-id="245b1-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="245b1-108">Można zmodyfikować plik csc.rsp i określić dodatkowe opcje kompilatora, które powinny być zawarte w każdej kompilacji z wiersza polecenia z csc.exe (z wyjątkiem opcji **-noconfig).**</span><span class="sxs-lookup"><span data-stu-id="245b1-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="245b1-109">Kompilator przetwarza opcje przekazane do polecenia **csc** ostatnio.</span><span class="sxs-lookup"><span data-stu-id="245b1-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="245b1-110">W związku z tym każda opcja w wierszu polecenia zastępuje ustawienie tej samej opcji w pliku csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="245b1-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="245b1-111">Jeśli nie chcesz, aby kompilator szukał i używał ustawień w pliku csc.rsp, określ **-noconfig**.</span><span class="sxs-lookup"><span data-stu-id="245b1-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="245b1-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="245b1-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="245b1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="245b1-113">See also</span></span>

- [<span data-ttu-id="245b1-114">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="245b1-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="245b1-115">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="245b1-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
