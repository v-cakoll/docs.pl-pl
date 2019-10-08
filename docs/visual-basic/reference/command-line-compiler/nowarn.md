---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 880fdf4931dadea547d64d0506bd3e978956468e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005402"
---
# <a name="-nowarn"></a><span data-ttu-id="ff313-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="ff313-102">-nowarn</span></span>
<span data-ttu-id="ff313-103">Pomija możliwość generowania ostrzeżeń przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="ff313-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff313-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff313-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff313-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ff313-105">Arguments</span></span>  
  
|<span data-ttu-id="ff313-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ff313-106">Term</span></span>|<span data-ttu-id="ff313-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ff313-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="ff313-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ff313-108">Optional.</span></span> <span data-ttu-id="ff313-109">Rozdzielana przecinkami lista numerów IDENTYFIKACYJNych ostrzeżeń, które kompilator powinien pominąć.</span><span class="sxs-lookup"><span data-stu-id="ff313-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="ff313-110">Jeśli nie określono identyfikatorów ostrzeżeń, wszystkie ostrzeżenia są pomijane.</span><span class="sxs-lookup"><span data-stu-id="ff313-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff313-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff313-111">Remarks</span></span>  
 <span data-ttu-id="ff313-112">Opcja `-nowarn` powoduje, że kompilator nie generuje ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="ff313-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="ff313-113">Aby pominąć pojedyncze ostrzeżenie, należy podać identyfikator ostrzeżenia dla opcji `-nowarn` po dwukropku.</span><span class="sxs-lookup"><span data-stu-id="ff313-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="ff313-114">Oddziel wiele numerów ostrzeżeń przecinkami.</span><span class="sxs-lookup"><span data-stu-id="ff313-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="ff313-115">Należy określić tylko część liczbową identyfikatora ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="ff313-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="ff313-116">Na przykład jeśli chcesz pominąć BC42024, Ostrzeżenie dla nieużywanych zmiennych lokalnych, określ `-nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="ff313-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="ff313-117">Aby uzyskać więcej informacji na temat numerów IDENTYFIKACYJNych ostrzeżeń, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ff313-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="ff313-118">Aby ustawić-nowarn w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ff313-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ff313-119">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="ff313-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ff313-120">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ff313-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ff313-121">2. Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="ff313-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="ff313-122">3. Zaznacz pole wyboru **Wyłącz wszystkie ostrzeżenia** , aby wyłączyć wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="ff313-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="ff313-123">oraz</span><span class="sxs-lookup"><span data-stu-id="ff313-123">- or -</span></span><br />     <span data-ttu-id="ff313-124">Aby wyłączyć określone ostrzeżenie, kliknij **Brak** z listy rozwijanej obok ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="ff313-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ff313-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff313-125">Example</span></span>  
 <span data-ttu-id="ff313-126">Poniższy kod kompiluje `T2.vb` i nie wyświetla żadnych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="ff313-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="ff313-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff313-127">Example</span></span>  
 <span data-ttu-id="ff313-128">Poniższy kod kompiluje `T2.vb` i nie wyświetla ostrzeżeń dla nieużywanych zmiennych lokalnych (42024).</span><span class="sxs-lookup"><span data-stu-id="ff313-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff313-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff313-129">See also</span></span>

- [<span data-ttu-id="ff313-130">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff313-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ff313-131">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ff313-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="ff313-132">Konfigurowanie ostrzeżeń w kodzie Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff313-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
