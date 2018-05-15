---
title: Visual Basic — Konwencje nazewnictwa
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: cb7e9f2a577e95e09fde885df1a78aea4e7fa466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="810bf-102">Visual Basic — Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="810bf-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="810bf-103">Po nadaniu nazwy elementu w aplikacji Visual Basic, pierwszym znakiem tej nazwy musi być literą lub znakiem podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="810bf-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="810bf-104">Należy jednak pamiętać, że nazwy rozpoczynające się od znaku podkreślenia. nie są zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="810bf-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="810bf-105">Poniższe sugestie dotyczą nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="810bf-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="810bf-106">Rozpocznij każdego wyrazu oddzielne w nazwie się wielką literą, podobnie jak w `FindLastRecord` i `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="810bf-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="810bf-107">Rozpocznij nazwy funkcji i metody z zlecenie, podobnie jak w `InitNameArray` lub `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="810bf-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="810bf-108">Rozpocznij klasy, struktury, moduł i nazwy właściwości z rzeczownik, podobnie jak w `EmployeeName` lub `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="810bf-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="810bf-109">Rozpocznij nazwy interfejs z prefiksem "I", a następnie rzeczownikiem lub frazę rzeczownik tak samo, jak `IComponent`, lub za pomocą przymiotnik tak samo, jak opisujący zachowanie interfejsu `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="810bf-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="810bf-110">Nie używa podkreślenia i skróty oszczędnie, ponieważ skróty może spowodować ryzyko pomyłek.</span><span class="sxs-lookup"><span data-stu-id="810bf-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="810bf-111">Zaczynać nazw programu obsługi zdarzeń rzeczownikiem opisujące typ zdarzenia, a następnie "`EventHandler`"sufiksu domeny, jak w"`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="810bf-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="810bf-112">W polu nazwy klas argument zdarzeń zawierają "`EventArgs`" sufiks.</span><span class="sxs-lookup"><span data-stu-id="810bf-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="810bf-113">Jeśli zdarzenie jest pojęcie "przed" lub "po", Użyj sufiksu w chwili obecnej lub przeszłego, podobnie jak w "`ControlAdd`"lub"`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="810bf-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="810bf-114">Długie lub często używanych terminów Użyj skróty do zachowania długości nazwy uzasadnione, na przykład "kod HTML", zamiast "Formacie HTML".</span><span class="sxs-lookup"><span data-stu-id="810bf-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="810bf-115">Ogólnie rzecz biorąc nazwy zmiennych, które są większe niż 32 znaki są trudne do odczytu na ustawioną w niskiej rozdzielczości monitora.</span><span class="sxs-lookup"><span data-stu-id="810bf-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="810bf-116">Ponadto upewnij się, że Twoje skróty są spójne w całym całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="810bf-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="810bf-117">Losowo przełączania w projekcie między "HTML" i "Hypertext Markup Language" może prowadzić do pomyłek.</span><span class="sxs-lookup"><span data-stu-id="810bf-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="810bf-118">Należy unikać nazw w zakresie wewnętrznym, które są takie same jak nazwy w zakresie zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="810bf-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="810bf-119">Błędy może spowodować, jeśli dostępna jest niewłaściwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="810bf-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="810bf-120">Jeśli występuje konflikt między zmienną i słowo kluczowe o takiej samej nazwie, należy określić słowa kluczowego, poprzedzając z biblioteką odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="810bf-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="810bf-121">Na przykład, jeśli masz zmiennej o nazwie `Date`, można użyć wewnętrznego `Date` funkcja tylko przez wywołanie metody <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="810bf-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810bf-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="810bf-122">See Also</span></span>  
 [<span data-ttu-id="810bf-123">Słowa kluczowe jako nazwy elementów w kodzie</span><span class="sxs-lookup"><span data-stu-id="810bf-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [<span data-ttu-id="810bf-124">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="810bf-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="810bf-125">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="810bf-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="810bf-126">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="810bf-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="810bf-127">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="810bf-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
