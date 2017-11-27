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
ms.openlocfilehash: d2b15853cdd6ee9fe12b8b3ba3388a74e49c9701
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig-c-compiler-options"></a><span data-ttu-id="a48ff-102">/noconfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a48ff-102">/noconfig (C# Compiler Options)</span></span>
<span data-ttu-id="a48ff-103">**/Noconfig** opcja informuje kompilator, aby nie kompilacji z pliku csc.rsp, który jest znajduje się w i załadowane z tym samym katalogu co plik csc.exe.</span><span class="sxs-lookup"><span data-stu-id="a48ff-103">The **/noconfig** option tells the compiler not to compile with the csc.rsp file, which is located in and loaded from the same directory as the csc.exe file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a48ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a48ff-104">Syntax</span></span>  
  
```console  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="a48ff-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a48ff-105">Remarks</span></span>  
 <span data-ttu-id="a48ff-106">Pliku csc.rsp odwołuje się do wszystkich zestawów, które są dostarczane z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a48ff-106">The csc.rsp file references all the assemblies shipped with the .NET Framework.</span></span> <span data-ttu-id="a48ff-107">Rzeczywiste odwołań, które zawiera środowisko projektowe Visual Studio .NET są zależne od typu projektu.</span><span class="sxs-lookup"><span data-stu-id="a48ff-107">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span>  
  
 <span data-ttu-id="a48ff-108">Można zmodyfikować pliku csc.rsp i określ opcje kompilatora dodatkowe, które powinny być uwzględnione w każdej kompilacji z wiersza polecenia z csc.exe (z wyjątkiem **/noconfig** opcja).</span><span class="sxs-lookup"><span data-stu-id="a48ff-108">You can modify the csc.rsp file and specify additional compiler options that should be included in every compilation from the command line with csc.exe (except the **/noconfig** option).</span></span>  
  
 <span data-ttu-id="a48ff-109">Kompilator przetwarza opcje przekazane do **csc** ostatniego polecenia.</span><span class="sxs-lookup"><span data-stu-id="a48ff-109">The compiler processes the options passed to the **csc** command last.</span></span> <span data-ttu-id="a48ff-110">W związku z tym każda opcja, w wierszu polecenia zastępuje ustawienie opcji tego samego pliku csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="a48ff-110">Therefore, any option on the command line overrides the setting of the same option in the csc.rsp file.</span></span>  
  
 <span data-ttu-id="a48ff-111">Jeśli nie chcesz kompilatora, aby wyszukać i użyj ustawień w pliku csc.rsp, określ **/noconfig**.</span><span class="sxs-lookup"><span data-stu-id="a48ff-111">If you do not want the compiler to look for and use the settings in the csc.rsp file, specify **/noconfig**.</span></span>  
  
 <span data-ttu-id="a48ff-112">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="a48ff-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a48ff-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a48ff-113">See Also</span></span>  
 [<span data-ttu-id="a48ff-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a48ff-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="a48ff-115">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="a48ff-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
