---
title: Konfigurowanie własnej aplikacji
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 9a1365bb567c552fb087e67a10e48fe0bc2da873
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652036"
---
# <a name="configuring-your-application"></a>Konfigurowanie własnej aplikacji
Windows Communication Foundation (WCF) używa systemu konfiguracji platformy .NET i pozwala na skonfigurowanie usługi w zakresie maszyn i aplikacji.  
  
 Ustawienia konfiguracji zdefiniowane przez architekturę WCF znajdują się w `<system.serviceModel>` grupy sekcji. Aby uzyskać więcej informacji o sposobie konfigurowania usługi WCF zobacz następujące tematy:  
  
- [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
  
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Ustawienia zdefiniowane przez aplikację konfiguracje są definiowane w `<appSettings>` grupy sekcji. Aby uzyskać więcej informacji o ustawieniach aplikacji w plikach konfiguracji .NET, zobacz [ \<appSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Za pomocą edytora konfiguracji  
 WCF [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umożliwia administratorom i deweloperom tworzenie i modyfikowanie ustawień konfiguracji dla usług WCF za pomocą graficznego interfejsu użytkownika. Za pomocą tego narzędzia można zarządzać ustawieniami dla wiązania WCF, zachowań, usług i diagnostyki, bez konieczności bezpośredniego edytowania pliki konfiguracji XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Edycja plików konfiguracji w programie Visual Studio  
 Aby edytować plik konfiguracji projektu usługi WCF w programie Visual Studio, kliknij prawym przyciskiem myszy w **Eksploratora rozwiązań** i wybierz polecenie **Edycja konfiguracji usługi WCF** element menu kontekstowego. Spowoduje to uruchomienie [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Jeśli edytujesz plik konfiguracji projektu usługi sieci Web WCF w programie Visual Studio, klikając go prawym przyciskiem myszy **Eksploratora rozwiązań**, zwróć uwagę, że **Edycja konfiguracji usługi WCF** brakuje w menu kontekstowym. Aby obejść ten problem, kliknij przycisk **narzędzia** menu i wybrać **Edytor konfiguracji usługi WCF**. Po tym, kliknij prawym przyciskiem myszy plik konfiguracji i używać **Edycja konfiguracji usługi WCF** element menu kontekstowego.  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
