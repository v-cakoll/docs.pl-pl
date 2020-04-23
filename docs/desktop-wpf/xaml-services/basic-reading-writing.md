---
title: Klasa XAMLServices i podstawowy odczyt lub zapis XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 264a8c4abcf9a7efceb7c7accd786495d35476e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071879"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Klasa XAMLServices i podstawowe odczytywanie lub zapisywanie XAML

<xref:System.Xaml.XamlServices>jest klasą udostępnianą przez .NET, która może służyć do adresowania scenariuszy XAML, które nie wymagają określonego dostępu do strumienia węzłów XAML lub do informacji o systemie typu XAML uzyskanych z tych węzłów. <xref:System.Xaml.XamlServices>Interfejs API można podsumować `Load` `Parse` w następujący sposób: lub `Save` do obsługi ścieżki obciążenia XAML, do obsługi ścieżki zapisywania XAML i `Transform` podać technikę, która łączy ścieżkę obciążenia i zapisz ścieżkę. `Transform`może służyć do zmiany z jednego schematu XAML na inny. W tym temacie podsumowano każdą z tych klasyfikacji interfejsu API i opisano różnice między przeciążenia określonej metody.

## <a name="load"></a>Ładowanie

Różne przeciążenia <xref:System.Xaml.XamlServices.Load%2A> implementacji pełnej logiki dla ścieżki obciążenia. Ścieżka ładowania używa XAML w jakiejś formie i wyprowadza strumień węzła XAML. Większość z tych ścieżek ładowania używa XAML w zakodowanym formularzu pliku tekstowego XML. Można jednak również załadować strumień ogólny lub załadować wstępnie załadowane źródło XAML, <xref:System.Xaml.XamlReader> które jest już zawarte w innej implementacji.

Najprostszym przeciążeniem dla większości <xref:System.Xaml.XamlServices.Load%28System.String%29>scenariuszy jest . To przeciążenie `fileName` ma parametr, który jest po prostu nazwą pliku tekstowego, który zawiera XAML do załadowania. Jest to odpowiednie dla scenariuszy aplikacji, takich jak pełne zaufanie aplikacji, które wcześniej serializowane stan lub dane do komputera lokalnego. Jest to również przydatne w przypadku struktur, w których definiujesz model aplikacji i chcesz załadować jeden ze standardowych plików, który definiuje zachowanie aplikacji, uruchamianie interfejsu użytkownika lub inne funkcje zdefiniowane przez platformę struktur, które używają XAML.

<xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29>ma podobne scenariusze. To przeciążenie może być przydatne, jeśli użytkownik wybierze pliki do załadowania, ponieważ jest częstym wyjściem <xref:System.IO.Stream> innych <xref:System.IO> interfejsów API, które mogą uzyskać dostęp do systemu plików. Lub można uzyskać dostęp do źródeł XAML za pośrednictwem pobierania asynchronicznej lub innych technik sieciowych, które również zapewniają strumień. (Ładowanie ze strumienia lub źródła wybranego przez użytkownika może mieć wpływ na bezpieczeństwo. Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące zabezpieczeń XAML](security-considerations.md).)

<xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29>i <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> są przeciążenia, które opierają się na czytniki formatów z poprzednich wersji .NET. Aby użyć tych przeciążeń, należy już utworzyć wystąpienie czytnika i użyć jego `Create` interfejsu API, aby załadować kod XAML w odpowiednim formularzu (tekst lub XML). Jeśli wskaźniki rekordów zostały już przeniesione w innych czytnikach lub wykonane inne operacje z nimi, nie jest to ważne. Logika ścieżki <xref:System.Xaml.XamlServices.Load%2A> obciążenia od zawsze przetwarza całe dane wejściowe XAML z katalogu głównego. Następujące scenariusze mogą uzasadniać użycie tych przeciążeń:

- Projektowanie powierzchni, w których można ująć proste możliwości edycji XAML z istniejącego edytora tekstu specyficznego dla XML.

- Warianty podstawowych <xref:System.IO> scenariuszy, w których używane są dedykowane czytniki do otwierania plików lub strumieni. Logika wykonuje podstawowe sprawdzanie lub przetwarzanie zawartości, zanim spróbuje załadować jako XAML.

Można załadować plik lub strumień, albo załadować <xref:System.IO.TextReader>program <xref:System.Xaml.XamlReader> <xref:System.Xml.XmlReader>, lub zawijanie danych wejściowych XAML przez załadowanie za pomocą interfejsów API czytnika.

Wewnętrznie każde z powyższych przeciążeń <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>jest ostatecznie <xref:System.Xml.XmlReader> , a przekazywane <xref:System.Xaml.XamlXmlReader>jest używane do tworzenia nowego .

Podpis, `Load` który zawiera bardziej zaawansowane <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>scenariusze jest . Tego podpisu można użyć w jednym z następujących przypadków:

- Zdefiniowałeś własną implementację pliku <xref:System.Xaml.XamlReader>.

- Należy określić ustawienia, <xref:System.Xaml.XamlReader> które różnią się od ustawień domyślnych.

Przykłady ustawień innych niż domyślne:

<xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>\
<xref:System.Xaml.XamlReaderSettings.BaseUri%2A>\
<xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>\
<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>\
<xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>.

Domyślnym <xref:System.Xaml.XamlServices> czytnikiem <xref:System.Xaml.XamlXmlReader>jest . Jeśli podasz <xref:System.Xaml.XamlXmlReader> własne ustawienia, następujące są właściwości, aby <xref:System.Xaml.XamlXmlReaderSettings>ustawić nie domyślne:

<xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>

## <a name="parse"></a>Analizuj

<xref:System.Xaml.XamlServices.Parse%2A>jest `Load` podobny, ponieważ jest to interfejs API ścieżki obciążenia, który tworzy strumień węzła XAML z danych wejściowych XAML. Jednak w tym przypadku dane wejściowe XAML jest dostarczany bezpośrednio jako ciąg, który zawiera wszystkie XAML do załadowania. <xref:System.Xaml.XamlServices.Parse%2A>jest lekkie podejście, które jest bardziej odpowiednie dla scenariuszy aplikacji niż scenariuszy ramowych. Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A>jest po <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> prostu zawinięte <xref:System.IO.StringReader> wywołanie, które obejmuje wewnętrznie.

## <a name="save"></a>Zapisz

Różne przeciążenia <xref:System.Xaml.XamlServices.Save%2A> ścieżki zapisywania. Wszystkie <xref:System.Xaml.XamlServices.Save%2A> metody wszystkie wziąć wykres obiektu jako dane wejściowe i produkcji <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> wyjściowej jako strumień, plik lub wystąpienie.

Oczekuje się, że obiekt wejściowy będzie obiektem głównym reprezentacji niektórych obiektów. Może to być pojedynczy katalog główny obiektu biznesowego, katalog główny drzewa obiektów dla strony w scenariuszu interfejsu użytkownika, robocza powierzchnia edycji z narzędzia do projektowania lub inne pojęcia obiektów głównych, które są odpowiednie dla scenariuszy.

W wielu scenariuszach drzewa obiektów, które można zapisać jest związane z oryginalnej operacji, która załadowany XAML z <xref:System.Xaml.XamlServices.Load%2A> lub z innym interfejsem API zaimplementowane przez model framework/application. Mogą istnieć różnice przechwycone w drzewie obiektów, które są spowodowane zmianami stanu, zmiany, w których aplikacja przechwycone ustawienia środowiska uruchomieniowego od użytkownika, zmieniony XAML, ponieważ aplikacja jest powierzchnią projektu XAML, itp. Ze zmianami lub bez zmian koncepcja pierwszego ładowania XAML z znaczników, a następnie zapisywania go ponownie i porównywania dwóch formularzy znaczników XAML jest czasami określana jako reprezentacja XAML w obie strony.

Wyzwanie z zapisywania i serializacji złożony obiekt, który jest ustawiony w formie znaczników jest osiągnięcie równowagi między pełną reprezentację bez utraty informacji, a szczegółowość, która sprawia, że XAML mniej czytelny dla człowieka. Ponadto różni klienci xaml mogą mieć różne definicje lub oczekiwania dotyczące sposobu ustalania tego salda. Interfejsy <xref:System.Xaml.XamlServices.Save%2A> API reprezentują jedną definicję tej równowagi. Interfejsy <xref:System.Xaml.XamlServices.Save%2A> API używają dostępnego kontekstu schematu XAML i <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlMember>domyślnych cech opartych na programie CLR , oraz innych wewnętrznych koncepcji systemu XAML i XAML, aby określić, gdzie niektóre konstrukcje strumienia węzłów XAML mogą być optymalizowane, gdy są zapisywane z powrotem w znacznikach. Na przykład <xref:System.Xaml.XamlServices> zapisz ścieżki można użyć opartego na programie CLR <xref:System.Xaml.XamlType> domyślnego kontekstu <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>schematu XAML, aby rozwiązać dla obiektów, można określić , a następnie można pominąć tagi elementu właściwości podczas zapisywania właściwości do zawartości XAML obiektu.

<a name="transform"></a>
## <a name="transform"></a>Przekształcanie

<xref:System.Xaml.XamlServices.Transform%2A>konwertuje lub przekształca kod XAML, łącząc ścieżkę obciążenia i ścieżkę zapisu jako pojedynczą operację. Inny kontekst schematu lub inny system typu <xref:System.Xaml.XamlReader> <xref:System.Xaml.XamlWriter>kopii może służyć do i , który wpływa na sposób przekształcania wynikowego XAML. Działa to dobrze w przypadku operacji transformacji szerokiej.

W przypadku operacji, które polegają na badaniu każdego węzła w <xref:System.Xaml.XamlServices.Transform%2A>strumieniu węzła XAML, zazwyczaj nie używa się . Zamiast tego należy zdefiniować własną serię operacji ścieżki zapisywania ścieżki obciążenia i wtrącić własną logikę. W jednej ze ścieżek użyj pary modułów zapisu czytnika XAML/XAML wokół własnej pętli węzłów. Na przykład załaduj <xref:System.Xaml.XamlXmlReader> początkowy kod XAML <xref:System.Xaml.XamlXmlReader.Read%2A> przy użyciu i krok do węzłów z kolejnych wywołań. Działając na poziomie strumienia węzła XAML można teraz dostosować poszczególne węzły (typy, elementy członkowskie, inne węzły), aby zastosować transformację lub pozostawić węzeł w stanie rzeczywistym. Następnie należy wysłać węzeł do `Write` odpowiedniego interfejsu <xref:System.Xaml.XamlObjectWriter> API obiektu i zapisać obiekt. Aby uzyskać więcej informacji, zobacz [Opis struktur i pojęć strumienia węzłów XAML](understanding-xaml-node-stream-structures-and-concepts.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [Usługi XAML](../../../api/index.md)
