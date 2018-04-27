---
title: Przegląd Drukowanie
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a36589ca670892398b4d6bb171e79a07060d458
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="printing-overview"></a>Przegląd Drukowanie
Z programu Microsoft .NET Framework, deweloperzy aplikacji przy użyciu [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ma bogaty zestaw nowe drukowania i wydruku system zarządzania [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. Z [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], niektóre z tych ulepszeń system drukowania są również dostępne dla deweloperów, którzy tworzą [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji i deweloperów przy użyciu niezarządzanych kodu. Stanowiącej podstawę tej nowej funkcji jest nowy [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] format pliku i [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ścieżki wydruku.  
  
 Ten temat zawiera następujące sekcje.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>O XPS  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] jest to format dokumentu elektronicznego, format pliku buforu i języka opisu strony. Jest format otwartego dokumentu, który używa [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]i inne standardy branżowe, tworzenie dokumentów i platform. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] upraszcza proces, za pomocą którego cyfrowe dokumenty są utworzone, udostępnionych drukowane, wyświetlać i archiwizowane. Aby uzyskać dodatkowe informacje na temat [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], zobacz [witryny sieci Web XPS](http://www.microsoft.com/xps).  
  
 Kilka technik do drukowania [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] na podstawie zawartości przy użyciu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przedstawiono w części [programowo plików XPS drukowania](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Mogą być przydatne do odwołania te przykłady podczas Przejrzyj elementy zawarte w tym temacie. (Deweloperom kodu niezarządzanego powinny być widoczne w dokumentacji [funkcja MXDC_ESCAPE](https://msdn.microsoft.com/library/windows/desktop/dd162739.aspx). [!INCLUDE[TLA2#tla_winforms#initcap](../../../../includes/tla2sharptla-winformssharpinitcap-md.md)] Deweloperzy muszą używać [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] w <xref:System.Drawing.Printing> przestrzeni nazw, który nie obsługuje pełny [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ścieżki wydruku, ale ma Obsługa ścieżki wydruku hybrydowego GDI-XPS. Zobacz **architektura ścieżki wydruku** poniżej.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Ścieżki wydruku XPS  
 [!INCLUDE[TLA#tla_metro](../../../../includes/tlasharptla-metro-md.md)] Ścieżki wydruku jest nowy [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] funkcja, która ponownie definiuje sposób obsługi drukowania w aplikacjach systemu Windows. Ponieważ [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] można zastąpić język prezentacji dokumentu (na przykład RTF), bufor wydruku format (WMF) i język opisu strony (na przykład PCL lub Postscript); przechowuje nowej ścieżki wydruku [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] format z aplikacji publikacji w celu końcowego przetwarzania sterownika drukarki lub urządzenia.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Ścieżki wydruku jest oparty na [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] modelu sterownika drukarki (XPSDrv), który zapewnia kilka korzyści dla deweloperów, takie jak [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] drukowania, Ulepszona obsługa koloru i znacznie wyższą wydajność drukowania. (Aby uzyskać więcej informacji na temat XPSDrv, zobacz [Windows Driver Development Kit](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
 Operacja bufor wydruku dla [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentów jest zasadniczo taki sam, jak w poprzednich wersjach systemu Windows. Jednak została rozszerzona w celu obsługi [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżki wydruku oprócz istniejące [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżki wydruku. Nowa ścieżka wydruku natywnie wykorzystuje [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] pliku buforu. Podczas trybu użytkownika sterowniki drukarki dla wcześniejszych wersji programu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] będą nadal działać, [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sterownika drukarki (XPSDrv) jest wymagana, aby można było używać [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżki wydruku.  
  
 Korzyści wynikające z [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżki wydruku są istotne, a obejmują:  
  
-   [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] Obsługa drukowania  
  
-   Macierzysty mechanizm obsługi profilów zaawansowane kolorów, które obejmują 32 bitów na kanał, CMYK, kolory o nazwie, n farby i macierzystą obsługę przejrzystości i gradienty.  
  
-   Większa wydajność wydruku zarówno dla [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] i [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacje.  
  
-   Branżowy standard [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] format.  
  
 W przypadku podstawowych scenariuszy wydruku a proste i intuicyjne [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] jest dostępna w programie jeden punkt wejścia dla użytkowników interface, konfiguracji i zadania przesyłania. Dla zaawansowanych scenariuszy, dodano obsługę dodatkowych [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dostosowywania (lub nie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w ogóle), synchronicznego lub asynchronicznego drukowanie i partii możliwości drukowania. Obie te opcje zapewniają obsługę drukowania w trybie pełnej lub częściowej relacji zaufania.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] została zaprojektowana z rozszerzeń na uwadze. Za pomocą strukturę rozszerzalności, funkcje i możliwości mogą być dodawane do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] w sposób modułowych. Funkcje rozszerzalności:  
  
-   Drukowanie schematu. Schemat publicznej jest regularnie aktualizowana i umożliwia szybkie rozszerzenie możliwości urządzenia. (Zobacz **PrintTicket i elementu PrintCapabilities** poniżej.)  
  
-   Potok rozszerzonego filtru. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Potoku filtru (XPSDrv) sterownika drukarki zaprojektowano tak, aby włączyć drukowanie zarówno bezpośrednio, jak i skalowalne [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentów. (Wyszukaj "XPSDrv" w [zestaw sterowników systemu Windows](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
### <a name="print-path-architecture"></a>Architektura drukowania ścieżki  
 Zarówno podczas [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikacje obsługują [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] aplikacje używają [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] konwersji, aby można było utworzyć [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sformatowaną zawartość dla [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sterownika drukarki (XPSDrv). Te aplikacje nie muszą korzystać z [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] drukowania ścieżki i mogą w dalszym ciągu używać [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] na podstawie drukowania. Jednak większość [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcje i ulepszenia, są dostępne tylko dla aplikacji, które odnoszą się do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżki wydruku.  
  
 Aby włączyć korzystanie z drukarek na podstawie XPSDrv przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] aplikacji, [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sterownika drukarki (XPSDrv) obsługuje konwersję z [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] format. XPSDrv model udostępnia również konwerter dla [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] format, aby [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji można drukować [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentów. Dla [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje, konwersja [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] format odbywa się automatycznie przez <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> klasy zawsze, gdy kolejka wydruku docelowy operacji zapisu nie ma Sterownik XPSDrv. ([!INCLUDE[TLA2#tla_winforms#initcap](../../../../includes/tla2sharptla-winformssharpinitcap-md.md)] aplikacje nie mogą drukować [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty.)  
  
 Poniższa ilustracja przedstawia podsystem wydruku i definiuje fragmenty udostępnione przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]i części zdefiniowanych przez producentów sprzętu i oprogramowania.  
  
 ![System drukowania XPS](../../../../docs/framework/wpf/advanced/media/xpsprint.PNG "XPSPrint")  
  
### <a name="basic-xps-printing"></a>Drukowanie podstawowe XPS  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definiuje zarówno podstawowego i zaawansowanego [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Dla tych aplikacji, które nie wymagają szeroką gamę drukowanie dostosowanie lub dostęp do pełnej [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] zestaw funkcji podstawowych wydruku Pomoc techniczna jest dostępna. Podstawowa pomoc techniczna wydruku jest uwidaczniany za pomocą formantu okna dialogowego drukowania, który wymaga minimalnej konfiguracji i funkcji znanych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Wiele [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcji dostępnych za pomocą uproszczonego modelu wydruku.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrola zapewnia jeden punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguracji i [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] przesyłania zadania. Aby uzyskać informacje o sposobie tworzenia wystąpienia oraz użycie kontroli, zobacz [Wywołaj okno dialogowe Drukuj](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Zaawansowane XPS drukowania  
 Pełny zestaw dostępu do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcje zaawansowane drukowania [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] musi być używany. Niektóre istotne [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] są opisane bardziej szczegółowo poniżej. Aby uzyskać pełną listę [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżki wydruku [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], zobacz <xref:System.Windows.Xps> i <xref:System.Printing> odwołania do przestrzeni nazw.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket i elementu PrintCapabilities  
 <xref:System.Printing.PrintTicket> i <xref:System.Printing.PrintCapabilities> klasy są foundation z zaawansowanych [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcji. Oba typy obiektów [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] sformatowany struktury zorientowane na drukowanie funkcje, takie jak sortowania druku dwustronnego, Obsługa zszywania, itp. Te struktury są definiowane przez schemat wydruku. A <xref:System.Printing.PrintTicket> powoduje, że drukarka jak przetwarzanie zadania drukowania. <xref:System.Printing.PrintCapabilities> Klasa definiuje możliwości drukarki. Badając możliwości drukarki, <xref:System.Printing.PrintTicket> mogą być tworzone, że wykorzystuje pełną drukarki na obsługiwane funkcje. Podobnie można uniknąć nieobsługiwane funkcje.  
  
 W poniższym przykładzie pokazano sposób wysyłania kwerend <xref:System.Printing.PrintCapabilities> drukarki i Utwórz <xref:System.Printing.PrintTicket> przy użyciu kodu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](../../../../samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer i PrintQueue  
 <xref:System.Printing.PrintServer> Klasa reprezentuje sieć serwera wydruku i <xref:System.Printing.PrintQueue> klasa reprezentuje drukarki i dane wyjściowe kolejki zadań skojarzonych z nim. Razem te [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Zezwalaj na Zaawansowane zarządzanie zadaniami drukowania na serwerze. A <xref:System.Printing.PrintServer>, lub jeden z jej klas pochodnych służy do zarządzania <xref:System.Printing.PrintQueue>. <xref:System.Printing.PrintQueue.AddJob%2A> Metoda służy do wstawiania nowe zadanie drukowania w kolejce.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Printing.LocalPrintServer> i uzyskiwać dostęp do domyślnej <xref:System.Printing.PrintQueue> przy użyciu kodu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter>, Z jego wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod, służy do zapisywania [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentów do <xref:System.Printing.PrintQueue>. Na przykład <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> metoda jest używana do wyjścia [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentu i <xref:System.Printing.PrintTicket> synchronicznie. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> Metoda jest używana do wyjścia [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentu i <xref:System.Printing.PrintTicket> asynchronicznie.  
  
 W poniższym przykładzie pokazano, jak utworzyć <xref:System.Windows.Xps.XpsDocumentWriter> przy użyciu kodu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Metody udostępniają również metody drukowania. Zobacz [programowane drukowanie plików XPS](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Aby uzyskać więcej informacji.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Ścieżki wydruku GDI  
 Gdy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje natywnie obsługują [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżki wydruku [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] aplikacje mogą również korzystać z niektórych [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcji. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Sterownika drukarki (XPSDrv) można przekonwertować [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] na podstawie danych wyjściowych do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] format. W zaawansowanych scenariuszach niestandardowe Konwersja zawartości jest obsługiwana przy użyciu [Microsoft XPS dokumentu konwertera (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx). Podobnie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji można również dane wyjściowe do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżki wydruku, wywołując jedną z <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> lub <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> klasy i wyznaczające drukarki z systemem innym niż XpsDrv jako miejsce docelowe kolejki wydruku.  

W przypadku aplikacji, które nie wymagają [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkcji lub pomocy technicznej, bieżący [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżki wydruku pozostaje niezmieniona.  
  
-   Odwołanie dodatkowe materiały na [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] ścieżki i różnych wydruku [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] opcje konwersji, zobacz [Microsoft XPS dokumentu konwertera (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx) i "XPSDrv" w [zestaw sterowników systemu Windows](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Model sterownika XPSDrv  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Ścieżki wydruku zwiększa wydajność bufor za pomocą [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] jako formatu macierzystego buforu wydruku podczas drukowania na [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] — włączone drukarki lub sterownika. Proces uproszczony buforowania eliminuje potrzebę Wygeneruj plik pośredni buforu, takich jak [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] pliku danych, przed umieszczonych w buforze dokumentu. Za pomocą mniejsze pliki buforu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ścieżki wydruku można zmniejszyć obciążenie sieci i zwiększyć wydajność drukowania.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] jest zamknięty formatu, który reprezentuje dane wyjściowe aplikacji jako serię wywołuje [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] usług renderowania. W odróżnieniu od [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] format buforu reprezentuje rzeczywisty dokumentu bez konieczności dalszej interpretacji podczas wypełniania wyjściowego [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]— na podstawie sterownika drukarki (XPSDrv). Sterowniki można korzystać bezpośrednio z danymi w formacie. Ta funkcja eliminuje danych i kolor konwersje miejsca wymagana, gdy używasz [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] plików i [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]— na podstawie sterowniki drukarek.  
  
 Rozmiary plików buforu zwykle zostaje ograniczone, korzystając z [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentów kierowanych [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sterownika drukarki (XPSDrv) w porównaniu z ich [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] odpowiedniki; istnieją wyjątki:  
  
-   Grafiki wektorowej, bardzo skomplikowane, nieefektywne napisane lub wielowarstwowy może być większy niż mapy bitowej wersji tej samej grafiki.  
  
-   Do wyświetlania ekranu pliki XPS osadzania czcionek urządzenia, a także czcionek oparte na komputerze; niezbędne pliki buforu GDI nie osadzaj czcionek urządzenia. Ale oba rodzaje czcionek są podzbiory (patrz poniżej) i sterowniki drukarki można usunąć czcionki urządzenia przed przekazaniem go do drukarki.  
  
 Zmniejszanie rozmiaru buforu realizuje kilka mechanizmów:  
  
-   **Korzystanie z podzbiorów czcionek**. Tylko znaki używane w tym dokumencie rzeczywiste są przechowywane w [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] pliku.  
  
-   **Zaawansowana obsługa grafiki**. Natywna obsługa podstawowych przejrzystości i gradientu pozwala uniknąć rasteryzacji zawartości w [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentu.  
  
-   **Identyfikacja wspólnych zasobów**. Zasoby, które są używane wielokrotnie (takich jak obraz, który reprezentuje logo firmy) są traktowane jako zasobów udostępnionych i są ładowane tylko raz.  
  
-   **Kompresja ZIP**. Wszystkie [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentów Użyj kompresji ZIP.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.PrintDialog>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.PrintQueue>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/printing-how-to-topics.md)  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [XPS](http://www.microsoft.com/xps)  
 [Serializacja dokumentu i przechowywanie](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)  
 [Konwerter (MXDC) dokumentów XPS firmy Microsoft](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx)
