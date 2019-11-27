---
title: Zadeklarowane nazwy elementów
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: e8620517b934a5f1a97ea25c5a94c8b932bb47b2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345431"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="4f47e-102">Zadeklarowane nazwy elementów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f47e-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="4f47e-103">Każdy zadeklarowany element ma nazwę, nazywaną również *identyfikatorem*, który jest używany przez kod do odwoływania się do niego.</span><span class="sxs-lookup"><span data-stu-id="4f47e-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4f47e-104">Reguły</span><span class="sxs-lookup"><span data-stu-id="4f47e-104">Rules</span></span>  
 <span data-ttu-id="4f47e-105">Nazwa elementu w Visual Basic musi być zgodna z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="4f47e-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="4f47e-106">Musi zaczynać się od litery lub znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="4f47e-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="4f47e-107">Musi zawierać tylko znaki alfanumeryczne, cyfry dziesiętne i podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="4f47e-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="4f47e-108">Musi zawierać co najmniej jedną literę lub cyfrę dziesiętną, jeśli zaczyna się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="4f47e-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="4f47e-109">Nie może być dłuższa niż 1023 znaków.</span><span class="sxs-lookup"><span data-stu-id="4f47e-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="4f47e-110">Limit długości 1023 znaków ma zastosowanie również do całego ciągu w pełni kwalifikowanej nazwy, takiej jak `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="4f47e-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="4f47e-111">Poniższy przykład pokazuje nieprawidłowe nazwy elementów.</span><span class="sxs-lookup"><span data-stu-id="4f47e-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="4f47e-112">W poniższym przykładzie przedstawiono niektóre nieprawidłowe nazwy elementów.</span><span class="sxs-lookup"><span data-stu-id="4f47e-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="4f47e-113">Pierwszy zawiera tylko podkreślenie, drugi zaczyna się cyfrą dziesiętną, a trzecia zawiera nieprawidłowy znak ($).</span><span class="sxs-lookup"><span data-stu-id="4f47e-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> <span data-ttu-id="4f47e-114">Nazwy elementów zaczynające się od znaku podkreślenia (`_`) nie są częścią [niezależną od języka i składników niezależnych od języka](../../../../standard/language-independence-and-language-independent-components.md) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który definiuje takie nazwy.</span><span class="sxs-lookup"><span data-stu-id="4f47e-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="4f47e-115">Jednakże podkreślenie w każdym innym miejscu w nazwie elementu jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="4f47e-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="4f47e-116">Wskazówki dotyczące długości nazwy</span><span class="sxs-lookup"><span data-stu-id="4f47e-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="4f47e-117">Ze względu na to, że Twoja nazwa powinna być tak krótka, jak to możliwe, podczas gdy nadal jasno identyfikuje charakter elementu.</span><span class="sxs-lookup"><span data-stu-id="4f47e-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="4f47e-118">Poprawia to czytelność kodu i zmniejsza długość wiersza i rozmiar pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4f47e-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="4f47e-119">Z drugiej strony, Twoja nazwa nie powinna być tak krótka, aby nie opisująca znaczenia elementu i sposobu jego użycia przez kod.</span><span class="sxs-lookup"><span data-stu-id="4f47e-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="4f47e-120">Jest to ważne dla czytelności kodu.</span><span class="sxs-lookup"><span data-stu-id="4f47e-120">This is important for the readability of your code.</span></span> <span data-ttu-id="4f47e-121">Jeśli ktoś inny próbuje zrozumieć ten element, lub jeśli ty przeglądasz ją przez długi czas po jego zapisaniu, odpowiednie nazwy elementów mogą zaoszczędzić znaczną ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="4f47e-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="4f47e-122">Nazwy o zmienionym znaczeniu</span><span class="sxs-lookup"><span data-stu-id="4f47e-122">Escaped Names</span></span>  
 <span data-ttu-id="4f47e-123">Ogólnie rzecz biorąc, nazwa elementu nie może być zgodna z żadnym ze słów kluczowych zarezerwowanych przez Visual Basic, takich jak `Case` lub `Friend`.</span><span class="sxs-lookup"><span data-stu-id="4f47e-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="4f47e-124">Można jednak zdefiniować *nazwę o zmienionym znaczeniu*, która jest ujęta w nawiasy kwadratowe (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="4f47e-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="4f47e-125">Nazwa o zmienionym znaczeniu może być zgodna ze słowem kluczowym Visual Basic, ponieważ nawiasy usuwają dowolną niejednoznaczność.</span><span class="sxs-lookup"><span data-stu-id="4f47e-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="4f47e-126">Możesz również użyć nawiasów, gdy odwołujesz się do nazwy w dalszej części kodu.</span><span class="sxs-lookup"><span data-stu-id="4f47e-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="4f47e-127">Ogólnie rzecz biorąc należy używać nazw unikowych tylko wtedy, gdy:</span><span class="sxs-lookup"><span data-stu-id="4f47e-127">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="4f47e-128">Twój kod został zmigrowany z poprzedniej wersji Visual Basic, która nie zarezerwował słowa kluczowego używanego jako nazwa; oraz</span><span class="sxs-lookup"><span data-stu-id="4f47e-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="4f47e-129">Pracujesz z kodem zapisanym w innym języku, w którym określone słowo kluczowe nie jest zarezerwowane.</span><span class="sxs-lookup"><span data-stu-id="4f47e-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="4f47e-130">W przeciwnym razie należy rozważyć zmianę nazwy elementu, jeśli jego nazwa powoduje konflikt ze słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="4f47e-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="4f47e-131">Zintegrowane środowisko programistyczne (IDE) zapewnia łatwy sposób wykonania tej czynności.</span><span class="sxs-lookup"><span data-stu-id="4f47e-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="4f47e-132">Aby uzyskać więcej informacji, zobacz [Refaktoryzacja](/visualstudio/ide/refactoring-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="4f47e-132">For more information, see [Refactoring](/visualstudio/ide/refactoring-in-visual-studio).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="4f47e-133">Rozróżnianie wielkości liter w nazwach</span><span class="sxs-lookup"><span data-stu-id="4f47e-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="4f47e-134">W nazwach elementów w Visual Basic nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="4f47e-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="4f47e-135">Oznacza to, że gdy kompilator porównuje dwie nazwy, które różnią się tylko wielkością liter, interpretuje je jako tę samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="4f47e-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="4f47e-136">Na przykład uważa, że `ABC` i `abc` do odwoływania się do tego samego zadeklarowanego elementu.</span><span class="sxs-lookup"><span data-stu-id="4f47e-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="4f47e-137">Jednak środowisko uruchomieniowe języka wspólnego (CLR) używa powiązania z rozróżnianiem wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="4f47e-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="4f47e-138">W związku z tym, podczas tworzenia zestawu lub biblioteki DLL i udostępnienia go innym zestawom nazwy nie są dłuższe.</span><span class="sxs-lookup"><span data-stu-id="4f47e-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="4f47e-139">Na przykład, jeśli zdefiniujesz klasę z elementem o nazwie `ABC`, a inne zestawy używają klasy przez środowisko uruchomieniowe języka wspólnego, muszą odwoływać się do elementu jako `ABC`.</span><span class="sxs-lookup"><span data-stu-id="4f47e-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="4f47e-140">Jeśli następnie ponownie skompilujesz klasę i zmienisz nazwę elementu na `abc`, inne zestawy korzystające z klasy nie będą miały już dostępu do tego elementu.</span><span class="sxs-lookup"><span data-stu-id="4f47e-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="4f47e-141">W związku z tym po wydaniu zaktualizowanej wersji zestawu nie należy zmieniać wielkości liter każdego z elementów publicznych.</span><span class="sxs-lookup"><span data-stu-id="4f47e-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="4f47e-142">Nazwy i ustawienia regionalne</span><span class="sxs-lookup"><span data-stu-id="4f47e-142">Names and Locales</span></span>  
 <span data-ttu-id="4f47e-143">Porównanie nazw jest niezależne od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="4f47e-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="4f47e-144">Jeśli dwie nazwy są zgodne z jednym ustawieniem regionalnym, są one gwarantowane do dopasowania we wszystkich ustawieniach regionalnych.</span><span class="sxs-lookup"><span data-stu-id="4f47e-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f47e-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f47e-145">See also</span></span>

- [<span data-ttu-id="4f47e-146">Zadeklarowane elementy</span><span class="sxs-lookup"><span data-stu-id="4f47e-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="4f47e-147">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="4f47e-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="4f47e-148">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="4f47e-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="4f47e-149">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="4f47e-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
