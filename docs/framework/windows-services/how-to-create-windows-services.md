---
title: 'Porady: tworzenie usług systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 7a529a94edf3a4cf71150c04994d82b8f21eb996
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170954"
---
# <a name="how-to-create-windows-services"></a>Porady: tworzenie usług systemu Windows
Podczas tworzenia usługi można użyć szablonu projektu programu Visual Studio o nazwie **usługi Windows**. Ten szablon automatycznie wykonuje znaczną część pracy za Ciebie, odwołując się do odpowiednich klas i przestrzenie nazw, konfigurując ustawienia dziedziczenia z klasy bazowej dla usług oraz zastępując kilka metod prawdopodobnie chcesz zastąpić.  
  
> [!WARNING]
>  Szablon projektu usług Windows nie jest dostępna w wersji Express programu Visual Studio.  
  
 Jako minimum Aby utworzyć usługę funkcjonalną należy:  
  
-   Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości.  
  
-   Utwórz niezbędne pliki instalacyjne dla aplikacji usługi.  
  
-   Zastąpienia i określ kod <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody dostosowania sposobów, w którym działa usługa.  
  
### <a name="to-create-a-windows-service-application"></a>Aby utworzyć aplikację Windows Service  
  
1.  Tworzenie **usługi Windows** projektu.  
  
    > [!NOTE]
    >  Aby uzyskać instrukcje dotyczące pisania usługi bez użycia szablonu, zobacz [porady: pisanie usług programowo](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
2.  W **właściwości** oknie <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości dla Twojej usługi.  
  
     ![Ustaw właściwość ServiceName. ](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  Wartość <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość musi zawsze odpowiadać nazwie zarejestrowanej w klasach Instalatora. Jeśli zmienisz tę właściwość, należy zaktualizować <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości również w klasach Instalatora.  
  
3.  Ustaw dowolne z następujących właściwości, aby określić, jak będzie działać usługa.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True` Aby wskazać, że usługa akceptuje żądania zatrzymania działania; `false` zapobiega zatrzymanie usługi.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True` Aby wskazać, że usługa chce otrzymywać powiadomienia o wyłączaniu komputera, na którym ją umieszczono, dzięki czemu może wywołać <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedury.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True` Aby wskazać, że usługa akceptuje żądania wstrzymania lub wznowienia działania; `false` aby uniemożliwić wstrzymywanie i wznawianie przez usługę.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True` Aby wskazać, że usługa może obsługiwać powiadomienia o zmianach stanu zasilania komputera `false` zapobiega bycia powiadamianym o tych zmianach usługi.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True` Aby zapisywać wpisy informacyjne w dzienniku zdarzeń aplikacji, gdy usługa wykonuje akcję; `false` Aby wyłączyć tę funkcję. Aby uzyskać więcej informacji, zobacz [jak: informacje dziennika dotyczące usług](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Uwaga:** domyślnie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> ustawiono `true`.|  
  
    > [!NOTE]
    >  Gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> lub <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> są ustawione na `false`, **Menedżera sterowania usługami** spowoduje wyłączenie odpowiednich opcji menu, aby zatrzymać, wstrzymać lub kontynuować usługę.  
  
4.  Wejdź do edytora kodu, a następnie wypełnij przetwarzania dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur.  
  
5.  Zastąpienie wszelkich innych metod, które mają zostać zdefiniowane funkcje.  
  
6.  Dodanie niezbędnych instalatorów dla aplikacji usługi. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
7.  Kompilowanie projektu przez wybranie **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
    > [!NOTE]
    >  Nie wciskaj F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.  
  
8.  Zainstaluj usługę. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: programowane pisanie usług](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [Instrukcje: dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Instrukcje: rejestrowanie informacji o usługach](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Instrukcje: uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Instrukcje: określanie kontekstu zabezpieczeń dla usług](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [Instrukcje: instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
