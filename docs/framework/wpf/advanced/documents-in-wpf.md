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
ms.openlocfilehash: b4057f54934fb5c7c9bb3d4fb97fe8e197e324ad
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313960"
---
# <a name="documents-in-wpf"></a>Dokumenty w WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferuje szeroką gamę funkcji dokumentu, które umożliwiają tworzenie zawartości o wysokiej wierności, która została zaprojektowana jako łatwiej uzyskuje się dostęp i odczytu niż w poprzednich generacji [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Oprócz rozszerzone możliwości i jakość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również udostępnia zintegrowane usługi do wyświetlania dokumentu, pakowania i zabezpieczeń. Ten temat zawiera wprowadzenie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typów dokumentów i pakowania w usłudze dokumentu.  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Typy dokumentów  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dokumenty są podzielone na dwie szerokie kategorie, w oparciu o ich przeznaczenie; te kategorie dokumentu są określane jako "Naprawiono dokumenty" i "dokumenty przepływu."  
  
 Naprawiono dokumenty są przeznaczone dla aplikacji, które wymagają precyzyjnego [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] prezentacji, niezależnie od ekranu lub drukarki sprzętu używanego. Typowe zastosowania Naprawiono dokumenty obejmują składu komputerowego, edytory tekstu i układu formularza, w którym gotowość do oryginalnego projektu strona ma kluczowe znaczenie. Jako część jej układ niezależnie od ekranu lub drukarki w użyciu dokładne pozycyjne rozmieszczenia elementów zawartości przechowuje stały dokumentu. Na przykład stały dokumentu wyświetlane na ekranie rozdzielczości 96 dpi zostanie wyświetlona strona dokładnie takie same, gdy jest wyprowadzana do 600 dpi drukarka laserowa jako, gdy jest ona dane wyjściowe do phototypesetter 4800 dpi. Układ strony pozostaje taki sam, we wszystkich przypadkach, gdy jakości dokumentu maksymalizuje do możliwości poszczególnych urządzeń.  
  
 Natomiast dokumenty przepływu zaprojektowano w celu zoptymalizowania wyświetlania i czytelności i najlepiej są wykorzystywane podczas czytelnej jest scenariusz użycia dokumentu głównego. Zamiast jest ustawiona na jeden układ wstępnie zdefiniowanych, dokumenty przepływu dynamicznie Dostosuj i przepełnieniem ich zawartości na podstawie zmiennych czasu wykonywania, takich jak rozmiar okna, rozdzielczość urządzenia i preferencje użytkownika opcjonalne. Strona sieci Web jest prosty przykład dokument przepływu, w którym zawartość strony jest dynamicznie sformatowane, aby dopasować bieżące okno. Dokumenty przepływu zoptymalizować wyświetlania i odczytu środowiska dla użytkownika, w oparciu o środowisko uruchomieniowe. Na przykład ten sam dokument przepływu będzie dynamicznie formatowania dla optymalnej czytelności 19-calowy rozdzielczości lub ekranu urządzenia PDA małych cala 2 x 3. Ponadto dokumenty przepływu ma szereg wbudowanych funkcji, w tym wyszukiwanie, wyświetlanie trybów, które optymalizują czytelności i możliwości zmiany rozmiaru i wygląd czcionek.  Zobacz [Przegląd dokumentu przepływu](flow-document-overview.md) ilustracje, przykłady i szczegółowe informacje na temat dokumenty przepływu.  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Formantów dokumentów i układ tekstu  
 .NET Framework zawiera zestaw wbudowanych formantów, które upraszczają przy użyciu stałej dokumentów, dokumenty przepływu i ogólne tekstu w aplikacji.  Wyświetlanie zawartości dokumentu stałej jest obsługiwane przy użyciu <xref:System.Windows.Controls.DocumentViewer> kontroli.  Wyświetlanie zawartości dokumentów przepływu jest obsługiwana przez trzy różne formanty: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer> które mapowania na różne scenariusze użytkownika (patrz poniżej).  Inne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy sterujące udostępniają uproszczone układu do obsługi ogólnego tekstu używa (zobacz [tekstu w interfejsie użytkownika](#text_in_the_user_interface)poniżej).  
  
### <a name="fixed-document-control---documentviewer"></a>Naprawiono DocumentViewer — Kontrola dokumentu —  
 <xref:System.Windows.Controls.DocumentViewer> Kontroli jest zaprojektowane w celu wyświetlenia <xref:System.Windows.Documents.FixedDocument> zawartości. <xref:System.Windows.Controls.DocumentViewer> Control oferuje intuicyjny interfejs użytkownika, który udostępnia wbudowaną obsługę dla typowych operacji, w tym wydruku danych wyjściowych, skopiuj do Schowka, powiększania i funkcji wyszukiwania tekstu. Kontrolka zapewnia dostęp do stron zawartości za pomocą dobrze znanych mechanizmu przewijania. Podobnie jak wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrolek <xref:System.Windows.Controls.DocumentViewer> obsługuje pełną lub częściową restyling, która umożliwia kontrolowanie, które wizualnie integracji w praktycznie dowolnej aplikacji lub środowiska.  
  
 <xref:System.Windows.Controls.DocumentViewer> Służy do wyświetlania zawartości w sposób tylko do odczytu. edycji lub zmianie zawartości jest niedostępna i nie jest obsługiwane.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Kontrole dokument przepływu  
 **Uwaga:** Aby uzyskać szczegółowe informacje na temat funkcji dokument przepływu i jak je utworzyć, zobacz [Przegląd dokumentu przepływu](flow-document-overview.md).  
  
 Wyświetlanie zawartości dokumentów przepływu jest obsługiwana przez trzy kontrolki: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> zawiera funkcje, które umożliwiają użytkownikowi dynamicznie do wyboru różnych trybów wyświetlania, w tym trybie jednej strony, przeglądania (strona na a-time), dwie strony na pojedynczych (w formacie czytania książki) wyświetlanie trybu i trybie przewijania ciągłego wyświetlania (nieograniczony).  Aby uzyskać więcej informacji dotyczących tych trybów wyświetlania, zobacz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Jeśli nie potrzebujesz możliwości dynamicznie przełączać się między trybami wyświetlania różnych <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> zapewniają podglądy zawartości, które zostały usunięte w trybie przeglądania określonego przepływu lekki.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer and FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> przedstawia zawartość strony w czasie trybu wyświetlania, podczas gdy <xref:System.Windows.Controls.FlowDocumentScrollViewer> pokazuje zawartości w trybie przewijania ciągłego.  Zarówno <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> są rozwiązywane do trybu wyświetlania określonego. Porównaj <xref:System.Windows.Controls.FlowDocumentReader>, która obejmuje funkcje, które umożliwiają użytkownikowi dynamicznie do wyboru różnych trybów wyświetlania (zgodnie z informacjami od <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> wyliczenie), kosztem trwa więcej zasobów niż <xref:System.Windows.Controls.FlowDocumentPageViewer> lub <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Domyślnie pionowy pasek przewijania jest zawsze wyświetlany, i poziomy pasek przewijania staje się widoczny, jeśli to konieczne. Wartość domyślna [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla <xref:System.Windows.Controls.FlowDocumentScrollViewer> nie obejmuje paska narzędzi & lt; jednak <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> właściwość może służyć do włączyć pasek narzędzi.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Tekst w interfejsie użytkownika  
 Oprócz dodawania tekstu do dokumentów, tekst oczywiście może służyć w interfejsie użytkownika aplikacji, takich jak formularze. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele kontrolek dla Rysowanie tekstu na ekranie. Każdy formant jest przeznaczona do innego scenariusza i ma swój własny listę funkcjami i ograniczeniami. Ogólnie rzecz biorąc <xref:System.Windows.Controls.TextBlock> element powinien być używany, gdy obsługa text ograniczony jest wymagane, na przykład krótkie zdanie w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> może służyć, gdy wymagana jest obsługa minimalnej ilości tekstu. Aby uzyskać więcej informacji, zobacz [TextBlock — Przegląd](../controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Pakowanie dokumentu  
 <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Zapewniają wydajny sposób organizowania danych aplikacji, treści dokumentu i powiązane zasoby w jeden kontener, który jest łatwy do dostępu, przenośne i łatwe do dystrybucji. Plik ZIP jest przykładem <xref:System.IO.Packaging.Package> typu może obsługiwać wiele obiektów jako pojedyncza jednostka. OPAKOWYWANIE [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] zapewniania domyślnego <xref:System.IO.Packaging.ZipPackage> implementacji zaprojektowany przy użyciu standardu otwarte konwencje pakietów przy użyciu architektury pliku XML i pliku ZIP. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Pakowania [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] znacznie upraszczają tworzenie pakietów oraz do przechowywania i dostępu do obiektów w ich. Obiekt zapisany w <xref:System.IO.Packaging.Package> nazywa się <xref:System.IO.Packaging.PackagePart> ("część"). Pakiety mogą również obejmować podpisem certyfikaty cyfrowe, które mogą służyć do identyfikowania inicjatorem części i do zweryfikowania, że zawartość pakietu nie zostały zmodyfikowane.  Pakiety również obejmować <xref:System.IO.Packaging.PackageRelationship> funkcja, która umożliwia dodatkowe informacje, które mają być dodane do pakietu lub skojarzone z określonymi częściami nie modyfikując zawartość istniejące składniki.  Pakiet również usług pomocy technicznej [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Architektura pakietu służy jako podstawa wielu kluczowych technologii:  
  
-   [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty odpowiadające [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)].  
  
-   Microsoft Office "12" otwartych dokumentach formatu XML (.docx).  
  
-   Formaty magazynu niestandardowego do projektu aplikacji.  
  
 Tworzenie pakietów interfejsów API w oparciu <xref:System.Windows.Xps.Packaging.XpsDocument> specjalnie do przechowywania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stałej zawartości dokumentów. <xref:System.Windows.Xps.Packaging.XpsDocument> Jest niezależny dokument, który można otworzyć w przeglądarce, wyświetlana w <xref:System.Windows.Controls.DocumentViewer> kontrolę, kierowane do buforu wydruku lub w danych wyjściowych bezpośrednio do [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-zgodnych drukarek.  
  
 Poniższe sekcje zawierają dodatkowe informacje o <xref:System.IO.Packaging.Package> i <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] dołączonym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Składniki pakietu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Pakowania interfejsy API umożliwiają danych aplikacji i dokumenty, aby organizować w pojedynczą jednostkę przenośnej. Plik ZIP jest jednym z najbardziej typowych pakietów i domyślny typ pakietu znajduje się za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> jest klasą abstrakcyjną, z którego <xref:System.IO.Packaging.ZipPackage> jest implementowany przy użyciu standardowego kodu XML i ZIP pliku architekturą otwarte.  <xref:System.IO.Packaging.Package.Open%2A> Metoda używa <xref:System.IO.Packaging.ZipPackage> tworzenie i używanie plików ZIP domyślnie. Pakiet może zawierać trzy podstawowe typy elementów:  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Pliki zawartości, danych, dokumentów i zasobów aplikacji.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certyfikat X.509] identyfikacji, uwierzytelniania i weryfikacji.|  
|<xref:System.IO.Packaging.PackageRelationship>|Dodano informacje dotyczące pakietu lub jego części.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> ("część") jest klasą abstrakcyjną, która odwołuje się do obiektu przechowywanego w <xref:System.IO.Packaging.Package>. W pliku ZIP części pakietu odnoszą się do poszczególnych plików, które są przechowywane w pliku ZIP.  <xref:System.IO.Packaging.ZipPackagePart> udostępnia domyślną implementację serializacji obiektów przechowywanych w <xref:System.IO.Packaging.ZipPackage>.  Takich jak system plików części zawartych w pakiecie są przechowywane w katalogu hierarchicznego lub organizacji "folder-style".  Za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pakowania interfejsów API, aplikacje można zapisać, przechowywanie i Odczyt wiele <xref:System.IO.Packaging.PackagePart> obiektów za pomocą jednego kontenera pliku ZIP.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Dla bezpieczeństwa <xref:System.IO.Packaging.PackageDigitalSignature> ("podpis cyfrowy") może być skojarzony z części pakietu. Element <xref:System.IO.Packaging.PackageDigitalSignature> zawiera [509], zapewnia dwie funkcje:  
  
1. Identyfikowanie i uwierzytelnianie inicjatorem części.  
  
2. Sprawdza, czy części nie zostały zmodyfikowane.  
  
 Podpis cyfrowy nie uniemożliwia część jest modyfikowany, ale sprawdzanie poprawności względem podpisu cyfrowego zakończy się niepowodzeniem, jeśli część jest w żaden sposób modyfikowany. Aplikacja może wtedy podjąć odpowiednie działania — na przykład Blokuj otwieranie części lub powiadamia użytkownika, że część została zmodyfikowana i nie jest bezpieczna.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 Element <xref:System.IO.Packaging.PackageRelationship> ("relacji") udostępnia mechanizm do kojarzenia dodatkowych informacji z pakietu lub części w pakiecie. Relacja to funkcji poziomie pakietu, który można skojarzyć dodatkowe informacje z częścią bez modyfikowania zawartości części rzeczywiste. Wstawianie nowych danych bezpośrednio do zawartości części zazwyczaj nie jest praktyczne w wielu przypadkach:  
  
-   Rzeczywisty typ części i jego zawartość schematu jest nieznany.  
  
-   Nawet wtedy, gdy znany, schemat zawartości może nie umożliwiają dodawania nowych informacji.  
  
-   Części mogą być cyfrowo podpisana lub zaszyfrowana i ograniczenia żadnych modyfikacji.  
  
 Relacje pakietu umożliwiają wykrywalny dodawania i skojarzyć dodatkowe informacje z poszczególnymi częściami lub cały pakiet. Pakiet relacje są używane dwie podstawowe funkcje:  
  
1. Definiowanie relacji zależności z jednej strony do innej części.  
  
2. Definiowanie relacji informacje, które dodawać notatki lub inne dane związane z części.  
  
 A <xref:System.IO.Packaging.PackageRelationship> zapewnia to szybki i wykrywalny do definiowania zależności i dodać inne informacje skojarzone z części pakietu lub pakiet jako całości.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Relacji zależności  
 Relacji zależności są używane do opisywania zależności, które sprawia, że jedną z części do innych części. Na przykład pakiet może zawierać części kodu HTML, który zawiera co najmniej jedną \<img > obrazu znaczników. Znaczniki obrazów odnoszą się do obrazów, które znajdują się albo inne części wewnętrznej do pakietu lub na zewnątrz pakietu (takie jak dostępne za pośrednictwem Internetu). Tworzenie <xref:System.IO.Packaging.PackageRelationship> skojarzone z HTML pliku ułatwia wykrywanie i uzyskiwania dostępu do zasobów zależnych, szybkie i łatwe. Aplikacja przeglądarki, lub podglądu można uzyskać bezpośredni dostęp do relacji części i natychmiast rozpocząć złożenia zależnych zasobów bez znajomości schematu lub analizowania dokumentu.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Informacje o relacjach  
 Podobnie jak notatki lub adnotacji, <xref:System.IO.Packaging.PackageRelationship> może również służyć do przechowywania innych typów informacji ma zostać skojarzony z częścią bez konieczności modyfikowania faktycznie samej zawartości części.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>Dokumenty XPS  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] dokument jest pakiet zawierający co najmniej jeden stałej dokumentów, wraz z wszystkich zasobów i wszystkie informacje wymagane do renderowania.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] jest również natywnych [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] format pliku buforu wydruku.  <xref:System.Windows.Xps.Packaging.XpsDocument> Są przechowywane w standardowych ZIP zestawu danych i może zawierać kombinację XML i binarny składników, takich jak pliki obrazów i czcionki. [PackageRelationships](#PackageRelationships) są używane do definiowania zależności między zawartości i zasobów potrzebnych do w pełni renderowania dokumentu.  <xref:System.Windows.Xps.Packaging.XpsDocument> Konstrukcja umożliwia rozwiązanie jednego dokumentu o wysokiej jakości, które obsługuje wielu zastosowań:  
  
-   Do czytania, zapisywania i przechowywania stałej dokumentu zawartości i zasobów w postaci jednego, przenośne i łatwo dystrybuować pliku.  
  
-   Wyświetlanie dokumentów za pomocą [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] aplikacji Podgląd.  
  
-   Wyprowadzanie dokumentów w macierzystym buforu wydruku danych wyjściowych format [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
-   Routing bezpośrednio do dokumentów [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-zgodnych drukarek.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Tekst](optimizing-performance-text.md)
- [Przegląd Dokument przepływu](flow-document-overview.md)
- [Przegląd Drukowanie](printing-overview.md)
- [Serializacja dokumentu i przechowywanie](document-serialization-and-storage.md)
