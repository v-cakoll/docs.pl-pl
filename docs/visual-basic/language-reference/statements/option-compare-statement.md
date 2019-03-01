---
title: Option Compare — instrukcja (Visual Basic)
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
ms.openlocfilehash: c90e07afb1515b50ad6e2fd2a1bbe42f6da5fa95
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968143"
---
# <a name="option-compare-statement"></a><span data-ttu-id="3cf15-102">Option Compare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="3cf15-102">Option Compare Statement</span></span>
<span data-ttu-id="3cf15-103">Deklaruje domyślną metodę porównywania do użycia podczas porównywania danych ciągu.</span><span class="sxs-lookup"><span data-stu-id="3cf15-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf15-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3cf15-104">Syntax</span></span>  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="3cf15-105">Części</span><span class="sxs-lookup"><span data-stu-id="3cf15-105">Parts</span></span>  
  
|<span data-ttu-id="3cf15-106">Termin</span><span class="sxs-lookup"><span data-stu-id="3cf15-106">Term</span></span>|<span data-ttu-id="3cf15-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="3cf15-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="3cf15-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3cf15-108">Optional.</span></span> <span data-ttu-id="3cf15-109">Wynikiem porównania ciągów, w oparciu o kolejność sortowania jest pochodną wewnętrzne binarne reprezentacje znaków.</span><span class="sxs-lookup"><span data-stu-id="3cf15-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="3cf15-110">Ten typ porównania przydaje się zwłaszcza, jeśli ciągi mogą zawierać znaków, które nie mają być interpretowane jako tekst.</span><span class="sxs-lookup"><span data-stu-id="3cf15-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="3cf15-111">W takim przypadku możesz zrezygnować z obciążenia porównania z wartością alfabetycznej równoważności, takie jak ignorowanie wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="3cf15-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="3cf15-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3cf15-112">Optional.</span></span> <span data-ttu-id="3cf15-113">Wyniki w porównań ciągów, w oparciu o kolejność sortowania bez uwzględniania wielkości liter tekstu, określane przez ustawienia regionalne Twojego systemu.</span><span class="sxs-lookup"><span data-stu-id="3cf15-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="3cf15-114">Ten typ porównania jest przydatne, jeśli Twoimi ciągami, zawierać wszystkie znaki, tekst, a chcesz porównać ich równoważniki alfabetyczne konta, takie jak ignorowanie wielkości liter i cyfr ściśle powiązanych z uwzględnieniem.</span><span class="sxs-lookup"><span data-stu-id="3cf15-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="3cf15-115">Na przykład możesz chcieć należy wziąć pod uwagę `A` i `a` równe, i `Ä` i `ä` przed `B` i `b`.</span><span class="sxs-lookup"><span data-stu-id="3cf15-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cf15-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3cf15-116">Remarks</span></span>  
 <span data-ttu-id="3cf15-117">Jeśli używane, `Option Compare` instrukcja musi znajdować się w pliku przed wszystkimi innymi instrukcjami kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3cf15-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="3cf15-118">`Option Compare` Instrukcja określa metodę porównywania ciągów (`Binary` lub `Text`).</span><span class="sxs-lookup"><span data-stu-id="3cf15-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="3cf15-119">Domyślna metoda porównania tekstu jest `Binary`.</span><span class="sxs-lookup"><span data-stu-id="3cf15-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="3cf15-120">A `Binary` porównania porównuje wartość liczbową Unicode każdego znaku w każdym ciągu.</span><span class="sxs-lookup"><span data-stu-id="3cf15-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="3cf15-121">A `Text` porównania porównuje każdego znaku Unicode, oparte na ich leksykalne znaczenia w bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="3cf15-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="3cf15-122">W Microsoft Windows kolejność sortowania jest określana przez stronę kodową.</span><span class="sxs-lookup"><span data-stu-id="3cf15-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="3cf15-123">Aby uzyskać więcej informacji, zobacz [stron kodowych](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="3cf15-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="3cf15-124">W poniższym przykładzie znaków na stronie kodowej angielski/Europejskiego (ANSI 1252) są sortowane za pomocą `Option Compare Binary`, która generuje typowych binarny porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="3cf15-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="3cf15-125">Kiedy te same znaki w tej samej stronie kodowej są sortowane za pomocą `Option Compare Text`, generowany jest tekstowy porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="3cf15-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="3cf15-126">W przypadku opcji Option Compare instrukcja nie jest obecny</span><span class="sxs-lookup"><span data-stu-id="3cf15-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="3cf15-127">Jeśli kod źródłowy nie zawiera `Option Compare` instrukcji **Option Compare** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany.</span><span class="sxs-lookup"><span data-stu-id="3cf15-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="3cf15-128">Jeśli używasz kompilatora wiersza polecenia, ustawienia określone przez [/optioncompare —](../../../visual-basic/reference/command-line-compiler/optioncompare.md) — opcja kompilatora jest używany.</span><span class="sxs-lookup"><span data-stu-id="3cf15-128">If you use the command-line compiler, the setting specified by the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="3cf15-129">Można ustawić opcji Option Compare w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="3cf15-129">To set Option Compare in the IDE</span></span>  
  
