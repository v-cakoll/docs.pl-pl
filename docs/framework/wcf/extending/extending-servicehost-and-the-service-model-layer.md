---
title: Rozszerzanie elementu ServiceHost i warstwy modelu usług
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: 9e08b5b7b11848262d2cb7b6ed5715799d597889
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991773"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>Rozszerzanie elementu ServiceHost i warstwy modelu usług
Warstwy modelu usług jest odpowiedzialny za ściąganie komunikaty przychodzące poza podstawowym kanały, tłumaczenie je na wywołania metody w kodzie aplikacji i wyniki są wysyłane do obiektu wywołującego. Rozszerzenia modelu usługi modyfikować ani implementować wykonywania lub zachowanie komunikacji i funkcje, obejmujące funkcje klienta lub dyspozytora, niestandardowe zachowania, wiadomości i przejmowanie parametru i innych funkcji rozszerzalności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md)  
 W tym artykule opisano interfejsy, które mogą przechwytywać i modyfikowania środowiska uruchomieniowego klienta, a także klasy, do których można wstawić niestandardowych rozszerzeń w aplikacjach klienckich. Na przykład można wykonać rejestrowania komunikatów niestandardowych klienta, wykonywać serializacji niestandardowy komunikat i tak dalej.  
  
 [Rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 W tym artykule opisano interfejsy, które mogą przechwytywać i zmodyfikować środowisko wykonawcze usług, a także klasy, do których można wstawić niestandardowych rozszerzeń w aplikacjach usługi. Na przykład można wykonać rejestrowania niestandardowych usług, weryfikacji wiadomości po stronie usługi, wysyłania niestandardowych i tak dalej.  
  
 [Obiekty rozszerzalne](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 W tym artykule opisano pięć obiekty rozszerzalne i <xref:System.ServiceModel.IExtensibleObject%601> wzorca. Wzorzec extensible object jest używany, albo rozszerzanie istniejących klas środowiska uruchomieniowego przy użyciu nowych funkcji lub dodanie nowego Państwa do obiektu. Rozszerzenia, dołączony do jednego z obiekty rozszerzalne umożliwiają zachowania w bardzo różnych etapach przetwarzania dostęp do udostępnionego stanu i dołączony do obiektu extensible wspólnego, które mogą uzyskiwać dostęp do funkcji.  
  
 [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 Aby zmienić ustawienia lub Wstaw rozszerzeń w środowisku uruchomieniowym usługi WCF, należy użyć zachowań. WCF zawiera zachowania zaimplementowana przez system kontrolowanie ograniczania przepustowości, wystąpień i wiele innych aspektów usług i operacji. W tej sekcji opisano, jak utworzyć własne niestandardowe zachowania i porady były dostępne do użycia zarówno programowo i za pomocą plików konfiguracji.  
  
 [Rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 Opisuje sposób rozszerzyć <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>i użyj <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> klasy do dostosowywania środowiska hosta.  
  
## <a name="reference"></a>Tematy pomocy  
  
## <a name="related-sections"></a>Sekcje pokrewne
