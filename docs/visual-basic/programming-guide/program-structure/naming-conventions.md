---
title: Konwencje nazewnictwa
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
ms.openlocfilehash: 20531e379ddf9b93a278795e9b3c0eb91b47e077
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398347"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="6ac19-102">Visual Basic — Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="6ac19-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="6ac19-103">Po wybraniu nazwy elementu w aplikacji Visual Basic pierwszy znak tej nazwy musi być znakiem alfabetycznym lub podkreśleniem.</span><span class="sxs-lookup"><span data-stu-id="6ac19-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="6ac19-104">Należy jednak zauważyć, że nazwy zaczynające się od znaku podkreślenia nie są zgodne z [zależnościami od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="6ac19-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="6ac19-105">Poniższe sugestie dotyczą nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="6ac19-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="6ac19-106">Zacznij od każdego oddzielnego wyrazu w nazwie wielką literą, jak w `FindLastRecord` i `RedrawMyForm` .</span><span class="sxs-lookup"><span data-stu-id="6ac19-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="6ac19-107">Rozpocznij funkcję i nazwy metod z czasownikiem, jak w `InitNameArray` lub `CloseDialog` .</span><span class="sxs-lookup"><span data-stu-id="6ac19-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="6ac19-108">Rozpocznij od klasy, struktury, modułu i nazw właściwości rzeczownik, jak w `EmployeeName` lub `CarAccessory` .</span><span class="sxs-lookup"><span data-stu-id="6ac19-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="6ac19-109">Rozpocznij nazwy interfejsów z prefiksem "I", po którym następuje rzeczownik lub fraza rzeczownikowa, taka jak `IComponent` lub za pomocą przymiotnika opisującego zachowanie interfejsu, na przykład `IPersistable` .</span><span class="sxs-lookup"><span data-stu-id="6ac19-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="6ac19-110">Nie używaj znaku podkreślenia i rzadko używaj skrótów, ponieważ skróty mogą spowodować pomyłkę.</span><span class="sxs-lookup"><span data-stu-id="6ac19-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="6ac19-111">Rozpocznij nazwy programu obsługi zdarzeń z rzeczownikiem opisującym typ zdarzenia, po którym następuje `EventHandler` sufiks "", jak w " `MouseEventHandler` ".</span><span class="sxs-lookup"><span data-stu-id="6ac19-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="6ac19-112">W nazwach klas argumentów zdarzeń zawiera `EventArgs` sufiks "".</span><span class="sxs-lookup"><span data-stu-id="6ac19-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="6ac19-113">Jeśli zdarzenie ma koncepcję "Before" lub "After", użyj sufiksu w obecności lub w ciągu ostatnich, jak w " `ControlAdd` " lub " `ControlAdded` ".</span><span class="sxs-lookup"><span data-stu-id="6ac19-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="6ac19-114">Dla długich lub często używanych terminów użyj skrótów, aby zachować odpowiednie długości nazw, na przykład "HTML", a nie "HTML".</span><span class="sxs-lookup"><span data-stu-id="6ac19-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="6ac19-115">Ogólnie rzecz biorąc, nazwy zmiennych o wartości większej niż 32 znaków są trudne do odczytania na monitorze o niskiej rozdzielczości.</span><span class="sxs-lookup"><span data-stu-id="6ac19-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="6ac19-116">Upewnij się również, że skróty są spójne w całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6ac19-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="6ac19-117">Losowe przełączanie w projekcie między "HTML" i "HTML" może prowadzić do pomyłek.</span><span class="sxs-lookup"><span data-stu-id="6ac19-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="6ac19-118">Należy unikać używania nazw w zakresie wewnętrznym, które są takie same jak nazwy w zewnętrznym zakresie.</span><span class="sxs-lookup"><span data-stu-id="6ac19-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="6ac19-119">Błędy mogą wynikać z niewłaściwej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6ac19-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="6ac19-120">Jeśli występuje konflikt między zmienną i słowem kluczowym o tej samej nazwie, należy zidentyfikować słowo kluczowe, poprzedzając je odpowiednią biblioteką typów.</span><span class="sxs-lookup"><span data-stu-id="6ac19-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="6ac19-121">Na przykład jeśli masz zmienną o nazwie, można `Date` użyć `Date` funkcji wewnętrznej tylko przez wywołanie <xref:System.DateTime.Date%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6ac19-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac19-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ac19-122">See also</span></span>

- [<span data-ttu-id="6ac19-123">Słowa kluczowe jako nazwy elementów w kodzie</span><span class="sxs-lookup"><span data-stu-id="6ac19-123">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)
- [<span data-ttu-id="6ac19-124">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="6ac19-124">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)
- [<span data-ttu-id="6ac19-125">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="6ac19-125">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="6ac19-126">Struktura programu i konwencje związane z kodem</span><span class="sxs-lookup"><span data-stu-id="6ac19-126">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="6ac19-127">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ac19-127">Visual Basic Language Reference</span></span>](../../language-reference/index.md)
