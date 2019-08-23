---
title: 'Instrukcje: Weryfikowanie i scalanie elementów PrintTickets'
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
ms.openlocfilehash: 9e5242c07179501e6b39840a36f8dd6364d65b84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918346"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="a298f-102">Instrukcje: Weryfikowanie i scalanie elementów PrintTickets</span><span class="sxs-lookup"><span data-stu-id="a298f-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="a298f-103">Schemat drukowania zawiera elastyczne i rozszerzalne <xref:System.Printing.PrintCapabilities> elementy i <xref:System.Printing.PrintTicket> . [](https://go.microsoft.com/fwlink/?LinkId=186397) [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a298f-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="a298f-104">Dawniej wyszczególniono możliwości urządzenia drukującego i te informacje określają, jak urządzenie powinno korzystać z tych funkcji w odniesieniu do określonej sekwencji dokumentów, pojedynczego dokumentu lub pojedynczej strony.</span><span class="sxs-lookup"><span data-stu-id="a298f-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="a298f-105">Typową sekwencją zadań dla aplikacji, która obsługuje drukowanie, będzie następująca.</span><span class="sxs-lookup"><span data-stu-id="a298f-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="a298f-106">Określ możliwości drukarki.</span><span class="sxs-lookup"><span data-stu-id="a298f-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="a298f-107">Skonfiguruj, <xref:System.Printing.PrintTicket> aby korzystać z tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a298f-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="a298f-108">Sprawdź poprawność <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="a298f-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="a298f-109">W tym artykule pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="a298f-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a298f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a298f-110">Example</span></span>  
 <span data-ttu-id="a298f-111">W prostym przykładzie interesuje tylko, czy drukarka może obsługiwać dupleks — drukowanie dwustronne.</span><span class="sxs-lookup"><span data-stu-id="a298f-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="a298f-112">Główne kroki są następujące.</span><span class="sxs-lookup"><span data-stu-id="a298f-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="a298f-113"><xref:System.Printing.PrintCapabilities> Pobierz obiekt <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="a298f-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="a298f-114">Przetestuj obecność potrzebnej możliwości.</span><span class="sxs-lookup"><span data-stu-id="a298f-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="a298f-115">W poniższym przykładzie przetestujemy <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> Właściwość <xref:System.Printing.PrintCapabilities> obiektu w celu wykrycia możliwości drukowania na obu stronach arkusza papieru z "wyłączaniem strony" wzdłuż długiej krawędzi arkusza.</span><span class="sxs-lookup"><span data-stu-id="a298f-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="a298f-116">Ponieważ <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> jest kolekcją, `Contains` używana jest metoda <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="a298f-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a298f-117">Ten krok nie jest ściśle konieczny.</span><span class="sxs-lookup"><span data-stu-id="a298f-117">This step is not strictly necessary.</span></span> <span data-ttu-id="a298f-118">Użyta poniżej <xref:System.Printing.PrintTicket> <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metoda sprawdzi każde żądanie w odniesieniu do możliwości drukarki.</span><span class="sxs-lookup"><span data-stu-id="a298f-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="a298f-119">Jeśli żądana funkcja nie jest obsługiwana przez drukarkę, sterownik drukarki zastępuje alternatywne żądanie w <xref:System.Printing.PrintTicket> zwracanym przez metodę.</span><span class="sxs-lookup"><span data-stu-id="a298f-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="a298f-120">Jeśli drukarka obsługuje dupleks, przykładowy kod tworzy <xref:System.Printing.PrintTicket> monit o dupleks.</span><span class="sxs-lookup"><span data-stu-id="a298f-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="a298f-121">Jednak aplikacja nie określa wszystkich możliwych ustawień drukarki dostępnych w <xref:System.Printing.PrintTicket> elemencie.</span><span class="sxs-lookup"><span data-stu-id="a298f-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="a298f-122">To wasteful zarówno programisty, jak i program.</span><span class="sxs-lookup"><span data-stu-id="a298f-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="a298f-123">Zamiast tego, kod ustawia tylko żądanie dupleksowania, a następnie scala ten <xref:System.Printing.PrintTicket> element z istniejącym, w pełni skonfigurowanym i zweryfikowanym, <xref:System.Printing.PrintTicket>w tym przypadku, w tym <xref:System.Printing.PrintTicket>przypadku, z wartością domyślną użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a298f-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="a298f-124">W związku z tym przykład wywołuje <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metodę, aby scalić nowe, minimalne, <xref:System.Printing.PrintTicket> z wartością domyślną <xref:System.Printing.PrintTicket>użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a298f-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="a298f-125">Zwraca wartość <xref:System.Printing.ValidationResult> , która zawiera nową <xref:System.Printing.PrintTicket> jako jedną z jej właściwości.</span><span class="sxs-lookup"><span data-stu-id="a298f-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="a298f-126">Następnie próbka przetestuje, <xref:System.Printing.PrintTicket> czy nowe żądania są dwustronne.</span><span class="sxs-lookup"><span data-stu-id="a298f-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="a298f-127">Jeśli tak, wówczas przykład tworzy nowy domyślny bilet drukowania dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a298f-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="a298f-128">Jeśli krok 2 został pozostawiony, a drukarka nie obsłużył dupleksu wzdłuż długiej strony, test miałby wynik `false`.</span><span class="sxs-lookup"><span data-stu-id="a298f-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="a298f-129">(Zobacz uwagi powyżej).</span><span class="sxs-lookup"><span data-stu-id="a298f-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="a298f-130">Ostatni znaczący krok polega na zatwierdzeniu zmiany <xref:System.Printing.PrintQueue.UserPrintTicket%2A> właściwości <xref:System.Printing.PrintQueue> przy użyciu <xref:System.Printing.PrintQueue.Commit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a298f-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="a298f-131">Dzięki temu możesz szybko przetestować ten przykład, pozostała część jest przedstawiona poniżej.</span><span class="sxs-lookup"><span data-stu-id="a298f-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="a298f-132">Utwórz projekt i przestrzeń nazw, a następnie wklej fragmenty kodu z tego artykułu do bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a298f-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="a298f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a298f-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="a298f-134">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="a298f-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="a298f-135">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="a298f-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="a298f-136">Drukuj schemat</span><span class="sxs-lookup"><span data-stu-id="a298f-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)
