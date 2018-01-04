---
title: Dokumenty w WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02f65d68cdaad8824905c4545239f5b607c672d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="documents-in-wpf"></a>Dokumenty w WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje szeroką gamę funkcji dokumentu, które umożliwiają tworzenie zawartości o wysokiej wierności, która ma być łatwiej uzyskuje się dostęp i odczytu niż w poprzednich generacji [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Oprócz udoskonalone funkcje i jakości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia zintegrowane usługi wyświetlania dokumentu, opakowywanie i zabezpieczeń. Ten temat zawiera wprowadzenie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typów dokumentów i pakowania dokumentu.  
  
  
<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Typy dokumentów  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dokumenty są podzielone na dwie szerokie kategorie, w oparciu o ich przeznaczenia; tych kategorii w dokumencie są określane jako "dokumenty stałej" i "przepływ dokumenty".  
  
 Stały dokumenty są przeznaczone dla aplikacji, które wymagają precyzyjnego [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] prezentacji, niezależnie od sprzętu wyświetlacza lub drukarki używanego. Typowe zastosowania stałym dokumenty obejmują DTP tekstów i układu formularza, których przestrzeganie oryginalny projekt strony jest szczególnie ważne. W ramach jego układ niezależnie od wyświetlania lub drukowania urządzenie używane dokładne pozycyjnych rozmieszczenia elementów zawartości zachowuje stałym dokumentu. Na przykład stałej dokumentu wyświetlane na ekranie 96 dpi zostanie wyświetlona strona dokładnie takie same, gdy jest on dane wyjściowe do drukarki laserowe 600 dpi jako w przypadku jest dane wyjściowe do phototypesetter 4800 dpi. Układ strony, jest taka sama we wszystkich przypadkach, gdy maksymalizuje jakości dokumentu do funkcji poszczególnych urządzeń.  
  
 W porównaniu przepływu dokumentów zostały zaprojektowane w celu zoptymalizowania wyświetlania i czytelności i najlepiej są wykorzystywane podczas czytelnej jest scenariusz użycia głównej dokumentu. Zamiast ustawiany jeden układ wstępnie zdefiniowane, dokumenty przepływu dynamicznie dostosować i ułożenia ich zawartość na podstawie czasu wykonywania zmiennych, takich jak rozmiar okna, rozdzielczość urządzenia i preferencje użytkownika opcjonalne. Strona sieci Web jest prosty przykład dokumentu przepływu, gdzie zawartość strony dynamicznie jest sformatowany do bieżącego okna. Dokumenty przepływu zoptymalizować wyświetlania i odczytywania środowisko dla użytkownika, na podstawie środowiska środowiska wykonawczego. Na przykład tego samego dokumentu przepływu będzie dynamicznie przeformatować do optymalnej czytelności rozdzielczości 19 cala lub ekranu urządzenia PDA małych cala 2 x 3. Ponadto przepływ dokumenty mają wiele wbudowane funkcje takie jak wyszukiwanie, przeglądanie tryby optymalizacji czytelności i możliwość zmiany rozmiaru i wyglądu czcionek.  Zobacz [przepływu dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md) ilustracje, przykłady i szczegółowe informacje na temat przepływu dokumentów.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Dokument formantów i układu tekstu  
 [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] Zawiera zestaw wbudowanych formantów, które upraszczają przy użyciu stałej dokumentów, dokumenty przepływu i ogólne tekst wewnątrz aplikacji.  Wyświetlanie zawartości dokumentu stałej jest obsługiwana za pomocą <xref:System.Windows.Controls.DocumentViewer> formantu.  Wyświetlanie zawartości dokumentów przepływu jest obsługiwana przez trzy inne formanty: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer> który mapowania na różne scenariusze użytkownika (patrz poniżej).  Inne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy sterujące udostępniają uproszczoną układu obsługuje ogólne tekstu używa (zobacz [tekst w interfejsie użytkownika](#text_in_the_user_interface), poniżej).  
  
### <a name="fixed-document-control---documentviewer"></a>Sterowanie stałym dokumentu - DocumentViewer  
 <xref:System.Windows.Controls.DocumentViewer> Formantu służy do wyświetlania <xref:System.Windows.Documents.FixedDocument> zawartości. <xref:System.Windows.Controls.DocumentViewer> Kontrola zapewnia intuicyjny interfejs użytkownika, który udostępnia wbudowaną obsługę dla typowych operacji w tym wydruku, skopiować do Schowka, powiększenia i funkcji wyszukiwania tekstu. Formant zapewnia dostęp do stron zawartości za pomocą znanych mechanizmu przewijania. Takich jak wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantów, <xref:System.Windows.Controls.DocumentViewer> obsługuje pełną lub częściową restyling, co pozwala kontroli być wizualnie zintegrowane praktycznie dowolne aplikacji lub w środowisku.  
  
 <xref:System.Windows.Controls.DocumentViewer>Służy do wyświetlania zawartości w sposób tylko do odczytu. Edycja lub zmiana zawartości nie jest dostępna i nie jest obsługiwany.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Przepływ kontroli dokumentów  
 **Uwaga:** bardziej szczegółowe informacje o funkcjach dokumentu przepływu i sposób ich tworzenia, zobacz [przepływu dokumentami — omówienie](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 Wyświetlanie zawartości dokumentów przepływu jest obsługiwana przez formanty trzy: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>zawiera funkcje, które umożliwiają użytkownikowi dynamicznie wybrać różne tryby wyświetlania, w tym tryb wyświetlania (strony na a-time) jednej strony, dwa strony na pojedynczych (format księgi odczytu) wyświetlanie trybu i trybie przewijania ciągłego wyświetlania (nieograniczone od dołu).  Aby uzyskać więcej informacji na temat trybów wyświetlania, zobacz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Jeśli nie potrzebujesz możliwości dynamicznie przełączać tryby wyświetlania różnych <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> Podaj zawartości przeglądarek, które zostały usunięte w trybie przeglądania określonego jaśniejszego wagi przepływu.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer i FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>Pokazuje zawartość strony w czasie trybu wyświetlania, podczas gdy <xref:System.Windows.Controls.FlowDocumentScrollViewer> pokazuje zawartości w trybie przewijania ciągłego.  Zarówno <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> zostały usunięte w trybie przeglądania określonego. Porównaj z <xref:System.Windows.Controls.FlowDocumentReader>, która obejmuje funkcje, które umożliwiają użytkownikowi dynamicznie wybrać różne tryby wyświetlania (zgodnie z <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> wyliczenie), kosztem jest więcej zasobów niż <xref:System.Windows.Controls.FlowDocumentPageViewer> lub <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Domyślnie pionowy pasek przewijania jest zawsze widoczne, a poziomy pasek przewijania jest widoczna, jeśli to konieczne. Wartość domyślna [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla <xref:System.Windows.Controls.FlowDocumentScrollViewer> nie obejmuje paska narzędzi, ale <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> właściwości może służyć do włączenia wbudowanego paska narzędzi.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Tekst w interfejsie użytkownika  
 Oprócz Dodawanie tekstu do dokumentów, tekst oczywiście można w aplikacji interfejsu użytkownika, takie jak formularze. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele formantów na rysowanie tekstu na ekranie. Każdej kontrolki jest przeznaczona do innego scenariusza i ma własną listę funkcji i ograniczenia. Ogólnie rzecz biorąc <xref:System.Windows.Controls.TextBlock> Jeśli obsługa ograniczona tekstu jest wymagane, na przykład krótki zdanie w, należy użyć elementu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>można można użyć, gdy wymagana jest obsługa minimalnej ilości tekstu. Aby uzyskać więcej informacji, zobacz [omówienie blok tekstu](../../../../docs/framework/wpf/controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>OPAKOWYWANIE dokumentu  
 <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Zapewnić skuteczne do organizowania danych aplikacji, zawartości dokumentu i powiązanych zasobów w jeden kontener, który jest łatwy do dostępu, przenośne i łatwe do dystrybucji. Plik ZIP jest przykładem <xref:System.IO.Packaging.Package> typu może obsługiwać wiele obiektów jako pojedyncza jednostka. OPAKOWYWANIE [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] zapewniania domyślnego <xref:System.IO.Packaging.ZipPackage> implementacji zaprojektowany przy użyciu standardu otwartych Konwencji pakietów z architekturą pliku XML i ZIP. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Pakowania [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ułatwiają do tworzenia pakietów i przechowywać i uzyskiwanie dostępu do obiektów w nich. Obiekt zapisany w <xref:System.IO.Packaging.Package> nazywa się <xref:System.IO.Packaging.PackagePart> ("części"). Pakiety mogą również obejmować podpisanych certyfikatów cyfrowych, które mogą służyć do identyfikowania inicjatorem części i do zweryfikowania, że zawartość pakietu nie został zmodyfikowany.  Obejmuje to też pakietów <xref:System.IO.Packaging.PackageRelationship> funkcja, która umożliwia dodatkowe informacje, które mają być dodane do pakietu lub skojarzone z określonych części nie modyfikując zawartość części istniejącej.  Pakiet również usług pomocy technicznej [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Architektura pakietu służy jako podstawa dla wielu technologii klucza:  
  
-   [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]dokumenty odpowiadające [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)].  
  
-   Microsoft Office "12" Otwórz format dokumentów XML (.docx).  
  
-   Formaty magazynu niestandardowego dla projektu aplikacji.  
  
 Oparte na opakowaniu interfejsów API, <xref:System.Windows.Xps.Packaging.XpsDocument> zaprojektowane specjalnie do przechowywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stałej zawartości dokumentów. <xref:System.Windows.Xps.Packaging.XpsDocument> Jest niezależna dokument, który można otworzyć w przeglądarce, wyświetlane w <xref:System.Windows.Controls.DocumentViewer> formantu, kierowane do buforu wydruku lub bezpośrednio do wyjścia [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-zgodne drukarki.  
  
 Poniższe sekcje zawierają dodatkowe informacje o <xref:System.IO.Packaging.Package> i <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] wyposażone [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Składniki pakietu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Interfejsy API umożliwiają dane aplikacji i dokumentów, aby uporządkować w jedną jednostkę przenośną opakowania. Plik ZIP jest jednym z najbardziej typowych pakietów i podano domyślny typ pakietu z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package>jest klasą abstrakcyjną, z którego <xref:System.IO.Packaging.ZipPackage> jest zaimplementowany przy użyciu Otwórz standardowe XML i ZIP pliku architektury.  <xref:System.IO.Packaging.Package.Open%2A> Używa metody <xref:System.IO.Packaging.ZipPackage> tworzenie i używanie plików ZIP domyślnie. Pakiet może zawierać trzy podstawowe typy elementów:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Pliki zawartości, danych, dokumentów i zasobów aplikacji.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certyfikat X.509] identyfikacji, uwierzytelniania i weryfikacji.|  
|<xref:System.IO.Packaging.PackageRelationship>|Dodano informacje dotyczące pakietu lub jego części.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> ("części") jest klasą abstrakcyjną, odnoszący się do obiektu przechowywanego w <xref:System.IO.Packaging.Package>. W pliku ZIP części pakietów odpowiadają poszczególnych plików przechowywanych w pliku ZIP.  <xref:System.IO.Packaging.ZipPackagePart>udostępnia domyślną implementację dla serializacji obiektów przechowywanych w <xref:System.IO.Packaging.ZipPackage>.  Jak system plików elementy zawarte w pakiecie są przechowywane w katalogu hierarchicznego lub organizacja "folder-style".  Przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pakowania interfejsów API, aplikacje można zapisać, przechowywania i odczytu wiele <xref:System.IO.Packaging.PackagePart> obiektów przy użyciu jednego kontenera pliku ZIP.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Dla bezpieczeństwa <xref:System.IO.Packaging.PackageDigitalSignature> ("podpis cyfrowy") może być skojarzony z części w ramach pakietu. A <xref:System.IO.Packaging.PackageDigitalSignature> zawiera [509] zapewnia dwie funkcje:  
  
1.  Identyfikuje i uwierzytelnia inicjatorem części.  
  
2.  Sprawdza, czy element nie został zmodyfikowany.  
  
 Podpis cyfrowy nie uniemożliwia części jest modyfikowany, ale sprawdzanie poprawności względem podpisu cyfrowego zakończy się niepowodzeniem, jeśli element został zmieniony w dowolny sposób. Aplikację można następnie automatycznie podjąć odpowiednie działania — na przykład blokowanie otwierania części lub powiadamia użytkownika, że element został zmodyfikowany i nie jest bezpieczna.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> ("relacji"), udostępnia mechanizm do kojarzenia dodatkowych informacji z pakietu lub części w pakiecie. Relacja jest zakładzie poziomie pakietu, który można skojarzyć dodatkowe informacje z częścią określającą bez modyfikowania zawartości części rzeczywistych. Wstawianie nowych danych bezpośrednio do zawartości części zazwyczaj nie jest praktyczne w wielu przypadkach:  
  
-   Rzeczywisty typ części i jego schematu zawartości nie jest znany.  
  
-   Nawet wtedy, gdy wiadomo, schematu zawartości może nie zawierać do dodawania nowych informacji.  
  
-   Część może być cyfrowo podpisana lub zaszyfrowana, ograniczenia żadnych modyfikacji.  
  
 Relacje pakietu umożliwiają wykrywalny dodawania i kojarzenie dodatkowe informacje z poszczególnych części lub cały pakiet. Pakiet relacje są używane dwie podstawowe funkcje:  
  
1.  Definiowanie relacji zależności z jednej strony do innej.  
  
2.  Definiowanie relacji informacje, które dodawać notatki lub innych danych związanych z części.  
  
 A <xref:System.IO.Packaging.PackageRelationship> zapewnia to szybki i łatwy do definiowania zależności i dodać inne informacje skojarzone z części pakietu lub pakiet jako całość.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Relacji zależności  
 Relacji zależności służą do opisywania zależności, które jedną część sprawia, że do innych części. Na przykład pakiet może zawierać części HTML, który zawiera co najmniej jedną \<img > obrazu znaczników. Tagi obrazu odwoływać się do obrazów, które znajdują się albo inne części wewnętrzny do pakietu lub na zewnątrz pakietu (takie jak dostępne za pośrednictwem Internetu). Tworzenie <xref:System.IO.Packaging.PackageRelationship> skojarzone z HTML pliku ułatwia wykrywanie i uzyskiwania dostępu do zasobów zależnych, szybkie i łatwe. Aplikacji przeglądarki, lub podglądu może bezpośrednio uzyskać dostępu do części relacje i natychmiast rozpocząć zebrania zasoby zależne, bez uprzedniego uzyskania informacji o schemacie lub analizowania dokumentu.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Informacje o relacjach  
 Podobnie jak Uwaga lub adnotacji, <xref:System.IO.Packaging.PackageRelationship> mogą służyć do przechowywania innych typów informacji ma zostać skojarzony z częścią określającą bez konieczności modyfikowania faktycznie samej zawartości części.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>Dokumenty XPS  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]dokument jest pakiet, który zawiera jeden lub więcej stałej dokumentów wraz z zasobów i informacje wymagane do renderowania.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]jest również natywnego [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] format pliku buforu wydruku.  <xref:System.Windows.Xps.Packaging.XpsDocument> Są przechowywane w standardowe ZIP zestawu danych i mogą zawierać kombinację XML i binarne składników, takich jak pliki obrazów i czcionki. [PackageRelationships](#PackageRelationships) są używane do definiowania zależności między zawartość i zasoby wymagane do renderowania pełni dokumentu.  <xref:System.Windows.Xps.Packaging.XpsDocument> Projekt zapewnia rozwiązanie jednego dokumentu o wysokiej wierności, który obsługuje wielu zastosowań:  
  
-   Czytania, zapisywania i przechowywania jako plik pojedynczego, przenośne i łatwe do dystrybucji zawartości dokumentu stałej i zasobów.  
  
-   Wyświetlanie dokumentów za pomocą [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] aplikację Podgląd.  
  
-   Generowanie dokumentów w macierzystym buforu wydruku wyjściowy format [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
-   Routing dokumentów bezpośrednio do [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-zgodne drukarki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Documents.FixedDocument>  
 <xref:System.Windows.Documents.FlowDocument>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.IO.Packaging.ZipPackage>  
 <xref:System.IO.Packaging.ZipPackagePart>  
 <xref:System.IO.Packaging.PackageRelationship>  
 <xref:System.Windows.Controls.DocumentViewer>  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Przegląd dokumentu przepływu](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Przegląd drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Serializacja dokumentu i przechowywanie](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)
