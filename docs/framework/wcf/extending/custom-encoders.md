---
title: Niestandardowe kodery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b1370adc510b26b14bff0dec45d83513a2f13b3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-encoders"></a>Niestandardowe kodery
W tym temacie omówiono tworzenie niestandardowe kodery.  
  
 W [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], możesz użyć *powiązania* do określenia sposobu transferu danych za pośrednictwem sieci między punktami końcowymi. Powiązanie składa się z sekwencji *elementów wiązania*. Powiązanie zawiera opcjonalne protokołu powiązania elementów, takich jak zabezpieczeń wymaganą *kodera wiadomości* element powiązania, a element powiązania transportu wymagane. Koder komunikatów jest reprezentowana przez powiązanie element kodowania komunikatu. Trzy koderów wiadomości są uwzględnione w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: Binary, mechanizmu optymalizacji transmisji wiadomości (MTOM) i tekstu.  
  
 Komunikat kodowania element powiązania serializuje wychodzące <xref:System.ServiceModel.Channels.Message> i przekazuje je do transportu, lub odbiera serializacji formę komunikat z transportu i przekazuje ją do warstwy protokołu, jeśli istnieje, lub do aplikacji, jeśli nie są zainstalowane.  
  
 Przekształć koderów komunikat <xref:System.ServiceModel.Channels.Message> wystąpień do i z reprezentacji danych przesyłanych w sieci. Mimo że koderów są nazywane siedzącą powyżej warstwy transportu w stosie kanału, znajdują się one wewnątrz warstwy transportowej. Wiadomość zgodnie z wymaganiami standardu transportu w formacie transportów (na przykład HTTP). Kodery (na przykład tekstu Xml) tylko kodowania komunikatu.  
  
 Podczas łączenia z istniejących klienta lub serwera, możesz nie mieć wybór o przy użyciu określonego komunikatu kodowania. Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług można udostępnić za pośrednictwem wiele punktów końcowych, każde z nich koder inny komunikat. Gdy jeden koder nie obejmuje całego odbiorców dla usługi, należy wziąć pod uwagę udostępnianie usługi przez wiele punktów końcowych. Aplikacje klienckie można wybrać punkt końcowy, który jest najlepsze dla nich. Przy użyciu wielu punktów końcowych pozwala na połączenie korzyści wynikające z koderów inny komunikat z innymi elementami powiązania.  
  
