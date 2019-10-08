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
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005230"
---
# <a name="-removeintchecks"></a><span data-ttu-id="d084a-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="d084a-102">-removeintchecks</span></span>
<span data-ttu-id="d084a-103">Włącza lub wyłącza przepełnienie — sprawdzanie błędów dla operacji całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d084a-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d084a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d084a-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d084a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d084a-105">Arguments</span></span>  
  
|<span data-ttu-id="d084a-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d084a-106">Term</span></span>|<span data-ttu-id="d084a-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d084a-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d084a-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d084a-108">`+` &#124; `-`</span></span>|<span data-ttu-id="d084a-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d084a-109">Optional.</span></span> <span data-ttu-id="d084a-110">Opcja `-removeintchecks-` powoduje, że kompilator sprawdza wszystkie obliczenia całkowite dla błędów przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="d084a-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="d084a-111">Wartość domyślna to `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="d084a-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="d084a-112">Określenie `-removeintchecks` lub `-removeintchecks+` zapobiega sprawdzaniu błędów i umożliwia szybsze Obliczanie liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d084a-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="d084a-113">Jednak bez sprawdzania błędów, a w przypadku przepełnienia zdolności do typów danych można przechowywać nieprawidłowe wyniki bez zgłaszania błędu.</span><span class="sxs-lookup"><span data-stu-id="d084a-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="d084a-114">Aby ustawić-removeintchecks w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d084a-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d084a-115">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d084a-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d084a-116">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d084a-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d084a-117">2. Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="d084a-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d084a-118">3. kliknij przycisk **Zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="d084a-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="d084a-119">4. Zmodyfikuj wartość pola **sprawdzania przepełnienia liczby całkowitej** .</span><span class="sxs-lookup"><span data-stu-id="d084a-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d084a-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="d084a-120">Example</span></span>  
 <span data-ttu-id="d084a-121">Poniższy kod kompiluje `Test.vb` i wyłącza przepełnienie liczby całkowitej — sprawdzanie błędów.</span><span class="sxs-lookup"><span data-stu-id="d084a-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d084a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d084a-122">See also</span></span>

- [<span data-ttu-id="d084a-123">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d084a-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d084a-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d084a-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
