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
ms.openlocfilehash: fbd4df8820073a3cdf2a8d5aad9c56bd7ca751df
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460530"
---
# <a name="documents-in-wpf"></a>Dokumenty w WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferuje szeroką gamę funkcji dokumentu, które umożliwiają tworzenie zawartości o wysokiej wierności, która została zaprojektowana tak, aby była łatwiej dostępna i odczytywana niż w poprzednich generacjach systemu Windows. Oprócz ulepszonych możliwości i jakości, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia również zintegrowane usługi do wyświetlania, pakowania i zabezpieczania dokumentów. Ten temat zawiera wprowadzenie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typów dokumentów i pakowania dokumentów.  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Typy dokumentów  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dzieli dokumenty na dwie szerokie kategorie w oparciu o ich zamierzone użycie; te kategorie dokumentów są określane jako "dokumenty stałe" i "dokumenty przepływu".  
  
 Stałe dokumenty są przeznaczone dla aplikacji, które wymagają dokładnej prezentacji "to, co widzisz" (WYSIWYG), niezależnie od używanego sprzętu wyświetlania lub drukarek. Typowe zastosowania w przypadku dokumentów stałych obejmują publikowanie komputerów, przetwarzanie słów i układ formularzy, gdzie zgodność z pierwotnym projektem strony ma kluczowe znaczenie. W ramach układu ustalony dokument zachowuje precyzyjne rozmieszczenie elementów zawartości niezależnie od używanego urządzenia wyświetlającego lub drukującego. Na przykład strona o stałym dokumencie wyświetlana na 96 dpi zostanie wyświetlona dokładnie tak samo, jak w przypadku danych wyjściowych na drukarce laserowej 600 dpi, tak jakby była wyjściowa do 4800 dpi phototypesetter. Układ strony pozostaje taki sam we wszystkich przypadkach, a jakość dokumentu maksymalizuje możliwości poszczególnych urządzeń.  
  
 Dzięki porównaniu dokumenty przepływu mają na celu optymalizację wyświetlania i czytelność i są najlepiej wykorzystywane, gdy łatwość odczytywania jest głównym scenariuszem zużycia dokumentu. Zamiast ustawić na jeden wstępnie zdefiniowany układ, dokumenty przepływu dynamicznie dostosowują i przepływają zawartość na podstawie zmiennych czasu wykonywania, takich jak rozmiar okna, rozdzielczość urządzenia i opcjonalne preferencje użytkownika. Strona sieci Web to prosty przykład dokumentu przepływu, w którym zawartość strony jest formatowana dynamicznie w celu dopasowania do bieżącego okna. Dokumenty przepływu optymalizują środowisko wyświetlania i odczytywania dla użytkownika w oparciu o środowisko uruchomieniowe. Na przykład ten sam dokument przepływu będzie dynamicznie przełączany w celu uzyskania optymalnego czytelności na wyświetlaczu o wysokiej rozdzielczości 19 cali lub małym ekranie urządzenia PDA 2x3. Ponadto dokumenty przepływu mają wiele wbudowanych funkcji, takich jak wyszukiwanie, wyświetlanie trybów, które optymalizują czytelność i możliwość zmiany rozmiaru i wyglądu czcionek.  Zobacz [Omówienie dokumentu przepływu](flow-document-overview.md) dla ilustracji, przykładów i szczegółowych informacji o dokumentach przepływu.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Kontrolki dokumentu i układ tekstu  
 .NET Framework zawiera zestaw wstępnie skompilowanych kontrolek, które upraszczają korzystanie z stałych dokumentów, dokumentów przepływu i tekstu ogólnego w aplikacji.  Wyświetlanie zawartości dokumentu o stałym rozmiarze jest obsługiwane przy użyciu kontrolki <xref:System.Windows.Controls.DocumentViewer>.  Wyświetlanie zawartości dokumentu przepływu jest obsługiwane przez trzy różne kontrolki: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>i <xref:System.Windows.Controls.FlowDocumentScrollViewer> mapowane na różne scenariusze użytkownika (zobacz sekcje poniżej).  Inne kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewniają uproszczony układ do obsługi ogólnego użycia tekstu (zobacz [tekst w interfejsie użytkownika](#text_in_the_user_interface), poniżej).  
  
### <a name="fixed-document-control---documentviewer"></a>Stała kontrola dokumentu — DocumentViewer  
 Formant <xref:System.Windows.Controls.DocumentViewer> służy do wyświetlania zawartości <xref:System.Windows.Documents.FixedDocument>. Formant <xref:System.Windows.Controls.DocumentViewer> zapewnia intuicyjny interfejs użytkownika, który zapewnia wbudowaną obsługę typowych operacji, takich jak drukowanie danych wyjściowych, kopiowanie do schowka, powiększanie i wyszukiwanie tekstu. Kontrolka zapewnia dostęp do stron zawartości za pomocą znanego mechanizmu przewijania. Podobnie jak w przypadku wszystkich kontrolek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Controls.DocumentViewer> obsługuje pełny lub częściowy przedziały, co umożliwia kontrolowanie wizualizacji w praktycznie dowolnej aplikacji lub środowisku.  
  
 <xref:System.Windows.Controls.DocumentViewer> jest zaprojektowana do wyświetlania zawartości w sposób tylko do odczytu; Edytowanie lub modyfikowanie zawartości jest niedostępne i nie jest obsługiwane.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Kontrolki dokumentu przepływu  

> [!NOTE]
> Aby uzyskać bardziej szczegółowe informacje na temat funkcji dokumentu przepływu i sposobu ich tworzenia, zobacz temat [przepływ — Omówienie](flow-document-overview.md).  
  
 Wyświetlanie zawartości dokumentu przepływu jest obsługiwane przez trzy kontrolki: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>i <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> obejmuje funkcje, które umożliwiają użytkownikowi dynamiczne wybieranie różnych trybów wyświetlania, w tym tryb wyświetlania pojedynczej strony (strona w czasie), tryb wyświetlania dwustronicowego (do odczytu książki) i przewijanie ciągłe (w dół) Tryb wyświetlania.  Aby uzyskać więcej informacji na temat tych trybów wyświetlania, zobacz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Jeśli nie potrzebujesz możliwości dynamicznego przełączania między różnymi trybami wyświetlania, <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> zapewniają jaśniejszą, wyglądającą zawartość przepływów, które są rozwiązane w określonym trybie wyświetlania.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer i FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> wyświetla zawartość w trybie wyświetlania strony w czasie, podczas gdy <xref:System.Windows.Controls.FlowDocumentScrollViewer> wyświetla zawartość w trybie przewijania ciągłego.  Oba <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> są naprawione do określonego trybu wyświetlania. Należy porównać do <xref:System.Windows.Controls.FlowDocumentReader>, która obejmuje funkcje, które umożliwiają użytkownikowi dynamiczne wybieranie różnych trybów wyświetlania (zgodnie z wyliczeniem <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>), przy kosztach większej ilości zasobów niż <xref:System.Windows.Controls.FlowDocumentPageViewer> lub <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Domyślnie pionowy pasek przewijania jest zawsze pokazywany, a poziomy pasek przewijania jest widoczny w razie konieczności. Domyślny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla <xref:System.Windows.Controls.FlowDocumentScrollViewer> nie zawiera paska narzędzi; jednak Właściwość <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> może być używana do włączania wbudowanego paska narzędzi.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Tekst w interfejsie użytkownika  
 Oprócz dodawania tekstu do dokumentów, można oczywiście używać tekstu w interfejsie użytkownika aplikacji, na przykład formularzy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele kontrolek do rysowania tekstu na ekranie. Każdy formant jest przeznaczony dla innego scenariusza i ma własną listę funkcji i ograniczeń. Ogólnie rzecz biorąc, element <xref:System.Windows.Controls.TextBlock> powinien być używany, gdy wymagana jest obsługa tekstu ograniczonego, na przykład krótkie zdanie w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> można użyć, gdy wymagana jest minimalna obsługa tekstu. Aby uzyskać więcej informacji, zobacz [TextBlock — Omówienie](../controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Pakowanie dokumentów  
 <xref:System.IO.Packaging> interfejsy API zapewniają efektywną metodę organizowania danych aplikacji, zawartości dokumentów i powiązanych zasobów w pojedynczym kontenerze, który jest prosty dla dostępu, przenośnego i łatwego do dystrybucji. Plik ZIP jest przykładem typu <xref:System.IO.Packaging.Package>, który umożliwia przechowywanie wielu obiektów jako pojedynczej jednostki. Interfejsy API tworzenia pakietów zapewniają domyślną implementację <xref:System.IO.Packaging.ZipPackage>, która została zaprojektowana przy użyciu standardu Open pakowanie Konwencji z architekturą plików XML i ZIP. Interfejsy API pakietów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwiają łatwe tworzenie pakietów oraz przechowywanie i dostęp do obiektów w nich. Obiekt przechowywany w <xref:System.IO.Packaging.Package> jest określany jako <xref:System.IO.Packaging.PackagePart> ("część"). Pakiety mogą również zawierać podpisane certyfikaty cyfrowe, których można użyć do identyfikacji nadawcy części i sprawdzenia, czy zawartość pakietu nie została zmodyfikowana.  Pakiety zawierają również funkcję <xref:System.IO.Packaging.PackageRelationship>, która umożliwia dodawanie dodatkowych informacji do pakietu lub skojarzonych z określonymi częściami bez konieczności modyfikowania zawartości istniejących części.  Usługi pakietów obsługują również Rights Management systemu Microsoft Windows (RM).  
  
 Architektura pakietu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] służy jako podstawa dla wielu kluczowych technologii:  
  
- Dokumenty XPS zgodne ze specyfikacją dokumentu XML (XPS).  
  
- Microsoft Office "12" otwieranie dokumentów w formacie XML (. docx).  
  
- Niestandardowe formaty magazynu dla własnego projektu aplikacji.  
  
 Na podstawie interfejsów API pakietów <xref:System.Windows.Xps.Packaging.XpsDocument> jest zaprojektowana specjalnie do przechowywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stałych dokumentów zawartości. <xref:System.Windows.Xps.Packaging.XpsDocument> to samodzielny dokument, który można otworzyć w przeglądarce, wyświetlany w kontrolce <xref:System.Windows.Controls.DocumentViewer>, kierowany do buforu wydruku lub bezpośrednio na drukarce zgodnej z XPS.  
  
 W poniższych sekcjach znajdują się dodatkowe informacje na temat <xref:System.IO.Packaging.Package> i <xref:System.Windows.Xps.Packaging.XpsDocument> interfejsów API, które są dostępne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Składniki pakietu  
 Interfejsy API tworzenia pakietów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwiają zorganizowanie danych i dokumentów aplikacji w jednej jednostce przenośnej. Plik ZIP jest jednym z najpopularniejszych typów pakietów i jest domyślnym typem pakietu dostarczanym z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> jest klasą abstrakcyjną, z której <xref:System.IO.Packaging.ZipPackage> jest implementowana przy użyciu otwartej standardowej architektury plików XML i ZIP.  Metoda <xref:System.IO.Packaging.Package.Open%2A> używa <xref:System.IO.Packaging.ZipPackage> do tworzenia i używania plików ZIP domyślnie. Pakiet może zawierać trzy podstawowe typy elementów:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Zawartość aplikacji, dane, dokumenty i pliki zasobów.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certyfikat X. 509] do identyfikacji, uwierzytelniania i weryfikacji.|  
|<xref:System.IO.Packaging.PackageRelationship>|Dodano informacje powiązane z pakietem lub określoną częścią.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>Element PackagePart  
 <xref:System.IO.Packaging.PackagePart> ("część") jest klasą abstrakcyjną, która odwołuje się do obiektu przechowywanego w <xref:System.IO.Packaging.Package>. W pliku ZIP części pakietu odpowiadają osobom plików przechowywanych w pliku ZIP.  <xref:System.IO.Packaging.ZipPackagePart> zapewnia implementację domyślną dla serializowanych obiektów przechowywanych w <xref:System.IO.Packaging.ZipPackage>.  Podobnie jak w przypadku systemu plików, części zawarte w pakiecie są przechowywane w katalogu hierarchicznym lub w organizacji "styl folderu".  Za pomocą interfejsów API tworzenia pakietów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje mogą zapisywać, przechowywać i odczytywać wiele obiektów <xref:System.IO.Packaging.PackagePart> przy użyciu jednego kontenera pliku ZIP.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 W celu zapewnienia bezpieczeństwa <xref:System.IO.Packaging.PackageDigitalSignature> ("podpis cyfrowy") można skojarzyć z częściami w pakiecie. <xref:System.IO.Packaging.PackageDigitalSignature> obejmuje [509], który oferuje dwie funkcje:  
  
1. Identyfikuje i uwierzytelnia nadawcę części.  
  
2. Sprawdza, czy część nie została zmodyfikowana.  
  
 Podpis cyfrowy nie wyklucza modyfikacji części, ale sprawdzenie poprawności podpisu cyfrowego zakończy się niepowodzeniem, jeśli część zostanie zmieniona w dowolny sposób. Aplikacja może następnie podjąć odpowiednie działania — na przykład zablokować otwarcie części lub Powiadom użytkownika, że część została zmodyfikowana i nie jest bezpieczna.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationship  
 <xref:System.IO.Packaging.PackageRelationship> ("relacja") zapewnia mechanizm kojarzenia dodatkowych informacji z pakietem lub częścią pakietu. Relacja to funkcja poziomu pakietu, która umożliwia kojarzenie dodatkowych informacji ze składnikiem bez modyfikowania rzeczywistej zawartości części. Wstawianie nowych danych bezpośrednio do zawartości częściowej jest zwykle niepraktyczne w wielu przypadkach:  
  
- Rzeczywisty typ części i jej schemat zawartości nie są znane.  
  
- Nawet jeśli znana, schemat zawartości może nie zapewniać środków do dodawania nowych informacji.  
  
- Część może być podpisana cyfrowo lub zaszyfrowana, co umożliwia modyfikację.  
  
 Relacje między pakietami zapewniają wykrywalny sposób dodawania i kojarzenia dodatkowych informacji z indywidualnymi częściami lub z całym pakietem. Relacje między pakietami są używane dla dwóch funkcji podstawowych:  
  
1. Definiowanie relacji zależności od jednej części do innej części.  
  
2. Definiowanie relacji informacji, które dodają notatki lub inne dane związane z częścią.  
  
 <xref:System.IO.Packaging.PackageRelationship> zapewnia szybkie, wykrywalne metody definiowania zależności i dodawanie innych informacji skojarzonych z częścią pakietu lub pakietu jako całości.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Relacje zależności  
 Relacje zależności są używane do opisywania zależności, które jedna część wykonuje w innych częściach. Na przykład pakiet może zawierać część HTML, która zawiera co najmniej jeden \<IMG > Tagi obrazu. Tagi obrazu odnoszą się do obrazów, które znajdują się w innych częściach wewnętrznych dla pakietu lub poza pakietem (na przykład dostępne przez Internet). Tworzenie <xref:System.IO.Packaging.PackageRelationship> skojarzonych z plikiem HTML umożliwia szybkie i łatwe odnajdywanie i uzyskiwanie dostępu do zasobów zależnych. Aplikacja przeglądarka lub przeglądarka może bezpośrednio uzyskać dostęp do relacji między częściami i od razu rozpocząć składanie zasobów zależnych bez znajomości schematu lub analizy dokumentu.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Relacje informacji  
 Podobnie jak w przypadku notatki lub adnotacji, <xref:System.IO.Packaging.PackageRelationship> może również służyć do przechowywania innych typów informacji, które mają być skojarzone z częścią bez konieczności faktycznego modyfikowania samej zawartości części.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>Dokumenty XPS  
 Dokument XML Paper Specification (XPS) to pakiet zawierający jeden lub więcej dokumentów stałych wraz ze wszystkimi zasobami i informacjami wymaganymi do renderowania.  Format XPS to również natywny plik buforu wydruku [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  <xref:System.Windows.Xps.Packaging.XpsDocument> jest przechowywany w standardowym zestawie danych ZIP i może zawierać kombinację składników XML i binarnych, takich jak pliki obrazów i czcionek. [Packagerelationships](#PackageRelationships) służy do definiowania zależności między zawartością a zasobami wymaganymi do pełnego renderowania dokumentu.  Projekt <xref:System.Windows.Xps.Packaging.XpsDocument> zapewnia jedno rozwiązanie dokumentu o wysokiej wierności, które obsługuje wiele użycia:  
  
- Odczytywanie, zapisywanie i przechowywanie dokumentów i zasobów o stałym dokumencie jako jednego, przenośnego i łatwego w obsłudze pliku.  
  
- Wyświetlanie dokumentów z aplikacją przeglądarka plików XPS.  
  
- Wyprowadzanie dokumentów w natywnym formacie wyjściowym buforu wydruku [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
- Kierowanie dokumentów bezpośrednio do drukarki zgodnej z systemem plików XPS.  
  
## <a name="see-also"></a>Zobacz także

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
