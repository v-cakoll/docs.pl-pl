---
title: Kodowanie komunikatu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ec7a85e95de9608d7a7daff11d70c9da3ff82989
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="message-encoding"></a>Kodowanie komunikatu
Kodowanie jest procesem przekształcania zestawu znaków Unicode do sekwencji bajtów. Dekodowanie jest procesu. Windows Communication Foundation (WCF) obejmuje trzy rodzaje kodowania protokołu SOAP wiadomości: tekst, dane binarne i mechanizmu optymalizacji transmisji wiadomości (MTOM).  
  
 `binaryMessageEncoding` Sekcji konfiguracji określa znak kodowanie i wersjonowanie wiadomości używanych dla komunikatów XML na podstawie danych binarnych. Koder komunikatów binarnych koduje wiadomości Windows Communication Foundation (WCF) w dane binarne w połączeniu. Chociaż ten typ kodowania w wyniku bardzo szybko transmisję wiadomości, współdziałanie opartych na WS-* standardów zostaną utracone.  
  
 `mtomMessageEncoding` Sekcji konfiguracji określa znak kodowanie i wersjonowanie wiadomości używanych dla wiadomości przy użyciu kodowania mechanizmu optymalizacji transmisji wiadomości (MTOM). (MTOM) to technologia wydajne przekazywania danych binarnych w wiadomości Windows Communication Foundation (WCF). Koder MTOM próbuje równowagę między wydajności i współdziałanie. Kodowanie MTOM przesyła większości XML w postaci tekstowej, ale optymalizuje dużych bloków danych binarnych, przekazując je jako — Brak konwersji na tekst.  
  
 `textMessageEncoding` Sekcji konfiguracji określa koder tekstu używany do tworzenia przesyłania wiadomości tekstowych. Komunikaty generowane przez ten koder nadają się do usługi WS-* na podstawie interop. Klienta usługi sieci Web lub usługi sieci Web zwykle zrozumieć tekstowy XML. Jednak przesyłania dużych bloków danych binarnych jako tekst jest najmniej efektywną metodę kodowania wiadomości XML  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Wybieranie kodera komunikatów](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
