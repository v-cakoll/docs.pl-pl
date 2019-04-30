---
title: -noconfig (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 8d28ef1334df847865721783fa98aaa9d8c576be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662689"
---
# <a name="-noconfig-c-compiler-options"></a><span data-ttu-id="df11c-102">-noconfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="df11c-102">-noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="df11c-103">**- Noconfig** opcji informuje kompilator, nie można skompilować przy użyciu pliku csc.rsp, który jest na terenie i ładowane z tym samym katalogu co plik csc.exe.</span><span class="sxs-lookup"><span data-stu-id="df11c-103">The **-noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df11c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df11c-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="df11c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df11c-105">Remarks</span></span>  
 <span data-ttu-id="df11c-106">Pliku csc.rsp odwołuje się do wszystkich zestawów, które są dostarczane z programem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="df11c-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="df11c-107">Rzeczywiste odwołań, które środowisko projektowe programu Visual Studio .NET zawiera zależą od typu projektu.</span><span class="sxs-lookup"><span data-stu-id="df11c-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="df11c-108">Można zmodyfikować pliku csc.rsp i określ opcje dodatkowe kompilatora, które powinny być uwzględnione w każdej kompilacji z wiersza polecenia przy użyciu csc.exe (z wyjątkiem **- noconfig** opcji).</span><span class="sxs-lookup"><span data-stu-id="df11c-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **-noconfig** option).</span></span>  
  
 <span data-ttu-id="df11c-109">Kompilator przetwarza opcje przekazywane do **csc** ostatnie polecenie.</span><span class="sxs-lookup"><span data-stu-id="df11c-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="df11c-110">W związku z tym dowolnej opcji w wierszu polecenia zastępuje ustawienie opcji tego samego pliku csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="df11c-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="df11c-111">Jeśli nie chcesz, aby kompilator, aby wyszukać i użyj ustawień w pliku csc.rsp, określ **- noconfig**.</span><span class="sxs-lookup"><span data-stu-id="df11c-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **-noconfig**.</span></span>  
  
 <span data-ttu-id="df11c-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="df11c-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df11c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df11c-113">See also</span></span>

- [<span data-ttu-id="df11c-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="df11c-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="df11c-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="df11c-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
