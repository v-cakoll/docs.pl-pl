---
title: "Instrukcje: Wdrażanie aplikacji integracji modelu COM+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c63478620a2b604d27f2d9d154383cb0bae6b6da
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a>Instrukcje: Wdrażanie aplikacji integracji modelu COM+
Raz napisano aplikacji COM + integration, warto wdrożyć ją na innym komputerze. W tym temacie opisano sposób przenoszenia aplikacji integracji modelu COM + z jednego komputera na inny.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Przenoszenie COM + hostowanej integracji aplikacji  
  
1.  Upewnij się, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest zainstalowany na obu komputerach.  
  
2.  Eksportowanie aplikacji z maszyny A.  
  
3.  Importuj aplikację na komputerze B.  
  
4.  Ustawianie katalogu głównego aplikacji. Według Konwencji jest to aplikacje %PROGRAMFILES%/ComPlus / {AppGUID}.  
  
5.  Skopiuj pliki Application.config i Application.manifest z katalogu głównego aplikacji na komputerze, A do katalogu głównego aplikacji na komputerze B.  
  
6.  Edytuj adresy punktów końcowych usługi w pliku Application.config na komputerze B, aby zidentyfikować odpowiednią maszyny. Na przykład zmień http://machineA/MyService http://machineB/MyService.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Przenoszenie aplikacji hostowanych w sieci Web integracji  
  
1.  Upewnij się, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest zainstalowany na obu komputerach.  
  
2.  Eksportowanie aplikacji z maszyny A.  
  
3.  Importuj aplikację na komputerze B.  
  
4.  Tworzenie głównego katalogu wirtualnego usług IIS na komputerze B.  
  
5.  Skopiuj plik SVC (componentName.svc) i plik Web.config z głównego katalogu wirtualnego na maszynie, A do nowo utworzonej głównego katalogu wirtualnego na maszynie B.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd integrowania z modelu COM + aplikacjami](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [Porady: Konfigurowanie ustawień usług COM +](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [Porady: Użyj narzędzia konfiguracji modelu usług COM +](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
