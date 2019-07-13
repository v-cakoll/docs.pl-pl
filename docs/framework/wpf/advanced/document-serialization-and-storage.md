---
title: Serializacja dokumentu i przechowywanie
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: b60b3964ff8e1b1f05b6c0820c63ec06d9ea0f4c
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859651"
---
# <a name="document-serialization-and-storage"></a>Serializacja dokumentu i przechowywanie

Microsoft .NET Framework oferuje zaawansowane środowisko do tworzenia i wyświetlanie dokumentów wysokiej jakości.  Ulepszone funkcje, które obsługują Naprawiono dokumenty i dokumenty przepływu, zaawansowane wyświetlania formantów, w połączeniu z zaawansowanych 2D i funkcje grafiki 3D aplikacji .NET Framework na nowy poziom jakości i środowisko użytkownika.  Możliwość elastycznego zarządzania reprezentacji w pamięci dokumentu jest kluczowym elementem programu .NET Framework i możliwość efektywnie zapisywanie i ładowanie dokumentów z magazynu danych jest niezbędne do niemal wszystkich aplikacji.  Proces konwersji dokumentu z reprezentacji w pamięci wewnętrznej do magazynu danych zewnętrznych jest określane jako serializacji.  Procesu odczytu z magazynu danych i ponowne utworzenie oryginalnego wystąpienia w pamięci jest określane jako deserializacji.

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>Informacje o serializacji dokumentu

Najlepiej proces serializacji i deserializacji dokumentu z, a następnie wstecz do pamięci jest niewidoczna dla aplikacji.  Aplikacja wywołuje element serializujący "write" metodę, aby zapisać dokumentu, podczas deserializacji "Odczyt" Metoda uzyskuje dostęp do magazynu danych oraz odtwarza oryginalnego wystąpienia w pamięci.  Określony format, którego dane są przechowywane w zwykle nie jest kwestią w aplikacji, jak długie jako serializacja i zdeserializować procesu odtwarza dokumentu z powrotem do ich oryginalnej postaci.

Aplikacje często oferują wiele opcji serializacji, które pozwalają użytkownikowi zapisywać dokumenty w innych nośników lub w innym formacie.  Na przykład aplikacja może zaoferować "Zapisz jako" Opcje zapisywania dokumentu do pliku dysku, bazy danych lub usługi sieci web.  Podobnie różnych serializatory może przechowywać dokumentu w różnych formatach takich jak HTML, RTF, XML, XPS, lub też w formacie innych firm.  Do aplikacji serializacji definiuje interfejs, który izoluje szczegółowe informacje o nośniku w implementacji każdego określonego elementu serializującego.  Oprócz korzyści z enkapsulacji szczegółów magazynu, .NET Framework <xref:System.Windows.Documents.Serialization> interfejsów API zapewniają kilka ważnych funkcji.

### <a name="features-of-net-framework-30-document-serializers"></a>Funkcje programu .NET Framework 3.0 dokumentu serializatorów

- Bezpośredni dostęp do obiektów wysokiego poziomu dokumentu (drzewo logiczne i wizualizacje) umożliwiają wydajne magazynu z podziałem na strony zawartości, elementy 2D/3D, obrazy, media, hiperłącza, adnotacji i innej zawartości pomocy technicznej.

- Operacja synchroniczne i asynchroniczne.

- Pomoc techniczna dla dodatku plug-in serializatory z udoskonalonymi funkcjami:

  - Dostęp do całego systemu dla wszystkich aplikacji .NET Framework.

  - Odnajdowanie wtyczki prostą aplikację.

  - Proste wdrożenie, instalacji i aktualizacji dla niestandardowych wtyczek innych firm.

  - Obsługa interfejsu użytkownika dla niestandardowych ustawień środowiska wykonawczego i opcje.

### <a name="xps-print-path"></a>Ścieżka wydruku XPS

