---
title: Serializacja dokumentu i przechowywanie
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: 7ddd887eefd67a3300795396dac26e855f30989e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254123"
---
# <a name="document-serialization-and-storage"></a>Serializacja dokumentu i przechowywanie

Microsoft .NET Framework zapewnia zaawansowane środowisko do tworzenia i wyświetlania dokumentów o wysokiej jakości.  Udoskonalone funkcje, które obsługują zarówno dokumenty o stałym rozmiarze, jak i dokumenty przepływu, zaawansowane kontrolki wyświetlania, połączone z zaawansowanymi możliwościami graficznymi 2D i 3W — są .NET Framework aplikacje na nowy poziom jakości i środowiska użytkownika.  Możliwość elastycznego zarządzania reprezentacją w pamięci dokumentu jest kluczową cechą .NET Framework i można efektywnie zapisywać i ładować dokumenty z magazynu danych jest konieczna niemal dla każdej aplikacji.  Proces konwersji dokumentu z wewnętrznej reprezentacji w pamięci na zewnętrzny magazyn danych jest długoterminową serializacji.  Proces wycofywania odczytywania magazynu danych i ponownego tworzenia oryginalnego wystąpienia w pamięci jest okresowo deserializacji.

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>Informacje o serializacji dokumentu

W idealnym przypadku proces serializowania i deserializacji dokumentu z i z powrotem do pamięci jest niewidoczny dla aplikacji.  Aplikacja wywołuje metodę "Write" serializatora w celu zapisania dokumentu, podczas gdy metoda deserializacji "read" uzyskuje dostęp do magazynu danych i ponownie tworzy oryginalne wystąpienie w pamięci.  Określony format, w którym dane są przechowywane, nie jest ogólnie problemem aplikacji, o ile proces serializacji i deserializacji odtworzy dokument z powrotem do jego oryginalnego formularza.

Aplikacje często udostępniają wiele opcji serializacji, które umożliwiają użytkownikowi zapisywanie dokumentów w różnych nośnikach lub w innym formacie.  Na przykład aplikacja może oferować opcje "Zapisz jako" do przechowywania dokumentu w pliku dysku, bazie danych lub usłudze sieci Web.  Podobnie różne serializatory mogą przechowywać dokument w różnych formatach, takich jak HTML, RTF, XML, XPS lub alternatywnie w formacie innej firmy.  W aplikacji Serializacja definiuje interfejs, który izoluje szczegóły nośnika magazynu w ramach implementacji każdego z określonych serializatorów.  Oprócz zalet hermetyzacji szczegółów magazynu .NET Framework <xref:System.Windows.Documents.Serialization> interfejsy API udostępniają kilka innych ważnych funkcji.

### <a name="features-of-net-framework-30-document-serializers"></a>Funkcje serializatorów dokumentów .NET Framework 3,0

- Bezpośredni dostęp do obiektów dokumentów wysokiego poziomu (logiczne drzewo i wizualizacje) umożliwia wydajne przechowywanie zawartości z podziałem na strony, elementów 2D/3W, obrazów, multimediów, hiperłączy, adnotacji i innych zawartości pomocy technicznej.

- Operacja synchroniczna i asynchroniczna.

- Obsługa serializatorów wtyczek z ulepszonymi możliwościami:

  - Dostęp na poziomie systemu do użytku przez wszystkie .NET Framework aplikacje.

  - Łatwe odnajdowanie wtyczki aplikacji.

  - Proste wdrażanie, Instalowanie i aktualizowanie niestandardowych wtyczek innych firm.

  - Obsługa interfejsu użytkownika dla niestandardowych ustawień i opcji czasu wykonywania.

### <a name="xps-print-path"></a>Ścieżka wydruku XPS

Ścieżka drukowania w formacie XPS programu Microsoft .NET Framework zapewnia także rozszerzalny mechanizm pisania dokumentów przy użyciu drukowania danych wyjściowych.  Plik XPS służy zarówno jako format pliku dokumentu, jak i jest natywnym formatem [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]buforu wydruku.  Dokumenty XPS można wysyłać bezpośrednio do drukarek zgodnych z formatem XPS bez konieczności konwersji do formatu pośredniego.  Zobacz [Omówienie drukowania](printing-overview.md) , aby uzyskać dodatkowe informacje na temat opcji i możliwości wyjściowych ścieżki wydruku.

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>Serializatory wtyczek

Interfejsy API zapewniają obsługę serializatorów wtyczek i połączonych serializatorów, które są instalowane niezależnie od aplikacji, w czasie wykonywania i są dostępne przy <xref:System.Windows.Documents.Serialization.SerializerProvider> użyciu mechanizmu odnajdywania. <xref:System.Windows.Documents.Serialization>  Serializatory wtyczek oferują ulepszone korzyści ułatwiające wdrażanie i korzystanie z całego systemu.  Połączone serializatory mogą być również zaimplementowane w środowiskach częściowego zaufania, [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] takich jak, w których serializatory wtyczki są niedostępne.  Połączone serializatory, które są oparte na pochodnej implementacji <xref:System.Windows.Documents.Serialization.SerializerWriter> klasy, są kompilowane i połączone bezpośrednio z aplikacją.  Zarówno serializatory wtyczki, jak i połączone serializatory działają przy użyciu identycznych metod publicznych i zdarzeń, co ułatwia użycie jednego lub obu typów serializacji w tej samej aplikacji.

