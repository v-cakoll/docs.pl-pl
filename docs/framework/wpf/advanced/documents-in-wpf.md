---
title: Dokumenty
ms.date: 03/30/2017
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
ms.openlocfilehash: e88604c42b253b48ee605f42f24fe301e339f74b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174683"
---
# <a name="documents-in-wpf"></a>Dokumenty w WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje szeroką gamę funkcji dokumentu, które umożliwiają tworzenie zawartości o wysokiej wierności, która jest zaprojektowana tak, aby była łatwiej dostępna i odczytywana niż w poprzednich generacjach systemu Windows. Oprócz zwiększonych możliwości i jakości, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia również zintegrowane usługi wyświetlania dokumentów, pakowania i bezpieczeństwa. Ten temat zawiera [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wprowadzenie do typów dokumentów i pakowania dokumentów.  

<a name="types_of_documents"></a>
## <a name="types-of-documents"></a>Rodzaje dokumentów  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dzieli dokumenty na dwie szerokie kategorie na podstawie ich przeznaczenia; te kategorie dokumentów są określane jako "dokumenty stałe" i "dokumenty przepływu".  
  
 Stałe dokumenty są przeznaczone do aplikacji, które wymagają precyzyjnej prezentacji "to, co widzisz, jest tym, co otrzymujesz" (WYSIWYG), niezależnie od używanego sprzętu wyświetlacza lub drukarki. Typowe zastosowania dokumentów stałych obejmują publikowanie na pulpicie, przetwarzanie tekstu i układ formularza, gdzie przestrzeganie oryginalnego projektu strony ma kluczowe znaczenie. W ramach swojego układu stały dokument zachowuje dokładne położenie elementów zawartości niezależnie od używanego wyświetlacza lub urządzenia drukującego. Na przykład stała strona dokumentu wyświetlana na wyświetlaczu o rozdzielczości 96 dpi będzie wyświetlana dokładnie tak samo, gdy zostanie wysuń do drukarki laserowej 600 dpi, jak wtedy, gdy zostanie wysunięty do fototyssetera 4800 dpi. Układ strony pozostaje taka sama we wszystkich przypadkach, podczas gdy jakość dokumentu maksymalizuje możliwości każdego urządzenia.  
  
 Dla porównania dokumenty przepływu są przeznaczone do optymalizacji wyświetlania i czytelności i są najlepiej wykorzystywane, gdy łatwość odczytu jest podstawowym scenariuszem zużycia dokumentu. Zamiast być ustawione na jeden wstępnie zdefiniowany układ, dokumenty przepływu dynamicznie dostosować i ponownie wlać zawartość na podstawie zmiennych czasu wykonywania, takich jak rozmiar okna, rozdzielczość urządzenia i opcjonalne preferencje użytkownika. Strona sieci Web jest prostym przykładem dokumentu przepływu, w którym zawartość strony jest dynamicznie formatowana w celu dopasowania do bieżącego okna. Dokumenty przepływu optymalizują środowisko wyświetlania i odczytywania dla użytkownika na podstawie środowiska wykonawczego. Na przykład ten sam dokument przepływu będzie dynamicznie formatować w celu uzyskania optymalnej czytelności na wyświetlaczu o wysokiej rozdzielczości 19-calowym lub małym ekranie PDA o wymiarach 2x3 cala. Ponadto dokumenty przepływu mają wiele wbudowanych funkcji, w tym wyszukiwanie, tryby wyświetlania, które optymalizują czytelność, oraz możliwość zmiany rozmiaru i wyglądu czcionek.  Zobacz [Omówienie dokumentu przepływu, aby](flow-document-overview.md) uzyskać ilustracje, przykłady i szczegółowe informacje na temat dokumentów przepływu.  
  
