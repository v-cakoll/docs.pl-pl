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
# <a name="how-to-validate-and-merge-printtickets"></a>Instrukcje: Weryfikowanie i scalanie elementów PrintTickets
Schemat drukowania zawiera elastyczne i rozszerzalne <xref:System.Printing.PrintCapabilities> elementy i <xref:System.Printing.PrintTicket> . [](https://go.microsoft.com/fwlink/?LinkId=186397) [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] Dawniej wyszczególniono możliwości urządzenia drukującego i te informacje określają, jak urządzenie powinno korzystać z tych funkcji w odniesieniu do określonej sekwencji dokumentów, pojedynczego dokumentu lub pojedynczej strony.  
  
 Typową sekwencją zadań dla aplikacji, która obsługuje drukowanie, będzie następująca.  
  
1. Określ możliwości drukarki.  
  
2. Skonfiguruj, <xref:System.Printing.PrintTicket> aby korzystać z tych funkcji.  
  
3. Sprawdź poprawność <xref:System.Printing.PrintTicket>.  
  
 W tym artykule pokazano, jak to zrobić.  
  
## <a name="example"></a>Przykład  
 W prostym przykładzie interesuje tylko, czy drukarka może obsługiwać dupleks — drukowanie dwustronne. Główne kroki są następujące.  
  
1. <xref:System.Printing.PrintCapabilities> Pobierz obiekt <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> za pomocą metody.  
  
2. Przetestuj obecność potrzebnej możliwości. W poniższym przykładzie przetestujemy <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> Właściwość <xref:System.Printing.PrintCapabilities> obiektu w celu wykrycia możliwości drukowania na obu stronach arkusza papieru z "wyłączaniem strony" wzdłuż długiej krawędzi arkusza. Ponieważ <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> jest kolekcją, `Contains` używana jest metoda <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    > Ten krok nie jest ściśle konieczny. Użyta poniżej <xref:System.Printing.PrintTicket> <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metoda sprawdzi każde żądanie w odniesieniu do możliwości drukarki. Jeśli żądana funkcja nie jest obsługiwana przez drukarkę, sterownik drukarki zastępuje alternatywne żądanie w <xref:System.Printing.PrintTicket> zwracanym przez metodę.  
  
3. Jeśli drukarka obsługuje dupleks, przykładowy kod tworzy <xref:System.Printing.PrintTicket> monit o dupleks. Jednak aplikacja nie określa wszystkich możliwych ustawień drukarki dostępnych w <xref:System.Printing.PrintTicket> elemencie. To wasteful zarówno programisty, jak i program. Zamiast tego, kod ustawia tylko żądanie dupleksowania, a następnie scala ten <xref:System.Printing.PrintTicket> element z istniejącym, w pełni skonfigurowanym i zweryfikowanym, <xref:System.Printing.PrintTicket>w tym przypadku, w tym <xref:System.Printing.PrintTicket>przypadku, z wartością domyślną użytkownika.  
  
4. W związku z tym przykład wywołuje <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metodę, aby scalić nowe, minimalne, <xref:System.Printing.PrintTicket> z wartością domyślną <xref:System.Printing.PrintTicket>użytkownika. Zwraca wartość <xref:System.Printing.ValidationResult> , która zawiera nową <xref:System.Printing.PrintTicket> jako jedną z jej właściwości.  
  
5. Następnie próbka przetestuje, <xref:System.Printing.PrintTicket> czy nowe żądania są dwustronne. Jeśli tak, wówczas przykład tworzy nowy domyślny bilet drukowania dla użytkownika. Jeśli krok 2 został pozostawiony, a drukarka nie obsłużył dupleksu wzdłuż długiej strony, test miałby wynik `false`. (Zobacz uwagi powyżej).  
  
6. Ostatni znaczący krok polega na zatwierdzeniu zmiany <xref:System.Printing.PrintQueue.UserPrintTicket%2A> właściwości <xref:System.Printing.PrintQueue> przy użyciu <xref:System.Printing.PrintQueue.Commit%2A> metody.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Dzięki temu możesz szybko przetestować ten przykład, pozostała część jest przedstawiona poniżej. Utwórz projekt i przestrzeń nazw, a następnie wklej fragmenty kodu z tego artykułu do bloku przestrzeni nazw.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)
- [Drukuj schemat](https://go.microsoft.com/fwlink/?LinkId=186397)
