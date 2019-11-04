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
ms.openlocfilehash: 0758a537ee457a8fe5a778e2a2c24a8ba13c263b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460863"
---
# <a name="printing-overview"></a>Przegląd Drukowanie
W przypadku Microsoft .NET Framework deweloperzy aplikacji korzystający z Windows Presentation Foundation (WPF) mają bogaty nowy zestaw interfejsów API zarządzania systemem drukowania i drukowania. Za pomocą [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]niektóre z tych ulepszeń systemu drukowania są również dostępne dla deweloperów tworzących [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacje i deweloperów korzystających z kodu niezarządzanego. Podstawą tej nowej funkcji jest nowy format XML Paper Specification (XPS) i ścieżka wydruku XPS.  
  
 Ten temat zawiera następujące sekcje.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>Informacje o XPS  
 XPS to format dokumentu elektronicznego, format pliku buforu i język opisu strony. Jest to otwarty format dokumentu, który używa [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], otwarte konwencje pakietów (OPC) i inne standardy branżowe do tworzenia dokumentów międzyplatformowych. XPS upraszcza proces tworzenia, udostępniania, drukowania, wyświetlania i archiwizowania dokumentów cyfrowych. Aby uzyskać dodatkowe informacje na temat XPS, zobacz [Dokumenty XPS](/windows/desktop/printdocs/documents).  
  
 Kilka technik drukowania zawartości opartej na plikach XPS przy użyciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przedstawiono w programie [programowo drukowanie plików XPS](how-to-programmatically-print-xps-files.md). Warto zapoznać się z tymi przykładami podczas przeglądu zawartości zawartej w tym temacie. (Deweloperzy kodu niezarządzanego powinni zobaczyć dokumentację [funkcji MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Windows Forms deweloperzy muszą używać interfejsu API w przestrzeni nazw <xref:System.Drawing.Printing>, która nie obsługuje pełnej ścieżki wydruku XPS, ale obsługuje hybrydową ścieżkę wydruku GDI-to-XPS. Zobacz temat **Architektura ścieżki drukowania** poniżej.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Ścieżka wydruku XPS  
 Ścieżka wydruku w formacie XML Paper Specification (XPS) to nowa funkcja systemu Windows, która ponownie definiuje sposób obsługi drukowania w aplikacjach systemu Windows. Ponieważ plik XPS może zastąpić język prezentacji dokumentu (taki jak RTF), format buforu wydruku (na przykład WMF) i język opisu strony (na przykład PCL lub PostScript); Nowa ścieżka drukowania zachowuje format XPS od publikacji aplikacji do ostatecznego przetwarzania w sterowniku lub urządzeniu drukowania.  
  
 Ścieżka wydruku XPS jest tworzona na podstawie modelu sterownika drukarki XPS (XPSDrv), który zapewnia kilka korzyści dla deweloperów, takich jak "co widzisz", co otrzymujesz: drukowanie "(WYSIWYG), ulepszona obsługa kolorów i znacznie lepsza wydajność drukowania. (Aby uzyskać więcej informacji na temat XPSDrv, zobacz [dokumentację zestawu Windows Driver Kit](/windows-hardware/drivers/)).  
  
 Operacja bufora wydruku dla dokumentów XPS jest zasadniczo taka sama jak w poprzednich wersjach systemu Windows. Ulepszono jednak obsługę ścieżki drukowania XPS oprócz istniejącej ścieżki drukowania GDI. Nowa ścieżka wydruku natywnie zużywa plik buforu XPS. Gdy sterowniki drukarki trybu użytkownika napisano dla poprzednich wersji systemu Windows, będą nadal działały, sterownik drukarki XPS (XPSDrv) jest wymagany, aby można było użyć ścieżki wydruku XPS.  
  
 Zalety ścieżki drukowania XPS są istotne i obejmują:  
  
- Obsługa drukowania w trybie WYSIWYG  
  
- Natywna obsługa zaawansowanych profilów kolorów, obejmująca 32 bitów na kanał (BPC), CMYK, kolory nazwane, atramenty n i Natywne wsparcie dla przezroczystości i gradientów.  
  
- Ulepszona wydajność drukowania dla aplikacji opartych na .NET Framework i [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)].  
  
- Standardowy format XPS w branży.  
  
 W przypadku podstawowych scenariuszy drukowania prosty i intuicyjny interfejs API jest dostępny z jednym punktem wejścia dla interfejsu użytkownika, konfiguracji i wysyłania zadań. W przypadku zaawansowanych scenariuszy dodano dodatkową pomoc techniczną do dostosowywania [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] (lub nie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w ogóle), drukowania synchronicznego lub asynchronicznego oraz funkcji drukowania wsadowego. Obie opcje zapewniają obsługę drukowania w trybie pełnego lub częściowego zaufania.  
  
 Plik XPS został zaprojektowany z myślą o rozszerzalności. Korzystając ze struktury rozszerzalności, funkcje i możliwości można dodać do formatu XPS w sposób modułowy. Funkcje rozszerzalności obejmują:  
  
- Drukuj schemat. Schemat publiczny jest regularnie aktualizowany i umożliwia szybkie rozszerzanie możliwości urządzeń. (Zobacz " **PrintTicket" i "PrintCapabilities** " poniżej).  
  
- Rozszerzalny potok filtru. Potok filtru sterowników drukarek XPS (XPSDrv) został zaprojektowany tak, aby umożliwić bezpośrednie i skalowalne drukowanie dokumentów XPS. Aby uzyskać więcej informacji, zobacz [sterowniki drukarek XPsDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Architektura ścieżki drukowania  
 Chociaż aplikacje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i .NET Framework obsługują aplikacje XPS, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i Windows Forms używają konwersji GDI to XPS, aby utworzyć zawartość sformatowaną w formacie XPS dla sterownika drukarki XPS (XPSDrv). Te aplikacje nie są wymagane do korzystania z ścieżki drukowania XPS i mogą nadal korzystać z funkcji drukowania w formacie metapliku (EMF). Większość funkcji i ulepszeń XPS jest jednak dostępna tylko dla aplikacji przeznaczonych dla ścieżki wydruku XPS.  
  
 Aby umożliwić korzystanie z drukarek opartych na XPSDrv przez aplikacje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i Windows Forms, sterownik drukarki XPS (XPSDrv) obsługuje konwersję formatu GDI na format XPS. Model XPSDrv zapewnia również konwerter dla formatu XPS na format GDI, dzięki czemu aplikacje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] mogą drukować dokumenty XPS. W przypadku aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Konwersja formatu XPS do interfejsu GDI jest wykonywana automatycznie przez <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody klasy <xref:System.Windows.Xps.XpsDocumentWriter>, gdy docelowa kolejka wydruku operacji zapisu nie ma sterownika XPSDrv. (Aplikacje Windows Forms nie mogą drukować dokumentów XPS).  
  
 Poniższa ilustracja przedstawia podsystem drukowania i definiuje części dostarczone przez firmę Microsoft oraz części zdefiniowane przez dostawców oprogramowania i sprzętu:  
  
 ![Zrzut ekranu przedstawia system drukowania XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Podstawowe drukowanie XPS  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definiuje zarówno podstawowy, jak i zaawansowany interfejs API. W przypadku aplikacji, które nie wymagają szerszego dostosowania drukowania lub dostępu do kompletnego zestawu funkcji XPS, dostępna jest podstawowa pomoc techniczna drukowania. Podstawowa pomoc techniczna drukowania jest dostępna za pomocą kontrolki okna dialogowego drukowania, która wymaga minimalnej konfiguracji i zawiera znane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Wiele funkcji XPS jest dostępnych przy użyciu tego uproszczonego modelu drukowania.  
  
#### <a name="printdialog"></a>PrintDialog  
 Kontrolka <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> zawiera pojedynczy punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguracji i przekazanie zadania XPS. Aby uzyskać informacje o sposobie tworzenia wystąpienia i używania kontrolki, zobacz [Wywołaj okno dialogowe drukowania](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Zaawansowane drukowanie plików XPS  
 Aby uzyskać dostęp do pełnego zestawu funkcji XPS, należy użyć zaawansowanego interfejsu API drukowania. Poniżej opisano kilka odpowiednich interfejsów API. Aby uzyskać pełną listę interfejsów API ścieżki drukowania XPS, zobacz odwołania do przestrzeni nazw <xref:System.Windows.Xps> i <xref:System.Printing>.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket i PrintCapabilities  
 Klasy <xref:System.Printing.PrintTicket> i <xref:System.Printing.PrintCapabilities> stanowią podstawę zaawansowanych funkcji XPS. Oba typy obiektów są [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] sformatowane struktury funkcji związanych z drukowaniem, takie jak sortowanie, drukowanie dwustronne, zszywanie itp. Struktury te są definiowane przez schemat drukowania. <xref:System.Printing.PrintTicket> informuje drukarkę o sposobie przetwarzania zadania drukowania. Klasa <xref:System.Printing.PrintCapabilities> definiuje możliwości drukarki. Wykonując zapytania o możliwości drukarki, można utworzyć <xref:System.Printing.PrintTicket>, które w pełni wykorzystują obsługiwane funkcje drukarki. Podobnie można uniknąć nieobsługiwanych funkcji.  
  
 W poniższym przykładzie pokazano, jak zbadać <xref:System.Printing.PrintCapabilities> drukarki i utworzyć <xref:System.Printing.PrintTicket> przy użyciu kodu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer i Kolejka PrintQueue  
 Klasa <xref:System.Printing.PrintServer> reprezentuje serwer wydruku sieciowego, a Klasa <xref:System.Printing.PrintQueue> reprezentuje drukarkę oraz skojarzoną z nią kolejkę zadań wyjściowych. Razem te interfejsy API umożliwiają zaawansowane zarządzanie zadaniami drukowania na serwerze. <xref:System.Printing.PrintServer>lub jedna z jej klas pochodnych służy do zarządzania <xref:System.Printing.PrintQueue>. Metoda <xref:System.Printing.PrintQueue.AddJob%2A> służy do wstawiania nowego zadania drukowania do kolejki.  
  
 W poniższym przykładzie pokazano, jak utworzyć <xref:System.Printing.LocalPrintServer> i uzyskać dostęp do jego domyślnego <xref:System.Printing.PrintQueue> przy użyciu kodu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter>z wieloma metodami <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> służy do zapisywania dokumentów XPS w <xref:System.Printing.PrintQueue>. Na przykład Metoda <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> jest używana do wyprowadzania dokumentu XPS i <xref:System.Printing.PrintTicket> synchronicznie. Metoda <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> jest używana do wyprowadzania dokumentu XPS i <xref:System.Printing.PrintTicket> asynchronicznie.  
  
 Poniższy przykład ilustruje sposób tworzenia <xref:System.Windows.Xps.XpsDocumentWriter> przy użyciu kodu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Metody <xref:System.Printing.PrintQueue.AddJob%2A> również zapewniają sposoby drukowania. Zobacz [programistyczne drukowanie plików XPS](how-to-programmatically-print-xps-files.md). Aby uzyskać szczegółowe informacje.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Ścieżka wydruku GDI  
 Chociaż aplikacje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] natywnie obsługują ścieżkę drukowania XPS, aplikacje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i Windows Forms mogą również korzystać z niektórych funkcji XPS. Sterownik drukarki XPS (XPSDrv) umożliwia konwertowanie danych wyjściowych opartych na interfejsie GDI na format XPS. W przypadku zaawansowanych scenariuszy konwersja zawartości jest obsługiwana przy użyciu [konwertera dokumentów XPS firmy Microsoft (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Podobnie aplikacje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mogą również wyprowadzać dane wyjściowe do ścieżki wydruku GDI przez wywołanie jednej z <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> lub <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod klasy <xref:System.Windows.Xps.XpsDocumentWriter> i wyznaczanie drukarki innej niż XpsDrv jako docelowej kolejki wydruku.  

W przypadku aplikacji, które nie wymagają funkcjonalności lub pomocy technicznej XPS, bieżąca ścieżka drukowania GDI pozostaje niezmieniona.  
  
- Dodatkowe materiały referencyjne dotyczące ścieżki wydruku GDI i różnych opcji konwersji XPS można znaleźć w temacie [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) i [XPsDrv Printer Drivers](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Model sterownika XPSDrv  
 Ścieżka wydruku XPS pozwala zwiększyć wydajność buforu przy użyciu formatu XPS jako natywnego buforu wydruku podczas drukowania do drukarki lub sterownika z obsługą formatu XPS. Uproszczony proces buforowania eliminuje konieczność wygenerowania pośredniego pliku buforu, takiego jak plik danych EMF, przed buforowaniem dokumentu. Przy mniejszych rozmiarach plików buforu ścieżka wydruku XPS może zmniejszyć ruch sieciowy i poprawić wydajność drukowania.  
  
 EMF jest formatem zamkniętym, który reprezentuje dane wyjściowe aplikacji jako serię wywołań do usługi GDI na potrzeby renderowania usług. W przeciwieństwie do EMF, format buforu XPS reprezentuje rzeczywisty dokument bez potrzeby dalszej interpretacji podczas wyprowadzania danych wyjściowych do sterownika drukarki opartego na formacie XPS (XPSDrv). Sterowniki mogą działać bezpośrednio na danych w formacie. Ta funkcja eliminuje konwersje danych i przestrzeni kolorów wymagane w przypadku korzystania z plików EMF i sterowników drukarek opartych na interfejsie GDI.  
  
 Rozmiary plików buforu są zwykle zmniejszane, gdy używasz dokumentów XPS przeznaczonych dla sterownika drukarki XPS (XPSDrv) w porównaniu z ich odpowiednikami w formacie EMF; Istnieją jednak wyjątki:  
  
- Grafika wektorowa, która jest bardzo złożona, wielowarstwowa lub niewydajnie zapisywana, może być większa niż wersja mapy bitowej tej samej grafiki.  
  
- W przypadku wyświetlania ekranu pliki XPS są osadzane na urządzeniach, a także czcionek opartych na komputerze; pliki buforu GDI nie osadzają czcionek urządzenia. Ale w przypadku obu rodzajów czcionek są podzbiorowe (patrz poniżej), a sterowniki drukarki mogą usunąć czcionki urządzenia przed przekazaniem go do drukarki.  
  
 Zmniejszenie rozmiaru buforu odbywa się przy użyciu kilku mechanizmów:  
  
- **Podustawienie czcionki**. W pliku XPS są przechowywane tylko znaki używane w bieżącym dokumencie.  
  
- **Zaawansowana obsługa grafiki**. Natywna obsługa przezroczystości i pierwotnych gradientów pozwala uniknąć rasteryzacji zawartości w dokumencie XPS.  
  
- **Identyfikowanie wspólnych zasobów**. Zasoby, które są używane wiele razy (na przykład obraz, który reprezentuje logo firmy) są traktowane jako zasoby udostępnione i są ładowane tylko raz.  
  
- **Kompresja zip**. Wszystkie dokumenty XPS używają kompresji ZIP.  
  
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
- [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