<a name="document_viewer"></a>
## <a name="document-controls-and-text-layout"></a>Kontrolki dokumentu i układ tekstu  
 .NET Framework zawiera zestaw wstępnie utworzonych formantów, które upraszczają przy użyciu dokumentów stałych, dokumentów przepływu i tekstu ogólnego w aplikacji.  Wyświetlanie stałej zawartości dokumentu jest <xref:System.Windows.Controls.DocumentViewer> obsługiwane za pomocą formantu.  Wyświetlanie zawartości dokumentu przepływu jest obsługiwane przez <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer>trzy <xref:System.Windows.Controls.FlowDocumentScrollViewer> różne kontrolki: , i które są mapowane na różne scenariusze użytkownika (patrz sekcje poniżej).  Inne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formanty zapewniają uproszczony układ do obsługi ogólnych zastosowań tekstu (patrz [Tekst w interfejsie użytkownika](#text_in_the_user_interface)poniżej).  
  
### <a name="fixed-document-control---documentviewer"></a>Poprawiona kontrola dokumentu — DocumentViewer  
 Formant <xref:System.Windows.Controls.DocumentViewer> jest przeznaczony <xref:System.Windows.Documents.FixedDocument> do wyświetlania zawartości. Formant <xref:System.Windows.Controls.DocumentViewer> zapewnia intuicyjny interfejs użytkownika, który zapewnia wbudowaną obsługę typowych operacji, w tym drukowania, kopiowania do schowka, powiększania i wyszukiwania tekstu. Formant zapewnia dostęp do stron zawartości za pośrednictwem znanego mechanizmu przewijania. Podobnie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jak <xref:System.Windows.Controls.DocumentViewer> wszystkie formanty, obsługuje pełną lub częściową restyling, która umożliwia wizualnie zintegrować formant z praktycznie dowolnej aplikacji lub środowiska.  
  
 <xref:System.Windows.Controls.DocumentViewer>jest przeznaczony do wyświetlania treści w sposób tylko do odczytu; edycja lub modyfikacja zawartości nie jest dostępna i nie jest obsługiwana.  
  
<a name="flow_document"></a>
### <a name="flow-document-controls"></a>Kontrolki dokumentu przepływu  

> [!NOTE]
> Aby uzyskać bardziej szczegółowe informacje na temat funkcji dokumentu przepływu i sposobu ich tworzenia, zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).  
  
 Wyświetlanie zawartości dokumentu przepływu jest obsługiwane <xref:System.Windows.Controls.FlowDocumentReader>przez <xref:System.Windows.Controls.FlowDocumentPageViewer>trzy <xref:System.Windows.Controls.FlowDocumentScrollViewer>formanty: , , i .  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>zawiera funkcje, które umożliwiają użytkownikowi dynamiczne wybieranie między różnymi trybami wyświetlania, w tym trybem wyświetlania jednej strony (page-at-a-time), trybem wyświetlania dwóch stron na raz (format czytania książek) oraz trybem wyświetlania ciągłego przewijania (bez dna).  Aby uzyskać więcej informacji na <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>temat tych trybów wyświetlania, zobacz .  Jeśli nie potrzebujesz możliwości dynamicznego przełączania się między <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> różnymi trybami wyświetlania i zapewnienia przeglądarki zawartości o mniejszej wadze, które są stałe w określonym trybie wyświetlania.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>Widok FlowDocumentPageViewer i FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>pokazuje zawartość w trybie przeglądania strony naraz, a jednocześnie <xref:System.Windows.Controls.FlowDocumentScrollViewer> pokazuje zawartość w trybie ciągłego przewijania.  Oba <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> i są stałe do określonego trybu wyświetlania. Porównaj <xref:System.Windows.Controls.FlowDocumentReader>z , który zawiera funkcje, które umożliwiają użytkownikowi dynamicznie <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> wybierać między różnymi trybami wyświetlania (zgodnie z wyliczeniem), kosztem jest bardziej zasobochłonne niż <xref:System.Windows.Controls.FlowDocumentPageViewer> lub <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Domyślnie zawsze wyświetlany jest pionowy pasek przewijania, a w razie potrzeby poziomy pasek przewijania staje się widoczny. Wartość [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] domyślna <xref:System.Windows.Controls.FlowDocumentScrollViewer> nie obejmuje paska narzędzi; jednak <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> właściwość może służyć do włączania wbudowanego paska narzędzi.  
  
<a name="text_in_the_user_interface"></a>
### <a name="text-in-the-user-interface"></a>Tekst w interfejsie użytkownika  
 Oprócz dodawania tekstu do dokumentów, tekst może być oczywiście używany w interfejsie użytkownika aplikacji, takich jak formularze. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele elementów sterujących rysowania tekstu na ekranie. Każdy formant jest przeznaczony do innego scenariusza i ma własną listę funkcji i ograniczeń. Ogólnie rzecz <xref:System.Windows.Controls.TextBlock> biorąc element powinien być używany, gdy wymagana jest ograniczona [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]obsługa tekstu, na przykład krótkie zdanie w pliku . <xref:System.Windows.Controls.Label>może być używany, gdy wymagana jest minimalna obsługa tekstu. Aby uzyskać więcej informacji, zobacz [Omówienie blokowania tekstu](../controls/textblock-overview.md).  
  
<a name="packaging"></a>
## <a name="document-packaging"></a>Pakowanie dokumentów  
 Interfejsy API zapewniają wydajne środki do organizowania <xref:System.IO.Packaging> danych aplikacji, zawartości dokumentu i powiązanych zasobów w jednym kontenerze, który jest łatwy w dostępie, przenośny i łatwy do dystrybucji. Plik ZIP jest przykładem <xref:System.IO.Packaging.Package> typu zdolnego do przechowywania wielu obiektów jako pojedynczej jednostki. Interfejsy API pakowania zapewniają <xref:System.IO.Packaging.ZipPackage> domyślną implementację zaprojektowaną przy użyciu standardu Open Packaging Conventions z architekturą plików XML i ZIP. Interfejsy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API pakowania ułatwiają tworzenie pakietów oraz przechowywanie i uzyskiwanie dostępu do obiektów w nich zawartych. Obiekt przechowywany w <xref:System.IO.Packaging.Package> a jest <xref:System.IO.Packaging.PackagePart> określany jako ("część"). Pakiety mogą również zawierać podpisane certyfikaty cyfrowe, które mogą służyć do identyfikacji inicjatora części i sprawdzania, czy zawartość pakietu nie została zmodyfikowana.  Pakiety zawierają <xref:System.IO.Packaging.PackageRelationship> również funkcję, która umożliwia dodawanie dodatkowych informacji do pakietu lub skojarzone z określonymi częściami bez faktycznej modyfikacji zawartości istniejących części.  Usługi pakietów obsługują również usługę Microsoft Windows Rights Management (RM).  
  
 Architektura [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pakietu służy jako podstawa dla wielu kluczowych technologii:  
  
- dokumentów XPS zgodnych ze specyfikacją papieru XML (XPS).  
  
- Pakiet Microsoft Office "12" otwiera dokumenty w formacie XML (docx).  
  
- Niestandardowe formaty pamięci masowej dla własnego projektu aplikacji.  
  
 Na podstawie interfejsów API <xref:System.Windows.Xps.Packaging.XpsDocument> opakowania, an jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] specjalnie zaprojektowany do przechowywania dokumentów o stałej zawartości. Jest <xref:System.Windows.Xps.Packaging.XpsDocument> to samodzielny dokument, który można otworzyć w przeglądarce, wyświetlić w <xref:System.Windows.Controls.DocumentViewer> formancie, przekierować do buforu wydruku lub wyjść bezpośrednio do drukarki zgodnej z xps.  
  
 Poniższe sekcje zawierają dodatkowe <xref:System.IO.Packaging.Package> <xref:System.Windows.Xps.Packaging.XpsDocument> informacje na temat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]interfejsów API i interfejsów API dostarczonych z .  
  
