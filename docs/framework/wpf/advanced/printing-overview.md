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
ms.openlocfilehash: 902d51341850b5245b9fa6410b1954b2ab373bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187201"
---
# <a name="printing-overview"></a>Przegląd Drukowanie
Dzięki programowi Microsoft .NET Framework deweloperzy aplikacji korzystający z programu Windows Presentation Foundation (WPF) mają nowy, bogaty zestaw interfejsów API zarządzania systemem drukowania i drukowania. W systemie Windows Vista niektóre z tych ulepszeń systemu drukowania są również dostępne dla deweloperów tworzących aplikacje windows forms i deweloperów korzystających z kodu niezarządzanego. Podstawą tej nowej funkcji jest nowy format pliku XML Paper Specification (XPS) i ścieżka drukowania XPS.  
  
 Ten temat zawiera poniższe sekcje.  
  
<a name="introduction_to_XPS"></a>
## <a name="about-xps"></a>Informacje o XPS  
 XPS to elektroniczny format dokumentu, format pliku buforu i język opisu strony. Jest to otwarty format dokumentu, który używa XML, Open Packaging Conventions (OPC) i innych standardów branżowych do tworzenia dokumentów międzyplatformowych. System XPS upraszcza proces tworzenia, udostępniania, drukowania, przeglądania i archiwizowania dokumentów cyfrowych. Aby uzyskać dodatkowe informacje na temat systemu XPS, zobacz [Dokumenty XPS](/windows/desktop/printdocs/documents).  
  
 Kilka technik drukowania zawartości opartej na XPS przy użyciu WPF są przedstawione w [programowo drukować pliki XPS](how-to-programmatically-print-xps-files.md). Może okazać się przydatne do odwoływania się do tych przykładów podczas przeglądu zawartości zawartej w tym temacie. (Deweloperzy kodu niezarządzanego powinni zapoznać się z dokumentacją [funkcji MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Deweloperzy formularzy systemu Windows <xref:System.Drawing.Printing> muszą używać interfejsu API w obszarze nazw, który nie obsługuje pełnej ścieżki drukowania xps, ale obsługuje hybrydową ścieżkę drukowania GDI-TO-XPS. Zobacz **architekturę ścieżki drukowania** poniżej).)  
  
<a name="XPS_print_path_intro"></a>
## <a name="xps-print-path"></a>Ścieżka drukowania XPS  
 Ścieżka drukowania XML Paper Specification (XPS) to nowa funkcja systemu Windows, która na nowo definiuje sposób obsługi drukowania w aplikacjach systemu Windows. Ponieważ system XPS może zastąpić język prezentacji dokumentu (na przykład RTF), format buforu wydruku (na przykład WMF) i język opisu strony (na przykład PCL lub Postscript); nowa ścieżka drukowania utrzymuje format XPS od publikacji aplikacji do ostatecznego przetwarzania w sterowniku lub urządzeniu drukującym.  
  
 Ścieżka drukowania XPS jest oparta na modelu sterownika drukarki XPS (XPSDrv), który zapewnia kilka korzyści dla programistów, takich jak "to, co widzisz, jest tym, co otrzymujesz" (WYSIWYG), ulepszona obsługa kolorów i znacznie lepsza wydajność drukowania. (Aby uzyskać więcej informacji na temat XPSDrv, zobacz [dokumentację zestawu sterowników systemu Windows](/windows-hardware/drivers/).)  
  
 Działanie buforu wydruku dla dokumentów XPS jest zasadniczo takie samo jak w poprzednich wersjach systemu Windows. Jednak oprócz istniejącej ścieżki drukowania GDI została on akces do obsługi ścieżki drukowania XPS. Nowa ścieżka drukowania natywnie zużywa plik buforu XPS. Podczas gdy sterowniki drukarki w trybie użytkownika napisane dla poprzednich wersji systemu Windows będą nadal działać, do korzystania ze ścieżki drukowania XPS wymagany jest sterownik drukarki XPS (XPSDrv).  
  
 Korzyści ze ścieżki drukowania XPS są znaczące i obejmują:  
  
