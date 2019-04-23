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
ms.openlocfilehash: 13bb50366d9c19751ef3387baf809ab69e27b5dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324152"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="70b7c-102">-nowarn (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="70b7c-102">-nowarn (C# Compiler Options)</span></span>
<span data-ttu-id="70b7c-103">**- Nowarn** opcja umożliwia pomijanie kompilatora wyświetlanie co najmniej jedno ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="70b7c-103">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="70b7c-104">Oddziel wiele numerów ostrzeżeń przecinkami.</span><span class="sxs-lookup"><span data-stu-id="70b7c-104">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70b7c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="70b7c-105">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="70b7c-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="70b7c-106">Arguments</span></span>  
 <span data-ttu-id="70b7c-107">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="70b7c-107">`number1`, `number2`</span></span>  
 <span data-ttu-id="70b7c-108">Numery ostrzeżeń, które kompilator, aby pominąć.</span><span class="sxs-lookup"><span data-stu-id="70b7c-108">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70b7c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70b7c-109">Remarks</span></span>  
 <span data-ttu-id="70b7c-110">Należy określić tylko część numeryczna identyfikatora ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="70b7c-110">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="70b7c-111">Na przykład, jeśli chcesz pominąć CS0028, można określić `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="70b7c-111">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="70b7c-112">Kompilator będzie po cichu ignorować numery ostrzeżeń, przekazana do `-nowarn` , które były prawidłowe w poprzednich wersjach, ale zostały usunięte z kompilatora.</span><span class="sxs-lookup"><span data-stu-id="70b7c-112">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="70b7c-113">Na przykład CS0679 jest prawidłowe w kompilator programu Visual Studio .NET 2002, ale później został usunięty.</span><span class="sxs-lookup"><span data-stu-id="70b7c-113">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="70b7c-114">Następujące ostrzeżenia nie może być pominięty przy `-nowarn` opcji:</span><span class="sxs-lookup"><span data-stu-id="70b7c-114">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
-   <span data-ttu-id="70b7c-115">Kompilatora (poziom 1) ostrzeżenie CS2002</span><span class="sxs-lookup"><span data-stu-id="70b7c-115">Compiler Warning (level 1) CS2002</span></span>  
  
-   <span data-ttu-id="70b7c-116">Kompilatora (poziom 1) ostrzeżenie CS2023</span><span class="sxs-lookup"><span data-stu-id="70b7c-116">Compiler Warning (level 1) CS2023</span></span>  
  
-   <span data-ttu-id="70b7c-117">Kompilatora (poziom 1) ostrzeżenie CS2029</span><span class="sxs-lookup"><span data-stu-id="70b7c-117">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="70b7c-118">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="70b7c-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="70b7c-119">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="70b7c-119">Open the **Properties** page for the project.</span></span> <span data-ttu-id="70b7c-120">Aby uzyskać więcej informacji, zobacz [Stroka kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="70b7c-120">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="70b7c-121">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="70b7c-121">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="70b7c-122">Modyfikowanie **Pomiń ostrzeżenia** właściwości.</span><span class="sxs-lookup"><span data-stu-id="70b7c-122">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="70b7c-123">Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="70b7c-123">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b7c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70b7c-124">See also</span></span>

- [<span data-ttu-id="70b7c-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="70b7c-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="70b7c-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="70b7c-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="70b7c-127">Błędy kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="70b7c-127">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
