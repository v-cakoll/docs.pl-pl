---
title: Zadeklarowane nazwy elementów (Visual Basic)
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
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814071"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="805a1-102">Zadeklarowane nazwy elementów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="805a1-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="805a1-103">Każdy element zadeklarowany ma nazwę, nazywany również *identyfikator*, czyli kod używa się do niego.</span><span class="sxs-lookup"><span data-stu-id="805a1-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="805a1-104">reguły</span><span class="sxs-lookup"><span data-stu-id="805a1-104">Rules</span></span>  
 <span data-ttu-id="805a1-105">Nazwa elementu w języku Visual Basic musi być zgodna z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="805a1-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
-   <span data-ttu-id="805a1-106">Musi zaczynać się od litery lub znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="805a1-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="805a1-107">Musi ona zawierać tylko znaki alfabetu, cyfry i znaki podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="805a1-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="805a1-108">Jeśli zaczyna się od znaku podkreślenia musi zawierać co najmniej jeden znak alfabetu lub cyfrę dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="805a1-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="805a1-109">Nie może być dłuższa niż 1023 znaków.</span><span class="sxs-lookup"><span data-stu-id="805a1-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="805a1-110">Limit długości 1023 znaków ma również zastosowanie do całego ciągu w pełni kwalifikowana nazwa, takich jak `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="805a1-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="805a1-111">Poniższy przykład przedstawia niektóre nazwy prawidłowego elementu.</span><span class="sxs-lookup"><span data-stu-id="805a1-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="805a1-112">Poniższy przykład przedstawia niektóre nazwy nieprawidłowy element.</span><span class="sxs-lookup"><span data-stu-id="805a1-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="805a1-113">Pierwszy zawiera tylko znak podkreślenia, drugi zaczyna się od cyfry dziesiętne, a trzeci zawiera nieprawidłowy znak ($).</span><span class="sxs-lookup"><span data-stu-id="805a1-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="805a1-114">Nazwy elementów rozpoczynające się od podkreślenia (`_`) nie są częścią [niezależność od języka i składniki niezależne od języka](../../../../standard/language-independence-and-language-independent-components.md) (CLS), dzięki czemu kod zgodny ze specyfikacją CLS nie można użyć składnika, który definiuje takich nazw.</span><span class="sxs-lookup"><span data-stu-id="805a1-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="805a1-115">Podkreślenia w innym miejscu, w nazwie elementu jest jednak zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="805a1-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="805a1-116">Wytyczne dotyczące długość nazwy</span><span class="sxs-lookup"><span data-stu-id="805a1-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="805a1-117">Jako to w praktyce Twoja nazwa powinna być możliwie krótkie podczas identyfikacji nadal wyraźnie rodzaj elementu.</span><span class="sxs-lookup"><span data-stu-id="805a1-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="805a1-118">To zwiększa czytelność kodu i zmniejsza rozmiar wiersza długości i pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="805a1-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="805a1-119">Z drugiej strony Twoja nazwa nie powinna być zbyt krótki, że nie odpowiednio opisano element reprezentuje i jak Twój kod używający tych informacji.</span><span class="sxs-lookup"><span data-stu-id="805a1-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="805a1-120">Jest to ważne dla czytelności kodu.</span><span class="sxs-lookup"><span data-stu-id="805a1-120">This is important for the readability of your code.</span></span> <span data-ttu-id="805a1-121">Jeśli ktoś inny spróbuje go zrozumieć lub samodzielnie przeglądasz go przez długi czas, po jego autorem, odpowiedni element nazw można zapisać znaczną ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="805a1-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="805a1-122">Nazwy wyjścia</span><span class="sxs-lookup"><span data-stu-id="805a1-122">Escaped Names</span></span>  
 <span data-ttu-id="805a1-123">Ogólnie rzecz biorąc, nazwa elementu nie może odpowiadać dowolnych słów kluczowych, zastrzeżone w języku Visual Basic, takie jak `Case` lub `Friend`.</span><span class="sxs-lookup"><span data-stu-id="805a1-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="805a1-124">Jednakże można zdefiniować *poprzedzone znakiem zmiany znaczenia nazwa*, która jest ujęta w nawiasy kwadratowe (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="805a1-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="805a1-125">Nazwa o zmienionym znaczeniu może odnosić się słowa kluczowego języka Visual Basic, ponieważ nawiasy, usuń wszelkie niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="805a1-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="805a1-126">Możesz także użyć nawiasów, gdy odwołujesz się do nazwy w dalszej części kodu.</span><span class="sxs-lookup"><span data-stu-id="805a1-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="805a1-127">Ogólnie rzecz biorąc, należy używać nazwy wyjścia tylko wtedy, gdy:</span><span class="sxs-lookup"><span data-stu-id="805a1-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="805a1-128">Kod został zmigrowany z poprzedniej wersji programu Visual Basic, który nie zarezerwować słowa kluczowego jako nazwy; lub</span><span class="sxs-lookup"><span data-stu-id="805a1-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="805a1-129">Pracujesz z kodu napisanego w innym języku, w którym dane słowo kluczowe nie jest zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="805a1-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="805a1-130">W przeciwnym razie należy rozważyć, jeśli jego nazwa jest w konflikcie ze słowem kluczowym, zmiana nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="805a1-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="805a1-131">Zintegrowane środowisko programistyczne (IDE) zapewnia prosty sposób, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="805a1-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="805a1-132">Aby uzyskać więcej informacji, zobacz [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="805a1-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="805a1-133">Rozróżnianie wielkości liter w nazwach</span><span class="sxs-lookup"><span data-stu-id="805a1-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="805a1-134">Nazwy elementów w języku Visual Basic jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="805a1-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="805a1-135">Oznacza to, że gdy kompilator porównuje dwie nazwy, które różnią się alfabetyczne tylko wielkością liter, interpretuje je jako tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="805a1-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="805a1-136">Na przykład, które uzna za `ABC` i `abc` do odwoływania się do tego samego elementu zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="805a1-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="805a1-137">Środowisko uruchomieniowe języka wspólnego (CLR) używa jednak powiązania z uwzględnieniem wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="805a1-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="805a1-138">W związku z tym podczas tworzenia zestawu lub biblioteki DLL i był dostępny dla innych zestawów, nazwy nie są już bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="805a1-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="805a1-139">Na przykład, jeśli zdefiniujesz klasę z elementu o nazwie `ABC`, i innych zestawów, należy użyć klasy za pomocą środowiska uruchomieniowego języka wspólnego, ich musi odwoływać się do elementu jako `ABC`.</span><span class="sxs-lookup"><span data-stu-id="805a1-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="805a1-140">Jeśli są później ponownie skompilować klasy i Zmień nazwę elementu do `abc`, zestawy, przy użyciu klasy nie będzie można uzyskać dostępu do tego elementu.</span><span class="sxs-lookup"><span data-stu-id="805a1-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="805a1-141">W związku z tym po zwolnieniu zaktualizowanej wersji zestawu, nie należy zmieniać wielkość liter alfabetu wszelkie publiczne elementy.</span><span class="sxs-lookup"><span data-stu-id="805a1-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="805a1-142">Nazwy i ustawienia regionalne</span><span class="sxs-lookup"><span data-stu-id="805a1-142">Names and Locales</span></span>  
 <span data-ttu-id="805a1-143">Porównanie nazw jest niezależne od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="805a1-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="805a1-144">Jeśli dwie nazwy są zgodne w jednym ustawień regionalnych, mają gwarancję, że odpowiada we wszystkich ustawieniach regionalnych.</span><span class="sxs-lookup"><span data-stu-id="805a1-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="805a1-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="805a1-145">See also</span></span>

- [<span data-ttu-id="805a1-146">Zadeklarowane elementy</span><span class="sxs-lookup"><span data-stu-id="805a1-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="805a1-147">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="805a1-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="805a1-148">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="805a1-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="805a1-149">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="805a1-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
