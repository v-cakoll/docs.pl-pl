---
title: Visual Basic — Konwencje kodowania
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f73648888b28c349104a70e78c29eb208d438b78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761692"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="e9e5d-102">Visual Basic — Konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="e9e5d-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="e9e5d-103">Microsoft rozwija przykłady i dokumentację, która jest zgodna z wytycznymi w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="e9e5d-104">Wykonanie tych samych konwencji kodowania możesz osiągnąć następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="e9e5d-105">Twój kod będzie miał jednolity wygląd, tak aby czytelnicy mogli lepiej skupić się na treści, a nie na układzie.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="e9e5d-106">Czytniki rozumieją Twój kod lepiej szybko, ponieważ mogą robić więjsze założenia na podstawie poprzednich doświadczeń.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="e9e5d-107">Można skopiować, zmieniać i utrzymywać kod, aby łatwiej.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-107">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="e9e5d-108">Uzyskujesz pewność, że Twój kod wykazuje,, "Najważniejsze wskazówki" dla języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="e9e5d-109">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="e9e5d-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="e9e5d-110">Aby uzyskać informacje o zasadach nazywania, zobacz [wytyczne dotyczące nazewnictwa](../../../standard/design-guidelines/naming-guidelines.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="e9e5d-111">Nie należy używać "Mój" lub "Mój" jako część nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="e9e5d-112">Praktyka ta tworzy omyłkowe `My` obiektów.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-112">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="e9e5d-113">Nie trzeba zmieniać nazwy obiektów w automatycznie wygenerowany kod, aby je dopasować do wytycznych.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="e9e5d-114">Konwencje układu</span><span class="sxs-lookup"><span data-stu-id="e9e5d-114">Layout Conventions</span></span>  
  
- <span data-ttu-id="e9e5d-115">Wstaw tabulatory jako spacje i Użyj inteligentnego wcięcia z czterokrotnym wcięciem.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="e9e5d-116">Użyj **formatowania kodu automatyczne formatowanie kodu** Aby sformatować kod w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="e9e5d-117">Aby uzyskać więcej informacji, zobacz [opcje, Edytor tekstów, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e9e5d-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="e9e5d-118">Użyj tylko jednej instrukcji na wiersz.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-118">Use only one statement per line.</span></span> <span data-ttu-id="e9e5d-119">Nie używaj znaku separatora wierszy programu Visual Basic (:).</span><span class="sxs-lookup"><span data-stu-id="e9e5d-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="e9e5d-120">Należy unikać znaku kontynuacji wiersza jawne "_" na rzecz niejawnej kontynuacji wiersza wszędzie tam, gdzie pozwala to język.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="e9e5d-121">Użyj tylko jednej deklaracji na wiersz.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-121">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="e9e5d-122">Jeśli **formatowania kodu automatyczne formatowanie kodu** nie formatuje wierszy kontynuacji automatycznie, ręcznie Utwórz wcięcia kontynuacji wierszy na jeden tabulator.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="e9e5d-123">Jednak zawsze wyrównuj do lewej elementy na liście.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="e9e5d-124">Dodaj co najmniej jeden pusty wiersz między definicje metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="e9e5d-125">Konwencje komentowania</span><span class="sxs-lookup"><span data-stu-id="e9e5d-125">Commenting Conventions</span></span>  
  
- <span data-ttu-id="e9e5d-126">Umieść komentarze w osobnym wierszu zamiast na końcu wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="e9e5d-127">Rozpocznij tekst komentarza wielką literą i tekst komentarza zakończenia kropką.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="e9e5d-128">Wstaw jedną spację między ogranicznik komentarza (') i tekst komentarza.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="e9e5d-129">Nie otaczaj komentarzy sformatowanymi blokami ani gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="e9e5d-130">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="e9e5d-130">Program Structure</span></span>  
  
- <span data-ttu-id="e9e5d-131">Kiedy używasz `Main` metody, użyj domyślnego konstruktora dla nowych aplikacji konsoli, a następnie użyj `My` dla argumentów wiersza poleceń.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="e9e5d-132">Wytyczne dotyczące języka</span><span class="sxs-lookup"><span data-stu-id="e9e5d-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="e9e5d-133">Typ danych ciągu</span><span class="sxs-lookup"><span data-stu-id="e9e5d-133">String Data Type</span></span>  
  
- <span data-ttu-id="e9e5d-134">Do łączenia ciągów, użyj handlowe "i" (&).</span><span class="sxs-lookup"><span data-stu-id="e9e5d-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#4)]  
  
- <span data-ttu-id="e9e5d-135">Aby dołączyć ciągi w pętli, należy użyć <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="e9e5d-136">Obniżone Delegaty w procedurach obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e9e5d-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="e9e5d-137">Nie kwalifikuj jawnie argumentów (obiekt i EventArgs) do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="e9e5d-138">Jeśli nie używasz argumentów zdarzeń, które są przekazywane do zdarzenia (na przykład nadawcy jako obiektu, e jako EventArg), użyj swobodnych delegatów i Opuść argumenty zdarzenia w kodzie:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="e9e5d-139">Typ danych bez znaku</span><span class="sxs-lookup"><span data-stu-id="e9e5d-139">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="e9e5d-140">Użyj `Integer` zamiast niepodpisanych typów, z wyjątkiem sytuacji, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="e9e5d-141">Tablice</span><span class="sxs-lookup"><span data-stu-id="e9e5d-141">Arrays</span></span>  
  
- <span data-ttu-id="e9e5d-142">Użyj skróconej składni podczas inicjowania tablic w wierszu deklaracji.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="e9e5d-143">Na przykład użyj następującej składni.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="e9e5d-144">Nie należy używać następującej składni.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="e9e5d-145">Umieść oznaczenie tablicy na typie, a nie na zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="e9e5d-146">Na przykład użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="e9e5d-147">Nie należy używać następującej składni:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="e9e5d-148">Do deklarowania i inicjowania tablic typów podstawowych danych, należy użyć składni {}.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="e9e5d-149">Na przykład użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="e9e5d-150">Nie należy używać następującej składni:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="e9e5d-151">Korzystanie ze słowem kluczowym</span><span class="sxs-lookup"><span data-stu-id="e9e5d-151">Use the With Keyword</span></span>  
 <span data-ttu-id="e9e5d-152">Wprowadzając szereg wywołań do jednego obiektu, należy wziąć pod uwagę przy użyciu `With` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="e9e5d-153">Użyj Try... CATCH i przy użyciu instrukcji, korzystając z obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="e9e5d-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="e9e5d-154">Nie używaj `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="e9e5d-155">Użyj słowa kluczowego IsNot</span><span class="sxs-lookup"><span data-stu-id="e9e5d-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="e9e5d-156">Użyj `IsNot` słowa kluczowego zamiast `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="e9e5d-157">New — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="e9e5d-157">New Keyword</span></span>  
  
- <span data-ttu-id="e9e5d-158">Użyj krótkiego tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-158">Use short instantiation.</span></span> <span data-ttu-id="e9e5d-159">Na przykład użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="e9e5d-160">Poprzedni wiersz jest równoważny następującemu wyrażeniu:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="e9e5d-161">Użyj inicjatorów obiektów dla nowych obiektów, a nie konstruktora bez parametrów:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="e9e5d-162">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e9e5d-162">Event Handling</span></span>  
  
- <span data-ttu-id="e9e5d-163">Użyj `Handles` zamiast `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="e9e5d-164">Użyj `AddressOf`i nie tworzyć wystąpienia pełnomocnika jawnie:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="e9e5d-165">Podczas definiowania zdarzenia, użyj skróconej składni i zezwolić kompilatorowi na zdefiniowanie delegata:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="e9e5d-166">Nie Weryfikuj, czy zdarzenie jest `Nothing` (null) przed wywołaniem `RaiseEvent` metody.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="e9e5d-167">`RaiseEvent` sprawdza, czy `Nothing` przed zzdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="e9e5d-168">Używanie udostępnionych elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="e9e5d-168">Using Shared Members</span></span>  
 <span data-ttu-id="e9e5d-169">Wywołaj `Shared` elementów członkowskich przy użyciu nazwy klasy, nie ze zmiennej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="e9e5d-170">Używanie literałów XML</span><span class="sxs-lookup"><span data-stu-id="e9e5d-170">Use XML Literals</span></span>  
 <span data-ttu-id="e9e5d-171">Literały XML upraszczają najbardziej typowe zadania, które można napotkać podczas pracy z danymi XML (na przykład obciążenie, zapytań i przekształcania).</span><span class="sxs-lookup"><span data-stu-id="e9e5d-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="e9e5d-172">Podczas pracy z danymi XML należy przestrzegać następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-172">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="e9e5d-173">Literały XML umożliwiają tworzenie dokumentów XML i fragmentów zamiast wywoływania interfejsów API XML bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="e9e5d-174">Zaimportuj przestrzenie nazw XML na poziomie pliku lub projektu, aby skorzystać z optymalizacji wydajności w literałach XML.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="e9e5d-175">Właściwości osi XML umożliwiają dostęp do elementów i atrybutów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="e9e5d-176">Użyj wyrażenia osadzone umożliwiają uwzględnienie wartości i tworzenie kodu XML na podstawie istniejących wartości, zamiast przy użyciu wywołań interfejsu API, takich jak `Add` metody:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="e9e5d-177">Zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="e9e5d-177">LINQ Queries</span></span>  
  
- <span data-ttu-id="e9e5d-178">Użyj nazw opisowych dla zmiennych kwerendy:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="e9e5d-179">Zapewnij nazwy elementów w zapytaniu, aby upewnić się, że nazwy właściwości anonimowych typów są kapitalizowane poprawnie przy użyciu obudowy Pascal wielkość liter w wyrazie:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="e9e5d-180">Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłby niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="e9e5d-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="e9e5d-181">Na przykład, jeśli zapytanie zwraca klienta nazwa i identyfikator zamówienia, zmień je zamiast pozostawiania je jako `Name` i `ID` w wyniku:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="e9e5d-182">Użyj wnioskowania o typie w deklaracji zmiennych kwerendy i zmiennych zakresu:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="e9e5d-183">Wyrównaj klauzule zapytania pod `From` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="e9e5d-184">Użyj `Where` klauzule przed innymi klauzulami kwerend powoduje, że późniejsze klauzule kwerend działają na zestawie filtrowanych danych:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="e9e5d-185">Użyj `Join` klauzuli umożliwia jawne zdefiniowanie operacji join w przeciwieństwie `Where` klauzuli umożliwia niejawnie określenie operacji join:</span><span class="sxs-lookup"><span data-stu-id="e9e5d-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="e9e5d-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9e5d-186">See also</span></span>

- [<span data-ttu-id="e9e5d-187">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="e9e5d-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
