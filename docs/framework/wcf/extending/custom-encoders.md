---
title: Niestandardowe kodery
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: 7b68725346a2de23d405ed21ead93e3a6a8374e6
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411372"
---
# <a name="custom-encoders"></a>Niestandardowe kodery
W tym temacie omówiono, jak utworzyć niestandardowe kodery.  
  
 W konsoli Windows Communication Foundation (WCF), możesz użyć *powiązania* do określenia sposobu transferu danych za pośrednictwem sieci między punktami końcowymi. Powiązanie składa się z sekwencji *elementów wiązania*. Powiązanie zawiera elementy powiązania protokołu opcjonalne takie jak zabezpieczenia wymaganą *koder komunikatów* element powiązania, a element powiązania transportu wymagane. Koder komunikatów jest reprezentowany przez element powiązania kodowania komunikatu. Trzy koderów komunikat znajdują się w programie WCF: Plik binarny mechanizmu optymalizacji transmisji wiadomości (MTOM) i tekst.  
  
 Kodowanie elementu powiązania serializuje wychodzący komunikat <xref:System.ServiceModel.Channels.Message> i przekazuje go do transportu, lub odbiera serializowane postaci wiadomość z transportu i przekazuje go do warstwy protokołu, jeśli jest obecna, lub do aplikacji, jeśli nie istnieje.  
  
 Przekształcanie komunikatów koderów <xref:System.ServiceModel.Channels.Message> wystąpień do i z reprezentacji o komunikacji sieciowej. Mimo że koderów są określane jako siedzenie powyżej warstwy transportu w stosie kanału, zostaną one umieszczone w warstwie transportowej. Wiadomość zgodnie z wymaganiami standardu transportu w formacie transportów (na przykład HTTP). Kodery (na przykład tekst Xml) po prostu kodowania komunikatu.  
  
 Podczas łączenia z istniejących klienta lub serwera, możesz nie mieć wyboru — informacje przy użyciu określonego komunikatu kodowania. Jednak usług WCF mogą być dostępne za pośrednictwem wielu punktów końcowych, każdy z użyciem kodera inny komunikat. W przypadku pojedynczego kodera nie obejmuje całego odbiorców dla Twojej usługi, należy rozważyć, udostępnianie usługi za pośrednictwem wielu punktów końcowych. Aplikacje klienckie można określić punktu końcowego, który jest najlepsze dla nich. Za pomocą wielu punktów końcowych pozwala połączyć zalety koderów inny komunikat z innymi elementami powiązania.  
  
