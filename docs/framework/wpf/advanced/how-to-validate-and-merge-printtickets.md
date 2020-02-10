---
title: Jak walidować i scalać PrintTickets
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
ms.openlocfilehash: bd7f399555b343a52ec6f36aa3b8c706747d8b06
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094530"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="59e32-102">Jak walidować i scalać PrintTickets</span><span class="sxs-lookup"><span data-stu-id="59e32-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="59e32-103">[Schemat drukowania](/windows/win32/printdocs/printschema) systemu Microsoft Windows zawiera elastyczne i rozszerzalne <xref:System.Printing.PrintCapabilities> i <xref:System.Printing.PrintTicket> elementy.</span><span class="sxs-lookup"><span data-stu-id="59e32-103">The Microsoft Windows [Print Schema](/windows/win32/printdocs/printschema) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="59e32-104">Dawniej wyszczególniono możliwości urządzenia drukującego i te informacje określają, jak urządzenie powinno korzystać z tych funkcji w odniesieniu do określonej sekwencji dokumentów, pojedynczego dokumentu lub pojedynczej strony.</span><span class="sxs-lookup"><span data-stu-id="59e32-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="59e32-105">Typową sekwencją zadań dla aplikacji, która obsługuje drukowanie, będzie następująca.</span><span class="sxs-lookup"><span data-stu-id="59e32-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="59e32-106">Określ możliwości drukarki.</span><span class="sxs-lookup"><span data-stu-id="59e32-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="59e32-107">Skonfiguruj <xref:System.Printing.PrintTicket>, aby korzystać z tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="59e32-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="59e32-108">Sprawdź poprawność <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="59e32-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="59e32-109">W tym artykule pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="59e32-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59e32-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="59e32-110">Example</span></span>  
 <span data-ttu-id="59e32-111">W prostym przykładzie interesuje tylko, czy drukarka może obsługiwać dupleks — drukowanie dwustronne.</span><span class="sxs-lookup"><span data-stu-id="59e32-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="59e32-112">Główne kroki są następujące.</span><span class="sxs-lookup"><span data-stu-id="59e32-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="59e32-113">Pobierz obiekt <xref:System.Printing.PrintCapabilities> za pomocą metody <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>.</span><span class="sxs-lookup"><span data-stu-id="59e32-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="59e32-114">Przetestuj obecność potrzebnej możliwości.</span><span class="sxs-lookup"><span data-stu-id="59e32-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="59e32-115">W poniższym przykładzie przetestujemy Właściwość <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> obiektu <xref:System.Printing.PrintCapabilities>, aby mieć możliwość drukowania na obu stronach arkusza papieru z "wyłączaniem strony" wzdłuż długiej krawędzi arkusza.</span><span class="sxs-lookup"><span data-stu-id="59e32-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="59e32-116">Ponieważ <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> jest kolekcją, używamy metody `Contains` <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="59e32-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="59e32-117">Ten krok nie jest ściśle konieczny.</span><span class="sxs-lookup"><span data-stu-id="59e32-117">This step is not strictly necessary.</span></span> <span data-ttu-id="59e32-118">Użyta poniżej metoda <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> sprawdzi każde żądanie w <xref:System.Printing.PrintTicket> z funkcjami drukarki.</span><span class="sxs-lookup"><span data-stu-id="59e32-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="59e32-119">Jeśli żądana funkcja nie jest obsługiwana przez drukarkę, sterownik drukarki spowoduje zastąpienie alternatywnego żądania w <xref:System.Printing.PrintTicket> zwróconego przez metodę.</span><span class="sxs-lookup"><span data-stu-id="59e32-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="59e32-120">Jeśli drukarka obsługuje dupleks, przykładowy kod tworzy <xref:System.Printing.PrintTicket>, który żąda dupleksu.</span><span class="sxs-lookup"><span data-stu-id="59e32-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="59e32-121">Jednak aplikacja nie określa wszystkich możliwych ustawień drukarki dostępnych w elemencie <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="59e32-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="59e32-122">To wasteful zarówno programisty, jak i program.</span><span class="sxs-lookup"><span data-stu-id="59e32-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="59e32-123">Zamiast tego, kod ustawia tylko żądanie dupleksowania, a następnie scala ten <xref:System.Printing.PrintTicket> z istniejącym, w pełni skonfigurowanym i sprawdzonym, <xref:System.Printing.PrintTicket>, w tym przypadku, <xref:System.Printing.PrintTicket>użytkownika domyślnego.</span><span class="sxs-lookup"><span data-stu-id="59e32-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="59e32-124">W związku z tym przykład wywołuje metodę <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>, aby scalić nowe, minimalne <xref:System.Printing.PrintTicket> z domyślną <xref:System.Printing.PrintTicket>użytkownika.</span><span class="sxs-lookup"><span data-stu-id="59e32-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="59e32-125">Spowoduje to zwrócenie <xref:System.Printing.ValidationResult>, która zawiera nowe <xref:System.Printing.PrintTicket> jako jedną z jej właściwości.</span><span class="sxs-lookup"><span data-stu-id="59e32-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="59e32-126">Następnie próbka przetestuje, że nowe <xref:System.Printing.PrintTicket> żądania dupleksowania.</span><span class="sxs-lookup"><span data-stu-id="59e32-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="59e32-127">Jeśli tak, wówczas przykład tworzy nowy domyślny bilet drukowania dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="59e32-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="59e32-128">Jeśli krok 2 został pozostawiony, a drukarka nie obsługiwała dupleksu wzdłuż długiej strony, test miałby wynik `false`.</span><span class="sxs-lookup"><span data-stu-id="59e32-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="59e32-129">(Zobacz uwagi powyżej).</span><span class="sxs-lookup"><span data-stu-id="59e32-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="59e32-130">Ostatni znaczący krok polega na zatwierdzeniu zmiany właściwości <xref:System.Printing.PrintQueue.UserPrintTicket%2A> <xref:System.Printing.PrintQueue> za pomocą metody <xref:System.Printing.PrintQueue.Commit%2A>.</span><span class="sxs-lookup"><span data-stu-id="59e32-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="59e32-131">Dzięki temu możesz szybko przetestować ten przykład, pozostała część jest przedstawiona poniżej.</span><span class="sxs-lookup"><span data-stu-id="59e32-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="59e32-132">Utwórz projekt i przestrzeń nazw, a następnie wklej fragmenty kodu z tego artykułu do bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="59e32-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="59e32-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59e32-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="59e32-134">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="59e32-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="59e32-135">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="59e32-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="59e32-136">Drukuj schemat</span><span class="sxs-lookup"><span data-stu-id="59e32-136">Print Schema</span></span>](/windows/win32/printdocs/printschema)
