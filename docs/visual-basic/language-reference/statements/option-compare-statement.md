---
title: Option Compare — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 1ffe3e45a296d02364f488540d987d85133013bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404385"
---
# <a name="option-compare-statement"></a><span data-ttu-id="7f05d-102">Option Compare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="7f05d-102">Option Compare Statement</span></span>
<span data-ttu-id="7f05d-103">Deklaruje domyślną metodę porównania do użycia podczas porównywania danych ciągu.</span><span class="sxs-lookup"><span data-stu-id="7f05d-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f05d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f05d-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="7f05d-105">Części</span><span class="sxs-lookup"><span data-stu-id="7f05d-105">Parts</span></span>  
  
|<span data-ttu-id="7f05d-106">Termin</span><span class="sxs-lookup"><span data-stu-id="7f05d-106">Term</span></span>|<span data-ttu-id="7f05d-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="7f05d-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="7f05d-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7f05d-108">Optional.</span></span> <span data-ttu-id="7f05d-109">Wyniki porównywania ciągów na podstawie kolejności sortowania pochodzącej z wewnętrznych reprezentacji binarnych znaków.</span><span class="sxs-lookup"><span data-stu-id="7f05d-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="7f05d-110">Ten typ porównania jest przydatny zwłaszcza wtedy, gdy ciągi mogą zawierać znaki, które nie są interpretowane jako tekst.</span><span class="sxs-lookup"><span data-stu-id="7f05d-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="7f05d-111">W tym przypadku nie chcesz porównań z odpowiednikami alfabetycznymi, na przykład bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="7f05d-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="7f05d-112">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7f05d-112">Optional.</span></span> <span data-ttu-id="7f05d-113">Wyniki porównywania ciągów na podstawie kolejności sortowania tekstu niezależnego od wielkości liter, ustalonej przez ustawienia regionalne systemu.</span><span class="sxs-lookup"><span data-stu-id="7f05d-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="7f05d-114">Ten typ porównania jest przydatny, jeśli ciągi zawierają wszystkie znaki tekstowe i chcesz je porównać przy uwzględnieniu równoważności alfabetycznej, takich jak nieuwzględnianie wielkości liter i ściśle powiązane litery.</span><span class="sxs-lookup"><span data-stu-id="7f05d-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="7f05d-115">Na przykład możesz chcieć rozważyć `A` i tak, aby `a` były równe i `Ä` i `ä` przed `B` i `b` .</span><span class="sxs-lookup"><span data-stu-id="7f05d-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f05d-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f05d-116">Remarks</span></span>  
 <span data-ttu-id="7f05d-117">Jeśli jest używana, `Option Compare` instrukcja musi pojawić się w pliku przed innymi instrukcjami kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="7f05d-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="7f05d-118">`Option Compare`Instrukcja określa metodę porównania ciągów ( `Binary` lub `Text` ).</span><span class="sxs-lookup"><span data-stu-id="7f05d-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="7f05d-119">Domyślną metodą porównywania tekstu jest `Binary` .</span><span class="sxs-lookup"><span data-stu-id="7f05d-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="7f05d-120">`Binary`Porównanie porównuje wartość liczbową Unicode każdego znaku w każdym ciągu.</span><span class="sxs-lookup"><span data-stu-id="7f05d-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="7f05d-121">`Text`Porównanie porównuje każdy znak Unicode na podstawie jego leksykalnego znaczenia w bieżącej kulturze.</span><span class="sxs-lookup"><span data-stu-id="7f05d-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="7f05d-122">W systemie Microsoft Windows kolejność sortowania jest określana przez stronę kodową.</span><span class="sxs-lookup"><span data-stu-id="7f05d-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="7f05d-123">Aby uzyskać więcej informacji, zobacz [stronę kodową](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="7f05d-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="7f05d-124">W poniższym przykładzie znaki na stronie kodowej angielski/Europa (ANSI 1252) są sortowane przy użyciu `Option Compare Binary` , co daje typowy binarny porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="7f05d-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="7f05d-125">Gdy te same znaki na tej samej stronie kodowej są sortowane przy użyciu `Option Compare Text` , generowany jest następujący porządek sortowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="7f05d-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="7f05d-126">Gdy nie ma instrukcji Compare</span><span class="sxs-lookup"><span data-stu-id="7f05d-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="7f05d-127">Jeśli kod źródłowy nie zawiera `Option Compare` instrukcji, **opcja Porównaj** ustawienia na [stronie kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używana.</span><span class="sxs-lookup"><span data-stu-id="7f05d-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="7f05d-128">Jeśli używasz kompilatora wiersza polecenia, ustawienie określone przez opcję kompilatora [-optioncompare](../../reference/command-line-compiler/optioncompare.md) jest używane.</span><span class="sxs-lookup"><span data-stu-id="7f05d-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="7f05d-129">Aby ustawić opcję Porównaj w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="7f05d-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="7f05d-130">W **Eksplorator rozwiązań**wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="7f05d-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="7f05d-131">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7f05d-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="7f05d-132">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="7f05d-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="7f05d-133">Ustaw wartość w polu **Compare (porównanie opcji** ).</span><span class="sxs-lookup"><span data-stu-id="7f05d-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="7f05d-134">Podczas tworzenia projektu **opcja Porównaj** ustawienie na karcie **kompilowania** jest ustawiona na **opcję Porównaj** ustawienia w oknie dialogowym **Opcje** .</span><span class="sxs-lookup"><span data-stu-id="7f05d-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="7f05d-135">Aby zmienić to ustawienie, w menu **Narzędzia** kliknij polecenie **Opcje**.</span><span class="sxs-lookup"><span data-stu-id="7f05d-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="7f05d-136">W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**.</span><span class="sxs-lookup"><span data-stu-id="7f05d-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="7f05d-137">Początkowe domyślne ustawienie w **języku VB** jest wartością **binarną**.</span><span class="sxs-lookup"><span data-stu-id="7f05d-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="7f05d-138">Aby ustawić opcję Compare w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="7f05d-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="7f05d-139">Dołącz opcję kompilatora [-optioncompare](../../reference/command-line-compiler/optioncompare.md) w poleceniu **VBC** .</span><span class="sxs-lookup"><span data-stu-id="7f05d-139">Include the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f05d-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f05d-140">Example</span></span>  
 <span data-ttu-id="7f05d-141">Poniższy przykład używa instrukcji, `Option Compare` Aby ustawić porównanie binarne jako domyślną metodę porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="7f05d-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="7f05d-142">Aby użyć tego kodu, Usuń komentarz `Option Compare Binary` instrukcji i umieść go w górnej części pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="7f05d-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="7f05d-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f05d-143">Example</span></span>  
 <span data-ttu-id="7f05d-144">Poniższy przykład używa instrukcji, `Option Compare` Aby ustawić kolejność sortowania tekstu bez uwzględniania wielkości liter jako domyślną metodę porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="7f05d-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="7f05d-145">Aby użyć tego kodu, Usuń komentarz `Option Compare Text` instrukcji i umieść go w górnej części pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="7f05d-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="7f05d-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f05d-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="7f05d-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="7f05d-147">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="7f05d-148">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="7f05d-148">Comparison Operators</span></span>](../operators/comparison-operators.md)
- [<span data-ttu-id="7f05d-149">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7f05d-149">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="7f05d-150">Like — Operator</span><span class="sxs-lookup"><span data-stu-id="7f05d-150">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="7f05d-151">Funkcje ciągów</span><span class="sxs-lookup"><span data-stu-id="7f05d-151">String Functions</span></span>](../functions/string-functions.md)
- [<span data-ttu-id="7f05d-152">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7f05d-152">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="7f05d-153">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="7f05d-153">Option Strict Statement</span></span>](option-strict-statement.md)
