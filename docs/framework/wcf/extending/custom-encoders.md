---
title: Niestandardowe kodery
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: 586207af0bfbe106512dfb61ee7439d4f5ce64c6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797218"
---
# <a name="custom-encoders"></a>Niestandardowe kodery
W tym temacie omówiono sposób tworzenia koderów niestandardowych.  
  
 W programie Windows Communication Foundation (WCF) można użyć *powiązania* , aby określić sposób transferu danych między punktami końcowymi. Powiązanie składa się z sekwencji *elementów powiązania*. Powiązanie obejmuje opcjonalne elementy powiązania protokołów, takie jak zabezpieczenia, wymagany element powiązania *kodera komunikatów* i wymagany element powiązania transportu. Koder komunikatów jest reprezentowany przez element powiązania kodowania komunikatów. W programie WCF są zawarte trzy kodery komunikatów: Plik binarny, mechanizm optymalizacji transmisji wiadomości (MTOM) i tekst.  
  
 Element powiązania kodowania komunikatu serializować wychodzące <xref:System.ServiceModel.Channels.Message> i przekazuje je do transportu lub otrzymuje serializowaną postać komunikatu z transportu i przekazuje go do warstwy protokołu, jeśli jest obecny lub do aplikacji, jeśli nie istnieje.  
  
 Kodery komunikatów przekształcają <xref:System.ServiceModel.Channels.Message> wystąpienia na i z reprezentacji przewodowej. Chociaż kodery są opisane jako miejsce powyżej warstwy transportu w stosie kanałów, znajdują się wewnątrz warstwy transportowej. Transporty (na przykład HTTP) formatują komunikat zgodnie z wymaganiami standardu transportowego. Kodery (na przykład tekstowe XML) po prostu kodują komunikat.  
  
 Podczas nawiązywania połączenia z istniejącym klientem lub serwerem może nie być możliwe wybranie określonego kodowania komunikatów. Jednak usługi WCF można udostępnić za pomocą wielu punktów końcowych, z których każdy ma inny koder komunikatów. Gdy pojedynczy koder nie obejmuje wszystkich odbiorców usługi, należy rozważyć udostępnienie usługi w wielu punktach końcowych. Aplikacje klienckie mogą następnie wybrać punkt końcowy, który jest najlepszy dla nich. Używanie wielu punktów końcowych pozwala łączyć zalety różnych koderów komunikatów z innymi elementami powiązania.  
  