Konstruktory wtyczek ułatwiają deweloperom aplikacji zapewnianie rozszerzalności do nowych projektów magazynu i formatów plików bez konieczności bezpośredniego kodu dla każdego potencjalnego formatu w czasie kompilacji.  Serializatory wtyczek mają również dostęp do deweloperów innych firm, zapewniając ustandaryzowaną metodę wdrażania, instalowania i aktualizacji wtyczek dostępnych dla systemu dla niestandardowych lub zastrzeżonych formatów plików.

### <a name="using-a-plug-in-serializer"></a>Korzystanie z serializatora wtyczki

Serializatory wtyczek są proste do użycia.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Klasa wylicza<xref:System.Windows.Documents.Serialization.SerializerDescriptor> obiekt dla każdej wtyczki zainstalowanej w systemie.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> Właściwość filtruje zainstalowane wtyczki w oparciu o bieżącą konfigurację i weryfikuje, czy serializator może być ładowany i używany przez aplikację.  Zawiera również inne właściwości, takie jak <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> i <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, które mogą być używane przez aplikację do monitowania użytkownika o wybranie serializatora dla dostępnego formatu danych wyjściowych. <xref:System.Windows.Documents.Serialization.SerializerDescriptor>  Domyślny serializator wtyczki dla XPS jest dostarczany z .NET Framework i jest zawsze wyliczany.  Gdy użytkownik wybierze format danych wyjściowych, <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> Metoda zostanie użyta do <xref:System.Windows.Documents.Serialization.SerializerWriter> utworzenia dla określonego formatu.  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> metodę można następnie wywołać, aby wyprowadzić strumień dokumentu do magazynu danych.

Poniższy przykład ilustruje aplikację, która używa <xref:System.Windows.Documents.Serialization.SerializerProvider> metody we właściwości "PlugInFileFilter".  PlugInFileFilter wylicza zainstalowane wtyczki i kompiluje ciąg filtru z dostępnymi opcjami plików dla <xref:Microsoft.Win32.SaveFileDialog>.

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

Po wybraniu przez użytkownika nazwy pliku wyjściowego Poniższy przykład ilustruje użycie <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> metody do przechowywania danego dokumentu w określonym formacie.

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>Instalowanie serializatorów wtyczek

<xref:System.Windows.Documents.Serialization.SerializerProvider> Klasa dostarcza interfejs aplikacji najwyższego poziomu dla funkcji odnajdywania serializatorów wtyczki i dostępu.  <xref:System.Windows.Documents.Serialization.SerializerProvider>lokalizuje i udostępnia aplikację listę serializatorów, które są zainstalowane i dostępne w systemie.  Charakterystyki zainstalowanych serializacji są zdefiniowane za pomocą ustawień rejestru.  Serializatory wtyczek można dodać do rejestru przy użyciu <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> metody lub jeśli .NET Framework nie jest jeszcze zainstalowana, skrypt instalacji wtyczki może bezpośrednio ustawić wartości rejestru.  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> Metoda może służyć do usuwania wcześniej zainstalowanej wtyczki lub ustawienia rejestru można resetować podobnie przez skrypt dezinstalacji.

### <a name="creating-a-plug-in-serializer"></a>Tworzenie serializatora wtyczki

Zarówno serializatory wtyczki, jak i połączone serializatory korzystają z tych samych, dostępnych publicznie metod i zdarzeń, a podobnie mogą być przeznaczone do działania synchronicznie lub asynchronicznie.  Istnieją trzy podstawowe kroki zwykle wykonywane w celu utworzenia serializatora wtyczki:

1. Zaimplementuj i Debuguj serializator najpierw jako połączony serializator.  Początkowo utworzenie serializatora skompilowanego i połączonego bezpośrednio w aplikacji testowej zapewnia pełen dostęp do punktów przerwania i innych usług debugowania przydatnych do testowania.

2. Po pełnym przetestowaniu <xref:System.Windows.Documents.Serialization.ISerializerFactory> serializatora interfejs zostanie dodany w celu utworzenia wtyczki.  Interfejs umożliwia pełny dostęp do wszystkich obiektów .NET Framework, które obejmują Drzewo logiczne, <xref:System.Windows.UIElement> obiekty <xref:System.Windows.Documents.IDocumentPaginatorSource>i <xref:System.Windows.Media.Visual> elementy. <xref:System.Windows.Documents.Serialization.ISerializerFactory>  Ponadto <xref:System.Windows.Documents.Serialization.ISerializerFactory> zapewnia te same metody synchroniczne i asynchroniczne oraz zdarzenia używane przez połączone serializatory.  Ponieważ duże dokumenty mogą przekroczyć czas, zalecane jest wykonanie operacji asynchronicznych w celu zapewnienia reakcji na interakcję użytkownika i zaoferowania opcji "Anuluj", jeśli wystąpi jakiś problem z magazynem danych.

3. Po utworzeniu serializatora wtyczki skrypt instalacyjny jest implementowany do dystrybucji i instalowania (i odinstalowywania) wtyczki (Zobacz powyżej "[Instalowanie serializatorów wtyczek](#InstallingPluginSerializers)").

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)
- [Specyfikacja papieru XML: omówienie](https://go.microsoft.com/fwlink?LinkID=106246)
