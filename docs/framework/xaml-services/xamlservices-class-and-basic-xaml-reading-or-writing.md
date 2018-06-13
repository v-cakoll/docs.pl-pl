---
title: Klasa XAMLServices i podstawowy odczyt lub zapis XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 27c7a45a45e8bbe3594813b29344d1548eecda5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565915"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Klasa XAMLServices i podstawowy odczyt lub zapis XAML
<xref:System.Xaml.XamlServices> to klasy .NET Framework XAML Services może służyć do adresów scenariusze XAML, które nie wymagają szczególnych dostęp do strumienia węzłów XAML lub informacje o systemie typu XAML uzyskane z tych węzłów. <xref:System.Xaml.XamlServices> Interfejsu API można podsumować w następujący sposób: `Load` lub `Parse` do obsługi ścieżką obciążenia XAML `Save` do obsługi XAML ścieżkę, zapisu i `Transform` do udostępniania technika, w której jest przyłączany ścieżki obciążenia i Zapisz ścieżkę. `Transform` można zmienić jeden schemat XAML na inne. Ten temat zawiera podsumowanie każdego z tych klasyfikacjach interfejsu API oraz opisano różnice między przeciążenia metody określonej.  
  
<a name="load"></a>   
## <a name="load"></a>Ładowanie  
 Różne przeciążenia <xref:System.Xaml.XamlServices.Load%2A> implementują logikę pełną ścieżką obciążenia. Ścieżka obciążenia używa XAML w jakiejś formie i wyprowadza strumień węzłów XAML. Większość tych załadować Użyj ścieżki XAML w formie zakodowanej plik tekstowy XML. Jednak można również ładować ogólne strumienia lub załadować wstępnie źródła XAML, który znajduje się już w innej <xref:System.Xaml.XamlReader> implementacji.  
  
 Jest najprostsza przeciążenie dla większości scenariuszy <xref:System.Xaml.XamlServices.Load%28System.String%29>. To przeciążenie ma `fileName` parametr, który jest po prostu nazwę pliku tekstowego, który zawiera kod XAML, aby załadować. Ta opcja jest odpowiednia dla scenariuszy aplikacji, takich jak aplikacje pełnego zaufania, które zostały wcześniej serializować stanu lub danych na komputerze lokalnym. Jest to również przydatne w przypadku platform, gdzie są definiowane model aplikacji i chcesz załadować jednej standardowe pliki, które definiuje zachowanie aplikacji, uruchamiania interfejsu użytkownika lub innych funkcji zdefiniowanych przez framework, korzystających z języka XAML.  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> ma podobne scenariusze. To przeciążenie mogą być przydatne w przypadku użytkowników, wybierz pliki, aby załadować, ponieważ <xref:System.IO.Stream> jest często dane wyjściowe innych <xref:System.IO> interfejsów API, które można uzyskać dostępu do systemu plików. Lub możesz może uzyskiwać dostęp do źródła XAML za pośrednictwem pobieranie asynchroniczne lub innych technik sieci, które oferują także strumienia. (Ładowanie ze strumienia lub źródło wybrane przez użytkownika może mieć wpływ na bezpieczeństwo. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29> i <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> są przeciążenia, które opierają się na czytników formatów z poprzednich wersji programu .NET Framework. Aby korzystać z tych przeciążenia, powinien już utworzone wystąpienie czytnika i używane jego `Create` interfejsu API można załadować pliku XAML w odpowiednim formularzu (tekst lub XML). Jeśli masz już przeniesione wskaźniki rekordu w innych czytników lub wykonywane inne operacje z nimi, to nie jest istotna. Logiki ścieżki obciążenia <xref:System.Xaml.XamlServices.Load%2A> zawsze przetwarza cały XAML danych wejściowych z katalogu głównego w dół. Scenariusze dotyczące tych przeciążenia może zawierać następujący wpis:  
  
-   Projektowanie powierzchni gdy zapewniają prosty XAML z istniejących Edytor tekstu XML specyficzne możliwości edycji.  
  
-   Wariantów podstawowe <xref:System.IO> scenariuszy, w którym dedykowanych czytników jest używany do otwierania plików lub strumieni. Logika wykonuje podstawowe sprawdzanie lub przetwarzania zawartości przed ponowną próbą załadowania jako XAML.  
  
 Albo można załadować pliku lub strumienia lub można załadować <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, lub <xref:System.Xaml.XamlReader> który zawijać dane wejściowe XAML przez ładowanie z interfejsami API czytelnika.  
  
 Wewnętrznie, każdy z powyższych przeciążeń jest ostatecznie <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>oraz przekazany <xref:System.Xml.XmlReader> służy do tworzenia nowego <xref:System.Xaml.XamlXmlReader>.  
  
 `Load` Podpisie, który zapewnia bardziej zaawansowanych scenariuszy jest <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Podpis można użyć jednej z następujących przypadkach:  
  
-   Zdefiniowano implementacji programu <xref:System.Xaml.XamlReader>.  
  
-   Należy określić ustawienia <xref:System.Xaml.XamlReader> który różnić się od ustawienia domyślne.  
  
 Przykłady z systemem innym niż domyślne ustawienia następujących ustawień: <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>; <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>; <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>; <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>; <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>. Czytnik domyślny dla <xref:System.Xaml.XamlServices> jest <xref:System.Xaml.XamlXmlReader>. Jeśli podasz własne <xref:System.Xaml.XamlXmlReader>, przy użyciu ustawień, poniżej przedstawiono właściwości, aby wybrać inny niż domyślny <xref:System.Xaml.XamlXmlReaderSettings>: <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>; <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>.  
  
<a name="parse"></a>   
## <a name="parse"></a>analizy  
 <xref:System.Xaml.XamlServices.Parse%2A> przypomina `Load` , ponieważ jest to ścieżka obciążenia interfejs API, który tworzy strumień węzłów XAML na podstawie danych wejściowych XAML. Jednak w takim przypadku XAML wprowadzono bezpośrednio jako ciąg, który zawiera wszystkie XAML do załadowania. <xref:System.Xaml.XamlServices.Parse%2A> jest to lekkie podejście, które jest bardziej odpowiednie dla scenariuszy aplikacji niż framework scenariuszy. Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A> jest tak naprawdę opakowana <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> wywołanie, która obejmuje <xref:System.IO.StringReader> wewnętrznie.  
  
<a name="save"></a>   
## <a name="save"></a>Zapisanie  
 Różne przeciążenia <xref:System.Xaml.XamlServices.Save%2A> zaimplementować Zapisz ścieżkę. Wszystkie <xref:System.Xaml.XamlServices.Save%2A> metody wszystkie zająć wykres obiektu jako argument wejściowy i generowania danych wyjściowych jako strumienia, pliku, lub <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> wystąpienia.  
  
 Obiekt wejściowy powinien być obiektem głównym niektórych reprezentacji obiektu. Może to być jednym elementem głównym obiektu biznesowego korzeń drzewa obiektów dla strony w przypadku interfejsu użytkownika, powierzchni edycji z narzędziem do projektu lub innych pojęcia obiektu głównego, które są odpowiednie w scenariuszach.  
  
 W wielu scenariuszach zapisywania drzewa obiektów jest powiązany z oryginalnej operacji załadowany XAML, za pomocą <xref:System.Xaml.XamlServices.Load%2A> lub z innego interfejsu API zaimplementowana przez model aplikacji/framework. Mogą wystąpić różnice przechwycone drzewa obiektów, które są z powodu zmian stanu, gdzie aplikacja przechwycić ustawienia środowiska uruchomieniowego od użytkownika, zmiany zmienić XAML, ponieważ aplikacja jest itp powierzchni, projektu XAML. Z lub bez zmian pojęcie pierwszy ładowania kodu XAML z poziomu znacznika i zapisać go ponownie i porównanie dwóch formach znaczników XAML jest czasami określana jako obustronne reprezentację XAML.  
  
 Żądanie zapisywania i serializacji złożonych obiekt, który jest ustawiony w formie znacznika jest uzyskanie równowagi między pełną reprezentacja bez utraty informacji, a poziom szczegółowości, który sprawia, że XAML mniej zrozumiałą dla użytkownika. Ponadto różnych klientów dla XAML może mieć różne definicje lub oczekiwania dotyczące konfiguracji tej równowagi. <xref:System.Xaml.XamlServices.Save%2A> Interfejsy API stanowią jedną definicję tej równowagi. <xref:System.Xaml.XamlServices.Save%2A> Używać interfejsów API dostępne kontekst schematu XAML i domyślne na podstawie CLR właściwości <xref:System.Xaml.XamlType>, <xref:System.Xaml.XamlMember>, a inne XAML wewnętrzne i języka XAML wpisz pojęć systemu, aby określić, gdzie może być niektórych konstrukcje strumienia węzłów XAML zoptymalizowana podczas zapisywania do znaczników. Na przykład <xref:System.Xaml.XamlServices> Zapisz ścieżek umożliwia kontekst schematu XAML CLR na podstawie domyślnego rozwiązania <xref:System.Xaml.XamlType> dla obiektów, można określić <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>, a następnie można pominąć znaczniki elementów właściwości, właściwości są zapisywane do zawartości XAML obiektu.  
  
<a name="transform"></a>   
## <a name="transform"></a>Transformacja  
 <xref:System.Xaml.XamlServices.Transform%2A> Konwertuje lub przekształca XAML łącząc ścieżki obciążenia i Zapisz ścieżkę jako jedna operacja. Kontekst inny schemat lub różnych bazowego typu systemu może służyć do <xref:System.Xaml.XamlReader> i <xref:System.Xaml.XamlWriter>, która jest, co wpływa na sposób jest przekształcana wynikowy XAML. To dobrze się sprawdza operacje szerokie transformacji.  
  
 Dla operacji, które opierają się na sprawdzenie każdego węzła w strumień węzłów XAML, zwykle nie jest używana <xref:System.Xaml.XamlServices.Transform%2A>. Zamiast tego należy definiować własne obciążenia Zapisz ścieżkę ścieżki operacji serii i interject własną logikę. W jednej ze ścieżek za pomocą pary XAML czytnika/XAML zapisywania wokół pętli własne węzła. Na przykład, ładowanie początkowej przy użyciu języka XAML <xref:System.Xaml.XamlXmlReader> i Wkrocz do węzłów z kolejnych <xref:System.Xaml.XamlXmlReader.Read%2A> wywołania. Działających na poziomie strumienia węzłów XAML można teraz dostosowanie poszczególne węzły (typy, elementy członkowskie, pozostałe węzły), aby zastosować przekształcenie lub pozostawienie węzła jako — jest. Następnie i jego nowszych wersjach wysłać węzeł odpowiednim `Write` interfejsu API z <xref:System.Xaml.XamlObjectWriter> i zapisać obiekt. Aby uzyskać więcej informacji, zobacz [opis XAML węzła strukturami i koncepcjami strumienia](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xaml.XamlObjectWriter>  
 <xref:System.Xaml.XamlServices>  
 [Usługi XAML](../../../docs/framework/xaml-services/index.md)
