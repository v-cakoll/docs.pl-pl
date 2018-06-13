---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c04bff4070b0f1c288c8853e5045fbf670d8e9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655672"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="fa35d-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa35d-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="fa35d-103">Umożliwia kompilatorowi na traktowanie pierwszego wystąpienia ostrzeżenie jako błąd.</span><span class="sxs-lookup"><span data-stu-id="fa35d-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa35d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa35d-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa35d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fa35d-105">Arguments</span></span>  
  
|<span data-ttu-id="fa35d-106">Termin</span><span class="sxs-lookup"><span data-stu-id="fa35d-106">Term</span></span>|<span data-ttu-id="fa35d-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="fa35d-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="fa35d-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="fa35d-108">+ &#124; -</span></span>|<span data-ttu-id="fa35d-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="fa35d-109">Optional.</span></span> <span data-ttu-id="fa35d-110">Domyślnie `-warnaserror-` jest obowiązująca; ostrzeżenia nie uniemożliwiają kompilator Tworzenie pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="fa35d-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="fa35d-111">`-warnaserror` Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia, które będą traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="fa35d-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="fa35d-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="fa35d-112">Optional.</span></span> <span data-ttu-id="fa35d-113">Rozdzielana przecinkami lista Identyfikator ostrzeżenia numery, do którego `-warnaserror` opcja ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="fa35d-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="fa35d-114">Jeśli nie ostrzeżenie określono Identyfikatora, `-warnaserror` opcja ma zastosowanie do wszystkich ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="fa35d-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa35d-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa35d-115">Remarks</span></span>  
 <span data-ttu-id="fa35d-116">`-warnaserror` Opcja traktuje wszystkie ostrzeżenia jako błędy.</span><span class="sxs-lookup"><span data-stu-id="fa35d-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="fa35d-117">Komunikaty, które będą zgłaszane zwykle są natomiast zgłoszonej ostrzeżenia jako błędy.</span><span class="sxs-lookup"><span data-stu-id="fa35d-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="fa35d-118">Kompilator zgłasza kolejne wystąpienia tej samej ostrzeżenie jako ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="fa35d-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="fa35d-119">Domyślnie `-warnaserror-` obowiązują, co powoduje, że ostrzeżenia informacyjne tylko do.</span><span class="sxs-lookup"><span data-stu-id="fa35d-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="fa35d-120">`-warnaserror` Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia, które będą traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="fa35d-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="fa35d-121">Jeśli chcesz tylko kilka konkretne ostrzeżenia, które będą traktowane jako błędy, można określić rozdzielana przecinkami lista numerów ostrzeżeń, które mają być traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="fa35d-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa35d-122">`-warnaserror` Opcji nie kontroluje sposób wyświetlania ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="fa35d-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="fa35d-123">Użyj [- nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) opcję, aby wyłączyć ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="fa35d-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="fa35d-124">Aby ustawić - warnaserror traktuje wszystkie ostrzeżenia jako błędy w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa35d-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="fa35d-125">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="fa35d-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fa35d-126">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fa35d-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fa35d-127">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="fa35d-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="fa35d-128">3.  Upewnij się, że **Wyłącz wszystkie ostrzeżenia** pole wyboru jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="fa35d-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="fa35d-129">4.  Sprawdź **traktuje wszystkie ostrzeżenia jako błędy** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="fa35d-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="fa35d-130">Aby ustawić - warnaserror Traktuj konkretne ostrzeżenia jako błędy w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa35d-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="fa35d-131">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="fa35d-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fa35d-132">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fa35d-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="fa35d-133">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="fa35d-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="fa35d-134">3.  Upewnij się, że **Wyłącz wszystkie ostrzeżenia** pole wyboru jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="fa35d-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="fa35d-135">4.  Upewnij się, że **traktuje wszystkie ostrzeżenia jako błędy** pole wyboru jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="fa35d-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="fa35d-136">5.  Wybierz **błąd** z **powiadomień** kolumny sąsiadujące ostrzeżenia, które powinny być traktowane jako błąd.</span><span class="sxs-lookup"><span data-stu-id="fa35d-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fa35d-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa35d-137">Example</span></span>  
 <span data-ttu-id="fa35d-138">Poniższy kod kompiluje `In.vb` i kieruje kompilator, aby wyświetlić błąd dla pierwszego wystąpienia każdego ostrzeżenia znajdzie.</span><span class="sxs-lookup"><span data-stu-id="fa35d-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="fa35d-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa35d-139">Example</span></span>  
 <span data-ttu-id="fa35d-140">Poniższy kod kompiluje `T2.vb` i traktuje ostrzeżenia dla nieużywane zmienne lokalne (42024) jako błąd.</span><span class="sxs-lookup"><span data-stu-id="fa35d-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa35d-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa35d-141">See Also</span></span>  
 [<span data-ttu-id="fa35d-142">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa35d-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="fa35d-143">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="fa35d-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="fa35d-144">Konfigurowanie ostrzeżeń w kodzie Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa35d-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
