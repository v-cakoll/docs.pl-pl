---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: f9ca5575e2a042d68fc490494f2e86991d58b80c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351706"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="f204c-102">-warnaserror — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f204c-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="f204c-103">Powoduje, że kompilator traktuje pierwsze wystąpienie ostrzeżenia jako błąd.</span><span class="sxs-lookup"><span data-stu-id="f204c-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f204c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f204c-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f204c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f204c-105">Arguments</span></span>  
  
|<span data-ttu-id="f204c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="f204c-106">Term</span></span>|<span data-ttu-id="f204c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="f204c-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="f204c-108">+ &#124;-</span><span class="sxs-lookup"><span data-stu-id="f204c-108">+ &#124; -</span></span>|<span data-ttu-id="f204c-109">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f204c-109">Optional.</span></span> <span data-ttu-id="f204c-110">Domyślnie `-warnaserror-` obowiązuje; ostrzeżenia nie uniemożliwiają kompilatorowi tworzenia pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="f204c-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="f204c-111">`-warnaserror` Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="f204c-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="f204c-112">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f204c-112">Optional.</span></span> <span data-ttu-id="f204c-113">Rozdzielana przecinkami lista numerów IDENTYFIKACYJNych ostrzeżeń, do których zostanie `-warnaserror` zastosowana opcja.</span><span class="sxs-lookup"><span data-stu-id="f204c-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="f204c-114">Jeśli nie określono identyfikatora ostrzeżenia, `-warnaserror` opcja ma zastosowanie do wszystkich ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="f204c-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f204c-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f204c-115">Remarks</span></span>  
 <span data-ttu-id="f204c-116">`-warnaserror` Opcja traktuje wszystkie ostrzeżenia jako błędy.</span><span class="sxs-lookup"><span data-stu-id="f204c-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="f204c-117">Wszystkie komunikaty, które zwykle są raportowane jako ostrzeżenia, są raportowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="f204c-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="f204c-118">Kompilator raportuje kolejne wystąpienia tego samego ostrzeżenia co ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="f204c-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="f204c-119">Domyślnie `-warnaserror-` obowiązuje, co powoduje, że ostrzeżenia są tylko informacyjne.</span><span class="sxs-lookup"><span data-stu-id="f204c-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="f204c-120">`-warnaserror` Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="f204c-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="f204c-121">Jeśli chcesz, aby tylko kilka określonych ostrzeżeń była traktowana jak błędy, możesz określić rozdzieloną przecinkami listę numerów ostrzeżeń, które mają być traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="f204c-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f204c-122">`-warnaserror` Opcja nie kontroluje sposobu wyświetlania ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="f204c-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="f204c-123">Użyj opcji [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) , aby wyłączyć ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="f204c-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="f204c-124">Aby ustawić-warnaserror — wszystkie ostrzeżenia jako błędy w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f204c-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="f204c-125">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="f204c-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f204c-126">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f204c-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f204c-127">2. Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="f204c-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f204c-128">3. Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f204c-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="f204c-129">4. Zaznacz pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** .</span><span class="sxs-lookup"><span data-stu-id="f204c-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="f204c-130">Aby ustawić-warnaserror — do traktowania określonych ostrzeżeń jako błędów w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f204c-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="f204c-131">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="f204c-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f204c-132">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f204c-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="f204c-133">2. Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="f204c-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f204c-134">3. Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f204c-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="f204c-135">4. Upewnij się, że pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f204c-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="f204c-136">5. Wybierz **błąd** z kolumny **powiadomień** sąsiadującej z ostrzeżeniem, które ma być traktowane jako błąd.</span><span class="sxs-lookup"><span data-stu-id="f204c-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f204c-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="f204c-137">Example</span></span>  
 <span data-ttu-id="f204c-138">Poniższy kod kompiluje `In.vb` i kieruje kompilator w celu wyświetlenia błędu pierwszego wystąpienia każdego ostrzeżenia, które znajdzie.</span><span class="sxs-lookup"><span data-stu-id="f204c-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="f204c-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="f204c-139">Example</span></span>  
 <span data-ttu-id="f204c-140">Poniższy kod kompiluje `T2.vb` i traktuje tylko Ostrzeżenie dla nieużywanych zmiennych lokalnych (42024) jako błąd.</span><span class="sxs-lookup"><span data-stu-id="f204c-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f204c-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f204c-141">See also</span></span>

- [<span data-ttu-id="f204c-142">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f204c-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f204c-143">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="f204c-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="f204c-144">Konfigurowanie ostrzeżeń w kodzie Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f204c-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
