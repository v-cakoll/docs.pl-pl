---
title: -Definiuj (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 5b2c0173416418f67446c5441a93e5b06e93dc12
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002371"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="af4fe-102">-Definiuj (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af4fe-102">-define (Visual Basic)</span></span>
<span data-ttu-id="af4fe-103">Definiuje warunkowe stałe kompilatora.</span><span class="sxs-lookup"><span data-stu-id="af4fe-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af4fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af4fe-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="af4fe-105">lub</span><span class="sxs-lookup"><span data-stu-id="af4fe-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="af4fe-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="af4fe-106">Arguments</span></span>  
  
|<span data-ttu-id="af4fe-107">Termin</span><span class="sxs-lookup"><span data-stu-id="af4fe-107">Term</span></span>|<span data-ttu-id="af4fe-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="af4fe-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="af4fe-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="af4fe-109">Required.</span></span> <span data-ttu-id="af4fe-110">Symbol do zdefiniowania.</span><span class="sxs-lookup"><span data-stu-id="af4fe-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="af4fe-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="af4fe-111">Optional.</span></span> <span data-ttu-id="af4fe-112">Wartość, która ma zostać przypisana `symbol`.</span><span class="sxs-lookup"><span data-stu-id="af4fe-112">The value to assign `symbol`.</span></span> <span data-ttu-id="af4fe-113">Jeśli `value` jest ciągiem, musi być ujęty w nawiasy odwrotne/sekwencje znaku cudzysłowu (\\ ") zamiast znaków cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="af4fe-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="af4fe-114">Jeśli żadna wartość nie zostanie określona, jest ona prawdziwa.</span><span class="sxs-lookup"><span data-stu-id="af4fe-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af4fe-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af4fe-115">Remarks</span></span>  
 <span data-ttu-id="af4fe-116">Opcja `-define` ma podobny efekt jak użycie dyrektywy preprocesora `#Const` w pliku źródłowym, z tą różnicą, że stałe zdefiniowane za pomocą `-define` są publiczne i stosowane do wszystkich plików w projekcie.</span><span class="sxs-lookup"><span data-stu-id="af4fe-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="af4fe-117">Możesz użyć symboli utworzonych przez tę opcję z dyrektywą `#If`... `Then`... `#Else`, aby warunkowo kompilować pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="af4fe-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="af4fe-118">`-d` jest krótką formą `-define`.</span><span class="sxs-lookup"><span data-stu-id="af4fe-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="af4fe-119">Można zdefiniować wiele symboli z `-define`, używając przecinka do oddzielania definicji symboli.</span><span class="sxs-lookup"><span data-stu-id="af4fe-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="af4fe-120">Aby ustawić/define w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="af4fe-120">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="af4fe-121">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="af4fe-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="af4fe-122">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="af4fe-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="af4fe-123">2. Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="af4fe-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="af4fe-124">3. kliknij pozycję **Zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="af4fe-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="af4fe-125">4. Zmodyfikuj wartość w polu **stałe niestandardowe** .</span><span class="sxs-lookup"><span data-stu-id="af4fe-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af4fe-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="af4fe-126">Example</span></span>  
 <span data-ttu-id="af4fe-127">Poniższy kod definiuje, a następnie używa dwóch warunkowych stałych kompilatora.</span><span class="sxs-lookup"><span data-stu-id="af4fe-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="af4fe-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af4fe-128">See also</span></span>

- [<span data-ttu-id="af4fe-129">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af4fe-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="af4fe-130">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="af4fe-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="af4fe-131">#Const, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="af4fe-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="af4fe-132">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="af4fe-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
