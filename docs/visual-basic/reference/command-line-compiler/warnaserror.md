---
title: -warnaserror — (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 4382ec8feda2df1e83fd2fdc509abb66984e501f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937255"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="88409-102">-warnaserror — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88409-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="88409-103">Powoduje, że kompilator traktuje pierwsze wystąpienie ostrzeżenia jako błąd.</span><span class="sxs-lookup"><span data-stu-id="88409-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88409-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88409-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="88409-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="88409-105">Arguments</span></span>  
  
|<span data-ttu-id="88409-106">Termin</span><span class="sxs-lookup"><span data-stu-id="88409-106">Term</span></span>|<span data-ttu-id="88409-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="88409-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="88409-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="88409-108">+ &#124; -</span></span>|<span data-ttu-id="88409-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="88409-109">Optional.</span></span> <span data-ttu-id="88409-110">Domyślnie program `-warnaserror-` jest w efekcie. ostrzeżenia nie uniemożliwiają kompilatorowi tworzenia pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="88409-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="88409-111">Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy. `-warnaserror`</span><span class="sxs-lookup"><span data-stu-id="88409-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="88409-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="88409-112">Optional.</span></span> <span data-ttu-id="88409-113">Rozdzielana przecinkami lista numerów identyfikacyjnych ostrzeżeń, do których zostanie `-warnaserror` zastosowana opcja.</span><span class="sxs-lookup"><span data-stu-id="88409-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="88409-114">Jeśli nie określono identyfikatora ostrzeżenia, `-warnaserror` opcja ma zastosowanie do wszystkich ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="88409-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88409-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88409-115">Remarks</span></span>  
 <span data-ttu-id="88409-116">`-warnaserror` Opcja traktuje wszystkie ostrzeżenia jako błędy.</span><span class="sxs-lookup"><span data-stu-id="88409-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="88409-117">Wszystkie komunikaty, które zwykle są raportowane jako ostrzeżenia, są raportowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="88409-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="88409-118">Kompilator raportuje kolejne wystąpienia tego samego ostrzeżenia co ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="88409-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="88409-119">Domyślnie `-warnaserror-` obowiązuje, co powoduje, że ostrzeżenia są tylko informacyjne.</span><span class="sxs-lookup"><span data-stu-id="88409-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="88409-120">Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy. `-warnaserror`</span><span class="sxs-lookup"><span data-stu-id="88409-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="88409-121">Jeśli chcesz, aby tylko kilka określonych ostrzeżeń była traktowana jak błędy, możesz określić rozdzieloną przecinkami listę numerów ostrzeżeń, które mają być traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="88409-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88409-122">`-warnaserror` Opcja nie kontroluje sposobu wyświetlania ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="88409-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="88409-123">Użyj opcji [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) , aby wyłączyć ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="88409-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="88409-124">Aby ustawić-warnaserror — wszystkie ostrzeżenia jako błędy w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88409-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="88409-125">1.  Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="88409-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="88409-126">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="88409-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="88409-127">2.  Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="88409-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="88409-128">3.  Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="88409-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="88409-129">4.  Zaznacz pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** .</span><span class="sxs-lookup"><span data-stu-id="88409-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="88409-130">Aby ustawić-warnaserror — do traktowania określonych ostrzeżeń jako błędów w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88409-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="88409-131">1.  Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="88409-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="88409-132">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="88409-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="88409-133">2.  Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="88409-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="88409-134">3.  Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="88409-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="88409-135">4.  Upewnij się, że pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="88409-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="88409-136">5.  Wybierz **błąd** z kolumny **powiadomień** sąsiadującej z ostrzeżeniem, które ma być traktowane jako błąd.</span><span class="sxs-lookup"><span data-stu-id="88409-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="88409-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="88409-137">Example</span></span>  
 <span data-ttu-id="88409-138">Poniższy kod kompiluje `In.vb` i kieruje kompilator w celu wyświetlenia błędu pierwszego wystąpienia każdego ostrzeżenia, które znajdzie.</span><span class="sxs-lookup"><span data-stu-id="88409-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="88409-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="88409-139">Example</span></span>  
 <span data-ttu-id="88409-140">Poniższy kod kompiluje `T2.vb` i traktuje tylko Ostrzeżenie dla nieużywanych zmiennych lokalnych (42024) jako błąd.</span><span class="sxs-lookup"><span data-stu-id="88409-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="88409-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88409-141">See also</span></span>

- [<span data-ttu-id="88409-142">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88409-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="88409-143">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="88409-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="88409-144">Konfigurowanie ostrzeżeń w kodzie Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88409-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
