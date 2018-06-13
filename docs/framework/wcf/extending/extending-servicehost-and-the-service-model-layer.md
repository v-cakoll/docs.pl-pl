---
title: Rozszerzanie elementu ServiceHost i warstwy modelu usług
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: 9e08b5b7b11848262d2cb7b6ed5715799d597889
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803479"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>Rozszerzanie elementu ServiceHost i warstwy modelu usług
Warstwy modelu usług jest odpowiedzialny za ściąganie wiadomości przychodzących poza podstawowej kanały, tłumaczenia je do wywołania metody w kodzie aplikacji i wysłaniem wyniki z powrotem do wywołującego. Rozszerzenia modelu usługi zmodyfikować, lub zaimplementuj wykonywania lub zachowanie komunikacji i funkcje dotyczące klienta lub dyspozytora funkcje, niestandardowe zachowania, wiadomości i przechwytywaniu parametru i innych funkcji rozszerzalności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md)  
 Opisuje interfejsy, które mogą przechwytywać i zmodyfikować środowiska uruchomieniowego klienta, a także klasy, do których można wstawić niestandardowych rozszerzeń w aplikacjach klienckich. Na przykład można wykonywać rejestrowanie komunikatów niestandardowego klienta, wykonywania serializacji niestandardowy komunikat i tak dalej.  
  
 [Rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 Opisuje interfejsy, które mogą przechwytywać i zmodyfikować środowiska uruchomieniowego usługi, a także klasy, do których można wstawić niestandardowych rozszerzeń w aplikacji usługi. Na przykład można wykonać rejestrowania usług niestandardowych, sprawdzanie poprawności komunikatu po stronie usługi, wysyłania niestandardowych i tak dalej.  
  
 [Obiekty rozszerzalne](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 W tym artykule opisano pięć obiekty rozszerzalne i <xref:System.ServiceModel.IExtensibleObject%601> wzorca. Wzorzec rozszerzonego obiektu jest używany, aby wydłużyć istniejące klasy środowiska uruchomieniowego z nowych funkcji lub aby dodać nowy stan do obiektu. Dołączony do jednego z obiekty rozszerzalne, dzięki rozszerzeniom zachowania w bardzo różnych etapach przetwarzania dostęp do stanu udostępnionego i dołączony do obiektu extensible wspólnej mogą uzyskiwać dostęp do funkcji.  
  
 [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 Aby zmienić ustawienia na lub Wstaw rozszerzenia w środowisku wykonawczym WCF, należy użyć zachowania. Usługi WCF zawiera zachowania zaimplementowana system kontroli przepustowości, wystąpień i wiele innych aspektów operacji dotyczących usług i. W tej sekcji opisano sposób tworzenia niestandardowych zachowania i porady były dostępne do użycia zarówno programowo i za pomocą plików konfiguracji.  
  
 [Rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 Opisuje sposób rozszerzyć <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>i użyj <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> klas, aby dostosować środowisku hosta.  
  
## <a name="reference"></a>Tematy pomocy  
  
## <a name="related-sections"></a>Sekcje pokrewne