## <a name="system-provided-encoders"></a>Kodery dostarczane przez system  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia kilka powiązania dostarczane przez system, które są zaprojektowane tak, aby pokrywał najbardziej typowych scenariuszy aplikacji. Każdy z tych powiązań połączenie transportu, kodera wiadomości i inne opcje (na przykład zabezpieczeń). W tym temacie opisano, jak rozszerzyć `Text`, `Binary`, i `MTOM` komunikatu koderów, które znajdują się w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], lub utworzyć niestandardowego kodera. Tekst koder komunikatów obsługuje zarówno zwykły Kodowanie XML oraz kodowania protokołu SOAP. Zwykły tryb kodowania XML kodera wiadomości tekstowych nosi nazwę kodera POX ("XML starego zwykły") odróżniający go od tekstowych kodowaniu protokołu SOAP.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kombinacje dostarczonych przez powiązania dostarczane przez system elementów powiązania w sekcji odpowiednie w [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Jak pracować z koderów dostarczane przez System  
 Kodowanie jest dodawany do powiązania za pomocą klasy pochodzącej od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia następujące elementy powiązania pochodną <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy, która może zapewnić tekstu, dane binarne i kodowanie mechanizmu optymalizacji transmisji wiadomości (MTOM):  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: Najbardziej współdziałanie, ale najmniej wydajne koder komunikatów XML. Usługa sieci Web lub klient usługi sieci Web zwykle zrozumieć tekstowy XML. Jednak przesyłania dużych bloków danych binarnych jako tekst nie jest skuteczne.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Reprezentuje element powiązania, który określa kodowanie znaków i komunikatu versioning używanego w formacie binarnym komunikatów XML. Jest to najbardziej efektywny opcji kodowania, ale najmniej interoperacyjne, ponieważ jest obsługiwany tylko przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktów końcowych.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement -->`System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>: reprezentuje element powiązania, który określa kodowanie znaków i wersji komunikatu używany przy użyciu mechanizmu optymalizacji transmisji wiadomości (MTOM) kodowania komunikatu. MTOM jest technologią wydajne przekazywania danych binarnych w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości. Koder MTOM próbuje równowaga między wydajności i współdziałanie. Kodowanie MTOM przesyła większości XML w postaci tekstowej, ale optymalizuje dużych bloków danych binarnych, przekazując je jako — Brak konwersji na tekst.  
  
 Tworzy element powiązania pliku binarnego, MTOM lub tekst <xref:System.ServiceModel.Channels.MessageEncoderFactory>. Tworzy fabrykę pliku binarnego, MTOM lub tekst <xref:System.ServiceModel.Channels.MessageEncoderFactory> wystąpienia. Zazwyczaj jest tylko jedno wystąpienie. Jednak sesji są używane, mogą być dostarczane do każdej sesji kodera innego. Kodera binarnego sprawia, że użycie tego do koordynowania słowniki dynamiczne (patrz infrastruktury XML).  
  
 <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> i <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> metody są podstawowe koderów. Metody zapewnienia czytania wiadomości z strumienia lub <xref:System.Byte> tablicy. Tablice typu byte są używane podczas transportu działa w trybie buforowanego. Wiadomości są zawsze zapisywane do strumieni. Jeśli transport musi buforu wiadomości, zapewnia strumienia, który wykonuje buforowania.  
  
 Pozostałe elementy pracy z zawartości, typów nośników pomocy technicznej i <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>. Transport wymaga tych metod kodera, aby sprawdzić, czy komunikat przychodzący może zostać odczytany przez ten lub w celu ustalenia, czy komunikatu wychodzącego jest prawidłowy dla tego kodera.  
  
 Każda z trzech implementacji kodera dodaje właściwości, które mają zastosowanie do określonego kodowania i jest w pełni konfigurowalne. Kodery uwidacznia również czytnika przydziałów, które mają bezpieczne ustawienia domyślne. Zobacz infrastruktura XML Omówienie przydziałów.  
  
## <a name="features-of-system-provided-encoders"></a>Funkcje koderów dostarczane przez System  
 Istnieje szereg funkcji udostępnianych przez kodery dostarczane przez system.  
  
### <a name="pooling"></a>Buforowanie  
 Każda z implementacji kodera próbuje puli, jak to możliwe. Zmniejszenie alokacji jest klucza sposób, aby poprawić wydajność kodu zarządzanego. Do wykonania tej puli, użyj implementacje `SynchronizedPool` klasy. C# plik zawiera opis dodatkowe optymalizacje używane przez tę klasę.  
  
 `XmlDictionaryReader`i `XmlDictionaryWriter` wystąpienia są grupowane w pulach i ponownie zainicjowano zapobiegające przydzielania nowych dla każdego komunikatu. Czytniki `OnClose` wywołania zwrotnego zwraca czytnik podczas `Close()` jest wywoływana. Koder odtwarza także niektóre obiekty stanu komunikatów używana podczas tworzenia wiadomości. Rozmiary te pule są konfigurowane przez `MaxReadPoolSize` i `MaxWritePoolSize` właściwości dla wszystkich trzech klas pochodnych <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>Kodowanie binarne  
 Gdy binarny kodowanie używane sesje, ciąg dynamiczny słownik powiadamia odbiorcy wiadomości. Jest to realizowane przez prefiksu wiadomości z ciągami dynamiczny słownik. Odbiornik taśmy poza ciągi, dodaje je do sesji i przetwarza wiadomość. Poprawnie przesłaniem słownika wymaga buforowane transportu.  
  
 Ciągi są dołączane do wiadomości przez wewnętrznego `AddSessionInformationToMessage` metody. Dodaje ciągi jako UTF-8 na początku prefiksem ich długość komunikatu. Nagłówek słownika całego jest następnie prefiksem długość danych. Odwrotna operacja została wykonana przez wewnętrznego `ExtractSessionInformationFromMessage` metody.  
  
 Oprócz przetwarzania dynamiczny słownik kluczy, buforowane sesyjnych komunikaty są odbierane w unikatowy sposób. Zamiast tworzenia modułu odczytującego za pośrednictwem dokumentu i przetwarzania go, używa wewnętrznej kodera binarnego `MessagePatterns` klasy deconstruct strumienia danych binarnych. Pomysł jest większość komunikatów w określonym zestawie nagłówków, które pojawiają się w określonej kolejności podczas generowania przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. System wzorzec dzieli komunikat od siebie oparte na go oczekuje. Jeśli ten zakończy się powodzeniem, inicjuje <xref:System.ServiceModel.Channels.MessageHeaders> obiektu bez podczas analizowania pliku XML. Jeśli nie, nastąpi powrót do standardowej metody.  
  
### <a name="mtom-encoding"></a>Kodowanie MTOM  
 <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> Klasa ma właściwość dodatkowe czynności konfiguracyjne o nazwie <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`. Wartość MaxBufferSize 2A % >. Górna granica zostanie umieszczone w ilości danych jest dozwolone do zbuforowania podczas odczytywania komunikatu. XML informacji o zestawie (obiekt typu Infoset) lub innych części MIME może być konieczne buforowane odtworzyć wszystkie części MIME w pojedynczym komunikacie.  
  
 Działała prawidłowo, protokołu HTTP, Wewnętrzna klasa koder komunikatu MTOM zapewnia niektórych wewnętrznych interfejsów API dla `GetContentType` (która jest również wewnętrznego) i `WriteMessage`, który nie jest publiczny i może zostać zastąpiona. Więcej komunikacji należy przeprowadzić, aby upewnić się, że wartości w nagłówkach HTTP zgodne z wartościami w nagłówkach MIME.  
  
 Wewnętrznie, MTOM koder komunikatów używa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na tekst czytelników i jest podobny do kodera tekstu. Główną różnicą jest optymalizowany duże zestawy danych binarnych lub "Duże obiekty binarne" (BLOB), konwertując nie je przed osadzona w bajtach komunikat kodowanie Base-64. Zamiast tego te obiekty BLOB są przechowywane wyodrębnionego i do którego istnieje odwołanie jako załączniki MIME.  
  
