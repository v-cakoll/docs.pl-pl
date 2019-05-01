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
ms.openlocfilehash: c086a031d5cef4563a6769e7683dcb1110b8fe49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788768"
---
# <a name="-removeintchecks"></a><span data-ttu-id="dd3fa-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="dd3fa-102">-removeintchecks</span></span>
<span data-ttu-id="dd3fa-103">Włącza sprawdzanie operacji liczby całkowitej lub wyłącz błąd przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd3fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd3fa-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="dd3fa-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dd3fa-105">Arguments</span></span>  
  
|<span data-ttu-id="dd3fa-106">Termin</span><span class="sxs-lookup"><span data-stu-id="dd3fa-106">Term</span></span>|<span data-ttu-id="dd3fa-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="dd3fa-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="dd3fa-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="dd3fa-108">`+` &#124; `-`</span></span>|<span data-ttu-id="dd3fa-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-109">Optional.</span></span> <span data-ttu-id="dd3fa-110">`-removeintchecks-` Opcja powoduje, że kompilator będzie sprawdzać wszystkich obliczeń na liczbach całkowitych błędy przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="dd3fa-111">Wartość domyślna to `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="dd3fa-112">Określanie `-removeintchecks` lub `-removeintchecks+` zapobiega, sprawdzanie błędów i może szybciej obliczeń na liczbach całkowitych.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="dd3fa-113">Jednak bez sprawdzania błędów, i jeśli są przepełnienie pojemności typu danych, bez zgłaszania błędu mogą być przechowywane niepoprawne wyniki.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="dd3fa-114">Aby ustawić - removeintchecks w programie Visual Studio zintegrowane środowisko projektowe</span><span class="sxs-lookup"><span data-stu-id="dd3fa-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="dd3fa-115">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="dd3fa-116">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="dd3fa-117">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="dd3fa-118">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="dd3fa-119">4.  Zmodyfikuj wartość **Usuń nadmiaru** pole.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dd3fa-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd3fa-120">Example</span></span>  
 <span data-ttu-id="dd3fa-121">Poniższy kod kompiluje `Test.vb` i wyłącza sprawdzanie błąd przepełnienia liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="dd3fa-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd3fa-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd3fa-122">See also</span></span>

- [<span data-ttu-id="dd3fa-123">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd3fa-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="dd3fa-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="dd3fa-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
