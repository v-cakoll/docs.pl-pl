---
title: 'Instrukcje: testowanie serwera proxy odnajdywania'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 78921d0a26f1116c87c2931b1472a161d6fed145
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592817"
---
# <a name="how-to-test-the-discovery-proxy"></a>Instrukcje: testowanie serwera proxy odnajdywania
Jest to czwarte z czterech tematów, w których pokazano, jak zaimplementować serwer proxy odnajdywania. W poprzednim temacie [jak: implementowanie aplikacji klienckiej, która używa serwera proxy odnajdywania w celu znalezienia usługi](client-app-discovery-proxy-to-find-a-service.md), zaimplementowano aplikację kliencką WCF, która używa serwera proxy odnajdywania do znajdowania usługi, a następnie wywołuje usługę. W tym temacie opisano sposób sprawdzania, czy serwer proxy odnajdywania, usługa i aplikacja kliencka działają zgodnie z oczekiwaniami.  
  
### <a name="run-the-discovery-proxy"></a>Uruchom serwer proxy odnajdywania  
  
1. Otwórz wiersz polecenia jako administrator.  
  
2. Może pojawić się okno dialogowe z informacją: Zapora systemu Windows zablokowała niektóre funkcje tego programu. Jeśli zobaczysz ten komunikat, kliknij przycisk **odblokowywanie** .  
  
3. W wierszu polecenia Uruchom serwer proxy odnajdywania, obiektu DiscoveryProxy. exe.  
  
4. Aplikacja powinna wyświetlać następujący tekst: `Proxy started. Hit Enter to exit` .  
  
### <a name="run-the-discoverable-service"></a>Uruchamianie usługi wykrywalnej  
  
1. Otwórz wiersz polecenia jako administrator.  
  
2. W wierszu polecenia Uruchom usługę wykrywalną Service. exe.  
  
3. Obiektu DiscoveryProxy. exe powinien wyświetlać następujący tekst: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>Uruchom aplikację kliencką  
  
1. Otwórz wiersz polecenia.  
  
2. W wierszu polecenia Uruchom aplikację Client. exe.  
  
3. Po kilku sekundach aplikacja kliencka wyświetli następujący tekst: łączenie z [Service-Endpoint].  
  
4. Program Service. exe powinien następnie wyświetlić następujący tekst: Odebrano żądanie powitania.  
  
5. Program Client. exe powinien następnie wyświetlić następujący tekst: Hello Client!  
  
### <a name="shut-down-the-applications"></a>Zamykanie aplikacji  
  
1. Zamknij aplikację kliencką.  
  
2. Zamknij usługę. Serwer proxy odnajdywania wyświetla następujący tekst: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******` .  
  
3. Zamknij serwer proxy odnajdywania.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie odnajdywania WCF](wcf-discovery-overview.md)
- [Instrukcje: Wdrażanie serwera proxy odnajdywania](how-to-implement-a-discovery-proxy.md)
- [Instrukcje: implementowanie odnajdywanej usługi rejestrowanej za pomocą serwera proxy odnajdywania](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [Instrukcje: wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania](client-app-discovery-proxy-to-find-a-service.md)
