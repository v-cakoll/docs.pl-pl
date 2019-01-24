---
title: Visual Basic — Konwencje kodowania
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f2b1676ae959c5426af3021bbd340980115c5da6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724885"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="8a041-102">Visual Basic — Konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="8a041-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="8a041-103">Microsoft rozwija przykłady i dokumentację, która jest zgodna z wytycznymi w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="8a041-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="8a041-104">Wykonanie tych samych konwencji kodowania możesz osiągnąć następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="8a041-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="8a041-105">Twój kod będzie miał jednolity wygląd, tak aby czytelnicy mogli lepiej skupić się na treści, a nie na układzie.</span><span class="sxs-lookup"><span data-stu-id="8a041-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="8a041-106">Czytniki rozumieją Twój kod lepiej szybko, ponieważ mogą robić więjsze założenia na podstawie poprzednich doświadczeń.</span><span class="sxs-lookup"><span data-stu-id="8a041-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="8a041-107">Można skopiować, zmieniać i utrzymywać kod, aby łatwiej.</span><span class="sxs-lookup"><span data-stu-id="8a041-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="8a041-108">Uzyskujesz pewność, że Twój kod wykazuje,, "Najważniejsze wskazówki" dla języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8a041-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="8a041-109">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="8a041-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="8a041-110">Aby uzyskać informacje o zasadach nazywania, zobacz [wytyczne dotyczące nazewnictwa](../../../standard/design-guidelines/naming-guidelines.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="8a041-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
-   <span data-ttu-id="8a041-111">Nie należy używać "Mój" lub "Mój" jako część nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8a041-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="8a041-112">Praktyka ta tworzy omyłkowe `My` obiektów.</span><span class="sxs-lookup"><span data-stu-id="8a041-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="8a041-113">Nie trzeba zmieniać nazwy obiektów w automatycznie wygenerowany kod, aby je dopasować do wytycznych.</span><span class="sxs-lookup"><span data-stu-id="8a041-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="8a041-114">Konwencje układu</span><span class="sxs-lookup"><span data-stu-id="8a041-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="8a041-115">Wstaw tabulatory jako spacje i Użyj inteligentnego wcięcia z czterokrotnym wcięciem.</span><span class="sxs-lookup"><span data-stu-id="8a041-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="8a041-116">Użyj **formatowania kodu automatyczne formatowanie kodu** Aby sformatować kod w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="8a041-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="8a041-117">Aby uzyskać więcej informacji, zobacz [opcje, Edytor tekstów, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8a041-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="8a041-118">Użyj tylko jednej instrukcji na wiersz.</span><span class="sxs-lookup"><span data-stu-id="8a041-118">Use only one statement per line.</span></span> <span data-ttu-id="8a041-119">Nie używaj znaku separatora wierszy programu Visual Basic (:).</span><span class="sxs-lookup"><span data-stu-id="8a041-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="8a041-120">Należy unikać znaku kontynuacji wiersza jawne "_" na rzecz niejawnej kontynuacji wiersza wszędzie tam, gdzie pozwala to język.</span><span class="sxs-lookup"><span data-stu-id="8a041-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="8a041-121">Użyj tylko jednej deklaracji na wiersz.</span><span class="sxs-lookup"><span data-stu-id="8a041-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="8a041-122">Jeśli **formatowania kodu automatyczne formatowanie kodu** nie formatuje wierszy kontynuacji automatycznie, ręcznie Utwórz wcięcia kontynuacji wierszy na jeden tabulator.</span><span class="sxs-lookup"><span data-stu-id="8a041-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="8a041-123">Jednak zawsze wyrównuj do lewej elementy na liście.</span><span class="sxs-lookup"><span data-stu-id="8a041-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="8a041-124">Dodaj co najmniej jeden pusty wiersz między definicje metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="8a041-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="8a041-125">Konwencje komentowania</span><span class="sxs-lookup"><span data-stu-id="8a041-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="8a041-126">Umieść komentarze w osobnym wierszu zamiast na końcu wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="8a041-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="8a041-127">Rozpocznij tekst komentarza wielką literą i tekst komentarza zakończenia kropką.</span><span class="sxs-lookup"><span data-stu-id="8a041-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="8a041-128">Wstaw jedną spację między ogranicznik komentarza (') i tekst komentarza.</span><span class="sxs-lookup"><span data-stu-id="8a041-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   <span data-ttu-id="8a041-129">Nie otaczaj komentarzy sformatowanymi blokami ani gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="8a041-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="8a041-130">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="8a041-130">Program Structure</span></span>  
  
-   <span data-ttu-id="8a041-131">Kiedy używasz `Main` metody, użyj domyślnego konstruktora dla nowych aplikacji konsoli, a następnie użyj `My` dla argumentów wiersza poleceń.</span><span class="sxs-lookup"><span data-stu-id="8a041-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="8a041-132">Wytyczne dotyczące języka</span><span class="sxs-lookup"><span data-stu-id="8a041-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="8a041-133">Typ danych ciągu</span><span class="sxs-lookup"><span data-stu-id="8a041-133">String Data Type</span></span>  
  
-   <span data-ttu-id="8a041-134">Do łączenia ciągów, użyj handlowe "i" (&).</span><span class="sxs-lookup"><span data-stu-id="8a041-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   <span data-ttu-id="8a041-135">Aby dołączyć ciągi w pętli, należy użyć <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8a041-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="8a041-136">Obniżone Delegaty w procedurach obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8a041-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="8a041-137">Nie kwalifikuj jawnie argumentów (obiekt i EventArgs) do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8a041-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="8a041-138">Jeśli nie używasz argumentów zdarzeń, które są przekazywane do zdarzenia (na przykład nadawcy jako obiektu, e jako EventArg), użyj swobodnych delegatów i Opuść argumenty zdarzenia w kodzie:</span><span class="sxs-lookup"><span data-stu-id="8a041-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="8a041-139">Typ danych bez znaku</span><span class="sxs-lookup"><span data-stu-id="8a041-139">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="8a041-140">Użyj `Integer` zamiast niepodpisanych typów, z wyjątkiem sytuacji, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="8a041-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="8a041-141">Tablice</span><span class="sxs-lookup"><span data-stu-id="8a041-141">Arrays</span></span>  
  
-   <span data-ttu-id="8a041-142">Użyj skróconej składni podczas inicjowania tablic w wierszu deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8a041-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="8a041-143">Na przykład użyj następującej składni.</span><span class="sxs-lookup"><span data-stu-id="8a041-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     <span data-ttu-id="8a041-144">Nie należy używać następującej składni.</span><span class="sxs-lookup"><span data-stu-id="8a041-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   <span data-ttu-id="8a041-145">Umieść oznaczenie tablicy na typie, a nie na zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8a041-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="8a041-146">Na przykład użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="8a041-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     <span data-ttu-id="8a041-147">Nie należy używać następującej składni:</span><span class="sxs-lookup"><span data-stu-id="8a041-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   <span data-ttu-id="8a041-148">Do deklarowania i inicjowania tablic typów podstawowych danych, należy użyć składni {}.</span><span class="sxs-lookup"><span data-stu-id="8a041-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="8a041-149">Na przykład użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="8a041-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     <span data-ttu-id="8a041-150">Nie należy używać następującej składni:</span><span class="sxs-lookup"><span data-stu-id="8a041-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="8a041-151">Korzystanie ze słowem kluczowym</span><span class="sxs-lookup"><span data-stu-id="8a041-151">Use the With Keyword</span></span>  
 <span data-ttu-id="8a041-152">Wprowadzając szereg wywołań do jednego obiektu, należy wziąć pod uwagę przy użyciu `With` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="8a041-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="8a041-153">Użyj Try... CATCH i przy użyciu instrukcji, korzystając z obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="8a041-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="8a041-154">Nie używaj `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="8a041-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="8a041-155">Użyj słowa kluczowego IsNot</span><span class="sxs-lookup"><span data-stu-id="8a041-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="8a041-156">Użyj `IsNot` słowa kluczowego zamiast `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="8a041-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="8a041-157">New — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="8a041-157">New Keyword</span></span>  
  
-   <span data-ttu-id="8a041-158">Użyj krótkiego tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8a041-158">Use short instantiation.</span></span> <span data-ttu-id="8a041-159">Na przykład użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="8a041-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     <span data-ttu-id="8a041-160">Poprzedni wiersz jest równoważny następującemu wyrażeniu:</span><span class="sxs-lookup"><span data-stu-id="8a041-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   <span data-ttu-id="8a041-161">Użyj inicjatorów obiektów dla nowych obiektów, a nie konstruktora bez parametrów:</span><span class="sxs-lookup"><span data-stu-id="8a041-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a><span data-ttu-id="8a041-162">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8a041-162">Event Handling</span></span>  
  
-   <span data-ttu-id="8a041-163">Użyj `Handles` zamiast `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="8a041-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   <span data-ttu-id="8a041-164">Użyj `AddressOf`i nie tworzyć wystąpienia pełnomocnika jawnie:</span><span class="sxs-lookup"><span data-stu-id="8a041-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   <span data-ttu-id="8a041-165">Podczas definiowania zdarzenia, użyj skróconej składni i zezwolić kompilatorowi na zdefiniowanie delegata:</span><span class="sxs-lookup"><span data-stu-id="8a041-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   <span data-ttu-id="8a041-166">Nie Weryfikuj, czy zdarzenie jest `Nothing` (null) przed wywołaniem `RaiseEvent` metody.</span><span class="sxs-lookup"><span data-stu-id="8a041-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="8a041-167">`RaiseEvent` sprawdza, czy `Nothing` przed zzdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8a041-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="8a041-168">Używanie udostępnionych elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="8a041-168">Using Shared Members</span></span>  
 <span data-ttu-id="8a041-169">Wywołaj `Shared` elementów członkowskich przy użyciu nazwy klasy, nie ze zmiennej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8a041-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="8a041-170">Używanie literałów XML</span><span class="sxs-lookup"><span data-stu-id="8a041-170">Use XML Literals</span></span>  
 <span data-ttu-id="8a041-171">Literały XML upraszczają najbardziej typowe zadania, które można napotkać podczas pracy z danymi XML (na przykład obciążenie, zapytań i przekształcania).</span><span class="sxs-lookup"><span data-stu-id="8a041-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="8a041-172">Podczas pracy z danymi XML należy przestrzegać następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="8a041-172">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="8a041-173">Literały XML umożliwiają tworzenie dokumentów XML i fragmentów zamiast wywoływania interfejsów API XML bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8a041-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="8a041-174">Zaimportuj przestrzenie nazw XML na poziomie pliku lub projektu, aby skorzystać z optymalizacji wydajności w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="8a041-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="8a041-175">Właściwości osi XML umożliwiają dostęp do elementów i atrybutów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="8a041-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="8a041-176">Użyj wyrażenia osadzone umożliwiają uwzględnienie wartości i tworzenie kodu XML na podstawie istniejących wartości, zamiast przy użyciu wywołań interfejsu API, takich jak `Add` metody:</span><span class="sxs-lookup"><span data-stu-id="8a041-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a><span data-ttu-id="8a041-177">Zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="8a041-177">LINQ Queries</span></span>  
  
-   <span data-ttu-id="8a041-178">Użyj nazw opisowych dla zmiennych kwerendy:</span><span class="sxs-lookup"><span data-stu-id="8a041-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   <span data-ttu-id="8a041-179">Zapewnij nazwy elementów w zapytaniu, aby upewnić się, że nazwy właściwości anonimowych typów są kapitalizowane poprawnie przy użyciu obudowy Pascal wielkość liter w wyrazie:</span><span class="sxs-lookup"><span data-stu-id="8a041-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   <span data-ttu-id="8a041-180">Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłby niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="8a041-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="8a041-181">Na przykład, jeśli zapytanie zwraca klienta nazwa i identyfikator zamówienia, zmień je zamiast pozostawiania je jako `Name` i `ID` w wyniku:</span><span class="sxs-lookup"><span data-stu-id="8a041-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   <span data-ttu-id="8a041-182">Użyj wnioskowania o typie w deklaracji zmiennych kwerendy i zmiennych zakresu:</span><span class="sxs-lookup"><span data-stu-id="8a041-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   <span data-ttu-id="8a041-183">Wyrównaj klauzule zapytania pod `From` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="8a041-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   <span data-ttu-id="8a041-184">Użyj `Where` klauzule przed innymi klauzulami kwerend powoduje, że późniejsze klauzule kwerend działają na zestawie filtrowanych danych:</span><span class="sxs-lookup"><span data-stu-id="8a041-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   <span data-ttu-id="8a041-185">Użyj `Join` klauzuli umożliwia jawne zdefiniowanie operacji join w przeciwieństwie `Where` klauzuli umożliwia niejawnie określenie operacji join:</span><span class="sxs-lookup"><span data-stu-id="8a041-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8a041-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a041-186">See also</span></span>
- [<span data-ttu-id="8a041-187">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="8a041-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