<a name="packages"></a>
### <a name="package-components"></a>Składniki pakietu  
 Interfejsy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API pakowania umożliwiają organizowanie danych i dokumentów aplikacji w jedną jednostkę przenośną. Plik ZIP jest jednym z najczęstszych typów pakietów i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jest domyślnym typem pakietu dostarczanym z programem .  <xref:System.IO.Packaging.Package>sama w sobie jest <xref:System.IO.Packaging.ZipPackage> klasą abstrakcyjną, z której jest implementowana przy użyciu otwartej standardowej architektury plików XML i ZIP.  Metoda <xref:System.IO.Packaging.Package.Open%2A> ta <xref:System.IO.Packaging.ZipPackage> jest domyślnie używana do tworzenia i używania plików ZIP. Pakiet może zawierać trzy podstawowe typy elementów:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Zawartość aplikacji, dane, dokumenty i pliki zasobów.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certyfikat X.509] do identyfikacji, uwierzytelniania i sprawdzania poprawności.|  
|<xref:System.IO.Packaging.PackageRelationship>|Dodano informacje związane z pakietem lub określoną częścią.|  
  
<a name="PackageParts"></a>
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> ("część") jest klasą abstrakcyjną, która <xref:System.IO.Packaging.Package>odwołuje się do obiektu przechowywanego w . W pliku ZIP części pakietu odpowiadają poszczególnym plikom przechowywanym w pliku ZIP.  <xref:System.IO.Packaging.ZipPackagePart>zapewnia domyślną implementację dla obiektów <xref:System.IO.Packaging.ZipPackage>serializable przechowywane w pliku .  Podobnie jak w systemie plików, części zawarte w pakiecie są przechowywane w hierarchicznym katalogu lub organizacji w stylu folderu.  Za [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pomocą interfejsów API pakowania aplikacje mogą <xref:System.IO.Packaging.PackagePart> zapisywać, przechowywać i odczytywać wiele obiektów przy użyciu jednego kontenera plików ZIP.  
  
<a name="PackageDigitalSignatures"></a>
#### <a name="packagedigitalsignatures"></a>PakietDigitalSygnatury  
 Ze względów <xref:System.IO.Packaging.PackageDigitalSignature> bezpieczeństwa ("podpis cyfrowy") można skojarzyć z częściami w pakiecie. A <xref:System.IO.Packaging.PackageDigitalSignature> zawiera [509], który zapewnia dwie funkcje:  
  
1. Identyfikuje i uwierzytelnia inicjatora części.  
  
2. Sprawdza, czy część nie została zmodyfikowana.  
  
 Podpis cyfrowy nie wyklucza modyfikacji części, ale sprawdzenie poprawności podpisu cyfrowego zakończy się niepowodzeniem, jeśli część zostanie w jakikolwiek sposób zmieniona. Aplikacja może następnie podjąć odpowiednie działania — na przykład zablokować otwarcie części lub powiadomić użytkownika, że część została zmodyfikowana i nie jest bezpieczna.  
  
<a name="PackageRelationships"></a>
#### <a name="packagerelationships"></a>PackageRelationships ( PackageRelationships )  
 A <xref:System.IO.Packaging.PackageRelationship> ("relacja") zapewnia mechanizm kojarzenia dodatkowych informacji z pakietem lub częścią w pakiecie. Relacja to obiekt na poziomie pakietu, który może wiązać dodatkowe informacje z częścią bez modyfikowania rzeczywistej zawartości części. Wstawianie nowych danych bezpośrednio do zawartości części zwykle nie jest praktyczne w wielu przypadkach:  
  
- Rzeczywisty typ części i jej schemat zawartości nie jest znany.  
  
- Nawet jeśli wiadomo, schemat zawartości może nie zapewnić środków do dodawania nowych informacji.  
  
- Część może być podpisana cyfrowo lub zaszyfrowana, wykluczając wszelkie modyfikacje.  
  
 Relacje pakietów zapewniają wykrywalny sposób dodawania i kojarzenia dodatkowych informacji z poszczególnymi częściami lub z całym pakietem. Relacje pakietów są używane dla dwóch podstawowych funkcji:  
  
1. Definiowanie relacji zależności z jednej części do drugiej.  
  
2. Definiowanie relacji informacyjnych, które dodają notatki lub inne dane związane z częścią.  
  
 A <xref:System.IO.Packaging.PackageRelationship> zapewnia szybkie, wykrywalne środki do definiowania zależności i dodawać inne informacje skojarzone z częścią pakietu lub pakietu jako całości.  
  
<a name="Dependency_Relationships"></a>
##### <a name="dependency-relationships"></a>Relacje zależności  
 Relacje zależności są używane do opisywania zależności, które jedna część sprawia, że do innych części. Na przykład pakiet może zawierać część HTML, \<która zawiera jeden lub więcej znaczników obrazu img>. Znaczniki obrazu odnoszą się do obrazów, które znajdują się jako inne części wewnętrzne do pakietu lub zewnętrzne do pakietu (na przykład dostępne przez Internet). Utworzenie skojarzonego z plikiem <xref:System.IO.Packaging.PackageRelationship> HTML sprawia, że odnajdywanie zasobów zależnych i uzyskiwanie do nich dostępu jest szybkie i łatwe. Aplikacja przeglądarki lub przeglądarki można bezpośrednio uzyskać dostęp do relacji części i natychmiast rozpocząć montaż zasobów zależnych bez znajomości schematu lub analizowania dokumentu.  
  
<a name="Information_Relationships"></a>
##### <a name="information-relationships"></a>Relacje informacyjne  
 Podobnie jak notatka lub adnotacja, a <xref:System.IO.Packaging.PackageRelationship> może być również używany do przechowywania innych typów informacji, które mają być skojarzone z częścią bez konieczności faktycznego modyfikowania samej zawartości części.  
  
<a name="XPS_Documents"></a>
## <a name="xps-documents"></a>Dokumenty XPS  
 Dokument specyfikacji papieru XML (XPS) to pakiet zawierający jeden lub więcej dokumentów stałych wraz ze wszystkimi zasobami i informacjami wymaganymi do renderowania.  XPS jest również natywnym formatem pliku buforu wydruku systemu Windows Vista.  An <xref:System.Windows.Xps.Packaging.XpsDocument> jest przechowywany w standardowym zestawie danych ZIP i może zawierać kombinację XML i składników binarnych, takich jak pliki obrazów i czcionek. [PackageRelations](#PackageRelationships) są używane do definiowania zależności między zawartością i zasobów wymaganych do pełnego renderowania dokumentu.  Projekt <xref:System.Windows.Xps.Packaging.XpsDocument> zapewnia pojedyncze rozwiązanie dokumentu o wysokiej wierności, które obsługuje wiele zastosowań:  
  
- Odczytywanie, zapisywanie i przechowywanie zawartości i zasobów dokumentów stałych jako pojedynczego, przenośnego i łatwego do dystrybucji pliku.  
  
- Wyświetlanie dokumentów za pomocą aplikacji XPS Viewer.  
  
- Wyprowadzanie dokumentów w natywnym formacie wyjściowym buforu wydruku systemu Windows Vista.  
  
- Routing dokumentów bezpośrednio do drukarki zgodnej z systemem XPS.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Tekst](optimizing-performance-text.md)
- [Przegląd dokumentu przepływu](flow-document-overview.md)
- [Przegląd drukowania](printing-overview.md)
- [Serializacja dokumentu i przechowywanie](document-serialization-and-storage.md)