- Obsługa druku WYSIWYG  
  
- Natywna obsługa zaawansowanych profili kolorów, które obejmują 32 bity na kanał (bpc), CMYK, nazwane kolory, n-farby i natywną obsługę przezroczystości i gradientów.  
  
- Poprawiono wydajność drukowania zarówno dla aplikacji opartych na platformie .NET Framework, jak i w aplikacji opartych na win32.  
  
- Standardowy format XPS.  
  
 W przypadku podstawowych scenariuszy drukowania dostępny jest prosty i intuicyjny interfejs API z jednym punktem wejścia do interfejsu użytkownika, konfiguracji i przesyłania zadań. W przypadku zaawansowanych scenariuszy dodawana jest dodatkowa obsługa [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dostosowywania (lub wcale), [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] drukowania synchronicznej lub asynchronicznej oraz możliwości drukowania wsadowego. Obie opcje zapewniają obsługę drukowania w trybie pełnego lub częściowego zaufania.  
  
 Xps został zaprojektowany z myślą o rozciągliwości. Za pomocą struktury rozszerzalności funkcje i możliwości można dodać do systemu XPS w sposób modułowy. Funkcje rozszerzalności obejmują:  
  
- Schemat drukowania. Schemat publiczny jest regularnie aktualizowany i umożliwia szybkie rozszerzanie możliwości urządzenia. (Zobacz **PrintTicket i PrintCapabilities** poniżej.)  
  
- Rozszerzalny potok filtrów. Potok filtrów sterownika drukarki XPS (XPSDrv) został zaprojektowany w celu umożliwienia zarówno bezpośredniego, jak i skalowalnego drukowania dokumentów XPS. Aby uzyskać więcej informacji, zobacz [Sterowniki drukarek XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).
  
### <a name="print-path-architecture"></a>Architektura ścieżki drukowania  
 Podczas gdy aplikacje Win32 i .NET Framework obsługują aplikacje XPS, aplikacje Win32 i Windows Forms używają konwersji GDI na XPS w celu utworzenia zawartości sformatowanej w formacie XPS dla sterownika drukarki XPS (XPSDrv). Te aplikacje nie są wymagane do korzystania ze ścieżki drukowania XPS i mogą nadal korzystać z drukowania opartego na rozszerzonym metafile (EMF). Jednak większość funkcji i ulepszeń systemu XPS jest dostępna tylko dla aplikacji, które są przeznaczone dla ścieżki drukowania XPS.  
  
 Aby umożliwić korzystanie z drukarek opartych na systemie XPSDrv przez aplikacje Win32 i Windows Forms, sterownik drukarki XPS (XPSDrv) obsługuje konwersję GDI do formatu XPS. Model XPSDrv zapewnia również konwerter dla formatu XPS do GDI, dzięki czemu aplikacje Win32 mogą drukować dokumenty XPS. W przypadku aplikacji WPF konwersja formatu XPS do <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> formatu GDI odbywa się automatycznie przez i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> klasy, gdy docelowa kolejka wydruku operacji zapisu nie ma sterownika XPSDrv. (Aplikacje Windows Forms nie mogą drukować dokumentów XPS).  
  
 Poniższa ilustracja przedstawia podsystem drukowania i definiuje części dostarczone przez firmę Microsoft oraz części zdefiniowane przez dostawców oprogramowania i sprzętu:  
  
 ![Zrzut ekranu pokazuje system drukowania XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Podstawowe drukowanie XPS  
 WPF WPF definiuje zarówno podstawowy, jak i zaawansowany interfejs API. W przypadku aplikacji, które nie wymagają rozbudowanych dostosowywania wydruku lub dostępu do pełnego zestawu funkcji XPS, dostępna jest podstawowa obsługa drukowania. Podstawowa obsługa drukowania jest widoczna za pomocą kontrolki okna dialogowego drukowania, która wymaga minimalnej konfiguracji i zawiera znajomy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]program . Wiele funkcji XPS jest dostępnych przy użyciu tego uproszczonego modelu drukowania.  
  
#### <a name="printdialog"></a>PrintDialog  
 Formant <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> zapewnia pojedynczy punkt [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]wejścia dla , konfiguracji i przesyłania zadań XPS. Aby uzyskać informacje dotyczące tworzenia wystąpienia i używania formantu, zobacz [Wywoływanie okna dialogowego drukowania](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Zaawansowane drukowanie XPS  
 Aby uzyskać dostęp do pełnego zestawu funkcji XPS, należy użyć zaawansowanego interfejsu API drukowania. Kilka odpowiednich api są opisane bardziej szczegółowo poniżej. Aby uzyskać pełną listę interfejsów API ścieżki <xref:System.Windows.Xps> drukowania systemu XPS, zobacz odwołania do obszaru nazw i <xref:System.Printing> obszarów nazw.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket i PrintCapabilities  
 Klasy <xref:System.Printing.PrintTicket> <xref:System.Printing.PrintCapabilities> i klasy są podstawą zaawansowanych funkcji XPS. Oba typy obiektów są sformatowanymi w formacie XML strukturami funkcji zorientowanych na wydruk, takich jak sortowanie, drukowanie dwustronne, zszywanie itp. Struktury te są definiowane przez schemat drukowania. A <xref:System.Printing.PrintTicket> instruuje drukarkę, jak przetworzyć zadanie drukowania. Klasa <xref:System.Printing.PrintCapabilities> definiuje możliwości drukarki. Poprzez zapytanie możliwości drukarki, <xref:System.Printing.PrintTicket> można utworzyć, który w pełni wykorzystuje obsługiwane funkcje drukarki. Podobnie można uniknąć nieobsługiwałych funkcji.  
  
 W poniższym przykładzie pokazano, jak <xref:System.Printing.PrintCapabilities> kwerendy <xref:System.Printing.PrintTicket> drukarki i utworzyć przy użyciu kodu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer i PrintQueue  
 Klasa <xref:System.Printing.PrintServer> reprezentuje serwer wydruku <xref:System.Printing.PrintQueue> sieciowego, a klasa reprezentuje drukarkę i skojarzoną z nią kolejkę zadań wyjściowych. Razem te interfejsy API umożliwiają zaawansowane zarządzanie zadaniami drukowania serwera. A <xref:System.Printing.PrintServer>lub jedna z jego klas pochodnych <xref:System.Printing.PrintQueue>jest używana do zarządzania . Metoda <xref:System.Printing.PrintQueue.AddJob%2A> służy do wstawiania nowego zadania drukowania do kolejki.  
  
 W poniższym przykładzie pokazano, jak utworzyć <xref:System.Printing.LocalPrintServer> i uzyskać dostęp do jego domyślne <xref:System.Printing.PrintQueue> przy użyciu kodu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 An <xref:System.Windows.Xps.XpsDocumentWriter>, z <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> jego <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> wielu i metod, służy do <xref:System.Printing.PrintQueue>pisania dokumentów XPS do . Na przykład <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> metoda jest używana do wyprowadzania <xref:System.Printing.PrintTicket> dokumentu XPS i synchronicznie. Metoda <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> jest używana do wyprowadzania <xref:System.Printing.PrintTicket> dokumentu XPS i asynchronicznie.  
  
 W poniższym przykładzie pokazano, jak utworzyć przy <xref:System.Windows.Xps.XpsDocumentWriter> użyciu kodu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Metody <xref:System.Printing.PrintQueue.AddJob%2A> zapewniają również sposoby drukowania. Zobacz [programowo drukowanie plików XPS](how-to-programmatically-print-xps-files.md). szczegółowe informacje.  
  
<a name="GDI_Print_Path_intro"></a>
## <a name="gdi-print-path"></a>Ścieżka drukowania GDI  
 Podczas gdy aplikacje WPF natywnie obsługują ścieżkę drukowania XPS, aplikacje Win32 i Windows Forms mogą również korzystać z niektórych funkcji systemu XPS. Sterownik drukarki XPS (XPSDrv) może konwertować dane wyjściowe oparte na GDI na format XPS. W przypadku zaawansowanych scenariuszy niestandardowa konwersja zawartości jest obsługiwana przy użyciu [konwertera dokumentów Microsoft XPS (MXDC).](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) Podobnie aplikacje WPF można również wyjść do ścieżki drukowania <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> GDI, wywołując jedną z lub <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> klasy i wyznaczając drukarki non-XpsDrv jako docelowej kolejki wydruku.  

W przypadku aplikacji, które nie wymagają funkcji lub obsługi systemu XPS, bieżąca ścieżka drukowania GDI pozostaje niezmieniona.  
  
- Aby uzyskać dodatkowy materiał referencyjny na ścieżce drukowania GDI i różnych opcjach konwersji XPS, zobacz [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) i [XPSDrv Printer Drivers](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>
## <a name="xpsdrv-driver-model"></a>Model sterownika XPSDrv  
 Ścieżka drukowania XPS zwiększa wydajność buforu przy użyciu systemu XPS jako natywnego formatu buforu wydruku podczas drukowania na drukarce lub sterowniku z obsługą systemu XPS. Uproszczony proces buforowania eliminuje konieczność generowania pliku buforu pośredniego, takiego jak plik danych EMF, przed buforowaniem dokumentu. Dzięki mniejszym rozmiarom plików buforu ścieżka drukowania XPS może zmniejszyć ruch sieciowy i poprawić wydajność drukowania.  
  
 EMF jest formatem zamkniętym, który reprezentuje dane wyjściowe aplikacji jako serię wywołań do GDI do renderowania usług. W przeciwieństwie do EMF format buforu XPS reprezentuje rzeczywisty dokument bez konieczności dalszej interpretacji podczas pracy do sterownika drukarki opartej na xps (XPSDrv). Sterowniki mogą działać bezpośrednio na danych w formacie. Ta funkcja eliminuje konwersje danych i przestrzeni kolorów wymagane podczas korzystania z plików EMF i sterowników wydruku opartych na GDI.  
  
 Rozmiary plików buforu są zwykle zmniejszane podczas korzystania z dokumentów XPS, które są przeznaczone dla sterownika drukarki XPS (XPSDrv) w porównaniu z ich odpowiednikami EMF; istnieją jednak wyjątki:  
  
- Grafika wektorowa, która jest bardzo złożona, wielowarstwowa lub nieefektywnie napisana, może być większa niż wersja bitmapowa tej samej grafiki.  
  
- Do celów wyświetlania ekranu pliki XPS osadzają czcionki urządzenia, a także czcionki komputerowe; mając na uwadze, że pliki buforu GDI nie osadzają czcionek urządzenia. Ale oba rodzaje czcionek są podzbiony (patrz poniżej) i sterowniki drukarek można usunąć czcionki urządzenia przed przesłaniem pliku do drukarki.  
  
 Zmniejszenie rozmiaru szpuli odbywa się za pomocą kilku mechanizmów:  
  
- **Podjednanie czcionek**. W pliku XPS są przechowywane tylko znaki używane w rzeczywistym dokumencie.  
  
- **Zaawansowana obsługa grafiki**. Natywna obsługa przezroczystości i ćwiaryzów gradientu pozwala uniknąć rasteryzacji zawartości w dokumencie XPS.  
  
- **Identyfikacja wspólnych zasobów**. Zasoby, które są używane wiele razy (na przykład obraz, który reprezentuje logo firmy) są traktowane jako zasoby udostępnione i są ładowane tylko raz.  
  
- **Kompresja ZIP**. Wszystkie dokumenty XPS korzystają z kompresji ZIP.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Tematy in jakże](printing-how-to-topics.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Dokumenty XPS](/windows/desktop/printdocs/documents)
- [Serializacja dokumentu i przechowywanie](document-serialization-and-storage.md)
- [Konwerter dokumentów Microsoft XPS (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
