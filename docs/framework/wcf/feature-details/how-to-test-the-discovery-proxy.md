---
title: 'Instrukcje: testowanie serwera proxy odnajdywania'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 13d2e8ca46e634e3b27c8eb967d89d860df1c72d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176283"
---
# <a name="how-to-test-the-discovery-proxy"></a>Instrukcje: testowanie serwera proxy odnajdywania
Jest to czwarta cztery tematy, pokazujący sposób wdrażania serwera proxy odnajdywania. W poprzednim temacie [jak: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), zaimplementować aplikację kliencką usługi WCF, która używa serwera proxy odnajdywania można znaleźć usługi, a następnie wywołuje usługę. W tym temacie opisano sposób weryfikacji serwera proxy odnajdywania, usługi i klienta aplikacji działają zgodnie z oczekiwaniami.  
  
### <a name="run-the-discovery-proxy"></a>Uruchamianie serwera Proxy odnajdywania  
  
1.  Otwórz wiersz polecenia jako administrator.  
  
2.  Może pojawić się okno dialogowe, które jest wyświetlany komunikat: Zapora Windows zablokowała niektórych funkcji tego programu. Jeśli ten komunikat jest wyświetlony, kliknij przycisk **odblokowanie** przycisku.  
  
3.  W wierszu polecenia Uruchom serwera proxy odnajdywania DiscoveryProxy.exe.  
  
4.  Aplikacja powinna wyświetlić następujący tekst: `Proxy started. Hit Enter to exit`.  
  
### <a name="run-the-discoverable-service"></a>Uruchom usługę wykrywalny  
  
1.  Otwórz wiersz polecenia jako administrator.  
  
2.  W wierszu polecenia Uruchom Service.exe odnajdywanej usługi.  
  
3.  DiscoveryProxy.exe powinien być wyświetlany następujący tekst: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>Uruchom aplikację klienta  
  
1.  Otwórz wiersz polecenia.  
  
2.  W wierszu polecenia Uruchom aplikację client.exe.  
  
3.  Po kilku sekundach aplikacja kliencka wyświetla następujący tekst: Łączenie [punktu końcowego usługi].  
  
4.  Service.exe należy następnie wyświetl następujący tekst: Umożliwia pozdrowienia Odebrano żądanie, czy będzie odpowiadać.  
  
5.  Client.exe należy następnie wyświetl następujący tekst: Klient Hello!  
  
### <a name="shut-down-the-applications"></a>Zamknij aplikacje  
  
1.  Zamykanie aplikacji klienta.  
  
2.  Wyłączenie usługi. Serwera proxy odnajdywania wyświetla następujący tekst: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.  
  
3.  Zamknij serwera proxy odnajdywania.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Instrukcje: wdrażanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [Instrukcje: implementowanie odnajdywanej usługi rejestrowanej za pomocą serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [Instrukcje: wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
