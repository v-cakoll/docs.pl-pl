---
title: -noconfig (C# opcje kompilatora)
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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602741"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="cb30b-102">-noconfig (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="cb30b-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="cb30b-103">Opcja **-noconfig** informuje kompilator, że nie kompiluje się z plikiem CSC. rsp, który znajduje się w i załadowany z tego samego katalogu co plik csc. exe.</span><span class="sxs-lookup"><span data-stu-id="cb30b-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb30b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb30b-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="cb30b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb30b-105">Remarks</span></span>  
 <span data-ttu-id="cb30b-106">Plik csc. rsp odwołuje się do wszystkich zestawów dostarczonych z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb30b-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="cb30b-107">Rzeczywiste odwołania, które zawiera środowisko programistyczne Visual Studio .NET, zależą od typu projektu.</span><span class="sxs-lookup"><span data-stu-id="cb30b-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="cb30b-108">Można zmodyfikować plik csc. rsp i określić dodatkowe opcje kompilatora, które powinny być zawarte w każdej kompilacji z wiersza polecenia w pliku CSC. exe (z wyjątkiem opcji **-noconfig** ).</span><span class="sxs-lookup"><span data-stu-id="cb30b-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="cb30b-109">Kompilator przetwarza opcje przesłane do polecenia **CSC** jako ostatni.</span><span class="sxs-lookup"><span data-stu-id="cb30b-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="cb30b-110">W związku z tym każda opcja w wierszu polecenia zastępuje ustawienie tej samej opcji w pliku CSC. rsp.</span><span class="sxs-lookup"><span data-stu-id="cb30b-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="cb30b-111">Jeśli nie chcesz, aby kompilator wyszukał i używał ustawień w pliku CSC. rsp, określ **-noconfig**.</span><span class="sxs-lookup"><span data-stu-id="cb30b-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="cb30b-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="cb30b-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb30b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb30b-113">See also</span></span>

- [<span data-ttu-id="cb30b-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="cb30b-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="cb30b-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="cb30b-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
