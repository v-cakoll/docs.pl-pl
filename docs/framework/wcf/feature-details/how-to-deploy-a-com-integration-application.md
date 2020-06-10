---
title: 'Instrukcje: Wdrażanie aplikacji integracji modelu COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: b4ae7f730296d54debc1cf2971b61e5700503430
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595430"
---
# <a name="how-to-deploy-a-com-integration-application"></a>Instrukcje: Wdrażanie aplikacji integracji modelu COM+
Po napisaniu aplikacji integracji modelu COM+ warto ją wdrożyć na innym komputerze. W tym temacie opisano sposób przenoszenia aplikacji integracji modelu COM+ z jednego komputera na inny.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Przemieszczanie hostowanej aplikacji integracji modelu COM+  
  
1. Upewnij się, że platforma WCF jest zainstalowana na obu komputerach.  
  
2. Wyeksportuj aplikację z komputera A.  
  
3. Zaimportuj aplikację na komputerze B.  
  
4. Ustaw katalog główny aplikacji. Zgodnie z Konwencją jest to% PROGRAMFILES%/ComPlus Applications/{AppGUID}.  
  
5. Skopiuj pliki Application. config i Application. manifest z katalogu głównego aplikacji na komputerze A do katalogu głównego aplikacji na komputerze B.  
  
6. Aby zidentyfikować odpowiednią maszynę, Edytuj adresy punktów końcowych usługi w pliku Application. config na komputerze B. Na przykład zmień `http://machineA/MyService` na `http://machineB/MyService` .  
  
### <a name="moving-a-web-hosted-integration-application"></a>Przeniesienie aplikacji integracji hostowanej w sieci Web  
  
1. Upewnij się, że platforma WCF jest zainstalowana na obu komputerach.  
  
2. Wyeksportuj aplikację z komputera A.  
  
3. Zaimportuj aplikację na komputerze B.  
  
4. Utwórz katalog główny usług IIS na komputerze B.  
  
5. Skopiuj plik SVC (ComponentName. svc) i plik Web. config z katalogu głównego na komputerze A do nowo utworzonego elementu głównego na komputerze B.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd integrowania z aplikacjami COM+](integrating-with-com-plus-applications-overview.md)
- [Instrukcje: konfigurowanie ustawień usługi COM+](how-to-configure-com-service-settings.md)
- [Instrukcje: używanie narzędzia konfiguracji modelu usług COM+](how-to-use-the-com-service-model-configuration-tool.md)
