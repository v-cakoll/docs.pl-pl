---
title: Dokumenty w WPF
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
ms.openlocfilehash: 9fac4e1a98f67c6d5d946ade1b7f2115ce0d5f8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964874"
---
# <a name="documents-in-wpf"></a>Dokumenty w WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]oferuje szeroką gamę funkcji dokumentu, które umożliwiają tworzenie zawartości o wysokiej wierności, która została zaprojektowana tak, aby była łatwiej dostępna i odczytywana niż w poprzednich generacjach systemu Windows. Oprócz ulepszonych możliwości i jakości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia także zintegrowane usługi do wyświetlania, pakowania i zabezpieczania dokumentów. Ten temat zawiera wprowadzenie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typów dokumentów i pakowania dokumentów.  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Typy dokumentów  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dzieli dokumenty na dwie szerokie kategorie w oparciu o ich zamierzone użycie; te kategorie dokumentów są określane jako "dokumenty stałe" i "dokumenty przepływu".  
  
 Stałe dokumenty są przeznaczone dla aplikacji, które wymagają precyzyjnej [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] prezentacji, niezależnie od używanego sprzętu wyświetlania lub drukarek. Typowe zastosowania w przypadku dokumentów stałych obejmują publikowanie komputerów, przetwarzanie słów i układ formularzy, gdzie zgodność z pierwotnym projektem strony ma kluczowe znaczenie. W ramach układu ustalony dokument zachowuje precyzyjne rozmieszczenie elementów zawartości niezależnie od używanego urządzenia wyświetlającego lub drukującego. Na przykład strona o stałym dokumencie wyświetlana na 96 dpi zostanie wyświetlona dokładnie tak samo, jak w przypadku danych wyjściowych na drukarce laserowej 600 dpi, tak jakby była wyjściowa do 4800 dpi phototypesetter. Układ strony pozostaje taki sam we wszystkich przypadkach, a jakość dokumentu maksymalizuje możliwości poszczególnych urządzeń.  
  
 Dzięki porównaniu dokumenty przepływu mają na celu optymalizację wyświetlania i czytelność i są najlepiej wykorzystywane, gdy łatwość odczytywania jest głównym scenariuszem zużycia dokumentu. Zamiast ustawić na jeden wstępnie zdefiniowany układ, dokumenty przepływu dynamicznie dostosowują i przepływają zawartość na podstawie zmiennych czasu wykonywania, takich jak rozmiar okna, rozdzielczość urządzenia i opcjonalne preferencje użytkownika. Strona sieci Web to prosty przykład dokumentu przepływu, w którym zawartość strony jest formatowana dynamicznie w celu dopasowania do bieżącego okna. Dokumenty przepływu optymalizują środowisko wyświetlania i odczytywania dla użytkownika w oparciu o środowisko uruchomieniowe. Na przykład ten sam dokument przepływu będzie dynamicznie przełączany w celu uzyskania optymalnego czytelności na wyświetlaczu o wysokiej rozdzielczości 19 cali lub małym ekranie urządzenia PDA 2x3. Ponadto dokumenty przepływu mają wiele wbudowanych funkcji, takich jak wyszukiwanie, wyświetlanie trybów, które optymalizują czytelność i możliwość zmiany rozmiaru i wyglądu czcionek.  Zobacz [Omówienie dokumentu przepływu](flow-document-overview.md) dla ilustracji, przykładów i szczegółowych informacji o dokumentach przepływu.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Kontrolki dokumentu i układ tekstu  
 .NET Framework zawiera zestaw wstępnie skompilowanych kontrolek, które upraszczają korzystanie z stałych dokumentów, dokumentów przepływu i tekstu ogólnego w aplikacji.  Wyświetlanie zawartości dokumentu o stałym rozmiarze jest obsługiwane przy <xref:System.Windows.Controls.DocumentViewer> użyciu formantu.  Wyświetlanie zawartości dokumentu przepływu jest obsługiwane przez trzy różne kontrolki: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer> które są mapowane na różne scenariusze użytkownika (zobacz sekcje poniżej).  Inne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolki zapewniają uproszczony układ do obsługi ogólnego użycia tekstu (zobacz [tekst w interfejsie użytkownika](#text_in_the_user_interface), poniżej).  
  
### <a name="fixed-document-control---documentviewer"></a>Stała kontrola dokumentu — DocumentViewer  
 Kontrolka jest zaprojektowana <xref:System.Windows.Documents.FixedDocument> do wyświetlania zawartości. <xref:System.Windows.Controls.DocumentViewer> <xref:System.Windows.Controls.DocumentViewer> Formant udostępnia intuicyjny interfejs użytkownika, który zapewnia wbudowaną obsługę typowych operacji, takich jak drukowanie danych wyjściowych, kopiowanie do schowka, powiększanie i wyszukiwanie tekstu. Kontrolka zapewnia dostęp do stron zawartości za pomocą znanego mechanizmu przewijania. Podobnie jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w przypadku <xref:System.Windows.Controls.DocumentViewer> wszystkich kontrolek, obsługuje pełny lub częściowy przedziały, co umożliwia wizualne zintegrowanie formantu z praktycznie każdą aplikacją lub środowiskiem.  
  
 <xref:System.Windows.Controls.DocumentViewer>służy do wyświetlania zawartości w sposób tylko do odczytu; Edytowanie lub modyfikowanie zawartości jest niedostępne i nie jest obsługiwane.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Kontrolki dokumentu przepływu  

> [!NOTE]
> Aby uzyskać bardziej szczegółowe informacje na temat funkcji dokumentu przepływu i sposobu ich tworzenia, zobacz temat [przepływ — Omówienie](flow-document-overview.md).  
  
 Wyświetlanie zawartości dokumentu przepływu jest obsługiwane przez trzy kontrolki: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>obejmuje funkcje, które umożliwiają użytkownikowi dynamiczne wybieranie różnych trybów wyświetlania, w tym tryb wyświetlania pojedynczej strony (strona w czasie), tryb wyświetlania dwustronicowego (do odczytu książki) i przewijanie ciągłego (w dół).  Aby uzyskać więcej informacji na temat tych trybów wyświetlania <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>, zobacz.  Jeśli nie potrzebujesz możliwości dynamicznego przełączania między różnymi trybami wyświetlania, <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> następnie udostępniaj jaśniejsze osoby przeglądające zawartość przepływu, które są rozwiązane w określonym trybie wyświetlania.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer i FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>Wyświetla zawartość w trybie wyświetlania strony w czasie, podczas gdy <xref:System.Windows.Controls.FlowDocumentScrollViewer> pokazuje zawartość w trybie przewijania ciągłego.  Oba <xref:System.Windows.Controls.FlowDocumentPageViewer> i<xref:System.Windows.Controls.FlowDocumentScrollViewer> są stałe do określonego trybu wyświetlania. Porównaj z <xref:System.Windows.Controls.FlowDocumentReader>, która obejmuje funkcje, które umożliwiają użytkownikowi dynamiczne wybieranie różnych trybów wyświetlania (zgodnie z <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> wyliczeniem), przy kosztach większej ilości zasobów niż <xref:System.Windows.Controls.FlowDocumentPageViewer> lub <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Domyślnie pionowy pasek przewijania jest zawsze pokazywany, a poziomy pasek przewijania jest widoczny w razie konieczności. Wartość domyślna [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla <xref:System.Windows.Controls.FlowDocumentScrollViewer> nie obejmuje <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> paska narzędzi; jednak właściwość może być używana do włączania wbudowanego paska narzędzi.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Tekst w interfejsie użytkownika  
 Oprócz dodawania tekstu do dokumentów, można oczywiście używać tekstu w interfejsie użytkownika aplikacji, na przykład formularzy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele kontrolek do rysowania tekstu na ekranie. Każdy formant jest przeznaczony dla innego scenariusza i ma własną listę funkcji i ograniczeń. Ogólnie rzecz biorąc, <xref:System.Windows.Controls.TextBlock> element powinien być używany, gdy wymagana jest obsługa tekstu ograniczonego, na przykład krótkie zdanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]w. <xref:System.Windows.Controls.Label>może być używany, gdy wymagana jest minimalna obsługa tekstu. Aby uzyskać więcej informacji, zobacz [TextBlock — Omówienie](../controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Pakowanie dokumentów  
 <xref:System.IO.Packaging> Interfejsy API zapewniają efektywną metodę organizowania danych aplikacji, zawartości dokumentów i pokrewnych zasobów w jednym kontenerze, który jest prosty dla dostępu, przenośnego i łatwego do dystrybucji. Plik zip jest przykładem typu, który <xref:System.IO.Packaging.Package> umożliwia przechowywanie wielu obiektów jako pojedynczej jednostki. Interfejsy API tworzenia pakietów udostępniają <xref:System.IO.Packaging.ZipPackage> domyślną implementację, która została zaprojektowana przy użyciu standardu Open pakowanie Konwencji z architekturą plików XML i zip. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Interfejsy API pakietów ułatwiają tworzenie pakietów i przechowywanie obiektów oraz uzyskiwanie do nich dostępu. Obiekt przechowywany w <xref:System.IO.Packaging.Package> elemencie jest określany <xref:System.IO.Packaging.PackagePart> jako ("część"). Pakiety mogą również zawierać podpisane certyfikaty cyfrowe, których można użyć do identyfikacji nadawcy części i sprawdzenia, czy zawartość pakietu nie została zmodyfikowana.  Pakiety zawierają <xref:System.IO.Packaging.PackageRelationship> również funkcję, która umożliwia dodawanie dodatkowych informacji do pakietu lub skojarzonych z określonymi częściami bez modyfikowania zawartości istniejących części.  Obsługiwane [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)]są również usługi pakietu.  
  
 Architektura [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pakietu służy jako podstawa dla wielu kluczowych technologii:  
  
- [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]dokumenty zgodne [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]z.  
  
- Microsoft Office "12" otwieranie dokumentów w formacie XML (. docx).  
  
- Niestandardowe formaty magazynu dla własnego projektu aplikacji.  
  
 W oparciu o interfejsy API <xref:System.Windows.Xps.Packaging.XpsDocument> tworzenia pakietów jest przeznaczony specjalnie do przechowywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości stałych dokumentów. Jest to dokument, który można otworzyć w przeglądarce, wyświetlany <xref:System.Windows.Controls.DocumentViewer> w kontrolce, kierowany do buforu wydruku [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]lub bezpośrednio na drukarkę zgodną z obsługą. <xref:System.Windows.Xps.Packaging.XpsDocument>  
  
 W poniższych sekcjach znajdują się dodatkowe <xref:System.IO.Packaging.Package> informacje <xref:System.Windows.Xps.Packaging.XpsDocument> na temat interfejsów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API i.  
  
<a name="packages"></a>   
### <a name="package-components"></a>Składniki pakietu  
 Interfejsy API tworzenia pakietów umożliwiają organizowanie danych i dokumentów aplikacji w jedną jednostkę przenośną. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Plik ZIP jest jednym z najpopularniejszych typów pakietów i jest domyślnym typem pakietu dostarczanym z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package>sama jest klasą abstrakcyjną, <xref:System.IO.Packaging.ZipPackage> z której jest implementowana przy użyciu otwartej standardowej architektury plików XML i zip.  <xref:System.IO.Packaging.Package.Open%2A> Metoda używa<xref:System.IO.Packaging.ZipPackage> do tworzenia i używania plików zip domyślnie. Pakiet może zawierać trzy podstawowe typy elementów:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Zawartość aplikacji, dane, dokumenty i pliki zasobów.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certyfikat X. 509] do identyfikacji, uwierzytelniania i weryfikacji.|  
|<xref:System.IO.Packaging.PackageRelationship>|Dodano informacje powiązane z pakietem lub określoną częścią.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>Element PackagePart  
 ("Część") jest klasą abstrakcyjną, która odwołuje się do obiektu przechowywanego <xref:System.IO.Packaging.Package>w. <xref:System.IO.Packaging.PackagePart> W pliku ZIP części pakietu odpowiadają osobom plików przechowywanych w pliku ZIP.  <xref:System.IO.Packaging.ZipPackagePart>zapewnia implementację domyślną dla obiektów, które można serializować <xref:System.IO.Packaging.ZipPackage>, przechowywanych w.  Podobnie jak w przypadku systemu plików, części zawarte w pakiecie są przechowywane w katalogu hierarchicznym lub w organizacji "styl folderu".  Za pomocą interfejsów API tworzenia <xref:System.IO.Packaging.PackagePart> pakietówaplikacjemogązapisywać,przechowywaćiodczytywaćwieleobiektówprzyużyciujednegokonteneraplikuzip.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 W celu zapewnienia bezpieczeństwa <xref:System.IO.Packaging.PackageDigitalSignature> ("podpis cyfrowy") można skojarzyć z częściami w ramach pakietu. A <xref:System.IO.Packaging.PackageDigitalSignature> [509] obejmuje dwie funkcje:  
  
1. Identyfikuje i uwierzytelnia nadawcę części.  
  
2. Sprawdza, czy część nie została zmodyfikowana.  
  
 Podpis cyfrowy nie wyklucza modyfikacji części, ale sprawdzenie poprawności podpisu cyfrowego zakończy się niepowodzeniem, jeśli część zostanie zmieniona w dowolny sposób. Aplikacja może następnie podjąć odpowiednie działania — na przykład zablokować otwarcie części lub Powiadom użytkownika, że część została zmodyfikowana i nie jest bezpieczna.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationship  
 <xref:System.IO.Packaging.PackageRelationship> ("Relacja") zapewnia mechanizm kojarzenia dodatkowych informacji z pakietem lub częścią pakietu. Relacja to funkcja poziomu pakietu, która umożliwia kojarzenie dodatkowych informacji ze składnikiem bez modyfikowania rzeczywistej zawartości części. Wstawianie nowych danych bezpośrednio do zawartości częściowej jest zwykle niepraktyczne w wielu przypadkach:  
  
- Rzeczywisty typ części i jej schemat zawartości nie są znane.  
  
- Nawet jeśli znana, schemat zawartości może nie zapewniać środków do dodawania nowych informacji.  
  
- Część może być podpisana cyfrowo lub zaszyfrowana, co umożliwia modyfikację.  
  
 Relacje między pakietami zapewniają wykrywalny sposób dodawania i kojarzenia dodatkowych informacji z indywidualnymi częściami lub z całym pakietem. Relacje między pakietami są używane dla dwóch funkcji podstawowych:  
  
1. Definiowanie relacji zależności od jednej części do innej części.  
  
2. Definiowanie relacji informacji, które dodają notatki lub inne dane związane z częścią.  
  
 A <xref:System.IO.Packaging.PackageRelationship> umożliwia szybkie i wykrywalne metody definiowania zależności oraz dodawanie innych informacji skojarzonych z częścią pakietu lub pakietu jako całości.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Relacje zależności  
 Relacje zależności są używane do opisywania zależności, które jedna część wykonuje w innych częściach. Na przykład pakiet może zawierać część HTML, która zawiera co najmniej jeden \<IMG > Tagi obrazu. Tagi obrazu odnoszą się do obrazów, które znajdują się w innych częściach wewnętrznych dla pakietu lub poza pakietem (na przykład dostępne przez Internet). <xref:System.IO.Packaging.PackageRelationship> Utworzenie skojarzonego z plikiem HTML umożliwia szybkie i łatwe odnajdywanie i uzyskiwanie dostępu do zasobów zależnych. Aplikacja przeglądarka lub przeglądarka może bezpośrednio uzyskać dostęp do relacji między częściami i od razu rozpocząć składanie zasobów zależnych bez znajomości schematu lub analizy dokumentu.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Relacje informacji  
 Podobnie jak w przypadku notatki lub adnotacji <xref:System.IO.Packaging.PackageRelationship> , można także użyć do przechowywania innych typów informacji, które mają być skojarzone z częścią bez konieczności faktycznego modyfikowania samej zawartości części.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>Dokumenty XPS  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]dokument to pakiet zawierający jeden lub więcej dokumentów stałych wraz ze wszystkimi zasobami i informacjami wymaganymi do renderowania.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]jest również natywny [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] format pliku buforu wydruku.  <xref:System.Windows.Xps.Packaging.XpsDocument> Jest przechowywany w standardowym zestawie danych zip i może zawierać kombinację składników XML i binarnych, takich jak pliki obrazów i czcionek. [Packagerelationships](#PackageRelationships) służy do definiowania zależności między zawartością a zasobami wymaganymi do pełnego renderowania dokumentu.  <xref:System.Windows.Xps.Packaging.XpsDocument> Projekt zapewnia jedno rozwiązanie dokumentu o wysokiej wierności, które obsługuje wiele użycia:  
  
- Odczytywanie, zapisywanie i przechowywanie dokumentów i zasobów o stałym dokumencie jako jednego, przenośnego i łatwego w obsłudze pliku.  
  
- Wyświetlanie dokumentów przy użyciu [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] aplikacji przeglądarki.  
  
- Wyprowadzanie dokumentów w natywnym formacie [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]danych wyjściowych buforu wydruku.  
  
- Kierowanie dokumentów bezpośrednio do [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]drukarki zgodnej ze standardami.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Text](optimizing-performance-text.md)
- [Przegląd dokumentu przepływu](flow-document-overview.md)
- [Przegląd drukowania](printing-overview.md)
- [Serializacja dokumentu i przechowywanie](document-serialization-and-storage.md)
