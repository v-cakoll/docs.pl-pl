---
title: Rozszerzanie elementu ServiceHost i warstwy modelu usług
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: e370316cd121f49953e00e83dfc9d2aec17de1e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795738"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>Rozszerzanie elementu ServiceHost i warstwy modelu usług
Warstwa modelu usług jest odpowiedzialna za ściąganie komunikatów przychodzących z kanałów, tłumaczenie ich na wywołania metod w kodzie aplikacji i wysyłanie wyników z powrotem do obiektu wywołującego. Rozszerzenia modelu usług modyfikują lub implementują zachowanie wykonywania lub komunikacji oraz funkcje, w tym funkcje klienta lub dyspozytora, niestandardowe zachowania, przechwycenie komunikatów i parametrów oraz inne funkcje rozszerzalności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rozszerzanie klientów](extending-clients.md)  
 Opisuje interfejsy, które mogą przechwycić i zmodyfikować środowisko uruchomieniowe klienta, a także klasy, w których można wstawić niestandardowe rozszerzenia w aplikacjach klienckich. Można na przykład wykonać niestandardowe rejestrowanie komunikatów klienta, wykonać niestandardową serializację komunikatów i tak dalej.  
  
 [Rozszerzanie dyspozytorów](extending-dispatchers.md)  
 Opisuje interfejsy, które mogą przechwycić i zmodyfikować środowisko uruchomieniowe usługi, a także klasy, w których można wstawić niestandardowe rozszerzenia w aplikacjach usług. Można na przykład przeprowadzić niestandardowe rejestrowanie usługi, sprawdzanie poprawności komunikatów po stronie usługi, niestandardowe wysyłanie i tak dalej.  
  
 [Obiekty rozszerzalne](extensible-objects.md)  
 Opisuje pięć rozszerzalnych obiektów i <xref:System.ServiceModel.IExtensibleObject%601> wzorca. Rozszerzalny wzór obiektu służy do rozszerzania istniejących klas środowiska uruchomieniowego o nowe funkcje lub do dodawania nowego stanu do obiektu. Rozszerzenia dołączone do jednego z rozszerzalnych obiektów, umożliwiają zachowanie zachowań na różnych etapach przetwarzania w celu uzyskania dostępu do udostępnionego stanu i funkcjonalności dołączonego do wspólnego rozszerzalnego obiektu, do którego mają dostęp.  
  
 [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md)  
 Aby zmienić ustawienia lub wstawić rozszerzenia w środowisku uruchomieniowym WCF, należy użyć zachowań. Funkcja WCF obejmuje zachowanie implementowane przez system w celu kontrolowania ograniczeń, wystąpień i wielu innych aspektów usług i operacji. W tej sekcji opisano sposób tworzenia własnych zachowań niestandardowych i sposobu udostępniania ich użytkownikom programistycznym i korzystającym z plików konfiguracji.  
  
 [Rozszerzanie hostingu za pomocą elementu ServiceHostFactory](extending-hosting-using-servicehostfactory.md)  
 Opisuje sposób <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>rozbudowania i użycia <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> klas w celu dostosowania środowiska hosta.  
  
## <a name="reference"></a>Tematy pomocy  
  
## <a name="related-sections"></a>Sekcje pokrewne