## <a name="writing-your-own-encoder"></a>Pisanie własnych kodera  
 Aby wdrożyć własny niestandardowy koder komunikatów, należy podać niestandardowy implementacje abstrakcyjnych klas podstawowych:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Konwertowanie z reprezentacji w pamięci wiadomości do reprezentacji, które mogą być zapisywane do strumienia jest hermetyzowany wewnątrz <xref:System.ServiceModel.Channels.MessageEncoder> klasy, która służy jako fabrykę dla czytników XML i zapisywania XML, które obsługują określone typy kodowań XML.  
  
-   Klucza metody tej klasy, który należy zastąpić to:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A>który bierze <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> obiektu i zapisuje go w <xref:System.IO.Stream> obiektu.  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A>który bierze <xref:System.IO.Stream> obiektu i rozmiar maksymalny nagłówka i zwraca <xref:System.ServiceModel.Channels.Message> obiektu.  
  
 Jest kod napisany w tych metod, obsługujący konwersja między protokołu transportu standardowe i niestandardowe kodowania.  
  
 Następnie należy kodu klasy fabryki, która tworzy niestandardowego kodera. Zastąpienie <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> można zwrócić wystąpienia niestandardowego <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
 Następnie podłącz niestandardowe <xref:System.ServiceModel.Channels.MessageEncoderFactory> stosu element powiązania, używany do konfigurowania usługi lub klienta przez zastąpienie <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> metodę, aby zwrócić wystąpienia tej fabryki.  
  
 Istnieją dwa przykłady z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] który zilustrowanie tego procesu z przykładowym kodzie: [niestandardowy koder komunikatów: niestandardowy koder tekstu](../../../../docs/framework/wcf/samples/custom-message-encoder-custom-text-encoder.md) i [niestandardowy koder komunikatów: koder kompresji](../../../../docs/framework/wcf/samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
 <xref:System.ServiceModel.Channels.MessageEncoder>  
 [Omówienie architektury transferu danych](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 [Wybieranie kodera komunikatów](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
