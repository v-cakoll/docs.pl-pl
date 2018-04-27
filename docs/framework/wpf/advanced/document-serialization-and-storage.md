---
title: Serializacja dokumentu i przechowywanie
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e65a20323e3797d6d56ac7941e4ac9aeeb0ed473
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="document-serialization-and-storage"></a>Serializacja dokumentu i przechowywanie
Program Microsoft .NET Framework udostępnia zaawansowane środowisko umożliwiające tworzenie i wyświetlanie dokumentów wysokiej jakości.  Udoskonalone funkcje, które obsługują dokumenty stałej i dokumenty przepływu, zaawansowane wyświetlania formantów, połączeniu z zaawansowanych 2W i podejmij możliwości grafiki 3D [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikacji do nowego poziomu jakości i środowisko użytkownika.  Możliwość elastycznego zarządzania reprezentacji w pamięci dokumentu jest kluczowym elementem [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)], i możliwość efektywnego zapisywanie i ładowanie dokumentów z magazynu danych potrzeby prawie każdej aplikacji.  Proces konwersji dokumentu z reprezentacji w pamięci wewnętrznej do magazynu danych zewnętrznych jest określane jako serializacji.  Procesu odczytu z magazynu danych i ponowne utworzenie oryginalnego wystąpienia w pamięci jest określane jako deserializacji.  
  
 
  
<a name="AboutSerialization"></a>   
## <a name="about-document-serialization"></a>Informacje o serializacji dokumentu  
 W idealnym przypadku proces serializacji i deserializacji dokumentu z, a następnie wstecz do pamięci jest niewidoczne dla aplikacji.  Aplikacja wywołuje element serializujący "write" metodę, aby zapisać dokument, podczas deserializacji "Przeczytaj" Metoda uzyskuje dostęp do magazynu danych i odtwarza oryginalnego wystąpienia w pamięci.  Określony format, którego dane są przechowywane w zwykle nie jest problemem aplikacji, jak długie jako serializacja i zdeserializować procesu odtwarza dokumentu z powrotem do postaci oryginalnej.  
  
 Aplikacje często udostępniają wiele opcji serializacji, które umożliwiają użytkownikom zapisywać dokumenty w innych nośników lub w innym formacie.  Na przykład aplikacja może oferować "Zapisz jako" Opcje przechowywania dokumentów do pliku dysku, bazy danych lub usługi sieci web.  Podobnie różnych serializatorów można przechowywać dokumentu w różnych formatach takich jak HTML, RTF, XML, XPS lub format innych firm.  Do aplikacji serializacji definiuje interfejs, który izoluje szczegółowe informacje o nośniku w implementacji każdego określonego serializatora.  Oprócz korzyści z zastosowania zawierający szczegóły magazynu [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] <xref:System.Windows.Documents.Serialization> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] podać kilka ważnych funkcji.  
  
### <a name="features-of-net-framework-30-document-serializers"></a>Funkcje programu .NET Framework 3.0 dokumentu serializatorów  
  
-   Bezpośredni dostęp do obiektów wysokiego poziomu dokumentu (drzewa logicznego i elementy wizualne) Włącz wydajnego magazynu podzielonym na strony zawartość, elementy 2D i 3D, obrazy, nośnik, hiperłącza, adnotacje i innej zawartości pomocy technicznej.  
  
-   Operacji synchronicznych i asynchronicznych.  
  