## <a name="system-provided-encoders"></a>Kodery dostarczone przez system  
 Funkcja WCF udostępnia kilka powiązań dostarczonych przez system, które są przeznaczone do obsługi najpopularniejszych scenariuszy aplikacji. Każde z tych powiązań łączy transport, koder komunikatów i inne opcje (na przykład zabezpieczenia). W tym temacie opisano sposób `Text`, w jaki można rozmieścić kodery, `Binary`, i `MTOM` , które znajdują się w programie WCF, lub utworzyć własny koder niestandardowy. Koder wiadomości SMS obsługuje zarówno zwykłe Kodowanie XML, jak i kodowania SOAP. Tryb zwykłego kodowania XML kodera wiadomości tekstowej nazywa się koderem POX ("zwykłym starym XML") w celu odróżnienia go od tekstowego kodowania SOAP.  
  
 Aby uzyskać więcej informacji na temat kombinacji elementów powiązania dostarczonych przez powiązania dostarczone przez system, zapoznaj się z odpowiednią sekcją w temacie [Wybieranie transportu](../feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Jak korzystać z koderów dostarczonych przez system  
 Kodowanie jest dodawane do powiązania przy użyciu klasy pochodnej z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Funkcja WCF udostępnia następujące typy elementów powiązania, które pochodzą z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy, która może zapewniać kodowanie tekstu, binarnego i mechanizmu optymalizacji transmisji wiadomości (MTOM):  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: Najbardziej interoperacyjny, ale najmniej wydajny koder dla wiadomości XML. Usługa sieci Web lub klient usługi sieci Web może ogólnie zrozumieć tekst XML. Jednak przesyłanie dużych bloków danych binarnych jako tekstu nie jest wydajne.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Reprezentuje element powiązania, który określa kodowanie znaków i przechowywanie wersji komunikatów używanych dla binarnych komunikatów XML. Jest to najbardziej wydajne Opcje kodowania, ale najmniej interoperacyjności, ponieważ są obsługiwane tylko przez punkty końcowe WCF.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>: Reprezentuje element powiązania, który określa kodowanie znaków i przechowywanie wersji komunikatów używanej przez komunikat przy użyciu mechanizmu optymalizacji transmisji wiadomości (MTOM). MTOM to wydajna technologia przesyłania danych binarnych w komunikatach programu WCF. Koder MTOM próbuje zrównoważyć wydajność i współdziałanie. Kodowanie MTOM przesyła większość XML w postaci tekstowej, ale optymalizuje duże bloki danych binarnych przez przesłanie ich bez konwersji do tekstu.  
  
 Element Binding tworzy dane binarne, MTOM lub text <xref:System.ServiceModel.Channels.MessageEncoderFactory>. Fabryka tworzy wystąpienie binarne, MTOM lub text <xref:System.ServiceModel.Channels.MessageEncoderFactory> . Zazwyczaj istnieje tylko jedno wystąpienie. Jeśli jednak są używane sesje, do każdej sesji może być określony inny koder. Koder binarny służy do koordynowania słowników dynamicznych (zobacz infrastruktura XML).  
  
 Metody <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> i<xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> są rdzeńmi koderów. Metody zapewniają odczytywanie wiadomości ze strumienia lub z <xref:System.Byte> tablicy. Tablice bajtowe są używane, gdy transport działa w trybie buforowanym. Komunikaty są zawsze zapisywane w strumieniach. Jeśli transport musi buforować komunikat, zapewnia strumień, który wykonuje buforowanie.  
  
 Pozostała część elementów członkowskich współpracuje z obsługą zawartości, typami nośników <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>i. Transport wywołuje te metody kodera, aby sprawdzić, czy może być zdekodowany komunikat przychodzący lub określić, czy komunikat wychodzący jest prawidłowy dla tego kodera.  
  
 Każdy z trzech implementacji kodera dodaje właściwości, które są istotne dla określonych kodowań i jest w pełni konfigurowalny. Kodery ujawniają również przydziały czytnika, które mają bezpieczne ustawienia domyślne. Zobacz infrastruktura XML, aby zapoznać się z omówieniem przydziałów.  
  
## <a name="features-of-system-provided-encoders"></a>Funkcje koderów dostarczonych przez system  
 Kodery dostarczone przez system zapewniają wiele funkcji.  
  
### <a name="pooling"></a>Buforowanie  
 Każda implementacja kodera próbuje być pulą, jak to możliwe. Zmniejszenie alokacji jest najważniejszym sposobem na zwiększenie wydajności kodu zarządzanego. W celu osiągnięcia tej puli, implementacje używają `SynchronizedPool` klasy. C# Plik zawiera opis dodatkowych optymalizacji używanych przez tę klasę.  
  
 <xref:System.Xml.XmlDictionaryReader>a <xref:System.Xml.XmlDictionaryWriter> wystąpienia są w puli i ponownie inicjowane, aby zapobiec przydzieleniu nowych dla każdego komunikatu. W przypadku czytników `OnClose` wywołanie zwrotne przejmuje czytelnika `Close()` po wywołaniu. Koder odtwarza także obiekty stanu komunikatów używane podczas konstruowania komunikatów. Rozmiary tych pul można konfigurować za pomocą `MaxReadPoolSize` właściwości i `MaxWritePoolSize` dla każdej z trzech klas pochodnych od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>Kodowanie binarne  
 Gdy kodowanie binarne używa sesji, ciąg słownika dynamicznego musi być przekazywany do odbiorcy wiadomości. W tym celu należy utworzyć prefiks komunikatu z ciągami słownika dynamicznego. Odbiornik rozłączy ciągi, dodaje je do sesji i przetwarza komunikat. Poprawne przekazywanie ciągów słownika wymaga, aby transport był buforowany.  
  
 Ciągi są dołączane do komunikatu przez wewnętrzną `AddSessionInformationToMessage` metodę. Dodaje ciągi jako UTF-8 na początku wiadomości poprzedzonej ich długością. Cały nagłówek słownika jest następnie poprzedzony długością jego danych. Operacja odwrotna jest wykonywana przez wewnętrzną `ExtractSessionInformationFromMessage` metodę.  
  
 Oprócz przetwarzania kluczy słownika dynamicznego w unikatowy sposób odbierane są buforowane komunikaty sesji. Zamiast tworzyć czytniki nad dokumentem i go przetwarzać, koder binarny używa wewnętrznej `MessagePatterns` klasy do dekonstrukcji strumienia binarnego. Najlepszym pomysłem jest to, że większość komunikatów ma określony zestaw nagłówków, który jest wyświetlany w określonej kolejności, gdy jest generowany przez funkcję WCF. System wzorzec dzieli komunikat niezależnie od oczekiwań. Jeśli operacja się powiedzie, inicjuje <xref:System.ServiceModel.Channels.MessageHeaders> obiekt bez analizowania kodu XML. W przeciwnym razie powraca do standardowej metody.  
  
### <a name="mtom-encoding"></a>Kodowanie MTOM  
 Klasa ma dodatkową właściwość konfiguracji o nazwie <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement.MaxBufferSize%2A>. <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> Powoduje to górną granicę ilości danych, które może buforować podczas procesu odczytywania wiadomości. Zestaw informacji XML (sprawdzonych) lub inne części MIME mogą wymagać buforowania w celu ponownego zebrania wszystkich części MIME w jednej wiadomości.  
  
 Aby można było poprawnie działać przy użyciu protokołu HTTP, wewnętrzna Klasa kodera komunikatów MTOM udostępnia `GetContentType` wewnętrzne interfejsy API dla (, które `WriteMessage`są również wewnętrzne) i, które są publiczne i mogą zostać zastąpione. Aby zapewnić, że wartości w nagłówkach HTTP są zgodne z wartościami w nagłówkach MIME, należy wykonać więcej komunikacji.  
  
 Wewnętrznie koder komunikatów MTOM używa czytelników tekstu WCF i jest podobny do kodera tekstu. Główna różnica polega na tym, że optymalizuje duże fragmenty danych binarnych lub "duże obiekty binarne" (BLOB), nie konwertując ich na kodowanie Base-64 przed osadzeniem w bajtach komunikatów. Zamiast tego obiekty blob są rozpakowywane i przywoływane jako załączniki MIME.  
  
## <a name="writing-your-own-encoder"></a>Pisanie własnego kodera  
 Aby zaimplementować własny niestandardowy koder komunikatów, należy dostarczyć niestandardowe implementacje następujących abstrakcyjnych klas podstawowych:  
  
- <xref:System.ServiceModel.Channels.MessageEncoder>  
  
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Konwersja z reprezentacji w pamięci komunikatu na reprezentację, która może być zapisywana w strumieniu, jest hermetyzowana w <xref:System.ServiceModel.Channels.MessageEncoder> obrębie klasy, która służy jako fabryka dla czytników XML i autorów XML, które obsługują określone typy kodowania XML.  
  
- Kluczowymi metodami tej klasy, które należy zastąpić, są:  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A>który pobiera <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> obiekt i zapisuje go <xref:System.IO.Stream> w obiekcie.  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A>który pobiera <xref:System.IO.Stream> obiekt i maksymalny rozmiar nagłówka i <xref:System.ServiceModel.Channels.Message> zwraca obiekt.  
  
 Jest to kod napisany w ramach tych metod, który obsługuje konwersję między standardowym protokołem transportowym i dostosowanym kodowaniem.  
  
 Następnie należy zakodować klasę fabryki, która tworzy koder niestandardowy. Zastąp <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> , aby zwracało wystąpienie niestandardowe <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
 Następnie połącz niestandardowe <xref:System.ServiceModel.Channels.MessageEncoderFactory> z stosem elementów powiązania używanym do konfigurowania usługi lub klienta, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> zastępując metodę w celu zwrócenia wystąpienia tej fabryki.  
  
 Istnieją dwa przykłady dostarczone z programem WCF, które ilustrują ten proces za pomocą przykładowego kodu: [Niestandardowy koder komunikatów: Niestandardowy koder](../samples/custom-message-encoder-custom-text-encoder.md) tekstowy i [niestandardowy koder komunikatów: Koder](../samples/custom-message-encoder-compression-encoder.md)kompresji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>
- <xref:System.ServiceModel.Channels.MessageEncoder>
- [Omówienie architektury transferu danych](../feature-details/data-transfer-architectural-overview.md)
- [Wybieranie kodera komunikatów](../feature-details/choosing-a-message-encoder.md)
- [Wybieranie transportu](../feature-details/choosing-a-transport.md)
