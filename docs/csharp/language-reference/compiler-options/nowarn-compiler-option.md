---
title: -nowarn (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 499203bb4714fa2d07b2c0e42958ffd0e472facc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn-c-compiler-options"></a><span data-ttu-id="d2757-102">/nowarn (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d2757-102">/nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="d2757-103">**/Nowarn** opcja pozwala pominąć kompilatora przy wyświetlaniu co najmniej jedno ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="d2757-103">The **/nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="d2757-104">Wiele numerów ostrzeżeń, które należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="d2757-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2757-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2757-105">Syntax</span></span>  
  
```console  
/nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d2757-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d2757-106">Arguments</span></span>  
 <span data-ttu-id="d2757-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="d2757-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="d2757-108">Numery ostrzeżeń, które kompilator, aby pominąć.</span><span class="sxs-lookup"><span data-stu-id="d2757-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2757-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2757-109">Remarks</span></span>  
 <span data-ttu-id="d2757-110">Należy określić tylko numeryczna część identyfikatora ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="d2757-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="d2757-111">Na przykład, jeśli chcesz pominąć CS0028, można określić `/nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="d2757-111">For example, if you want to suppress CS0028, you could specify `/nowarn:28`.</span></span>  
  
 <span data-ttu-id="d2757-112">Kompilator będzie dyskretne ignorowanie numerów ostrzeżeń, które przekazany do `/nowarn` , które były nieprawidłowe w poprzednich wersjach, ale zostały usunięte z kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d2757-112">The compiler will silently ignore warning numbers passed to `/nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="d2757-113">Na przykład CS0679 jest prawidłowe w kompilatorze w Visual Studio .NET 2002, ale później został usunięty.</span><span class="sxs-lookup"><span data-stu-id="d2757-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="d2757-114">Nie można pominąć następujące ostrzeżenia przez `/nowarn` opcji:</span><span class="sxs-lookup"><span data-stu-id="d2757-114">The following warnings cannot be suppressed by the `/nowarn` option:</span></span>  
  
-   <span data-ttu-id="d2757-115">Kompilator CS2002 ostrzegawcze (poziom 1)</span><span class="sxs-lookup"><span data-stu-id="d2757-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="d2757-116">Kompilator CS2023 ostrzegawcze (poziom 1)</span><span class="sxs-lookup"><span data-stu-id="d2757-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="d2757-117">Kompilator CS2029 ostrzegawcze (poziom 1)</span><span class="sxs-lookup"><span data-stu-id="d2757-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d2757-118">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2757-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d2757-119">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="d2757-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="d2757-120">Aby uzyskać więcej informacji, zobacz [strona kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="d2757-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="d2757-121">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2757-121">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d2757-122">Modyfikowanie **pomijania ostrzeżeń** właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2757-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="d2757-123">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2757-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2757-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2757-124">See Also</span></span>  
 [<span data-ttu-id="d2757-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d2757-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="d2757-126">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="d2757-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="d2757-127">Błędy kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d2757-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
