---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 37851f99eb88543e939ce48995ded41958e57cc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397491"
---
# <a name="-nowarn"></a><span data-ttu-id="631da-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="631da-102">-nowarn</span></span>
<span data-ttu-id="631da-103">Pomija możliwość generowania ostrzeżeń przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="631da-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="631da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="631da-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="631da-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="631da-105">Arguments</span></span>  
  
|<span data-ttu-id="631da-106">Termin</span><span class="sxs-lookup"><span data-stu-id="631da-106">Term</span></span>|<span data-ttu-id="631da-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="631da-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="631da-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="631da-108">Optional.</span></span> <span data-ttu-id="631da-109">Rozdzielana przecinkami lista numerów IDENTYFIKACYJNych ostrzeżeń, które kompilator powinien pominąć.</span><span class="sxs-lookup"><span data-stu-id="631da-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="631da-110">Jeśli nie określono identyfikatorów ostrzeżeń, wszystkie ostrzeżenia są pomijane.</span><span class="sxs-lookup"><span data-stu-id="631da-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="631da-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="631da-111">Remarks</span></span>  
 <span data-ttu-id="631da-112">`-nowarn`Opcja powoduje, że kompilator nie generuje ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="631da-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="631da-113">Aby pominąć pojedyncze ostrzeżenie, należy podać identyfikator ostrzeżenia dla `-nowarn` opcji po dwukropku.</span><span class="sxs-lookup"><span data-stu-id="631da-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="631da-114">Oddziel wiele numerów ostrzeżeń przecinkami.</span><span class="sxs-lookup"><span data-stu-id="631da-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="631da-115">Należy określić tylko część liczbową identyfikatora ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="631da-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="631da-116">Na przykład jeśli chcesz pominąć BC42024, Ostrzeżenie dla nieużywanych zmiennych lokalnych, określ `-nowarn:42024` .</span><span class="sxs-lookup"><span data-stu-id="631da-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="631da-117">Aby uzyskać więcej informacji na temat numerów IDENTYFIKACYJNych ostrzeżeń, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="631da-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="631da-118">Aby ustawić-nowarn w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="631da-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="631da-119">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="631da-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="631da-120">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="631da-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="631da-121">2. Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="631da-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="631da-122">3. Zaznacz pole wyboru **Wyłącz wszystkie ostrzeżenia** , aby wyłączyć wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="631da-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="631da-123">— lub —</span><span class="sxs-lookup"><span data-stu-id="631da-123">- or -</span></span><br />     <span data-ttu-id="631da-124">Aby wyłączyć określone ostrzeżenie, kliknij **Brak** z listy rozwijanej obok ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="631da-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="631da-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="631da-125">Example</span></span>  
 <span data-ttu-id="631da-126">Poniższy kod kompiluje `T2.vb` i nie wyświetla żadnych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="631da-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="631da-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="631da-127">Example</span></span>  
 <span data-ttu-id="631da-128">Poniższy kod kompiluje `T2.vb` i nie wyświetla ostrzeżeń dotyczących nieużywanych zmiennych lokalnych (42024).</span><span class="sxs-lookup"><span data-stu-id="631da-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="631da-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="631da-129">See also</span></span>

- [<span data-ttu-id="631da-130">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="631da-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="631da-131">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="631da-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="631da-132">Konfigurowanie ostrzeżeń w kodzie Visual Basic</span><span class="sxs-lookup"><span data-stu-id="631da-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
