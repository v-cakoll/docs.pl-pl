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
# <a name="how-to-validate-and-merge-printtickets"></a>Jak walidować i scalać PrintTickets
[Schemat drukowania](/windows/win32/printdocs/printschema) systemu Microsoft Windows zawiera elastyczne i rozszerzalne <xref:System.Printing.PrintCapabilities> i <xref:System.Printing.PrintTicket> elementy. Dawniej wyszczególniono możliwości urządzenia drukującego i te informacje określają, jak urządzenie powinno korzystać z tych funkcji w odniesieniu do określonej sekwencji dokumentów, pojedynczego dokumentu lub pojedynczej strony.  
  
 Typową sekwencją zadań dla aplikacji, która obsługuje drukowanie, będzie następująca.  
  
1. Określ możliwości drukarki.  
  
2. Skonfiguruj <xref:System.Printing.PrintTicket>, aby korzystać z tych funkcji.  
  
3. Sprawdź poprawność <xref:System.Printing.PrintTicket>.  
  
 W tym artykule pokazano, jak to zrobić.  
  
## <a name="example"></a>Przykład  
 W prostym przykładzie interesuje tylko, czy drukarka może obsługiwać dupleks — drukowanie dwustronne. Główne kroki są następujące.  
  
1. Pobierz obiekt <xref:System.Printing.PrintCapabilities> za pomocą metody <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>.  
  
2. Przetestuj obecność potrzebnej możliwości. W poniższym przykładzie przetestujemy Właściwość <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> obiektu <xref:System.Printing.PrintCapabilities>, aby mieć możliwość drukowania na obu stronach arkusza papieru z "wyłączaniem strony" wzdłuż długiej krawędzi arkusza. Ponieważ <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> jest kolekcją, używamy metody `Contains` <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    > Ten krok nie jest ściśle konieczny. Użyta poniżej metoda <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> sprawdzi każde żądanie w <xref:System.Printing.PrintTicket> z funkcjami drukarki. Jeśli żądana funkcja nie jest obsługiwana przez drukarkę, sterownik drukarki spowoduje zastąpienie alternatywnego żądania w <xref:System.Printing.PrintTicket> zwróconego przez metodę.  
  
3. Jeśli drukarka obsługuje dupleks, przykładowy kod tworzy <xref:System.Printing.PrintTicket>, który żąda dupleksu. Jednak aplikacja nie określa wszystkich możliwych ustawień drukarki dostępnych w elemencie <xref:System.Printing.PrintTicket>. To wasteful zarówno programisty, jak i program. Zamiast tego, kod ustawia tylko żądanie dupleksowania, a następnie scala ten <xref:System.Printing.PrintTicket> z istniejącym, w pełni skonfigurowanym i sprawdzonym, <xref:System.Printing.PrintTicket>, w tym przypadku, <xref:System.Printing.PrintTicket>użytkownika domyślnego.  
  
4. W związku z tym przykład wywołuje metodę <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>, aby scalić nowe, minimalne <xref:System.Printing.PrintTicket> z domyślną <xref:System.Printing.PrintTicket>użytkownika. Spowoduje to zwrócenie <xref:System.Printing.ValidationResult>, która zawiera nowe <xref:System.Printing.PrintTicket> jako jedną z jej właściwości.  
  
5. Następnie próbka przetestuje, że nowe <xref:System.Printing.PrintTicket> żądania dupleksowania. Jeśli tak, wówczas przykład tworzy nowy domyślny bilet drukowania dla użytkownika. Jeśli krok 2 został pozostawiony, a drukarka nie obsługiwała dupleksu wzdłuż długiej strony, test miałby wynik `false`. (Zobacz uwagi powyżej).  
  
6. Ostatni znaczący krok polega na zatwierdzeniu zmiany właściwości <xref:System.Printing.PrintQueue.UserPrintTicket%2A> <xref:System.Printing.PrintQueue> za pomocą metody <xref:System.Printing.PrintQueue.Commit%2A>.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Dzięki temu możesz szybko przetestować ten przykład, pozostała część jest przedstawiona poniżej. Utwórz projekt i przestrzeń nazw, a następnie wklej fragmenty kodu z tego artykułu do bloku przestrzeni nazw.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)
- [Drukuj schemat](/windows/win32/printdocs/printschema)
