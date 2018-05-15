---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 338b4672d215968275c30d37a2f8061e764aed8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-nowarn"></a><span data-ttu-id="28f5d-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="28f5d-102">-nowarn</span></span>
<span data-ttu-id="28f5d-103">Pomija możliwość generowania ostrzeżeń kompilatora.</span><span class="sxs-lookup"><span data-stu-id="28f5d-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28f5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28f5d-104">Syntax</span></span>  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="28f5d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="28f5d-105">Arguments</span></span>  
  
|<span data-ttu-id="28f5d-106">Termin</span><span class="sxs-lookup"><span data-stu-id="28f5d-106">Term</span></span>|<span data-ttu-id="28f5d-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="28f5d-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="28f5d-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="28f5d-108">Optional.</span></span> <span data-ttu-id="28f5d-109">Rozdzielana przecinkami lista identyfikatorów ostrzeżenia kompilatora ma pomijać.</span><span class="sxs-lookup"><span data-stu-id="28f5d-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="28f5d-110">Jeśli ostrzeżenie identyfikatory nie są określone, wszystkie ostrzeżenia będą pomijane.</span><span class="sxs-lookup"><span data-stu-id="28f5d-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28f5d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28f5d-111">Remarks</span></span>  
 <span data-ttu-id="28f5d-112">`-nowarn` Opcja powoduje, że kompilator, aby nie generować ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="28f5d-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="28f5d-113">Aby pominąć poszczególnych ostrzeżenie, należy podać identyfikator ostrzeżenia, aby `-nowarn` opcji po dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="28f5d-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="28f5d-114">Wiele numerów ostrzeżeń, które należy oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="28f5d-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="28f5d-115">Należy określić numeryczna część identyfikatora ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="28f5d-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="28f5d-116">Na przykład, jeśli chcesz pominąć BC42024, ostrzeżenie dotyczące nieużywane zmienne lokalne, określ `-nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="28f5d-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="28f5d-117">Aby uzyskać więcej informacji na numery identyfikatorów ostrzeżenia, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="28f5d-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="28f5d-118">Aby ustawić - nowarn w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="28f5d-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="28f5d-119">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="28f5d-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="28f5d-120">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="28f5d-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="28f5d-121">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="28f5d-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="28f5d-122">3.  Wybierz **Wyłącz wszystkie ostrzeżenia** pole wyboru, aby wyłączyć wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="28f5d-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="28f5d-123">- lub -</span><span class="sxs-lookup"><span data-stu-id="28f5d-123">- or -</span></span><br />     <span data-ttu-id="28f5d-124">Aby wyłączyć ostrzeżenie, kliknij przycisk **Brak** z listy rozwijanej obok ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="28f5d-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="28f5d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="28f5d-125">Example</span></span>  
 <span data-ttu-id="28f5d-126">Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="28f5d-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="28f5d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="28f5d-127">Example</span></span>  
 <span data-ttu-id="28f5d-128">Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia dotyczące nieużywane zmienne lokalne (42024).</span><span class="sxs-lookup"><span data-stu-id="28f5d-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="28f5d-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28f5d-129">See Also</span></span>  
 [<span data-ttu-id="28f5d-130">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28f5d-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="28f5d-131">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="28f5d-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="28f5d-132">Konfigurowanie ostrzeżeń w kodzie Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28f5d-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
