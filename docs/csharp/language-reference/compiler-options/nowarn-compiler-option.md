---
title: -nowarn (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 1c5e8bc7ad065c4662cd489930b2226e8a4b8962
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="3ca28-102">-nowarn (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="3ca28-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="3ca28-103">**- Nowarn** opcja pozwala pominąć kompilatora przy wyświetlaniu co najmniej jedno ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="3ca28-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="3ca28-104">Wiele numerów ostrzeżeń, które należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="3ca28-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ca28-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ca28-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3ca28-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3ca28-106">Arguments</span></span>  
 <span data-ttu-id="3ca28-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="3ca28-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="3ca28-108">Numery ostrzeżeń, które kompilator, aby pominąć.</span><span class="sxs-lookup"><span data-stu-id="3ca28-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ca28-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ca28-109">Remarks</span></span>  
 <span data-ttu-id="3ca28-110">Należy określić tylko numeryczna część identyfikatora ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="3ca28-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="3ca28-111">Na przykład, jeśli chcesz pominąć CS0028, można określić `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="3ca28-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="3ca28-112">Kompilator będzie dyskretne ignorowanie numerów ostrzeżeń, które przekazany do `-nowarn` , które były nieprawidłowe w poprzednich wersjach, ale zostały usunięte z kompilatora.</span><span class="sxs-lookup"><span data-stu-id="3ca28-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="3ca28-113">Na przykład CS0679 jest prawidłowe w kompilatorze w Visual Studio .NET 2002, ale później został usunięty.</span><span class="sxs-lookup"><span data-stu-id="3ca28-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="3ca28-114">Nie można pominąć następujące ostrzeżenia przez `-nowarn` opcji:</span><span class="sxs-lookup"><span data-stu-id="3ca28-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
-   <span data-ttu-id="3ca28-115">Kompilator CS2002 ostrzegawcze (poziom 1)</span><span class="sxs-lookup"><span data-stu-id="3ca28-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="3ca28-116">Kompilator CS2023 ostrzegawcze (poziom 1)</span><span class="sxs-lookup"><span data-stu-id="3ca28-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="3ca28-117">Kompilator CS2029 ostrzegawcze (poziom 1)</span><span class="sxs-lookup"><span data-stu-id="3ca28-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3ca28-118">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3ca28-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3ca28-119">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="3ca28-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="3ca28-120">Aby uzyskać więcej informacji, zobacz [strona kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="3ca28-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="3ca28-121">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="3ca28-121">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="3ca28-122">Modyfikowanie **pomijania ostrzeżeń** właściwości.</span><span class="sxs-lookup"><span data-stu-id="3ca28-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="3ca28-123">Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ca28-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca28-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ca28-124">See Also</span></span>  
 [<span data-ttu-id="3ca28-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="3ca28-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="3ca28-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="3ca28-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="3ca28-127">Błędy kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="3ca28-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
