---
title: "Jak walidować i scalać PrintTickets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5cf2091d50433bb936b3d4976d1c3eabea73edc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="5147a-102">Jak walidować i scalać PrintTickets</span><span class="sxs-lookup"><span data-stu-id="5147a-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="5147a-103">[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Schematu drukowania](http://go.microsoft.com/fwlink/?LinkId=186397) obejmuje elastyczny i rozszerzalny <xref:System.Printing.PrintCapabilities> i <xref:System.Printing.PrintTicket> elementy.</span><span class="sxs-lookup"><span data-stu-id="5147a-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](http://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="5147a-104">Pierwsza itemizes możliwości drukarki, a drugie Określa, jak urządzenia należy używać tych funkcji w odniesieniu do określonej sekwencji dokumentów, pojedynczy dokument lub pojedynczej strony.</span><span class="sxs-lookup"><span data-stu-id="5147a-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="5147a-105">Typowy sekwencji zadań dla aplikacji, która obsługuje drukowanie będą w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5147a-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1.  <span data-ttu-id="5147a-106">Należy określić możliwości drukarki.</span><span class="sxs-lookup"><span data-stu-id="5147a-106">Determine a printer's capabilities.</span></span>  
  
2.  <span data-ttu-id="5147a-107">Skonfiguruj <xref:System.Printing.PrintTicket> używać tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="5147a-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3.  <span data-ttu-id="5147a-108">Sprawdź poprawność <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="5147a-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="5147a-109">W tym artykule pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="5147a-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5147a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5147a-110">Example</span></span>  
 <span data-ttu-id="5147a-111">W poniższym przykładzie prosty, Dbamy o tylko czy drukarka może obsługiwać dupleksu — druku dwustronnego.</span><span class="sxs-lookup"><span data-stu-id="5147a-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="5147a-112">Oto główne kroki.</span><span class="sxs-lookup"><span data-stu-id="5147a-112">The major steps are as follows.</span></span>  
  
1.  <span data-ttu-id="5147a-113">Pobierz <xref:System.Printing.PrintCapabilities> obiekt z <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5147a-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2.  <span data-ttu-id="5147a-114">Test na obecność możliwości, który ma.</span><span class="sxs-lookup"><span data-stu-id="5147a-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="5147a-115">W poniższym przykładzie firma Microsoft testuje <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> właściwość <xref:System.Printing.PrintCapabilities> obiekt obecność możliwości drukowania po obu stronach arkusza papieru "zwroty strony" wzdłuż długa po stronie arkusza.</span><span class="sxs-lookup"><span data-stu-id="5147a-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="5147a-116">Ponieważ <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> jest kolekcją, używamy `Contains` metody <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="5147a-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5147a-117">Ten krok nie jest bezwzględnie konieczne.</span><span class="sxs-lookup"><span data-stu-id="5147a-117">This step is not strictly necessary.</span></span> <span data-ttu-id="5147a-118"><xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Metodę poniżej sprawdzi każdego żądania <xref:System.Printing.PrintTicket> z możliwościami drukarki.</span><span class="sxs-lookup"><span data-stu-id="5147a-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="5147a-119">Jeśli żądana funkcja nie jest obsługiwana przez drukarkę, alternatywne żądania w zostanie zastąpiony przez sterownik drukarki <xref:System.Printing.PrintTicket> zwracany przez metodę.</span><span class="sxs-lookup"><span data-stu-id="5147a-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3.  <span data-ttu-id="5147a-120">Jeśli drukarka obsługuje dupleksu, przykładowy kod tworzy <xref:System.Printing.PrintTicket> która poprosi o podanie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="5147a-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="5147a-121">Ale aplikacja nie określa każdej drukarki możliwe ustawienie dostępne w <xref:System.Printing.PrintTicket> elementu.</span><span class="sxs-lookup"><span data-stu-id="5147a-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="5147a-122">Wyniesie niepotrzebne programisty i godziny programu.</span><span class="sxs-lookup"><span data-stu-id="5147a-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="5147a-123">Zamiast tego kod ustawia tylko żądanie dupleksu i następnie scala to <xref:System.Printing.PrintTicket> z istniejącym, w pełni skonfigurowana i zweryfikowany, dlatego <xref:System.Printing.PrintTicket>, w tym przypadku domyślnego użytkownika <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="5147a-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4.  <span data-ttu-id="5147a-124">W związku z tym przykład wywołuje <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metody można scalić nowych, minimalnym, <xref:System.Printing.PrintTicket> z domyślnymi użytkownika <xref:System.Printing.PrintTicket>.</span><span class="sxs-lookup"><span data-stu-id="5147a-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="5147a-125">To polecenie zwróci <xref:System.Printing.ValidationResult> zawiera nowe <xref:System.Printing.PrintTicket> jako jeden z jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="5147a-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5.  <span data-ttu-id="5147a-126">Przykład następnie testów, które nowe <xref:System.Printing.PrintTicket> żądań dupleksu.</span><span class="sxs-lookup"><span data-stu-id="5147a-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="5147a-127">Jeśli tak, próbki tworzy nowy domyślny biletu wydruku dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5147a-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="5147a-128">Jeśli krok 2. powyżej zostałyby pozostawione i drukarki nie obsługuje dupleksu wzdłuż krawędzi długi, a następnie spowodowałaby testu `false`.</span><span class="sxs-lookup"><span data-stu-id="5147a-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="5147a-129">(Zobacz uwagi powyżej).</span><span class="sxs-lookup"><span data-stu-id="5147a-129">(See the note above.)</span></span>  
  
6.  <span data-ttu-id="5147a-130">Ostatnim krokiem istotne jest Zatwierdź zmiany <xref:System.Printing.PrintQueue.UserPrintTicket%2A> właściwość <xref:System.Printing.PrintQueue> z <xref:System.Printing.PrintQueue.Commit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5147a-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="5147a-131">Tak, aby w tym przykładzie można szybko sprawdzić, do końca znajduje się poniżej.</span><span class="sxs-lookup"><span data-stu-id="5147a-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="5147a-132">Tworzenie projektu i przestrzeni nazw, a następnie wklej fragmenty kodu w tym artykule do bloku przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5147a-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="5147a-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5147a-133">See Also</span></span>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="5147a-134">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="5147a-134">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="5147a-135">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="5147a-135">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="5147a-136">Drukowanie schematu</span><span class="sxs-lookup"><span data-stu-id="5147a-136">Print Schema</span></span>](http://go.microsoft.com/fwlink/?LinkId=186397)
