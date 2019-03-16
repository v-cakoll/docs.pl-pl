---
title: Klasa XAMLServices i podstawowy odczyt lub zapis XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 68211babbce2e9512689fa329dcf33be0afa4a0c
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58027131"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Klasa XAMLServices i podstawowy odczyt lub zapis XAML
<xref:System.Xaml.XamlServices> jest klasą dostarczone przez .NET Framework XAML Services może służyć do scenariuszy XAML, które nie wymagają określonej dostęp do strumienia węzłów XAML lub informacje o systemie typu XAML uzyskany z tych węzłów. <xref:System.Xaml.XamlServices> Interfejs API można podsumować w następujący: `Load` lub `Parse` do obsługi ścieżką obciążenia XAML `Save` do obsługi XAML Zapisz ścieżkę, i `Transform` do udostępniania technika, która dołącza ścieżki obciążenia i Zapisz ścieżkę. `Transform` może służyć do zmiany z jednego schematu XAML do innego. Ten temat zawiera podsumowanie wszystkich te klasyfikacje interfejsu API i opisano różnice między przeciążeń określonej metody.  
  
<a name="load"></a>   
## <a name="load"></a>Ładowanie  
 Różne przeciążenia <xref:System.Xaml.XamlServices.Load%2A> implementują logikę pełną ścieżką obciążenia. Ścieżka obciążenia używa XAML w pewnej postaci i generuje strumień węzłów XAML. Większość z nich obciążenia, użyj ścieżki XAML w formie zakodowanej plik tekstowy XML. Jednak można również załadować ogólne strumienia lub załadować załadowanych źródła XAML, który znajduje się już w innej <xref:System.Xaml.XamlReader> implementacji.  
  
 To najprostsza przeciążenie dla większości scenariuszy <xref:System.Xaml.XamlServices.Load%28System.String%29>. Ma to przeciążenie `fileName` parametr, który jest po prostu nazwą pliku tekstowego zawierającego XAML do załadowania. Ta opcja jest odpowiednia dla scenariuszy aplikacji, takich jak w pełni zaufane aplikacje, które zostały wcześniej serializowane, stanu lub danych na komputerze lokalnym. Jest to również przydatne w przypadku środowisk, w którym definiowania modelu aplikacji i chcesz załadować jednej standardowe pliki, które definiuje zachowanie aplikacji, od interfejsu użytkownika lub innych zdefiniowanych funkcji, korzystających z XAML.  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> zawiera podobne scenariusze. Tego przeciążenia mogą być przydatne, jeśli masz użytkownikowi na wybranie pliki należy załadować, ponieważ <xref:System.IO.Stream> częste dane wyjściowe innych <xref:System.IO> interfejsów API, które mogą uzyskać dostępu do systemu plików. Lub użytkownik może uzyskiwać dostęp do źródła XAML za pomocą asynchronicznego pliki do pobrania lub innych technik sieci, które oferują także strumień. (Ładowanie ze strumienia lub wybrane przez użytkownika źródłowego może mieć wpływ na zabezpieczenia. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XAML](xaml-security-considerations.md).)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29> i <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> są przeciążenia, które korzystają z czytników formaty z poprzednich wersji programu .NET Framework. Aby korzystać z tych przeciążeń, powinien już utworzonego wystąpienia czytnika i używać jej `Create` interfejsu API, aby załadować XAML w odpowiednim formularzu (tekstowym lub XML). Jeśli masz już przeniesiony wskaźniki rekordu na inne czytniki lub wykonać inne operacje z nimi, to nie jest ważna. Logika ścieżki obciążenia z <xref:System.Xaml.XamlServices.Load%2A> zawsze przetwarza całego XAML, dane wejściowe z katalogu głównego w dół. Scenariusze te przeciążenia mogą obejmować następujące czynności:  
  
-   Zaprojektuj powierzchni, gdy zapewniają prosty XAML funkcje z istniejących edytora tekstu XML specyficzne edycji.  
  
-   Warianty podstawowe <xref:System.IO> scenariuszach, gdzie dedykowanych czytelnicy jest używany do otwierania plików i strumieni. Logika wykonuje podstawowe sprawdzenie lub przetwarzania zawartości przed ponowną próbą załadowania jako XAML.  
  
 Możesz załadować pliku lub strumienia lub załadować <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, lub <xref:System.Xaml.XamlReader> , zawijanie dane wejściowe XAML, ładując za pomocą interfejsów API czytelnika.  
  
 Wewnętrznie każda z poprzednim przeciążenia ostatecznie to klient jest <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>i przekazany <xref:System.Xml.XmlReader> służy do tworzenia nowego <xref:System.Xaml.XamlXmlReader>.  
  
 `Load` Podpisu, który zawiera bardziej zaawansowane scenariusze jest <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Ta sygnatura można użyć jednej z następujących przypadkach:  
  
-   Zdefiniowano własną implementację <xref:System.Xaml.XamlReader>.  
  
-   Należy określić ustawienia <xref:System.Xaml.XamlReader> , różnią się od ustawienia domyślne.  
  
 Przykłady innych niż domyślne ustawień dowolną z następujących ustawień: <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>; <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>; <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>; <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>; <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>. Czytnik domyślne <xref:System.Xaml.XamlServices> jest <xref:System.Xaml.XamlXmlReader>. Jeśli podasz własne <xref:System.Xaml.XamlXmlReader>, przy użyciu ustawień, poniżej przedstawiono właściwości, aby ustawić wartości niedomyślnej <xref:System.Xaml.XamlXmlReaderSettings>: <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>; <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>.  
  
