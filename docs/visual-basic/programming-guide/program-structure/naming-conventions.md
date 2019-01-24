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
ms.openlocfilehash: ebb9d21e32993f2eb035993d32dc3de7d97b49f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672139"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="5891a-102">Visual Basic — Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="5891a-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="5891a-103">Nazwa elementu w aplikacji Visual Basic, musi być pierwszym znakiem tej nazwy, litery alfabetu lub znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="5891a-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="5891a-104">Należy jednak pamiętać, że nazwy rozpoczynające się od znaku podkreślenia nie są zgodne z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="5891a-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="5891a-105">Poniższe sugestie dotyczą nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="5891a-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="5891a-106">Rozpoczęcie każdego wyrazu oddzielne nazwę wielką literą, podobnie jak w `FindLastRecord` i `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="5891a-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="5891a-107">Rozpocznij nazwy funkcji i metody z zlecenie, podobnie jak w `InitNameArray` lub `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="5891a-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="5891a-108">Rozpocznij klasy, struktury, moduł i nazwy właściwości zawierające rzeczownik, podobnie jak w `EmployeeName` lub `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="5891a-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="5891a-109">Rozpocznij interfejsu nazw z prefiksem "I", następuje rzeczownik lub frazy rzeczownik, takie jak `IComponent`, lub przymiotnikiem, opisujący zachowanie interfejsu, takie jak `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="5891a-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="5891a-110">Nie używać znaku podkreślenia i skróty oszczędnie, ponieważ skróty może spowodować błąd.</span><span class="sxs-lookup"><span data-stu-id="5891a-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="5891a-111">Nazwy programów obsługi zdarzeń zaczynać się od opisujące typ zdarzenia następuje rzeczownik "`EventHandler`"sufiksu, jak w"`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="5891a-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="5891a-112">W polu nazwy klas argument zdarzeń zawierają "`EventArgs`" sufiks.</span><span class="sxs-lookup"><span data-stu-id="5891a-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="5891a-113">Jeśli zdarzenie utworzono według koncepcji "before" lub "after", użyj przyrostka, w chwili obecnej czasu teraźniejszego lub przeszłego, podobnie jak w "`ControlAdd`"or"`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="5891a-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="5891a-114">Długa lub często używanych terminów Użyj skrótów zapewnienie długości nazwy rozsądne, na przykład, "HTML", a nie "Formacie HTML".</span><span class="sxs-lookup"><span data-stu-id="5891a-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="5891a-115">Ogólnie rzecz biorąc nazwy zmiennych, które są większe niż 32 znaki są trudne do odczytania na monitorze równa niskiej rozdzielczości.</span><span class="sxs-lookup"><span data-stu-id="5891a-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="5891a-116">Ponadto upewnij się, że Twoje skróty są spójne w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5891a-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="5891a-117">Losowo przełączania w projekcie między "HTML" i "Formacie HTML" można wprowadzać w błąd.</span><span class="sxs-lookup"><span data-stu-id="5891a-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="5891a-118">Unikaj używania nazw w zakresie wewnętrznym, które są takie same jak nazwy w zewnętrznym zakresie.</span><span class="sxs-lookup"><span data-stu-id="5891a-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="5891a-119">Jeśli problem wchodzisz, mogą wystąpić błędy.</span><span class="sxs-lookup"><span data-stu-id="5891a-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="5891a-120">Jeśli występuje konflikt między zmienną i słowo kluczowe o takiej samej nazwie, należy określić słowo kluczowe, poprzedzając je za pomocą biblioteki odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="5891a-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="5891a-121">Na przykład, jeśli masz zmienną o nazwie `Date`, można użyć wewnętrznego `Date` funkcji tylko przez wywołanie metody <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5891a-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5891a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5891a-122">See also</span></span>
- [<span data-ttu-id="5891a-123">Słowa kluczowe jako nazwy elementów w kodzie</span><span class="sxs-lookup"><span data-stu-id="5891a-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [<span data-ttu-id="5891a-124">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="5891a-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="5891a-125">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="5891a-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="5891a-126">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="5891a-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="5891a-127">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5891a-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
