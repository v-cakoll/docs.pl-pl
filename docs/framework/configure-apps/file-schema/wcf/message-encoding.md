---
title: Kodowanie komunikatu
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: 8e5a71095ba62e0e2e6592c8b7b83b67602ef7e7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69931598"
---
# <a name="message-encoding"></a>Kodowanie komunikatu
Kodowanie jest procesem przekształcania zestawu znaków Unicode w sekwencję bajtów. Dekodowanie jest procesem wycofywania. Windows Communication Foundation (WCF) zawiera trzy typy kodowania komunikatów protokołu SOAP: tekst, binarny i mechanizm optymalizacji transmisji wiadomości (MTOM).  
  
 `binaryMessageEncoding`Sekcja konfiguracji określa kodowanie znaków i przechowywanie wersji komunikatów używanych w przypadku binarnych komunikatów XML. Koder komunikatów binarnych koduje wiadomości Windows Communication Foundation (WCF) w postaci binarnej w sieci. Chociaż to kodowanie skutkuje bardzo szybką transmisją komunikatów, współpraca oparta na standardach protokołu WS-* zostanie utracona.  
  
 `mtomMessageEncoding`Sekcja konfiguracji określa kodowanie znaków i przechowywanie wersji komunikatów używanych dla wiadomości za pomocą kodowania mechanizmu optymalizacji transmisji wiadomości (MTOM). (MTOM) to wydajna technologia przesyłania danych binarnych w wiadomościach Windows Communication Foundation (WCF). Koder MTOM próbuje zrównoważyć równowagę między wydajnością i współdziałaniem. Kodowanie MTOM przesyła większość XML w postaci tekstowej, ale optymalizuje duże bloki danych binarnych przez przesłanie ich bez konwersji do tekstu.  
  
 `textMessageEncoding`Sekcja konfiguracji określa koder tekstowy służący do tworzenia komunikatów tekstowych w sieci. Komunikaty generowane przez ten koder są odpowiednie dla międzyoperacyjności opartego na protokole WS-*. Usługa sieci Web lub klient usługi sieci Web może ogólnie zrozumieć tekst XML. Jednak przesyłanie dużych bloków danych binarnych jako tekstu jest najmniejszą efektywną metodą kodowania komunikatów XML  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Wybieranie kodera komunikatów](../../../wcf/feature-details/choosing-a-message-encoder.md)