<a name="parse"></a>   
## <a name="parse"></a>Analizy  
 <xref:System.Xaml.XamlServices.Parse%2A> przypomina `Load` ponieważ jest ścieżką obciążenia interfejsu API, który tworzy strumień węzłów XAML z XAML w danych wejściowych. Jednak w takim przypadku dane wejściowe XAML znajduje się bezpośrednio jako ciąg, który zawiera wszystkie XAML do załadowania. <xref:System.Xaml.XamlServices.Parse%2A> jest uproszczone podejście, które są bardziej odpowiednie dla scenariuszy aplikacji niż scenariuszy framework. Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A> jest tak naprawdę tylko opakowana <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> wywołania, które obejmuje <xref:System.IO.StringReader> wewnętrznie.  
  
<a name="save"></a>   
## <a name="save"></a>Zapisanie  
 Różne przeciążenia <xref:System.Xaml.XamlServices.Save%2A> zaimplementować Zapisz ścieżkę. Wszystkie <xref:System.Xaml.XamlServices.Save%2A> pliku podjąć wszystkie wykresu obiektu jako dane wejściowe i generować dane wyjściowe jako strumień, metody lub <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> wystąpienia.  
  
 Oczekuje obiektu wejściowego obiektu głównego niektóre reprezentacji obiektu. Może to być jednym elementem głównym obiektu biznesowego z katalogu głównego drzewa obiektów dla strony w przypadku interfejsu użytkownika powierzchni edycji z narzędziem do projektowania lub inne, które są odpowiednie w scenariuszach pojęcia obiektu głównego.  
  
 W wielu scenariuszach drzewa obiektów, który można zapisać jest powiązany z operacji pierwotnej, który załadować XAML, albo za pomocą <xref:System.Xaml.XamlServices.Load%2A> lub inny interfejs API implementowany przez model framework/aplikacji. Mogą wystąpić różnice przechwycone w drzewie obiektów, które są spowodowane przez zmiany stanu, zmiany, gdzie aplikacja przechwycone ustawień środowiska uruchomieniowego od użytkownika, zmienić XAML, ponieważ aplikacji XAML projekt powierzchni, itp. Z lub bez konieczności wprowadzania zmian koncepcji pierwszego ładowania XAML z kodu znaczników i zapisać go ponownie i porównywanie dwóch formach znaczników XAML jest czasami określane jako obustronne reprezentacja XAML.  
  
 Wyzwanie, zapisywania i serializacji obiekt złożony, który jest ustawiony w postaci znaczników jest w osiągnięciu równowagi między pełną reprezentację bez utraty informacji, a poziom szczegółowości, który sprawia, że XAML mniej czytelny dla człowieka. Ponadto różnych klientów dla XAML może mieć różne definicje lub oczekiwania dotyczące konfiguracji tej równowagi. <xref:System.Xaml.XamlServices.Save%2A> Interfejsów API reprezentuje jedną definicję tej równowagi. <xref:System.Xaml.XamlServices.Save%2A> Interfejsy API używają dostępne kontekst schematu XAML i domyślne CLR na podstawie charakterystyki <xref:System.Xaml.XamlType>, <xref:System.Xaml.XamlMember>, a inne XAML wewnętrzne i XAML wpisz pojęć systemu, aby określić, gdzie może być niektórych konstrukcji strumienia węzłów XAML zoptymalizowane pod kątem, gdy są one zapisywane do znaczników. Na przykład <xref:System.Xaml.XamlServices> zapisywanie ścieżek umożliwia kontekst schematu XAML CLR na podstawie domyślnego rozwiązania <xref:System.Xaml.XamlType> dla obiektów, można określić <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>, a następnie można pominąć tagów elementu właściwości, są zapisywane do zawartości XAML obiektu właściwości.  
  
<a name="transform"></a>   
## <a name="transform"></a>Transformacja  
 <xref:System.Xaml.XamlServices.Transform%2A> Konwertuje lub przekształca XAML, łącząc ścieżki obciążenia i Zapisz ścieżkę jako pojedyncza operacja. Kontekst innego schematu lub tworzenie innej kopii typu systemu może służyć do <xref:System.Xaml.XamlReader> i <xref:System.Xaml.XamlWriter>, czyli, co ma wpływ na sposób wynikowy XAML jest przekształcane. Działa to dobrze w przypadku operacji przekształcania szerokiego.  
  
 Dla operacji, które opierają się na sprawdzenie każdego węzła w strumień węzłów XAML, zwykle nie jest używana <xref:System.Xaml.XamlServices.Transform%2A>. Zamiast tego należy zdefiniować własne obciążenia Zapisz ścieżkę ścieżki operacji serii i interject własnej logiki. W jednej ze ścieżek za pomocą pary moduł zapisujący czytnika/XAML XAML wokół własne pętli węzła. Na przykład, ładowanie początkowe przy użyciu XAML <xref:System.Xaml.XamlXmlReader> i Wkrocz do węzłów z kolejnych <xref:System.Xaml.XamlXmlReader.Read%2A> wywołania. Działających na poziomie strumienia węzłów XAML można teraz dostosować poszczególne węzły (typy, elementy członkowskie, inne węzły), aby zastosować przekształcenie, lub pozostaw węzła jako-to. Następnie i nowszych wersjach wysłać węzeł odpowiednim `Write` interfejsu API <xref:System.Xaml.XamlObjectWriter> i zapisać obiekt. Aby uzyskać więcej informacji, zobacz [opis XAML węzła Stream strukturami i koncepcjami](understanding-xaml-node-stream-structures-and-concepts.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [Usługi XAML](index.md)
