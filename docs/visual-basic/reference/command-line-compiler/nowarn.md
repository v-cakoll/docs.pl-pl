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
ms.openlocfilehash: d1eafe8d7ccd6f2c71b754dadc343518948e7146
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nowarn"></a><span data-ttu-id="8ed17-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="8ed17-102">/nowarn</span></span>
<span data-ttu-id="8ed17-103">Pomija możliwość generowania ostrzeżeń kompilatora.</span><span class="sxs-lookup"><span data-stu-id="8ed17-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ed17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ed17-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8ed17-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8ed17-105">Arguments</span></span>  
  
|<span data-ttu-id="8ed17-106">Termin</span><span class="sxs-lookup"><span data-stu-id="8ed17-106">Term</span></span>|<span data-ttu-id="8ed17-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="8ed17-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="8ed17-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8ed17-108">Optional.</span></span> <span data-ttu-id="8ed17-109">Rozdzielana przecinkami lista identyfikatorów ostrzeżenia kompilatora ma pomijać.</span><span class="sxs-lookup"><span data-stu-id="8ed17-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="8ed17-110">Jeśli ostrzeżenie identyfikatory nie są określone, wszystkie ostrzeżenia będą pomijane.</span><span class="sxs-lookup"><span data-stu-id="8ed17-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ed17-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ed17-111">Remarks</span></span>  
 <span data-ttu-id="8ed17-112">`/nowarn` Opcja powoduje, że kompilator, aby nie generować ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="8ed17-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="8ed17-113">Aby pominąć poszczególnych ostrzeżenie, należy podać identyfikator ostrzeżenia, aby `/nowarn` opcji po dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="8ed17-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="8ed17-114">Wiele numerów ostrzeżeń, które należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="8ed17-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="8ed17-115">Należy określić numeryczna część identyfikatora ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="8ed17-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="8ed17-116">Na przykład, jeśli chcesz pominąć BC42024, ostrzeżenie dotyczące nieużywane zmienne lokalne, określ `/nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="8ed17-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="8ed17-117">Aby uzyskać więcej informacji na numery identyfikatorów ostrzeżenia, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8ed17-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="8ed17-118">Aby ustawić/nowarn w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="8ed17-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8ed17-119">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="8ed17-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8ed17-120">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="8ed17-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8ed17-121">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="8ed17-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="8ed17-122">3.  Wybierz **Wyłącz wszystkie ostrzeżenia** pole wyboru, aby wyłączyć wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="8ed17-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="8ed17-123">- lub -</span><span class="sxs-lookup"><span data-stu-id="8ed17-123">- or -</span></span><br />     <span data-ttu-id="8ed17-124">Aby wyłączyć ostrzeżenie, kliknij przycisk **Brak** z listy rozwijanej obok ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="8ed17-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8ed17-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ed17-125">Example</span></span>  
 <span data-ttu-id="8ed17-126">Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="8ed17-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="8ed17-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ed17-127">Example</span></span>  
 <span data-ttu-id="8ed17-128">Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia dotyczące nieużywane zmienne lokalne (42024).</span><span class="sxs-lookup"><span data-stu-id="8ed17-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ed17-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ed17-129">See Also</span></span>  
 [<span data-ttu-id="8ed17-130">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ed17-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8ed17-131">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="8ed17-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="8ed17-132">Konfigurowanie ostrzeżeń w kodzie Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ed17-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