Microsoft .NET Framework [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ścieżka wydruku także rozszerzony mechanizm do zapisywania dokumentów za pośrednictwem wydruku danych wyjściowych.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] Służy jako zarówno format pliku dokumentu i format natywnych buforu wydruku dla [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty, które mogą być wysyłane bezpośrednio do [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-zgodnymi drukarkami, bez potrzeby konwersji do formatu pośredniego.  Zobacz [Omówienie drukowania](printing-overview.md) dodatkowe informacje na temat opcji wyjściowych ścieżka wydruku i możliwości.

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>Wtyczka serializatorów

<xref:System.Windows.Documents.Serialization> Interfejsów API zapewnia obsługę zarówno serializatorów wtyczka serializatory połączone, które są instalowane osobno od aplikacji, powiązania w czasie wykonywania i są dostępne przy użyciu <xref:System.Windows.Documents.Serialization.SerializerProvider> mechanizm odnajdywania.  Serializatorów wtyczka oferują rozszerzone korzyści w celu ułatwienia wdrażania i używania całego systemu.  Połączone serializatory może też być implementowany w środowiskach częściowej relacji zaufania takich jak [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] gdzie serializatorów wtyczka nie są dostępne.  Połączone serializatory, które są oparte na pochodnej implementacji <xref:System.Windows.Documents.Serialization.SerializerWriter> klasy, są skompilowane i połączone bezpośrednio do aplikacji.  Serializatory połączone i serializatorów wtyczka działać przez identyczne publicznej metody i zdarzenia, które ułatwiają używać jednego lub obu tych typów serializatory w tej samej aplikacji.

Serializatorów wtyczka pomoc deweloperom aplikacji, zapewniając rozszerzenia działania do nowych projektów magazynu oraz formaty plików bez konieczności kodu bezpośrednio dla każdego potencjalnego formatu w czasie kompilacji.  Wtyczka serializatory również korzystać deweloperzy innych firm, zapewniając standardowy sposób wdrożyć, zainstalować i zaktualizować system dostępne dodatki plug-in dla formatów niestandardowych lub chronione prawem własności plików.

### <a name="using-a-plug-in-serializer"></a>Za pomocą wtyczki serializatora

Serializatory wtyczki są proste w użyciu.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Wylicza klasy <xref:System.Windows.Documents.Serialization.SerializerDescriptor> obiektu dla każdej wtyczki zainstalowane w systemie.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> Właściwość filtry zainstalowane dodatki plug-in na podstawie bieżącej konfiguracji i sprawdza, czy serializator może być załadowany i używanych przez aplikację.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor> Także inne właściwości, takie jak <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> i <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, używane przez aplikację monitu przy wyborze serializatora dla format wyjściowy dostępne.  Domyślne serializatora wtyczki dla [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] jest dostarczany z programem .NET Framework i zawsze są wyliczane.  Po wybraniu przez użytkownika format danych wyjściowych <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> metoda służy do tworzenia <xref:System.Windows.Documents.Serialization.SerializerWriter> dla określonego formatu.  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> następnie można wywołać metody służący do wypełniania wyjściowego strumienia dokumentu do magazynu danych.

W poniższym przykładzie pokazano aplikację, która używa <xref:System.Windows.Documents.Serialization.SerializerProvider> metoda we właściwości "PlugInFileFilter".  PlugInFileFilter wylicza zainstalowanych wtyczek i tworzy ciąg filtru, opcje plików <xref:Microsoft.Win32.SaveFileDialog>.

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

Po wybraniu przez użytkownika nazwa pliku wyjściowego w poniższym przykładzie pokazano użycie <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> metodę, aby przechowywać danego dokumentu w określonym formacie.

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>Instalowanie wtyczki serializatorów

<xref:System.Windows.Documents.Serialization.SerializerProvider> Klasy dostarcza interfejs aplikacji wyższego poziomu dla wtyczki serializator odnajdywania i dostęp.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Lokalizuje i lista aplikacji serializatory, które są zainstalowane i jest dostępny w systemie.  Szczegółowe informacje na temat zainstalowanych serializatory są definiowane za pomocą ustawień rejestru.  Serializatorów wtyczka można dodać do rejestru przy użyciu <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> metody; lub jeśli .NET Framework nie są jeszcze zainstalowane, skrypt instalacji dodatku typu plug-in bezpośrednio ustawić wartości rejestru, sam.  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> Metoda może służyć do usunięcia w poprzednio zainstalowanej wtyczki lub ustawienia rejestru można zresetować podobnie przez skrypt dezinstalacji.

### <a name="creating-a-plug-in-serializer"></a>Tworzenie wtyczki serializatora

Zarówno serializatorów wtyczka połączone serializatory korzystanie z tych samych metod publicznych narażonych i zdarzeń i podobnie, można zaprojektować do działania synchronicznie lub asynchronicznie.  Istnieją trzy podstawowe kroki, które zwykle używany do tworzenia serializatora wtyczki:

1. Wdrożenie i Debuguj element serializujący najpierw jako połączony element serializujący.  Początkowo tworzenia serializatora skompilowane i połączone bezpośrednio w aplikacji test zapewnia pełny dostęp do punktów przerwania i innych usług debugowania przydatne do testowania.

2. Po serializator jest w pełni przetestowane, <xref:System.Windows.Documents.Serialization.ISerializerFactory> interfejs jest dodawany do tworzenia dodatku typu plug-in.  <xref:System.Windows.Documents.Serialization.ISerializerFactory> Interfejsu zezwala na pełny dostęp do wszystkich obiektów .NET Framework, która zawiera drzewo logiczne <xref:System.Windows.UIElement> obiektów <xref:System.Windows.Documents.IDocumentPaginatorSource>, i <xref:System.Windows.Media.Visual> elementów.  Ponadto <xref:System.Windows.Documents.Serialization.ISerializerFactory> zapewnia te same synchroniczne i asynchroniczne metody i zdarzenia używane przez połączone serializatory.  Ponieważ dużych dokumentów może trwać do wypełniania wyjściowego, operacje asynchroniczne są zalecane do obsługi interakcji z użytkownikiem odpowiada i oferty z opcją "Anuluj", jeśli wystąpi problem, z magazynem danych.

3. Po utworzeniu dodatku typu plug-in serializator skrypt instalacji został zaimplementowany dla dystrybucji i instalacji (i odinstalowywania) wtyczki (zobacz powyżej, "[Instalowanie wtyczki Serializatory](#InstallingPluginSerializers)").

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd drukowania](printing-overview.md)
- [Formatu XML Paper Specification: omówienie](https://go.microsoft.com/fwlink?LinkID=106246)
