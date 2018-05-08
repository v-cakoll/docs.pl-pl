---
title: 'Porady: testowanie serwera Proxy odnajdywania'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 35edbd03e912ae2d9c491afb28dee1c4a3055d14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-test-the-discovery-proxy"></a>Porady: testowanie serwera Proxy odnajdywania
Jest to czwarty cztery tematów, pokazujący sposób wdrożenia serwera proxy odnajdywania. W poprzednim temacie [porady: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), zaimplementowana aplikacji klienta WCF, która używa serwera proxy odnajdywania można znaleźć usługi, a następnie wywołuje usługę. W tym temacie opisano sposób weryfikacji serwera proxy odnajdywania, usługi i klienta aplikacji działają zgodnie z oczekiwaniami.  
  
### <a name="run-the-discovery-proxy"></a>Uruchamianie serwera Proxy odnajdywania  
  
1.  Otwórz wiersz polecenia jako administrator.  
  
2.  Okno dialogowe z informacją, może zostać wyświetlony: Zapora systemu Windows zablokowała niektóre funkcje tego programu. Jeśli ten komunikat zostanie wyświetlony, kliknij przycisk **Odblokuj** przycisku.  
  
3.  W wierszu polecenia Uruchom serwera proxy odnajdywania DiscoveryProxy.exe.  
  
4.  Aplikacja powinna wyświetl następujący tekst: `Proxy started. Hit Enter to exit`.  
  
### <a name="run-the-discoverable-service"></a>Uruchom wykrywalnej usługi  
  
1.  Otwórz wiersz polecenia jako administrator.  
  
2.  W wierszu polecenia Uruchom Service.exe wykrywalnej usługi.  
  
3.  DiscoveryProxy.exe powinien być wyświetlany następujący tekst: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>Uruchom aplikację klienta  
  
1.  Otwórz wiersz polecenia.  
  
2.  W wierszu polecenia Uruchom aplikację client.exe.  
  
3.  Po kilku sekundach aplikacja kliencka będzie wyświetlony następujący tekst: nawiązywanie [punktu końcowego usługi].  
  
4.  Service.exe należy następnie wyświetl następujący tekst: pozdrowienia Odebrano żądanie, I będzie odpowiadać.  
  
5.  Client.exe należy następnie wyświetl następujący tekst: Hello klienta!  
  
### <a name="shut-down-the-applications"></a>Zamknij aplikacje  
  
1.  Zamknij aplikację klienta.  
  
2.  Zatrzymania usługi. Serwera proxy odnajdywania wyświetla następujący tekst: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.  
  
3.  Zamknij serwera proxy odnajdywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Instrukcje: wdrażanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [Instrukcje: implementowanie odnajdywanej usługi rejestrowanej za pomocą serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [Instrukcje: wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
