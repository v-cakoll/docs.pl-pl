---
title: Visual Basic — Konwencje kodowania
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: b686747b46529b53b0802a7deb38b5b4949f4d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="9e0ee-102">Visual Basic — Konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="9e0ee-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="9e0ee-103">Microsoft rozwija przykłady i dokumentację postępuj zgodnie z wytycznymi, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="9e0ee-104">Po wykonaniu tej samej Konwencji kodowania mogą zyskać następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="9e0ee-105">Kod będzie mieć spójny wygląd, tak aby czytników lepiej można skupić się na zawartości, nie układu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="9e0ee-106">Czytniki poznać kod więcej szybko ponieważ mogą one ułatwić założenia doświadczenia w oparciu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="9e0ee-107">Można skopiować, zmienianie i łatwiej Obsługa kodu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="9e0ee-108">Pomoc, upewnij się, że kod pokazuje "najlepsze rozwiązania" w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="9e0ee-109">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="9e0ee-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="9e0ee-110">Informacje o wskazówki dotyczące nazewnictwa, zobacz [nazewnictwa wytyczne](../../../standard/design-guidelines/naming-guidelines.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
-   <span data-ttu-id="9e0ee-111">Nie używaj "Moje" lub "Moje" jako część nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="9e0ee-112">Takie rozwiązanie tworzy pomylenia z `My` obiektów.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="9e0ee-113">Nie trzeba zmienić nazwy obiektów w automatycznie wygenerowany kod, aby je dopasować wytyczne.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="9e0ee-114">Konwencje układu</span><span class="sxs-lookup"><span data-stu-id="9e0ee-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="9e0ee-115">Wstaw jako spacje i użyj inteligentne tworzenia wcięć za pomocą czterech miejsca wcięcia.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="9e0ee-116">Użyj **automatycznego formatowania kodu (ponowne formatowanie) z** do ponownego formatowania kodu w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="9e0ee-117">Aby uzyskać więcej informacji, zobacz [opcje, Edytor tekstów, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="9e0ee-118">Użyj tylko jednej instrukcji w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-118">Use only one statement per line.</span></span> <span data-ttu-id="9e0ee-119">Nie używaj znaku separatora linii Visual Basic (:).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="9e0ee-120">Unikaj używania znak kontynuacji wiersza jawne "_" na rzecz kontynuacji wiersza niejawne wszędzie tam, gdzie pozwala języka.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="9e0ee-121">Użyj tylko jedna deklaracja w wierszu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="9e0ee-122">Jeśli **automatycznego formatowania kodu (ponowne formatowanie) z** nie Formatuj kontynuacji linie automatycznie, ręcznie wcięcie kontynuacji wierszy jednego tabulatora.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="9e0ee-123">Jednak zawsze lewej align elementów na liście.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="9e0ee-124">Dodaj co najmniej jeden pusty wiersz między definicje metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="9e0ee-125">Konwencje komentowania</span><span class="sxs-lookup"><span data-stu-id="9e0ee-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="9e0ee-126">Wprowadzone komentarze w osobnym wierszu zamiast na końcu wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="9e0ee-127">Uruchom tekst komentarza od wielkiej litery i tekst komentarza zakończenia kropką.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="9e0ee-128">Wstaw spację jednego między ogranicznik komentarza (') i tekst komentarza.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   <span data-ttu-id="9e0ee-129">Nie należy ująć komentarze sformatowany bloki gwiazdek.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="9e0ee-130">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="9e0ee-130">Program Structure</span></span>  
  
-   <span data-ttu-id="9e0ee-131">Jeśli używasz `Main` metody konstrukcji domyślne dla nowych aplikacji konsoli i wykorzystaj `My` dla argumentów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="9e0ee-132">Wytyczne dotyczące języka</span><span class="sxs-lookup"><span data-stu-id="9e0ee-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="9e0ee-133">Typ danych ciągu</span><span class="sxs-lookup"><span data-stu-id="9e0ee-133">String Data Type</span></span>  
  
-   <span data-ttu-id="9e0ee-134">Aby ciągów, należy użyć handlowego "i" (&).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   <span data-ttu-id="9e0ee-135">Aby dołączyć ciągów w pętli, należy użyć <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="9e0ee-136">Swobodna delegatów w obsłudze zdarzeń</span><span class="sxs-lookup"><span data-stu-id="9e0ee-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="9e0ee-137">Nie jawnie kwalifikują się argumentów (obiektu i EventArgs) do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="9e0ee-138">Jeśli nie używasz argumenty zdarzenia, które są przekazywane do zdarzeń (na przykład nadawcy jako obiekt, e jako EventArgs), używać delegatów swobodna i Opuść argumenty zdarzeń w kodzie:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="9e0ee-139">Typ danych bez znaku</span><span class="sxs-lookup"><span data-stu-id="9e0ee-139">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="9e0ee-140">Użyj `Integer` zamiast typy bez znaku, z wyjątkiem przypadków, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="9e0ee-141">Tablice</span><span class="sxs-lookup"><span data-stu-id="9e0ee-141">Arrays</span></span>  
  
-   <span data-ttu-id="9e0ee-142">Podczas inicjowania tablic w wierszu deklaracji, należy użyć składni krótki.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="9e0ee-143">Na przykład użyj następującej składni.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     <span data-ttu-id="9e0ee-144">Nie należy użyć następującej składni.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   <span data-ttu-id="9e0ee-145">W typie, a nie na zmiennej, umieść oznaczeniem tablicy.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="9e0ee-146">Na przykład użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     <span data-ttu-id="9e0ee-147">Nie należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   <span data-ttu-id="9e0ee-148">Po zadeklarowaniu i zainicjować tablice typów podstawowych danych, należy użyć składni {}.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="9e0ee-149">Na przykład użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     <span data-ttu-id="9e0ee-150">Nie należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="9e0ee-151">Użyj ze słowem kluczowym</span><span class="sxs-lookup"><span data-stu-id="9e0ee-151">Use the With Keyword</span></span>  
 <span data-ttu-id="9e0ee-152">Po wprowadzeniu szereg wywołania do jednego obiektu, należy rozważyć użycie `With` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="9e0ee-153">Użyj Try... CATCH i przy użyciu instrukcji, korzystając z obsługą wyjątków</span><span class="sxs-lookup"><span data-stu-id="9e0ee-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="9e0ee-154">Nie używaj `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="9e0ee-155">Użyj słowa kluczowego IsNot</span><span class="sxs-lookup"><span data-stu-id="9e0ee-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="9e0ee-156">Użyj `IsNot` słowa kluczowego zamiast `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="9e0ee-157">New, słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="9e0ee-157">New Keyword</span></span>  
  
-   <span data-ttu-id="9e0ee-158">Użyj wystąpienia krótki.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-158">Use short instantiation.</span></span> <span data-ttu-id="9e0ee-159">Na przykład użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     <span data-ttu-id="9e0ee-160">Poprzedni wiersz jest odpowiednikiem to:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   <span data-ttu-id="9e0ee-161">Inicjatory obiektów należy użyć dla nowych obiektów zamiast konstruktora bez parametrów:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a><span data-ttu-id="9e0ee-162">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="9e0ee-162">Event Handling</span></span>  
  
-   <span data-ttu-id="9e0ee-163">Użyj `Handles` zamiast `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   <span data-ttu-id="9e0ee-164">Użyj `AddressOf`, a nie wystąpienia delegat jawnie:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   <span data-ttu-id="9e0ee-165">Podczas definiowania zdarzenia należy użyć składni krótki i umożliwić kompilatora zdefiniuj delegata:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   <span data-ttu-id="9e0ee-166">Sprawdza, czy zdarzenie jest `Nothing` (null), przed wywołaniem `RaiseEvent` metody.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="9e0ee-167">`RaiseEvent` sprawdza, czy `Nothing` przed zgłasza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="9e0ee-168">Przy użyciu udostępniane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9e0ee-168">Using Shared Members</span></span>  
 <span data-ttu-id="9e0ee-169">Wywołanie `Shared` elementów członkowskich za pomocą nazwy klasy, nie z zmienna wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="9e0ee-170">Używaj literałów XML</span><span class="sxs-lookup"><span data-stu-id="9e0ee-170">Use XML Literals</span></span>  
 <span data-ttu-id="9e0ee-171">Literały XML uprościć najbardziej typowych zadań, które wystąpią podczas pracy z XML (na przykład, obciążenia, zapytań i przekształcenie).</span><span class="sxs-lookup"><span data-stu-id="9e0ee-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="9e0ee-172">Podczas pracy z danymi XML, skorzystaj z następujących wskazówek:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-172">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="9e0ee-173">Literały XML umożliwia tworzenie dokumentów XML i fragmentów, zamiast bezpośredniego wywoływania interfejsów API XML.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="9e0ee-174">Importuj przestrzeni nazw XML na poziomie pliku lub projektu, aby skorzystać z optymalizacji wydajności dla literałów XML.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="9e0ee-175">Właściwości osi XML umożliwia dostęp do elementów i atrybutów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="9e0ee-176">Użyj wyrażenia osadzone wartości mają zostać uwzględnione i utworzyć XML z istniejącymi wartościami zamiast przy użyciu interfejsu API, takich jak `Add` metody:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a><span data-ttu-id="9e0ee-177">Zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="9e0ee-177">LINQ Queries</span></span>  
  
-   <span data-ttu-id="9e0ee-178">Użyj łatwy do rozpoznania nazwy zmiennych zapytania:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   <span data-ttu-id="9e0ee-179">Nazwy elementów w zapytaniu, aby upewnić się, że nazwy właściwości typu anonimowego poprawnie kapitalizacji przy użyciu Pascal wielkości liter:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   <span data-ttu-id="9e0ee-180">Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłoby niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="9e0ee-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="9e0ee-181">Na przykład, jeśli zapytanie zwraca klienta nazwa i identyfikator zamówienia, zmień ich zamiast zostawiać je jako `Name` i `ID` w wyniku:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   <span data-ttu-id="9e0ee-182">Wnioskowanie o typie należy użyć w deklaracji zmiennych zakresu i zmiennych zapytania:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   <span data-ttu-id="9e0ee-183">Dopasuj klauzule zapytań w obszarze `From` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   <span data-ttu-id="9e0ee-184">Użyj `Where` klauzule przed innymi kwerendy w klauzulach sposób nowsze klauzule zapytań działać na odfiltrowanego zbioru danych:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   <span data-ttu-id="9e0ee-185">Użyj `Join` klauzuli, aby jawnie definiować operacji tworzenia sprzężenia zamiast `Where` klauzuli niejawnie określenie operacji tworzenia sprzężenia:</span><span class="sxs-lookup"><span data-stu-id="9e0ee-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9e0ee-186">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e0ee-186">See Also</span></span>  
 [<span data-ttu-id="9e0ee-187">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="9e0ee-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
