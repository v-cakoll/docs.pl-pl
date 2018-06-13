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
ms.openlocfilehash: 11160d7ec59914afbe501ba731c0c04a85ffc4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548496"
---
# <a name="how-to-validate-and-merge-printtickets"></a>Jak walidować i scalać PrintTickets
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Schematu drukowania](http://go.microsoft.com/fwlink/?LinkId=186397) obejmuje elastyczny i rozszerzalny <xref:System.Printing.PrintCapabilities> i <xref:System.Printing.PrintTicket> elementy. Pierwsza itemizes możliwości drukarki, a drugie Określa, jak urządzenia należy używać tych funkcji w odniesieniu do określonej sekwencji dokumentów, pojedynczy dokument lub pojedynczej strony.  
  
 Typowy sekwencji zadań dla aplikacji, która obsługuje drukowanie będą w następujący sposób.  
  
1.  Należy określić możliwości drukarki.  
  
2.  Skonfiguruj <xref:System.Printing.PrintTicket> używać tych funkcji.  
  
3.  Sprawdź poprawność <xref:System.Printing.PrintTicket>.  
  
 W tym artykule pokazano, jak to zrobić.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie prosty, Dbamy o tylko czy drukarka może obsługiwać dupleksu — druku dwustronnego. Oto główne kroki.  
  
1.  Pobierz <xref:System.Printing.PrintCapabilities> obiekt z <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metody.  
  
2.  Test na obecność możliwości, który ma. W poniższym przykładzie firma Microsoft testuje <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> właściwość <xref:System.Printing.PrintCapabilities> obiekt obecność możliwości drukowania po obu stronach arkusza papieru "zwroty strony" wzdłuż długa po stronie arkusza. Ponieważ <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> jest kolekcją, używamy `Contains` metody <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    >  Ten krok nie jest bezwzględnie konieczne. <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Metodę poniżej sprawdzi każdego żądania <xref:System.Printing.PrintTicket> z możliwościami drukarki. Jeśli żądana funkcja nie jest obsługiwana przez drukarkę, alternatywne żądania w zostanie zastąpiony przez sterownik drukarki <xref:System.Printing.PrintTicket> zwracany przez metodę.  
  
3.  Jeśli drukarka obsługuje dupleksu, przykładowy kod tworzy <xref:System.Printing.PrintTicket> która poprosi o podanie dupleksu. Ale aplikacja nie określa każdej drukarki możliwe ustawienie dostępne w <xref:System.Printing.PrintTicket> elementu. Wyniesie niepotrzebne programisty i godziny programu. Zamiast tego kod ustawia tylko żądanie dupleksu i następnie scala to <xref:System.Printing.PrintTicket> z istniejącym, w pełni skonfigurowana i zweryfikowany, dlatego <xref:System.Printing.PrintTicket>, w tym przypadku domyślnego użytkownika <xref:System.Printing.PrintTicket>.  
  
4.  W związku z tym przykład wywołuje <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metody można scalić nowych, minimalnym, <xref:System.Printing.PrintTicket> z domyślnymi użytkownika <xref:System.Printing.PrintTicket>. To polecenie zwróci <xref:System.Printing.ValidationResult> zawiera nowe <xref:System.Printing.PrintTicket> jako jeden z jego właściwości.  
  
5.  Przykład następnie testów, które nowe <xref:System.Printing.PrintTicket> żądań dupleksu. Jeśli tak, próbki tworzy nowy domyślny biletu wydruku dla użytkownika. Jeśli krok 2. powyżej zostałyby pozostawione i drukarki nie obsługuje dupleksu wzdłuż krawędzi długi, a następnie spowodowałaby testu `false`. (Zobacz uwagi powyżej).  
  
6.  Ostatnim krokiem istotne jest Zatwierdź zmiany <xref:System.Printing.PrintQueue.UserPrintTicket%2A> właściwość <xref:System.Printing.PrintQueue> z <xref:System.Printing.PrintQueue.Commit%2A> metody.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Tak, aby w tym przykładzie można szybko sprawdzić, do końca znajduje się poniżej. Tworzenie projektu i przestrzeni nazw, a następnie wklej fragmenty kodu w tym artykule do bloku przestrzeni nazw.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Przegląd drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Drukowanie schematu](http://go.microsoft.com/fwlink/?LinkId=186397)
