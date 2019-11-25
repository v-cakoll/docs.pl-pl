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
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="d8cf1-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8cf1-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="d8cf1-103">Causes the compiler to treat the first occurrence of a warning as an error.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8cf1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8cf1-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d8cf1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d8cf1-105">Arguments</span></span>  
  
|<span data-ttu-id="d8cf1-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d8cf1-106">Term</span></span>|<span data-ttu-id="d8cf1-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d8cf1-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d8cf1-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="d8cf1-108">+ &#124; -</span></span>|<span data-ttu-id="d8cf1-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-109">Optional.</span></span> <span data-ttu-id="d8cf1-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="d8cf1-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="d8cf1-112">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-112">Optional.</span></span> <span data-ttu-id="d8cf1-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="d8cf1-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8cf1-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8cf1-115">Remarks</span></span>  
 <span data-ttu-id="d8cf1-116">The `-warnaserror` option treats all warnings as errors.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="d8cf1-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="d8cf1-118">The compiler reports subsequent occurrences of the same warning as warnings.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="d8cf1-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="d8cf1-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="d8cf1-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8cf1-122">The `-warnaserror` option does not control how warnings are displayed.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="d8cf1-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="d8cf1-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="d8cf1-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d8cf1-125">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d8cf1-126">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d8cf1-127">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d8cf1-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d8cf1-129">4.  Check the **Treat all warnings as errors** check box.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="d8cf1-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="d8cf1-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d8cf1-131">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d8cf1-132">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="d8cf1-133">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d8cf1-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d8cf1-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="d8cf1-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d8cf1-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8cf1-137">Example</span></span>  
 <span data-ttu-id="d8cf1-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="d8cf1-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8cf1-139">Example</span></span>  
 <span data-ttu-id="d8cf1-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span><span class="sxs-lookup"><span data-stu-id="d8cf1-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8cf1-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8cf1-141">See also</span></span>

- [<span data-ttu-id="d8cf1-142">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="d8cf1-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d8cf1-143">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d8cf1-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="d8cf1-144">Konfigurowanie ostrzeżeń w kodzie Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8cf1-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
