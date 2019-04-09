---
title: Implementowanie serwera proxy odnajdywania
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 5d9296d8ba70d4c9e8d8339fa3a032d9c4c62826
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141007"
---
# <a name="implementing-a-discovery-proxy"></a>Implementowanie serwera proxy odnajdywania
W tej sekcji opisano kroki wymagane do wdrożenia serwera proxy odnajdywania. Serwera proxy odnajdywania to autonomiczna usługa, który zawiera repozytorium usług. Klienci mogą wysyłać zapytania serwera proxy odnajdywania można znaleźć wykrywalny usług, które ma informacje o serwerze proxy. Jak serwer proxy jest wypełniana przy użyciu usługi zależy od implementujący. Na przykład serwera proxy odnajdywania można nawiązać połączenie z istniejącym repozytorium usługi i stał się wykrywalny, administrator może użyć interfejsu API zarządzania nad dodaniem usług wykrywalny do serwera proxy lub serwera proxy odnajdywania może korzystać z funkcji anons, aby te informacje aktualizowanie swojej wewnętrznej pamięci podręcznej.  
  
 Implementacja programu WCF zapewnia klas bazowych, które umożliwiają łatwe tworzenie serwera proxy. Korzystanie z tych interfejsów API do tworzenia serwera Proxy odnajdywania na podstawie istniejącego repozytorium.  
  
 Serwera proxy odnajdywania zaimplementowane w tym miejscu jest podobnie jak inne usługi WCF, możesz również stał się wykrywalny serwera proxy odnajdywania i klienci mogą zlokalizować jego punkty końcowe.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: wdrażanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 W tym artykule opisano sposób wdrażania serwera proxy odnajdywania.  
  
 [Instrukcje: implementowanie odnajdywanej usługi rejestrowanej za pomocą serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Opisuje sposób Implementowanie odnajdywanej usługi WCF, rejestrowanej za pomocą serwera proxy odnajdywania.  
  
 [Instrukcje: wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 W tym artykule opisano, jak wdrożyć aplikację kliencką usługi WCF, która używa serwera proxy odnajdywania do wyszukiwania dla usługi.  
  
 [Instrukcje: testowanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Zawiera opis sposobu testowania kodu napisanego w poprzednich tematach trzy.  
  
## <a name="see-also"></a>Zobacz także

- [Odnajdywanie w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