-   Obsługa wtyczek serializatorów z rozszerzonymi funkcjami:  
  
    -   Dostęp do całego systemu do użytku przez wszystkie [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikacji.  
  
    -   Odnajdowanie wtyczki prostą aplikację.  
  
    -   Proste wdrożenie, instalacji i aktualizacji niestandardowych wtyczek innych firm.  
  
    -   Obsługa interfejsu użytkownika dla ustawień niestandardowych środowiska wykonawczego i opcje.  
  
### <a name="xps-print-path"></a>Ścieżki wydruku XPS  
 Microsoft .NET Framework [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ścieżki wydruku również zapewnia mechanizm extensible zapisywanie dokumentów za pomocą drukowania.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] pełni rolę zarówno format pliku dokumentu i format macierzysty buforu wydruku dla [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty mogą być wysyłane bezpośrednio do [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-zgodnych drukarek bez konieczności konwersji do formatu pośrednich.  Zobacz [Omówienie drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md) dodatkowe informacje na temat opcji wyjściowych ścieżki wydruku i możliwości.  
  
<a name="PluginSerializers"></a>   
## <a name="plug-in-serializers"></a>Wtyczka serializatorów  
 <xref:System.Windows.Documents.Serialization> Interfejsów API zapewniają obsługę dla wtyczki serializatorów i serializatorów połączone, które są instalowane osobno z aplikacji, wiązania w czasie wykonywania i są dostępne za pomocą <xref:System.Windows.Documents.Serialization.SerializerProvider> mechanizmu odnajdowania.  Wtyczka serializatorów oferują rozszerzoną korzyści w celu ułatwienia wdrażania i używania całego systemu.  Połączone serializatorów również można zaimplementować w środowiskach częściowej relacji zaufania takich jak [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] gdzie serializatorów wtyczka nie są dostępne.  Połączone serializatorów, oparte na pochodnej implementacja <xref:System.Windows.Documents.Serialization.SerializerWriter> klasy, kompilowania i połączone bezpośrednio do aplikacji.  Zarówno serializatorów wtyczki, jak i połączonych serializatorów działać przez identycznych metod publicznych i zdarzenia, które ułatwiają Użyj jednego lub obu tych rodzajów serializatorów w tej samej aplikacji.  
  
 Wtyczki serializatorów pomocy deweloperzy aplikacji, zapewniając rozszerzeń formaty plików i nowe projekty magazynu bez konieczności kodu bezpośrednio dla każdego potencjalnych format w czasie kompilacji.  Wtyczka serializatorów również korzystać inne firmy przez zapewnienie standardowej metody wdrażania, instalacji i aktualizacji systemu dostępne dodatki plug-in formatów plików niestandardowych lub zastrzeżonych.  
  
### <a name="using-a-plug-in-serializer"></a>Przy użyciu serializatora wtyczki  
 Wtyczka serializatorów są proste w użyciu.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Wylicza klasy <xref:System.Windows.Documents.Serialization.SerializerDescriptor> obiekt dla każdego wtyczki zainstalowane w systemie.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> Właściwość filtruje zainstalowanych wtyczek na podstawie bieżącej konfiguracji i sprawdza, czy serializator może załadować i używane przez aplikację.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor> Dostępne są także inne właściwości, takie jak <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> i <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, które aplikacji można używać w celu monitowania użytkownika o wyborze serializator dla formatu dostępnych danych wyjściowych.  Domyślna wtyczka serializatora dla [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] jest dostarczana z [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] i jest zawsze wyliczyć.  Po wybraniu przez użytkownika format danych wyjściowych <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> metoda służy do tworzenia <xref:System.Windows.Documents.Serialization.SerializerWriter> dla określonego formatu.  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> następnie można wywołać metody do wyjściowego strumienia dokumentów w magazynie danych.  
  
 Poniżej przedstawiono przykładową aplikację, która używa <xref:System.Windows.Documents.Serialization.SerializerProvider> metody we właściwości "PlugInFileFilter".  PlugInFileFilter wylicza zainstalowane dodatki plug-in i tworzy ciąg filtru z opcjami dostępności pliku <xref:Microsoft.Win32.SaveFileDialog>.  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 Po wybraniu przez użytkownika nazwa pliku wyjściowego poniższy przykład przedstawia użycie <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> metody do przechowywania danego dokumentu w określonym formacie.  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### <a name="installing-plug-in-serializers"></a>Instalowanie wtyczki serializatorów  
 <xref:System.Windows.Documents.Serialization.SerializerProvider> Klasa zapewnia interfejs wyższego poziomu dla odnajdywania szeregującego wtyczki i dostępu.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Lokalizuje i lista aplikacji serializatorów, które są zainstalowane i jest dostępny w systemie.  Szczegółowe informacje na temat zainstalowanych serializatorów są definiowane za pomocą ustawień rejestru.  Wtyczka serializatorów można dodać do rejestru za pomocą <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> metody; lub, jeśli [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] nie jest jeszcze zainstalowany, może skryptu instalacja dodatku bezpośrednio zestaw rejestru wartości samej siebie.  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> Metody można użyć do usunięcia wcześniej zainstalowane wtyczki lub ustawienia rejestru można zresetować podobnie przez skrypt dezinstalacji skryptu.  
  
### <a name="creating-a-plug-in-serializer"></a>Tworzenie szeregującego wtyczki  
 Zarówno wtyczki serializatorów połączonego serializatorów korzystanie z tych samych metod publicznych narażonych i zdarzeń i podobnie można zaprojektować działanie synchronicznie lub asynchronicznie.  Istnieją trzy podstawowe kroki, które zwykle zachowana w celu utworzenia szeregującego wtyczki:  
  
1.  Wdrożenie i debugowania serializator najpierw jako połączony serializatora.  Początkowo tworzenie serializator skompilowany i połączone bezpośrednio w aplikacji test zapewnia pełny dostęp do punktów przerwania i innych usług debugowania przydatne do testowania.  
  
2.  Po serializator został w pełni przetestowany, <xref:System.Windows.Documents.Serialization.ISerializerFactory> interfejs jest dodawany do tworzenia dodatku plug-in.  <xref:System.Windows.Documents.Serialization.ISerializerFactory> Interfejsu zezwala na dostęp do wszystkich [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] obiektów, takich jak drzewa logicznego <xref:System.Windows.UIElement> obiektów, <xref:System.Windows.Documents.IDocumentPaginatorSource>, i <xref:System.Windows.Media.Visual> elementy.  Ponadto <xref:System.Windows.Documents.Serialization.ISerializerFactory> zapewnia te same metody synchroniczne i asynchroniczne i zdarzenia używane przez połączone serializatorów.  Ponieważ dużych dokumentów może trwać do wyjściowego, operacje asynchroniczne zaleca się obsługa interakcji z użytkownikiem reakcji i oferuje opcji "Anuluj", jeśli występuje problem związany z magazynem danych.  
  
3.  Po utworzeniu szeregującego wtyczki skrypt instalacji jest zaimplementowany dla dystrybucji i instalowanie (i odinstalowywanie) wtyczki (zobacz powyżej, "[Instalowanie dodatku typu Plug-in serializatorów](#InstallingPluginSerializers)").  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Documents.Serialization>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Przegląd drukowania](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Formatu XML Paper Specification: omówienie](http://go.microsoft.com/fwlink?LinkID=106246)
