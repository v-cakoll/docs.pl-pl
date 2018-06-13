---
title: Konfigurowanie własnej aplikacji
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 1844c20ef961f191fb667e31d548518b193a7134
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803653"
---
# <a name="configuring-your-application"></a>Konfigurowanie własnej aplikacji
Windows Communication Foundation (WCF) używa systemu konfiguracji platformy .NET i pozwala na skonfigurowanie usługi w zakresie komputera i aplikacji.  
  
 Konfiguracja ustawień zdefiniowanych przez WCF znajdują się w `<system.serviceModel>` grupy sekcji. Aby uzyskać więcej informacji na temat konfigurowania usługi WCF zobacz następujące tematy:  
  
-   [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Ustawienia zdefiniowane przez aplikację konfiguracje są definiowane w `<appSettings>` grupy sekcji. Aby uzyskać więcej informacji o ustawieniach aplikacji w plikach konfiguracji platformy .NET, zobacz [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Za pomocą edytora konfiguracji  
 Usługi WCF[narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umożliwia administratorów i deweloperów, tworzenie i modyfikowanie ustawień konfiguracji dla usług WCF za pomocą graficznego interfejsu użytkownika. Z tego narzędzia można zarządzać ustawieniami dla wiązania WCF, zachowania, usług i diagnostyki bez konieczności bezpośredniego edytowania plików XML konfiguracji.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Edycję plików konfiguracyjnych w programie Visual Studio  
 Aby edytować plik konfiguracji projektu usługi WCF w programie Visual Studio, kliknij prawym przyciskiem myszy w **Eksploratora rozwiązań** i wybierz polecenie **Edycja konfiguracji usługi WCF** elementu menu kontekstowego. Spowoduje to uruchomienie [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Po zmodyfikowaniu pliku konfiguracyjnego projektu usługi sieci Web WCF w programie Visual Studio, klikając prawym przyciskiem myszy w **Eksploratora rozwiązań**, zwróć uwagę, że **Edycja konfiguracji WCF** brakuje elementu menu kontekstowego. Obejście tego problemu, kliknij przycisk **narzędzia** menu i wybierz polecenie **Edytor konfiguracji usługi WCF**. Po tym, kliknij prawym przyciskiem myszy plik konfiguracji i użyj **Edycja konfiguracji WCF** elementu menu kontekstowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
