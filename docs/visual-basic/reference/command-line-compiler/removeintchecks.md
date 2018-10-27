---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: f061497083dc23fd07f61108938a4129c0af5f3a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188541"
---
# <a name="-removeintchecks"></a><span data-ttu-id="d75f0-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="d75f0-102">-removeintchecks</span></span>
<span data-ttu-id="d75f0-103">Włącza sprawdzanie operacji liczby całkowitej lub wyłącz błąd przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="d75f0-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d75f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d75f0-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d75f0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d75f0-105">Arguments</span></span>  
  
|<span data-ttu-id="d75f0-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d75f0-106">Term</span></span>|<span data-ttu-id="d75f0-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d75f0-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d75f0-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d75f0-108">`+` &#124; `-`</span></span>|<span data-ttu-id="d75f0-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d75f0-109">Optional.</span></span> <span data-ttu-id="d75f0-110">`-removeintchecks-` Opcja powoduje, że kompilator będzie sprawdzać wszystkich obliczeń na liczbach całkowitych błędy przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="d75f0-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="d75f0-111">Wartość domyślna to `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="d75f0-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="d75f0-112">Określanie `-removeintchecks` lub `-removeintchecks+` zapobiega, sprawdzanie błędów i może szybciej obliczeń na liczbach całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d75f0-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="d75f0-113">Jednak bez sprawdzania błędów, i jeśli są przepełnienie pojemności typu danych, bez zgłaszania błędu mogą być przechowywane niepoprawne wyniki.</span><span class="sxs-lookup"><span data-stu-id="d75f0-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="d75f0-114">Aby ustawić - removeintchecks w programie Visual Studio zintegrowane środowisko projektowe</span><span class="sxs-lookup"><span data-stu-id="d75f0-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d75f0-115">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d75f0-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d75f0-116">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d75f0-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d75f0-117">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="d75f0-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d75f0-118">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d75f0-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="d75f0-119">4.  Zmodyfikuj wartość **Usuń nadmiaru** pole.</span><span class="sxs-lookup"><span data-stu-id="d75f0-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d75f0-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="d75f0-120">Example</span></span>  
 <span data-ttu-id="d75f0-121">Poniższy kod kompiluje `Test.vb` i wyłącza sprawdzanie błąd przepełnienia liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="d75f0-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d75f0-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d75f0-122">See Also</span></span>  
 [<span data-ttu-id="d75f0-123">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d75f0-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d75f0-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d75f0-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
