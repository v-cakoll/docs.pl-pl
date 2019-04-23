---
title: 'Instrukcje: wdrażanie aplikacji integracji modelu COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: fcf525943e6e453253c6f4d3bcfa8a1a08df6909
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343385"
---
# <a name="how-to-deploy-a-com-integration-application"></a>Instrukcje: wdrażanie aplikacji integracji modelu COM+
Po napisaniu aplikacji COM +, integracja, warto wdrożyć ją na innym komputerze. W tym temacie opisano sposób przenoszenia aplikacji integracji modelu COM + z jednego komputera na inny.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Przenoszenie modelu COM + hostowanych integracji aplikacji  
  
1. Upewnij się, że WCF jest zainstalowany na obu komputerach.  
  
2. Eksportowanie aplikacji z komputera A.  
  
3. Importuj aplikację na komputerze B.  
  
4. Ustaw katalog główny aplikacji. Według Konwencji jest to aplikacje %PROGRAMFILES%/ComPlus / {AppGUID}.  
  
5. Skopiuj pliki Application.config i Application.manifest z katalogu głównego aplikacji na maszynie, A do katalogu głównego aplikacji na maszynie B.  
  
6. Edytuj adresy punktów końcowych usługi w pliku Application.config na komputerze B, aby zidentyfikować odpowiedni komputer. Na przykład zmienić `http://machineA/MyService` do `http://machineB/MyService`.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Przenoszenie aplikacji hostowanej w sieci Web integracji  
  
1. Upewnij się, że WCF jest zainstalowany na obu komputerach.  
  
2. Eksportowanie aplikacji z komputera A.  
  
3. Importuj aplikację na komputerze B.  
  
4. Tworzenie vroot usług IIS na maszynie B.  
  
5. Skopiuj plik .svc (componentName.svc) i plik Web.config z głównego katalogu wirtualnego na maszynie, A do nowo utworzonego głównego katalogu wirtualnego na maszynie B.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd integrowania z aplikacjami COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [Instrukcje: Konfigurowanie ustawień usługi COM +](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [Instrukcje: Używanie narzędzia konfiguracji modelu usług COM +](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
