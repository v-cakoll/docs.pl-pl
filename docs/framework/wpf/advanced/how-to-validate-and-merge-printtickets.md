---
title: 'Instrukcje: Waliduj i scalaj PrintTickets'
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
ms.openlocfilehash: 2be08f5d3c2cd82e50569a105e3fa15f12ad352c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355171"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="b3580-102">Instrukcje: Waliduj i scalaj PrintTickets</span><span class="sxs-lookup"><span data-stu-id="b3580-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="b3580-103">[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Schematu drukowania](https://go.microsoft.com/fwlink/?LinkId=186397) obejmuje elastyczna i rozszerzalna <xref:System.Printing.PrintCapabilities> i <xref:System.Printing.PrintTicket> elementów.</span><span class="sxs-lookup"><span data-stu-id="b3580-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="b3580-104">Pierwsza wyszczególniono możliwości drukarki, a jego Określa, jak urządzenia powinny używać tych możliwości w odniesieniu do określonej sekwencji dokumentów, dokument lub pojedynczej strony.</span><span class="sxs-lookup"><span data-stu-id="b3580-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="b3580-105">Typowe sekwencji zadań dla aplikacji, która obsługuje drukowanie byłoby w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b3580-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1.  <span data-ttu-id="b3580-106">Określ drukarkę możliwości.</span><span class="sxs-lookup"><span data-stu-id="b3580-106">Determine a printer's capabilities.</span></span>  
  
2.  <span data-ttu-id="b3580-107">Konfigurowanie <xref:System.Printing.PrintTicket> na korzystanie z tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="b3580-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3.  <span data-ttu-id="b3580-108">Sprawdź poprawność <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="b3580-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="b3580-109">W tym artykule pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="b3580-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3580-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3580-110">Example</span></span>  
 <span data-ttu-id="b3580-111">W poniższym przykładzie prostego, jesteśmy zainteresowani tylko tego, czy drukarka może obsługiwać dupleksu — drukowania dwustronnego.</span><span class="sxs-lookup"><span data-stu-id="b3580-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="b3580-112">Główne kroki są następujące.</span><span class="sxs-lookup"><span data-stu-id="b3580-112">The major steps are as follows.</span></span>  
  
1.  <span data-ttu-id="b3580-113">Pobierz <xref:System.Printing.PrintCapabilities> obiekt z <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b3580-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2.  <span data-ttu-id="b3580-114">Test na obecność możliwości, które chcesz.</span><span class="sxs-lookup"><span data-stu-id="b3580-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="b3580-115">W poniższym przykładzie przetestujemy <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> właściwość <xref:System.Printing.PrintCapabilities> obiektu na obecność możliwość drukowania po obu stronach arkusz papieru, "Włączanie strony" długo po stronie arkusza.</span><span class="sxs-lookup"><span data-stu-id="b3580-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="b3580-116">Ponieważ <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> jest kolekcją, używamy `Contains` metody <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="b3580-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b3580-117">Ten krok nie jest bezwzględnie konieczne.</span><span class="sxs-lookup"><span data-stu-id="b3580-117">This step is not strictly necessary.</span></span> <span data-ttu-id="b3580-118"><xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Metodę poniżej zostanie zaewidencjonowany przez każde żądanie <xref:System.Printing.PrintTicket> z możliwościami drukarki.</span><span class="sxs-lookup"><span data-stu-id="b3580-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="b3580-119">Jeśli żądana funkcja nie jest obsługiwana przez drukarkę, sterownik drukarki zostanie zastąpiony przez żądanie alternatywnych w <xref:System.Printing.PrintTicket> zwracany przez metodę.</span><span class="sxs-lookup"><span data-stu-id="b3580-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3.  <span data-ttu-id="b3580-120">Jeśli drukarka obsługuje dupleksu, przykładowy kod tworzy <xref:System.Printing.PrintTicket> która poprosi o podanie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="b3580-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="b3580-121">Ale aplikacja nie określa każdej drukarki możliwe ustawienie dostępne w <xref:System.Printing.PrintTicket> elementu.</span><span class="sxs-lookup"><span data-stu-id="b3580-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="b3580-122">Byłoby marnotrawstwa programisty i godziny programu.</span><span class="sxs-lookup"><span data-stu-id="b3580-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="b3580-123">Zamiast tego kod ustawia tylko żądanie dupleksu, a następnie scala to <xref:System.Printing.PrintTicket> z istniejącym, w pełni skonfigurowane i sprawdzeniu poprawności <xref:System.Printing.PrintTicket>, w tym przypadku użytkownika domyślnego <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="b3580-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4.  <span data-ttu-id="b3580-124">W związku z tym przykład wywołuje <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metody do scalenia z nowej, minimalnymi <xref:System.Printing.PrintTicket> z domyślną użytkownika <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="b3580-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="b3580-125">Spowoduje to zwrócenie <xref:System.Printing.ValidationResult> zawierającego nowe <xref:System.Printing.PrintTicket> jako jeden z jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="b3580-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5.  <span data-ttu-id="b3580-126">Następnie testy próbki nowy <xref:System.Printing.PrintTicket> dupleksu żądań.</span><span class="sxs-lookup"><span data-stu-id="b3580-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="b3580-127">Jeśli tak jest, następnie próbki sprawia, że nowy bilet drukowania domyślny dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b3580-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="b3580-128">Jeśli w kroku 2 powyżej miał pozostawiono i drukarki nie obsługują dupleksu długo po stronie, a następnie spowodowałaby testu `false`.</span><span class="sxs-lookup"><span data-stu-id="b3580-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="b3580-129">(Zobacz uwagi powyżej).</span><span class="sxs-lookup"><span data-stu-id="b3580-129">(See the note above.)</span></span>  
  
6.  <span data-ttu-id="b3580-130">Ostatnim krokiem istotne jest aby zatwierdzić zmiany <xref:System.Printing.PrintQueue.UserPrintTicket%2A> właściwość <xref:System.Printing.PrintQueue> z <xref:System.Printing.PrintQueue.Commit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b3580-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="b3580-131">Dlatego, że możesz szybko przetestować, w tym przykładzie, do końca znajduje się poniżej.</span><span class="sxs-lookup"><span data-stu-id="b3580-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="b3580-132">Utwórz projekt i przestrzeń nazw, a następnie wklej fragmenty kodu w tym artykule, w bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b3580-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="b3580-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3580-133">See also</span></span>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="b3580-134">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="b3580-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="b3580-135">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="b3580-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="b3580-136">Drukuj schematu</span><span class="sxs-lookup"><span data-stu-id="b3580-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)
