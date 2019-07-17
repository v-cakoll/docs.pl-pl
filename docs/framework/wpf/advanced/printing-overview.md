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
ms.openlocfilehash: bb3737ca879f3687b25b021348da0c50f663c58e
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238673"
---
# <a name="printing-overview"></a>Przegląd Drukowanie
Za pomocą programu Microsoft .NET Framework deweloperzy aplikacji przy użyciu Windows Presentation Foundation (WPF) mają bogaty zestaw nowych drukowanie i interfejsy API umożliwiające zarządzanie systemem drukowania. Za pomocą [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], niektóre z tych rozszerzeń systemu drukowania są również dostępne dla programistów tworzących [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji i deweloperzy korzystający z niezarządzanego kodu. W ramach tej nowej funkcji jest nowy [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] format pliku i [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ścieżka wydruku.  
  
 Ten temat zawiera następujące sekcje.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>Temat XPS  
 XPS to format dokumentu elektronicznego, format pliku buforu i języka opisu strony. Jest format Otwórz dokument, który używa [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]i innych standardów branżowych, do tworzenia dokumentów dla wielu platform. XPS upraszcza ten proces, za pomocą którego cyfrowe dokumenty są utworzone, udostępniony, drukowane, wyświetlać i archiwizowane. Aby uzyskać dodatkowe informacje na temat XPS, zobacz [dokumenty XPS](/windows/desktop/printdocs/documents).  
  
 Kilka technik drukowanie plików XPS oparte na zawartości przy użyciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zostały przedstawione w [programowe drukowanie plików XPS](how-to-programmatically-print-xps-files.md). Może okazać się przydatne odwołać te przykłady podczas przeglądu zawartości znajdujących się w tym temacie. (Deweloperzy niezarządzany kod powinien zostać wyświetlony dokumentacji [funkcja MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Programiści Windows Forms, należy użyć interfejsu API w <xref:System.Drawing.Printing> przestrzeni nazw, który nie obsługuje pełnej [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ścieżka wydruku, ale obsługa ma ścieżkę drukowania hybrydowego GDI do plików XPS. Zobacz **architektura ścieżka wydruku** poniżej.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Ścieżka wydruku XPS  
 Ścieżka wydruku systemu nazw domen (XPS, XML Paper Specification) to nowa [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] funkcja, która redefiniuje jak drukowanie odbywa się w aplikacji Windows. Ponieważ [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] można zastąpić języka prezentacji dokumentu, (na przykład RTF), bufor wydruku formatu (WMF) i język opisu strony (na przykład PCL lub Postscript); Nowa ścieżka wydruku obsługuje format pliku XPS, z publikacji aplikacji końcowe przetwarzanie sterownik drukarki lub urządzenia.  
  
 Ścieżka wydruku XPS jest oparte na modelu sterownika drukarki XPS (XPSDrv), która zapewnia kilka korzyści dla deweloperów, takie jak [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] drukowania, Ulepszona obsługa kolorów i znaczne zwiększenie wydajności drukowania. (Aby uzyskać więcej informacji o XPSDrv, zobacz [dokumentację Windows Driver Kit](/windows-hardware/drivers/).)  
  
 Operacja buforu wydruku dokumenty XPS jest zasadniczo taki sam, jak w poprzednich wersjach systemu Windows. Jednak ma został rozszerzony o obsługę ścieżka wydruku XPS, oprócz istniejącej [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżka wydruku. Nowa ścieżka wydruku natywnie wykorzystuje plik buforu XPS. While napisanych dla wcześniejszych wersji sterowników drukarek trybu użytkownika [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] będą nadal działać, sterownik drukarki XPS (XPSDrv) jest wymagane, aby można było używać ścieżka wydruku XPS.  
  
 Ścieżka wydruku XPS są istotne oraz obejmują:  
  
- [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] Obsługa drukowania  
  
- Macierzysta obsługa Profile zaawansowane kolorów, które obejmują 32 bitów na kanał, CMYK, o nazwie kolory, n farby i natywną obsługę przejrzystości i gradientów.  
  
- Zwiększona wydajność wydruku dla obu .NET Framework i [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] na podstawie aplikacji.  
  
- Standardowy format branżowy XPS.  
  
 W przypadku podstawowych scenariuszy drukowania prostego i intuicyjnego interfejsu API jest dostępny za pomocą pojedynczego punktu wejścia do przesłania interfejsu, konfiguracji i zadania użytkownika. W przypadku zaawansowanych scenariuszy dodatkowa pomoc techniczna jest dodawany do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dostosowywania (lub nie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na wszystkich), synchroniczna lub asynchroniczna drukowanie i batch możliwość drukowania. Obie udostępniają Obsługa drukowania w trybie pełnej lub częściowej relacji zaufania.  
  
 XPS zaprojektowano pod kątem rozszerzalności na uwadze. Za pomocą strukturę rozszerzalności, funkcje i możliwości można dodać do plików XPS w sposób moduły. Rozszerzalność funkcje obejmują:  
  
- Drukowanie schematu. Schemat publicznej jest regularnie aktualizowana, a także umożliwia szybkie rozszerzenie możliwości urządzenia. (Zobacz **PrintTicket — i printcapabilities —** poniżej.)  
  
- Potok rozszerzonego filtru. Potoku filtru (XPSDrv) sterownika drukarki XPS zaprojektowano tak, aby włączyć zarówno bezpośrednich, jak i skalowalne drukowanie dokumentów XPS. Aby uzyskać więcej informacji, zobacz [sterowników drukarek XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Ścieżka wydruku architektury  
 Podczas gdy obie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i aplikacji programu .NET Framework obsługuje XPS, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i używać w aplikacjach Windows Forms [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] do plików XPS konwersji, aby można było utworzyć XPS sformatowaną zawartość dla sterownika drukarki XPS (XPSDrv). Te aplikacje nie trzeba używać ścieżki drukowanie plików XPS i mogą w dalszym ciągu używać [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] na podstawie drukowania. Jednak większość XPS funkcje i rozszerzenia są dostępne tylko do aplikacji, których platformą docelową ścieżka wydruku XPS.  
  
 Aby włączyć korzystanie z drukarek oparte na XPSDrv przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i aplikacjach Windows Forms, sterownik drukarki XPS (XPSDrv) obsługuje konwersję [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] do plików XPS formatowania. XPSDrv model udostępnia także konwertera XPS do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] format tak, aby [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji można wydrukować [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentów. Dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje, konwersja XPS do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] format jest wykonywane automatycznie przez <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> klasy zawsze wtedy, gdy kolejki wydruku docelowy operacji zapisu nie ma sterownika XPSDrv. (Nie można wydrukować w aplikacjach Windows Forms [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty.)  
  
 Poniższa ilustracja przedstawia podsystem wydruku i definiuje fragmenty, dostarczone przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]i fragmenty zdefiniowane przez producentów sprzętu i oprogramowania:  
  
 ![Zrzut ekranu pokazuje, że system drukowania XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Drukowanie plików XPS podstawowe  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definiuje zarówno podstawowych i zaawansowanych interfejsów API. Dla tych aplikacji, które nie wymagają dokładne dostosowanie drukowania lub dostęp do funkcji XPS pełną ustawiona, podstawowa obsługa drukowania jest dostępna. Podstawowa pomoc techniczna drukowania jest dostępna za pośrednictwem formantu w oknie dialogowym drukowania, który wymaga minimalnej konfiguracji i funkcje powszechnie znane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Wiele funkcji XPS są dostępne za pośrednictwem tego uproszczony model drukowania.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrola zapewnia jeden punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguracji i przesyłanie zadań do plików XPS. Aby uzyskać informacje o sposobie tworzenia instancji i korzystanie z kontrolki, zobacz [Wywołaj okno dialogowe Drukuj](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Zaawansowane XPS, drukowanie  
 Aby uzyskać dostęp do pełnego zestawu funkcji XPS, należy użyć zaawansowanych drukowania interfejsu API. Kilka istotnych interfejsu API są opisane bardziej szczegółowo poniżej. Aby uzyskać pełną listę ścieżka wydruku XPS interfejsów API, zobacz <xref:System.Windows.Xps> i <xref:System.Printing> odwołania do przestrzeni nazw.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket — i printcapabilities —  
 <xref:System.Printing.PrintTicket> i <xref:System.Printing.PrintCapabilities> klasy stanowiących zaawansowane funkcje XPS. Oba typy obiektów są [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] sformatowane struktury zorientowane na drukowanie funkcji, takich jak sortowanie, drukowania dwustronnego, zszywanie itp. Te struktury są zdefiniowane w schemacie drukowania. A <xref:System.Printing.PrintTicket> powoduje, że drukarki sposób przetwarzania zadania drukowania. <xref:System.Printing.PrintCapabilities> Klasa definiuje możliwościach drukarki. Sondując możliwościach drukarki, <xref:System.Printing.PrintTicket> mogą być tworzone, że wykorzystuje pełną drukarki na obsługiwane funkcje. Podobnie można uniknąć nieobsługiwanych funkcji.  
  
 Poniższy przykład pokazuje sposób wykonywania zapytań <xref:System.Printing.PrintCapabilities> drukarki i utworzyć <xref:System.Printing.PrintTicket> przy użyciu kodu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer i PrintQueue  
 <xref:System.Printing.PrintServer> Klasa reprezentuje serwer wydruku sieci i <xref:System.Printing.PrintQueue> klasa reprezentuje drukarki i danych wyjściowych kolejki zadań skojarzonych z nim. Razem te interfejsy API umożliwiają Zaawansowane zarządzanie zadaniami drukowania na serwerze. A <xref:System.Printing.PrintServer>, lub jeden z jej klas pochodnych, jest używany do zarządzania <xref:System.Printing.PrintQueue>. <xref:System.Printing.PrintQueue.AddJob%2A> Metoda służy do wstawiania nowego zadania drukowania do kolejki.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Printing.LocalPrintServer> i uzyskiwać dostęp do domyślnej <xref:System.Printing.PrintQueue> przy użyciu kodu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter>, Za pomocą jego wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod, używany do zapisywania dokumentów XPS <xref:System.Printing.PrintQueue>. Na przykład <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> metoda jest używana do wypełniania wyjściowego dokument XPS i <xref:System.Printing.PrintTicket> synchronicznie. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> Metoda jest używana do wypełniania wyjściowego dokument XPS i <xref:System.Printing.PrintTicket> asynchronicznie.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Xps.XpsDocumentWriter> przy użyciu kodu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Metody udostępniają metody drukowania. Zobacz [programowe drukowanie plików XPS](how-to-programmatically-print-xps-files.md). Aby uzyskać szczegółowe informacje.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Ścieżka wydruku GDI  
 Gdy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje natywnie obsługują ścieżka wydruku XPS [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i aplikacjach Windows Forms można również korzystać z niektórych funkcji XPS. Sterownik drukarki XPS (XPSDrv) można przekonwertować [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] na podstawie danych wyjściowych do formatu plików XPS. W przypadku zaawansowanych scenariuszy konwersji niestandardowej zawartości jest obsługiwane przy użyciu [Microsoft XPS dokumentu konwerter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Podobnie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje mogą również przesyłać dane wyjściowe do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżka wydruku, wywołując jedną z <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> lub <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> klasy i wyznaczanie drukarek innych XpsDrv jako element docelowy kolejki wydruku.  

W przypadku aplikacji, które nie wymagają funkcji XPS lub pomocy technicznej, bieżący [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżka wydruku pozostaje bez zmian.  
  
- Aby uzyskać dodatkowe materiały dotyczące [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] drukowania ścieżkę i różne opcje konwersji XPS, zobacz temat [Microsoft XPS dokumentu konwerter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) i [sterowników drukarek XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Model sterownika XPSDrv  
 Ścieżka wydruku XPS zwiększa efektywność buforowania przy użyciu XPS w formacie natywnych buforu wydruku, jeśli drukowanie do plików XPS — włączone drukarki lub sterownika. Proces uproszczonej buforowania eliminuje potrzebę Generowanie pliku pośredniego buforu, takich jak [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] pliku danych, zanim dokumentu jest buforowany. Za pomocą mniejsze rozmiary plików buforu ścieżka wydruku XPS można zmniejszenie ruchu w sieci i zwiększyć wydajność drukowania.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] jest zamknięte formatu, który reprezentuje dane wyjściowe aplikacji jako szereg wywołań do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] usługi renderowania. W odróżnieniu od [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], format buforu XPS reprezentuje rzeczywisty dokumentu bez konieczności dalszej interpretacji, gdy dane wyjściowe do sterownika drukarki na podstawie XPS (XPSDrv). Sterowniki może operować bezpośrednio na danych w formacie. Ta funkcja pozwala wyeliminować konwersje przestrzeni danych i kolor wymagana, gdy używasz [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] plików i [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]— na podstawie sterowników drukarek.  
  
 Rozmiary plików buforu zwykle są mniejsze, gdy używasz dokumenty XPS, przeznaczonych dla XPS sterownika drukarki (XPSDrv) w porównaniu z ich [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] odpowiedniki; istnieje jednak wyjątki:  
  
- Grafiki wektorowej, który jest bardzo złożonych, wielowarstwowych lub nieefektywnie napisane może być większy niż mapy bitowej wersji tego samego pliku graficznego.  
  
- Do wyświetlania ekranu pliki XPS osadzania czcionek urządzenia, a także czcionek oparte na komputerze; natomiast plików buforu interfejsu GDI nie osadzaj czcionek urządzenia. Ale podzbiory (patrz poniżej) są oba rodzaje czcionek i sterowniki drukarki można usunąć czcionki urządzenia przed przekazaniem go do drukarki.  
  
 Zmniejszanie rozmiaru buforu jest wykonywane przy użyciu kilku mechanizmów:  
  
- **Korzystanie z podzbiorów czcionek**. Tylko znaki używane w dokumencie rzeczywistych są przechowywane w pliku XPS.  
  
- **Zaawansowana obsługa grafiki**. Natywna obsługa podstawowych przejrzystości i gradientu pozwala uniknąć rasteryzacji zawartość [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentu.  
  
- **Identyfikowanie wspólnych zasobów**. Zasoby, które są używane wielokrotnie (takich jak obraz, który reprezentuje logo firmy), są traktowane jako zasobów udostępnionych i są ładowane tylko raz.  
  
- **Kompresji ZIP**. Wszystkie dokumenty XPS używają kompresji ZIP.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Tematy z instrukcjami](printing-how-to-topics.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Dokumenty XPS](/windows/desktop/printdocs/documents)
- [Serializacja dokumentu i przechowywanie](document-serialization-and-storage.md)
- [Konwerter (MXDC) dokumentów XPS firmy Microsoft](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
