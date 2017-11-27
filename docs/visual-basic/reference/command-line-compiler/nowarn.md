---
title: /nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8da27ea2f9f0a4d370928d70cda1a796b822d97c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn"></a><span data-ttu-id="1fc5a-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="1fc5a-102">/nowarn</span></span>
<span data-ttu-id="1fc5a-103">Pomija możliwość generowania ostrzeżeń kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fc5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fc5a-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1fc5a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1fc5a-105">Arguments</span></span>  
  
|<span data-ttu-id="1fc5a-106">Termin</span><span class="sxs-lookup"><span data-stu-id="1fc5a-106">Term</span></span>|<span data-ttu-id="1fc5a-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="1fc5a-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="1fc5a-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-108">Optional.</span></span> <span data-ttu-id="1fc5a-109">Rozdzielana przecinkami lista identyfikatorów ostrzeżenia kompilatora ma pomijać.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="1fc5a-110">Jeśli ostrzeżenie identyfikatory nie są określone, wszystkie ostrzeżenia będą pomijane.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fc5a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fc5a-111">Remarks</span></span>  
 <span data-ttu-id="1fc5a-112">`/nowarn` Opcja powoduje, że kompilator, aby nie generować ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="1fc5a-113">Aby pominąć poszczególnych ostrzeżenie, należy podać identyfikator ostrzeżenia, aby `/nowarn` opcji po dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="1fc5a-114">Wiele numerów ostrzeżeń, które należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="1fc5a-115">Należy określić numeryczna część identyfikatora ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="1fc5a-116">Na przykład, jeśli chcesz pominąć BC42024, ostrzeżenie dotyczące nieużywane zmienne lokalne, określ `/nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="1fc5a-117">Aby uzyskać więcej informacji na numery identyfikatorów ostrzeżenia, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1fc5a-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="1fc5a-118">Aby ustawić/nowarn w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="1fc5a-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1fc5a-119">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1fc5a-120">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="1fc5a-121">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="1fc5a-121">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="1fc5a-122">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1fc5a-123">3.  Wybierz **Wyłącz wszystkie ostrzeżenia** pole wyboru, aby wyłączyć wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="1fc5a-124">- lub -</span><span class="sxs-lookup"><span data-stu-id="1fc5a-124">- or -</span></span><br />     <span data-ttu-id="1fc5a-125">Aby wyłączyć ostrzeżenie, kliknij przycisk **Brak** z listy rozwijanej obok ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1fc5a-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fc5a-126">Example</span></span>  
 <span data-ttu-id="1fc5a-127">Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="1fc5a-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="1fc5a-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fc5a-128">Example</span></span>  
 <span data-ttu-id="1fc5a-129">Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia dotyczące nieużywane zmienne lokalne (42024).</span><span class="sxs-lookup"><span data-stu-id="1fc5a-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fc5a-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1fc5a-130">See Also</span></span>  
 [<span data-ttu-id="1fc5a-131">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fc5a-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1fc5a-132">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="1fc5a-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="1fc5a-133">Konfigurowanie ostrzeżeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fc5a-133">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
