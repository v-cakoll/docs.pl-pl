---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 31f7a2b771cfa1bcc6581d720aa0de3505aec826
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828215"
---
# <a name="-nowarn"></a><span data-ttu-id="fb5e9-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="fb5e9-102">-nowarn</span></span>
<span data-ttu-id="fb5e9-103">Pomija zdolność kompilatora do generowania ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb5e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb5e9-104">Syntax</span></span>  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb5e9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fb5e9-105">Arguments</span></span>  
  
|<span data-ttu-id="fb5e9-106">Termin</span><span class="sxs-lookup"><span data-stu-id="fb5e9-106">Term</span></span>|<span data-ttu-id="fb5e9-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="fb5e9-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="fb5e9-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-108">Optional.</span></span> <span data-ttu-id="fb5e9-109">Rozdzielana przecinkami lista numerów Identyfikacyjnych ostrzeżenia, które kompilator powinien pominąć.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="fb5e9-110">Jeśli nie określono ostrzeżenie identyfikatorów, wszystkie ostrzeżenia są pomijane.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb5e9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb5e9-111">Remarks</span></span>  
 <span data-ttu-id="fb5e9-112">`-nowarn` Opcji powoduje, że kompilator generuje ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="fb5e9-113">Aby pominąć to ostrzeżenie indywidualnych, należy podać identyfikator ostrzeżenie do `-nowarn` opcji zgodnie z dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="fb5e9-114">Oddziel wiele numerów ostrzeżeń przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="fb5e9-115">Należy określić tylko część numeryczna identyfikatora ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="fb5e9-116">Na przykład, jeśli chcesz pominąć BC42024, ostrzeżenie dotyczące nieużywane zmienne lokalne, określ `-nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="fb5e9-117">Aby uzyskać więcej informacji na temat identyfikatorów ostrzeżenie, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fb5e9-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="fb5e9-118">Aby ustawić - nowarn — w programie Visual Studio zintegrowane środowisko projektowe</span><span class="sxs-lookup"><span data-stu-id="fb5e9-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="fb5e9-119">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fb5e9-120">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fb5e9-121">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="fb5e9-122">3.  Wybierz **Wyłącz wszystkie ostrzeżenia** pole wyboru, aby wyłączyć wszystkie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="fb5e9-123">- lub -</span><span class="sxs-lookup"><span data-stu-id="fb5e9-123">- or -</span></span><br />     <span data-ttu-id="fb5e9-124">Aby wyłączyć określonego ostrzeżenia, kliknij pozycję **Brak** z listy rozwijanej obok ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fb5e9-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb5e9-125">Example</span></span>  
 <span data-ttu-id="fb5e9-126">Poniższy kod kompiluje `T2.vb` i nie zawiera żadnych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="fb5e9-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="fb5e9-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb5e9-127">Example</span></span>  
 <span data-ttu-id="fb5e9-128">Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia dotyczące nieużywane zmienne lokalne (42024).</span><span class="sxs-lookup"><span data-stu-id="fb5e9-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb5e9-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb5e9-129">See also</span></span>

- [<span data-ttu-id="fb5e9-130">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb5e9-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fb5e9-131">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="fb5e9-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="fb5e9-132">Konfigurowanie ostrzeżeń w kodzie Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb5e9-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
