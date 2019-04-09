---
title: Przegląd Drukowanie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: 2aeafa7065b587497fb6f3b23605c21dca291cd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075863"
---
# <a name="printing-overview"></a>Przegląd Drukowanie
Za pomocą programu Microsoft .NET Framework, deweloperzy aplikacji przy użyciu Windows Presentation Foundation (WPF) mają bogaty zestaw nowych Zarządzanie systemem drukowania i wydruku [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. Za pomocą [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], niektóre z tych rozszerzeń systemu drukowania są również dostępne dla programistów tworzących [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji i deweloperzy korzystający z niezarządzanego kodu. W ramach tej nowej funkcji jest nowy [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] format pliku i [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ścieżka wydruku.  
  
 Ten temat zawiera następujące sekcje.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>Temat XPS  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] jest format dokumentu elektronicznego, format pliku buforu i języka opisu strony. Jest format Otwórz dokument, który używa [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]i innych standardów branżowych, do tworzenia dokumentów dla wielu platform. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Upraszcza to proces, za pomocą którego cyfrowe dokumenty są utworzone, udostępniony, drukowane, wyświetlać i archiwizowane. Aby uzyskać dodatkowe informacje na temat [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], zobacz [dokumenty XPS](/windows/desktop/printdocs/documents).  
  
 Kilka technik do drukowania [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] na podstawie zawartości przy użyciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zostały przedstawione w [programowe drukowanie plików XPS](how-to-programmatically-print-xps-files.md). Może okazać się przydatne odwołać te przykłady podczas przeglądu zawartości znajdujących się w tym temacie. (Deweloperzy niezarządzany kod powinien zostać wyświetlony dokumentacji [funkcja MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Windows Forms deweloperzy muszą używać [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] w <xref:System.Drawing.Printing> przestrzeni nazw, który nie obsługuje pełnej [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ścieżka wydruku, ale obsługa ma ścieżkę drukowania hybrydowego GDI do plików XPS. Zobacz **architektura ścieżka wydruku** poniżej.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Ścieżka wydruku XPS  
 [!INCLUDE[TLA#tla_metro](../../../../includes/tlasharptla-metro-md.md)] Ścieżka wydruku jest nowym [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] funkcja, która redefiniuje jak drukowanie odbywa się w aplikacji Windows. Ponieważ [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] można zastąpić języka prezentacji dokumentu, (na przykład RTF), bufor wydruku formatu (WMF) i język opisu strony (na przykład PCL lub Postscript); obsługuje nową ścieżkę drukowania [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] format z aplikacji Publikacja do przetwarzania końcowego do sterownika drukarki lub urządzenia.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Ścieżka wydruku jest oparty na [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] modelu sterownika drukarki (XPSDrv), która zapewnia kilka korzyści dla deweloperów, takie jak [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] drukowania, Ulepszona obsługa kolorów i znaczne zwiększenie wydajności drukowania. (Aby uzyskać więcej informacji o XPSDrv, zobacz [dokumentację Windows Driver Kit](/windows-hardware/drivers/).)  
  
 Działanie bufor wydruku dla [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentów jest zasadniczo taki sam, jak w poprzednich wersjach systemu Windows. Jednak został rozszerzony w celu obsługi [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżka wydruku oprócz istniejącej [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżka wydruku. Nowa ścieżka wydruku natywnie wykorzystuje [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] pliku buforu. While napisanych dla wcześniejszych wersji sterowników drukarek trybu użytkownika [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] będą nadal działać, [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sterownika drukarki (XPSDrv) jest wymagana, aby można było używać [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżka wydruku.  
  
 Korzyści wynikające z [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżka wydruku jest znaczna i obejmują:  
  
-   [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] obsługa drukowania  
  
-   Macierzysta obsługa Profile zaawansowane kolorów, które obejmują 32 bitów na kanał, CMYK, o nazwie kolory, n farby i natywną obsługę przejrzystości i gradientów.  
  
-   Zwiększona wydajność wydruku dla obu .NET Framework i [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] na podstawie aplikacji.  
  
-   Standardem branżowym [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formatu.  
  
 W przypadku podstawowych scenariuszy wydruku a proste i intuicyjne [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] dostępnej za pomocą pojedynczego punktu wejścia do przesłania interfejsu, konfiguracji i zadania użytkownika. W przypadku zaawansowanych scenariuszy dodatkowa pomoc techniczna jest dodawany do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dostosowywania (lub nie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na wszystkich), synchroniczna lub asynchroniczna drukowanie i batch możliwość drukowania. Obie udostępniają Obsługa drukowania w trybie pełnej lub częściowej relacji zaufania.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] zaprojektowano pod kątem rozszerzalności na uwadze. Za pomocą strukturę rozszerzalności, funkcje i możliwości mogą być dodawane do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] w sposób moduły. Rozszerzalność funkcje obejmują:  
  
-   Drukowanie schematu. Schemat publicznej jest regularnie aktualizowana, a także umożliwia szybkie rozszerzenie możliwości urządzenia. (Zobacz **PrintTicket — i printcapabilities —** poniżej.)  
  
-   Potok rozszerzonego filtru. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Potoku filtru (XPSDrv) sterownika drukarki zaprojektowano tak, aby włączyć drukowanie bezpośrednie i skalowalne [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentów. Aby uzyskać więcej informacji, zobacz [sterowników drukarek XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Ścieżka wydruku architektury  
 Podczas gdy obie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i obsługę aplikacji programu .NET Framework [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i używać w aplikacjach Windows Forms [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] konwersji, aby można było utworzyć [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sformatowaną zawartość dla [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]sterownika drukarki (XPSDrv). Te aplikacje nie są wymagane do użycia [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżka wydruku i mogą w dalszym ciągu używać [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] na podstawie drukowania. Jednak większość [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcje i rozszerzenia są dostępne tylko dla aplikacji przeznaczonych dla [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżka wydruku.  
  
 Umożliwia korzystanie z drukarek oparte na XPSDrv przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji Windows Forms i [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sterownika drukarki (XPSDrv) obsługuje konwersję [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formatu. XPSDrv model zapewnia również konwerter służący do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formatu, aby [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji można wydrukować [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentów. Dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje, konwersja [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] format jest wykonywane automatycznie przez <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> klasy zawsze wtedy, gdy nie ma kolejki wydruku docelowy operacji zapisu Sterownik XPSDrv. (Nie można wydrukować w aplikacjach Windows Forms [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty.)  
  
 Poniższa ilustracja przedstawia podsystem wydruku i definiuje fragmenty, dostarczone przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]i fragmenty zdefiniowane przez producentów sprzętu i oprogramowania:  
  
 ![Zrzut ekranu pokazuje, że system drukowania XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Drukowanie plików XPS podstawowe  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definiuje zarówno podstawowe i zaawansowane [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Dla tych aplikacji, które nie wymagają rozbudowane drukowanie dostosowywania lub dostęp do pełnego [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] zestawu funkcji podstawowych drukowania Pomoc techniczna jest dostępna. Podstawowa pomoc techniczna drukowania jest dostępna za pośrednictwem formantu w oknie dialogowym drukowania, który wymaga minimalnej konfiguracji i funkcje powszechnie znane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Wiele [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcji dostępnych za pomocą tego uproszczony model drukowania.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrola zapewnia jeden punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguracji i [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] przesyłania zadania. Aby uzyskać informacje o sposobie tworzenia instancji i korzystanie z kontrolki, zobacz [Wywołaj okno dialogowe Drukuj](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Zaawansowane XPS, drukowanie  
 Aby dostęp do pełnego zestawu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcje zaawansowane drukowania [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] musi być używana. Kilka istotnych [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] są opisane bardziej szczegółowo poniżej. Aby uzyskać pełną listę [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżka wydruku [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], zobacz <xref:System.Windows.Xps> i <xref:System.Printing> odwołania do przestrzeni nazw.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket — i printcapabilities —  
 <xref:System.Printing.PrintTicket> i <xref:System.Printing.PrintCapabilities> klasy stanowiących zaawansowanych [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcji. Oba typy obiektów są [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] sformatowane struktury zorientowane na drukowanie funkcji, takich jak sortowanie, drukowania dwustronnego, zszywanie itp. Te struktury są zdefiniowane w schemacie drukowania. A <xref:System.Printing.PrintTicket> powoduje, że drukarki sposób przetwarzania zadania drukowania. <xref:System.Printing.PrintCapabilities> Klasa definiuje możliwościach drukarki. Sondując możliwościach drukarki, <xref:System.Printing.PrintTicket> mogą być tworzone, że wykorzystuje pełną drukarki na obsługiwane funkcje. Podobnie można uniknąć nieobsługiwanych funkcji.  
  
 Poniższy przykład pokazuje sposób wykonywania zapytań <xref:System.Printing.PrintCapabilities> drukarki i utworzyć <xref:System.Printing.PrintTicket> przy użyciu kodu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer i PrintQueue  
 <xref:System.Printing.PrintServer> Klasa reprezentuje serwer wydruku sieci i <xref:System.Printing.PrintQueue> klasa reprezentuje drukarki i danych wyjściowych kolejki zadań skojarzonych z nim. Razem te [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] umożliwia zaawansowane zarządzanie zadaniami drukowania na serwerze. A <xref:System.Printing.PrintServer>, lub jeden z jej klas pochodnych, jest używany do zarządzania <xref:System.Printing.PrintQueue>. <xref:System.Printing.PrintQueue.AddJob%2A> Metoda służy do wstawiania nowego zadania drukowania do kolejki.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Printing.LocalPrintServer> i uzyskiwać dostęp do domyślnej <xref:System.Printing.PrintQueue> przy użyciu kodu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter>, Za pomocą jego wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod, używany do zapisywania [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentów do <xref:System.Printing.PrintQueue>. Na przykład <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> używana jest metoda danych wyjściowych [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentu i <xref:System.Printing.PrintTicket> synchronicznie. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> Używana jest metoda danych wyjściowych [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentu i <xref:System.Printing.PrintTicket> asynchronicznie.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Xps.XpsDocumentWriter> przy użyciu kodu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Metody udostępniają metody drukowania. Zobacz [programowe drukowanie plików XPS](how-to-programmatically-print-xps-files.md). Aby uzyskać szczegółowe informacje.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Ścieżka wydruku GDI  
 Gdy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje natywnie obsługują [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżka wydruku [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i aplikacjach Windows Forms można również korzystać z niektórych [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcji. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Sterownika drukarki (XPSDrv) można przekonwertować [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] na podstawie danych wyjściowych do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formatu. W przypadku zaawansowanych scenariuszy konwersji niestandardowej zawartości jest obsługiwane przy użyciu [Microsoft XPS dokumentu konwerter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Podobnie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje mogą również przesyłać dane wyjściowe do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżka wydruku, wywołując jedną z <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> lub <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> klasy i wyznaczanie drukarek innych XpsDrv jako element docelowy kolejki wydruku.  

W przypadku aplikacji, które nie wymagają [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcji lub pomocy technicznej, bieżący [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżka wydruku pozostaje bez zmian.  
  
-   Aby uzyskać dodatkowe materiały dotyczące [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] drukować ścieżki i różnych [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] opcje konwersji, zobacz [Microsoft XPS dokumentu konwerter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) i [sterowników drukarek XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Model sterownika XPSDrv  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Ścieżka wydruku zwiększa efektywność buforowania przy użyciu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formacie natywnych buforu wydruku podczas drukowania na [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] — włączone drukarki lub sterownika. Proces uproszczonej buforowania eliminuje potrzebę Generowanie pliku pośredniego buforu, takich jak [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] pliku danych, zanim dokumentu jest buforowany. Za pomocą mniejsze rozmiary plików buforu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżka wydruku można zmniejszyć ruch sieciowy i zwiększyć wydajność drukowania.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] jest zamknięte formatu, który reprezentuje dane wyjściowe aplikacji jako szereg wywołań do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] usługi renderowania. W odróżnieniu od [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] format buforu reprezentuje rzeczywisty dokumentu bez konieczności dalszej interpretacji, gdy dane wyjściowe do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]— na podstawie sterownika drukarki (XPSDrv). Sterowniki może operować bezpośrednio na danych w formacie. Ta funkcja pozwala wyeliminować konwersje przestrzeni danych i kolor wymagana, gdy używasz [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] plików i [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]— na podstawie sterowników drukarek.  
  
 Rozmiary plików buforu zwykle są mniejsze, gdy używasz [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumenty, których platformą docelową [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sterownika drukarki (XPSDrv) w porównaniu z ich [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] odpowiedniki; istnieją jednak wyjątki:  
  
-   Grafiki wektorowej, który jest bardzo złożonych, wielowarstwowych lub nieefektywnie napisane może być większy niż mapy bitowej wersji tego samego pliku graficznego.  
  
-   Do wyświetlania ekranu pliki XPS osadzania czcionek urządzenia, a także czcionek oparte na komputerze; natomiast plików buforu interfejsu GDI nie osadzaj czcionek urządzenia. Ale podzbiory (patrz poniżej) są oba rodzaje czcionek i sterowniki drukarki można usunąć czcionki urządzenia przed przekazaniem go do drukarki.  
  
 Zmniejszanie rozmiaru buforu jest wykonywane przy użyciu kilku mechanizmów:  
  
-   **Korzystanie z podzbiorów czcionek**. Tylko znaki używane w dokumencie rzeczywistych są przechowywane w [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] pliku.  
  
-   **Zaawansowana obsługa grafiki**. Natywna obsługa podstawowych przejrzystości i gradientu pozwala uniknąć rasteryzacji zawartość [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentu.  
  
-   **Identyfikowanie wspólnych zasobów**. Zasoby, które są używane wielokrotnie (takich jak obraz, który reprezentuje logo firmy), są traktowane jako zasobów udostępnionych i są ładowane tylko raz.  
  
-   **Kompresji ZIP**. Wszystkie [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentów Użyj kompresji ZIP.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [— Tematy porad](printing-how-to-topics.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Dokumenty XPS](/windows/desktop/printdocs/documents)
- [Serializacja dokumentu i przechowywanie](document-serialization-and-storage.md)
- [Konwerter (MXDC) dokumentów XPS firmy Microsoft](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
