---
title: 'Porady: testowanie serwera Proxy odnajdywania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9c721a0ef357feeb4df540cb5b7b74d067dc807
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-test-the-discovery-proxy"></a>Porady: testowanie serwera Proxy odnajdywania
Jest to czwarty cztery tematów, pokazujący sposób wdrożenia serwera proxy odnajdywania. W poprzednim temacie [porady: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), zostanie zaimplementowana [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji klienckiej, która używa serwera proxy odnajdywania można znaleźć usługi, a następnie wywołuje Usługa. W tym temacie opisano sposób weryfikacji serwera proxy odnajdywania, usługi i klienta aplikacji działają zgodnie z oczekiwaniami.  
  
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
 [Porady: Implementowanie serwera Proxy odnajdywania](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [Porady: Implementowanie wykrywalnej usługi, który rejestruje przy użyciu serwera Proxy odnajdywania](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [Porady: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
