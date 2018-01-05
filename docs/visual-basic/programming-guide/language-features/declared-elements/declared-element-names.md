---
title: "Zadeklarowane nazwy elementów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22595eff2509d3954b3ce9d5038b19a681fbfbbe
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="27bf5-102">Zadeklarowane nazwy elementów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27bf5-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="27bf5-103">Każdy element zadeklarowane ma nazwę, nazywany również *identyfikator*, czyli w kodzie użyto odwoływanie się do niego.</span><span class="sxs-lookup"><span data-stu-id="27bf5-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="27bf5-104">Reguły</span><span class="sxs-lookup"><span data-stu-id="27bf5-104">Rules</span></span>  
 <span data-ttu-id="27bf5-105">Nazwa elementu w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] musi być zgodna z poniższymi regułami:</span><span class="sxs-lookup"><span data-stu-id="27bf5-105">An element name in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must observe the following rules:</span></span>  
  
-   <span data-ttu-id="27bf5-106">Musi zaczynać się od litery lub znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="27bf5-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="27bf5-107">Musi ona zawierać tylko znaki alfabetyczne, cyfry dziesiętne i podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="27bf5-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="27bf5-108">Musi ona zawierać co najmniej jedną literę alfabetu lub cyfrę, jeśli zaczyna się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="27bf5-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="27bf5-109">Nie może być dłuższa niż 1023 znaków.</span><span class="sxs-lookup"><span data-stu-id="27bf5-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="27bf5-110">Limit długości 1023 znaków ma również zastosowanie do całego ciągu nazwy FQDN, takich jak `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="27bf5-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="27bf5-111">W poniższym przykładzie przedstawiono niektóre nazwy elementów prawidłową.</span><span class="sxs-lookup"><span data-stu-id="27bf5-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="27bf5-112">W poniższym przykładzie przedstawiono niektóre nazwy nieprawidłowy element.</span><span class="sxs-lookup"><span data-stu-id="27bf5-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="27bf5-113">Pierwszy zawiera tylko znak podkreślenia, drugi rozpoczyna się od cyfry dziesiętne i trzeci zawiera nieprawidłowy znak ($).</span><span class="sxs-lookup"><span data-stu-id="27bf5-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="27bf5-114">Nazwy elementów, począwszy od znaku podkreślenia (`_`) czy nie jest częścią [niezależność od języka i elementy niezależne od języka](../../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie można użyć składnika, który definiuje takich nazw.</span><span class="sxs-lookup"><span data-stu-id="27bf5-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="27bf5-115">Jednak podkreślenia w inne położenie w nazwie elementu jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="27bf5-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="27bf5-116">Wskazówki dotyczące długość nazwy</span><span class="sxs-lookup"><span data-stu-id="27bf5-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="27bf5-117">Jak to w praktyce Twoja nazwa powinna być możliwie krótki podczas nadal jednoznacznie identyfikujący rodzaj elementu.</span><span class="sxs-lookup"><span data-stu-id="27bf5-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="27bf5-118">To poprawia czytelność kodu i zmniejsza rozmiar linii długość i pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="27bf5-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="27bf5-119">Z drugiej strony nie należy tak krótki, że nie można ją było właściwie opisano reprezentuje element i jak kod używający nazwę.</span><span class="sxs-lookup"><span data-stu-id="27bf5-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="27bf5-120">Jest to ważne w przypadku czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="27bf5-120">This is important for the readability of your code.</span></span> <span data-ttu-id="27bf5-121">Jeśli ktoś próbuje go zrozumieć lub samodzielnie poszukujesz go przez długi czas, po jego zapisano, nazwy odpowiednich elementów można zapisać znaczną ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="27bf5-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="27bf5-122">Nazwy wyjścia</span><span class="sxs-lookup"><span data-stu-id="27bf5-122">Escaped Names</span></span>  
 <span data-ttu-id="27bf5-123">Ogólnie rzecz biorąc, nazwa elementu musi pasuje do żadnego słowa zastrzeżone przez [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], takich jak `Case` lub `Friend`.</span><span class="sxs-lookup"><span data-stu-id="27bf5-123">Generally, an element name must not match any of the keywords reserved by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], such as `Case` or `Friend`.</span></span> <span data-ttu-id="27bf5-124">Można jednak zdefiniować *zmieniona nazwa*, która jest ujęta w nawiasy klamrowe (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="27bf5-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="27bf5-125">Nazwa zmienionym może pasować dowolny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] — słowo kluczowe, ponieważ nawiasy usunąć niejednoznaczność.</span><span class="sxs-lookup"><span data-stu-id="27bf5-125">An escaped name can match any [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="27bf5-126">Można również użyć nawiasów, w przypadku odwoływania się do nazwy w dalszej części kodu.</span><span class="sxs-lookup"><span data-stu-id="27bf5-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="27bf5-127">Ogólnie rzecz biorąc, należy użyć nazwy wyjścia tylko wtedy, gdy:</span><span class="sxs-lookup"><span data-stu-id="27bf5-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="27bf5-128">Kod został zmigrowany z poprzedniej wersji [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] słowa kluczowego jako nazwy; nie rezerwa lub</span><span class="sxs-lookup"><span data-stu-id="27bf5-128">Your code has migrated from a previous version of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="27bf5-129">Pracujesz kod napisany w innym języku, w którym dane słowo kluczowe nie jest zarezerwowana.</span><span class="sxs-lookup"><span data-stu-id="27bf5-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="27bf5-130">W przeciwnym razie należy rozważyć, jeśli jego nazwa powoduje konflikt ze słowem kluczowym, zmiana nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="27bf5-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="27bf5-131">Zintegrowane środowisko programistyczne (IDE) zapewnia prosty sposób w tym celu.</span><span class="sxs-lookup"><span data-stu-id="27bf5-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="27bf5-132">Aby uzyskać więcej informacji, zobacz [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="27bf5-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="27bf5-133">Uwzględniana wielkość liter w nazwach</span><span class="sxs-lookup"><span data-stu-id="27bf5-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="27bf5-134">Nazwy elementu w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="27bf5-134">Element names in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] are case-insensitive.</span></span> <span data-ttu-id="27bf5-135">Oznacza to, że gdy kompilator porównuje dwie nazwy, które różnią się od litery alfabetu tylko wielkością liter, jego interpretuje je jako takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="27bf5-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="27bf5-136">Na przykład traktuje `ABC` i `abc` do odwoływania się do tego samego elementu zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="27bf5-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="27bf5-137">Środowisko uruchomieniowe języka wspólnego (CLR) nie korzysta jednak powiązania z uwzględnieniem wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="27bf5-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="27bf5-138">W związku z tym podczas tworzenia zestawu lub biblioteki DLL i był dostępny do innych zestawów nazwy nie są już bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="27bf5-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="27bf5-139">Na przykład można zdefiniować klasę z element o nazwie `ABC`, i innych zestawów użyć klasy przez środowisko uruchomieniowe języka wspólnego, ich musi odwoływać się do elementu jako `ABC`.</span><span class="sxs-lookup"><span data-stu-id="27bf5-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="27bf5-140">Jeśli są później ponownie skompilowana, klasy i Zmień nazwę elementu, aby `abc`, innych zestawów przy użyciu klasy nie może uzyskać dostępu do tego elementu.</span><span class="sxs-lookup"><span data-stu-id="27bf5-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="27bf5-141">W związku z tym po zwolnieniu zaktualizowanej wersji zestawu, nie należy zmieniać w przypadku alfabetyczne żadnych publicznych elementów.</span><span class="sxs-lookup"><span data-stu-id="27bf5-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="27bf5-142">Nazwy i ustawień regionalnych</span><span class="sxs-lookup"><span data-stu-id="27bf5-142">Names and Locales</span></span>  
 <span data-ttu-id="27bf5-143">Porównanie nazw zależy od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="27bf5-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="27bf5-144">Jeśli dwie nazwy są zgodne z ustawieniami regionalnymi jeden, ich dotrą do dopasowania wszystkich ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="27bf5-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bf5-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27bf5-145">See Also</span></span>  
 [<span data-ttu-id="27bf5-146">Zadeklarowane elementy</span><span class="sxs-lookup"><span data-stu-id="27bf5-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [<span data-ttu-id="27bf5-147">Charakterystyka zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="27bf5-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="27bf5-148">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="27bf5-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="27bf5-149">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="27bf5-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