1.  <span data-ttu-id="3cf15-130">W **Eksploratora rozwiązań**, wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="3cf15-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="3cf15-131">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="3cf15-131">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="3cf15-132">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="3cf15-132">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="3cf15-133">Ustaw wartość w **Option Compare** pole.</span><span class="sxs-lookup"><span data-stu-id="3cf15-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="3cf15-134">Podczas tworzenia projektu, **Option Compare** ustawienie **skompilować** karta jest ustawiona na **Option Compare** w **opcje** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="3cf15-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="3cf15-135">Aby zmienić to ustawienie, na **narzędzia** menu, kliknij przycisk **opcje**.</span><span class="sxs-lookup"><span data-stu-id="3cf15-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="3cf15-136">W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**.</span><span class="sxs-lookup"><span data-stu-id="3cf15-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="3cf15-137">Ustawieniem domyślnym początkowej w **ustawienia domyślne VB** jest **binarne**.</span><span class="sxs-lookup"><span data-stu-id="3cf15-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="3cf15-138">Można ustawić opcji Option Compare, w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="3cf15-138">To set Option Compare on the command line</span></span>  
  
-   <span data-ttu-id="3cf15-139">Obejmują [/optioncompare —](../../../visual-basic/reference/command-line-compiler/optioncompare.md) w — opcja kompilatora **vbc** polecenia.</span><span class="sxs-lookup"><span data-stu-id="3cf15-139">Include the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cf15-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf15-140">Example</span></span>  
 <span data-ttu-id="3cf15-141">W poniższym przykładzie użyto `Option Compare` instrukcję, aby ustawić porównanie binarne jako domyślną metodę porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="3cf15-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="3cf15-142">Aby użyć tego kodu, usuń znaczniki komentarza `Option Compare Binary` instrukcji i umieścić go w górnej części pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3cf15-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="3cf15-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="3cf15-143">Example</span></span>  
 <span data-ttu-id="3cf15-144">W poniższym przykładzie użyto `Option Compare` instrukcję, aby ustawić kolejność sortowania bez uwzględniania wielkości liter tekstu jako domyślną metodę porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="3cf15-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="3cf15-145">Aby użyć tego kodu, usuń znaczniki komentarza `Option Compare Text` instrukcji i umieścić go w górnej części pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3cf15-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="3cf15-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3cf15-146">See also</span></span>
- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="3cf15-147">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="3cf15-147">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="3cf15-148">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="3cf15-148">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="3cf15-149">Operatory porównania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3cf15-149">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="3cf15-150">Like, operator</span><span class="sxs-lookup"><span data-stu-id="3cf15-150">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="3cf15-151">Funkcje ciągów</span><span class="sxs-lookup"><span data-stu-id="3cf15-151">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)
- [<span data-ttu-id="3cf15-152">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3cf15-152">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="3cf15-153">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3cf15-153">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