## <a name="system-provided-encoders"></a>Kodery dostarczane przez system  
 Usługi WCF zapewnia kilka powiązania dostarczane przez system, które są przeznaczone do najbardziej typowych scenariuszy aplikacji. Połącz każdego z tych powiązań, transport, koder komunikatów i inne opcje (na przykład zabezpieczenia). W tym temacie opisano, jak rozszerzyć `Text`, `Binary`, i `MTOM` koderów, które znajdują się w usłudze WCF lub utworzyć niestandardowy koder komunikatów. Koder komunikatu tekstowego obsługuje zarówno zwykłe Kodowanie XML oraz kodowania SOAP. Zwykły tryb kodowania XML koder komunikatu tekstowego nosi nazwę kodera POX "Zwykłe stare XML (") w odróżnieniu od oparte na tekście kodowaniem SOAP.  
  
 Aby uzyskać więcej informacji na temat kombinacji elementy powiązania dostarczane przez powiązania dostarczane przez system, zobacz odpowiedniej sekcji w [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Jak pracować z koderów dostarczane przez System  
 Kodowanie jest dodawany do powiązania przy użyciu klasy pochodzącej od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 WCF zawiera następujące elementy powiązania pochodną <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy, która może zapewnić tekstowych, plik binarny i kodowanie komunikatu transmisji optymalizacji mechanizm (MTOM):  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: Najbardziej międzyoperacyjnych, ale co najmniej wydajne kodera komunikatów XML. Usługi sieci Web lub klient usługi sieci Web zazwyczaj może zrozumieć tekstowych XML. Przesyłanie dużych bloków danych binarnych jako tekst nie jest jednak wydajne.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Reprezentuje element powiązania, który określa kodowanie znaków i wiadomości versioning używany dla wiadomości XML na podstawie pliku binarnego. Jest to najbardziej efektywny sposób opcji kodowania, ale co najmniej międzyoperacyjnych, ponieważ jest ona obsługiwana tylko przez punktami końcowymi programu WCF.  
  
-   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>: Reprezentuje element powiązania, który określa kodowanie znaków i wersji komunikatu używany dla wiadomości przy użyciu kodowania komunikatu transmisji optymalizacji mechanizm (MTOM). MTOM to technologia wydajne przekazywania danych binarnych w wiadomościach WCF. Koder MTOM próbuje zachować równowagę między współdziałania i wydajność. Kodowanie MTOM przesyła większość kodu XML w postaci tekstowej, ale optymalizuje dużych bloków danych binarnych, przekazywania ich jako — jest bez konwersji na tekst.  
  
 Element powiązania tworzy plik binarny, MTOM lub tekst <xref:System.ServiceModel.Channels.MessageEncoderFactory>. Fabryka tworzy plik binarny, MTOM lub tekst <xref:System.ServiceModel.Channels.MessageEncoderFactory> wystąpienia. Zazwyczaj jest tylko jedno wystąpienie. Jednak sesji są używane, mogą być udostępniane do każdej sesji kodera innego. Kodera binarnego sprawia, że użycie tego do zapewnienia koordynacji słowników dynamiczne (patrz infrastruktury XML).  
  
 <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> i <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> metody stanowią podstawę koderów. Metody zapewnienia czytania wiadomości ze strumienia lub z <xref:System.Byte> tablicy. Tablice typu byte są używane, gdy transport działają w trybie buforowanego. Komunikaty są zawsze zapisywane do strumieni. Jeśli transport buffer, wiadomości, zapewnia strumienia, który obsługuje buforowania.  
  
 Pozostałe elementy członkowskie pracować obsługi zawartości, typy nośników, a <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>. Transport wywołuje te metody kodera, aby sprawdzić, czy przychodzący komunikat może zostać odczytany przez niego lub do określenia, czy komunikatu wychodzącego jest nieprawidłowa dla tego kodera.  
  
 Każda z trzech implementacji kodera dodaje właściwości, które mają zastosowanie do określonego kodowania i jest w pełni konfigurowalne. Kodery również ujawnić przydziały czytnika, które mają wartości domyślne bezpieczne. Dyskusję na temat limitów przydziału można znaleźć w infrastrukturze XML.  
  
## <a name="features-of-system-provided-encoders"></a>Funkcje koderów dostarczane przez System  
 Istnieje kilka funkcji oferowanych przez koderów dostarczane przez system.  
  
### <a name="pooling"></a>Buforowanie  
 Każda z implementacji kodera próbuje jak najszerzej w puli. Zmniejszenie alokacji jest kluczowe sposób poprawienia wydajności kodu zarządzanego. Aby wykonać tej buforowanie, należy użyć implementacji `SynchronizedPool` klasy. C# Plik zawiera opis dodatkowe optymalizacje używane przez tę klasę.  
  
 <xref:System.Xml.XmlDictionaryReader> i <xref:System.Xml.XmlDictionaryWriter> wystąpienia są w puli i ponownie zainicjować w celu zapobieżenia alokowania nowe dla każdego komunikatu. Czytniki `OnClose` wywołania zwrotnego odzyskuje czytnik podczas `Close()` jest wywoływana. Koder odtwarza również niektóre obiekty stan komunikatu używany podczas tworzenia wiadomości. Rozmiary te pule są konfigurowane przez `MaxReadPoolSize` i `MaxWritePoolSize` właściwości na wszystkich trzech klasach pochodnych <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>Kodowanie binarne  
 Gdy binarny sesje używa kodowania, ciąg dynamiczny słownik muszą przekazane odbiorcy wiadomości. Odbywa się to przez dodanie przedrostka wiadomości z ciągami dynamiczny słownik. Odbiornik paski Wyłącz ciągi, dodaje je do sesji i przetwarza wiadomości. Poprawnie przekazywanie ciągów w słowniku wymaga buforowane transportu.  
  
 Ciągi są dołączane do komunikatów przez wewnętrzną `AddSessionInformationToMessage` metody. Dodaje ciągi jako UTF-8 na początku wiadomości prefiksem ich długości. Nagłówek słownika całego następnie jest poprzedzony znakiem długość jego danych. Odwrotna operacja odbywa się przez wewnętrzną `ExtractSessionInformationFromMessage` metody.  
  
 Oprócz przetwarzania dynamiczny słownik kluczy, buforowane sesji komunikaty są odbierane w nietypowy sposób. Zamiast tworzenia modułu odczytującego za pośrednictwem dokumentu, a następnie przetwarza go, używa wewnętrznego kodera binarnego `MessagePatterns` klasy dekonstruować strumień danych binarnych. Chodzi o to, że większość komunikaty mają zestaw nagłówków, które pojawiają się w określonej kolejności podczas generowania przez architekturę WCF. System wzorzec przerywa komunikatu od siebie na podstawie jego oczekuje. Jeśli to się powiodło, inicjuje <xref:System.ServiceModel.Channels.MessageHeaders> obiekt bez analiza kodu XML. W przeciwnym razie nastąpi powrót do standardową metodę.  
  
### <a name="mtom-encoding"></a>Kodowanie MTOM  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> Klasa ma właściwość dodatkowe czynności konfiguracyjne o nazwie <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement.MaxBufferSize%2A>. Te umieszcza górną granicę na ile danych jest ona dozwolona do zbuforowania podczas odczytywania wiadomości. XML informacji o zestawie (zestaw informacji) lub innych części MIME może być konieczne buforowane odtworzyć wszystkie części MIME w pojedynczym komunikacie.  
  
 Działała prawidłowo, za pośrednictwem protokołu HTTP, wewnętrzny klasy koder MTOM wiadomości zawiera niektórych wewnętrznych interfejsów API dla `GetContentType` (jest to również wewnętrznego) i `WriteMessage`, która jest publiczna i może zostać zastąpiona. Więcej komunikacji musi wystąpić, aby upewnić się, że wartości w nagłówkach HTTP zgadza się z wartości nagłówków MIME.  
  
 Wewnętrznie MTOM koder komunikatów używa czytelnicy tekst firmy WCF i jest podobna do koder tekstu. Główną różnicą jest optymalizowany duże zestawy danych binarnych lub "Duże obiekty binarne" (BLOB), nie konwertowania go na potrzeby kodowania Base-64 przed są osadzone w bajtów wiadomości. Zamiast tego tych obiektów blob są utrzymywane na wyodrębniony i do którego istnieje odwołanie jako załączniki MIME.  
  
## <a name="writing-your-own-encoder"></a>Pisanie własnego kodera  
 Aby zaimplementować własny niestandardowy koder komunikatów, należy podać niestandardowych implementacji abstrakcyjnych klas bazowych:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Konwertowanie z reprezentacji w pamięci, wiadomości na reprezentację w postaci, które mogą być zapisywane do strumienia jest zhermetyzowany wewnątrz <xref:System.ServiceModel.Channels.MessageEncoder> klasy, która służy jako fabrykę dla XML czytników i składników zapisywania XML, które obsługują określone typy kodowania XML.  
  
-   Klucza metody tej klasy, które musisz przesłonić to:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> który bierze <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> obiektu i zapisuje go do <xref:System.IO.Stream> obiektu.  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> który bierze <xref:System.IO.Stream> obiektu i rozmiar maksymalny nagłówka i zwraca <xref:System.ServiceModel.Channels.Message> obiektu.  
  
 Jest kod napisany w tych metodach, który obsługuje konwersję między protokołu transportowego standardowe i niestandardowe kodowania.  
  
 Następnie trzeba klasę fabryki, która tworzy niestandardowy koder kodu. Zastąp <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> do zwrócenia wystąpienia niestandardowego <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
 Następnie połącz niestandardowe <xref:System.ServiceModel.Channels.MessageEncoderFactory> stosu element powiązania, używany do konfigurowania usługi lub klienta przez zastąpienie <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> metodę, aby zwrócić wystąpienia tej fabryki.  
  
 Istnieją dwa przykłady dostarczane z programem WCF, które ilustrują ten proces za pomocą przykładowego kodu: [Niestandardowy koder komunikatów: Niestandardowy koder tekstu](../../../../docs/framework/wcf/samples/custom-message-encoder-custom-text-encoder.md) i [niestandardowy koder komunikatów: Koder kompresji](../../../../docs/framework/wcf/samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>
- <xref:System.ServiceModel.Channels.MessageEncoder>
- [Omówienie architektury transferu danych](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)
- [Wybieranie kodera komunikatów](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
