---
title: "Porady: tworzenie usług systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 7d93f8543b9e6e370827f5a666315d562e28ee76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-windows-services"></a>Porady: tworzenie usług systemu Windows
Podczas tworzenia usługi za pomocą szablonu projektu programu Visual Studio o nazwie **usługi systemu Windows**. Ten szablon automatycznie nie większość zadań można za pomocą odwołań do odpowiednich klas i przestrzenie nazw, konfigurowanie dziedziczenia z klasy podstawowej dla usług, i zastępowanie kilka metod prawdopodobnie do zastąpienia.  
  
> [!WARNING]
>  Szablon projektu usług systemu Windows nie jest dostępna w wersji Express programu Visual Studio.  
  
 Co najmniej Aby utworzyć usługę funkcjonalną należy:  
  
-   Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości.  
  
-   Utwórz niezbędne pliki instalacyjne aplikacji usługi.  
  
-   Zastąpienia i określ kod <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody dostosowania sposoby, w którym działa usługa.  
  
### <a name="to-create-a-windows-service-application"></a>Aby utworzyć aplikację usługi systemu Windows  
  
1.  Utwórz **usługi systemu Windows** projektu.  
  
    > [!NOTE]
    >  Aby uzyskać instrukcje dotyczące zapisywania usługi bez użycia szablonu, zobacz [porady: programowane pisanie usług](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
2.  W **właściwości** ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości usługi.  
  
     ![Ustaw właściwość ServiceName. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  Wartość <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość zawsze musi odpowiadać nazwie rejestrowane w klasach Instalatora. Jeśli zmienisz tę właściwość, należy zaktualizować <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość również klas Instalatora.  
  
3.  Ustaw dowolne z poniższych właściwości, aby określić, jak działają usługi.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True`Aby wskazać, że usługa będzie akceptować żądania przestanie działać; `false` aby zapobiec zatrzymania usługi.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True`Aby wskazać, że chce otrzymywać powiadomienia, gdy komputer, na którym mieszka wyłączany, co go do wywołania usługi <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedury.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True`Aby wskazać, że usługa będzie akceptować żądania, aby wstrzymać lub wznowić uruchomiony; `false` zapobiegające usługi wstrzymać i wznowić.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True`Aby wskazać, że usługa może obsługiwać powiadomień o zmianach stanu zasilania komputera; `false` aby zapobiec powiadomienia o tych zmianach usługi.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True`na zapisywanie wpisów informacyjny w dzienniku zdarzeń aplikacji, gdy usługa wykonuje akcję; `false` wyłączenie tej funkcji. Aby uzyskać więcej informacji, zobacz [porady: dziennika informacji o usługach](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Uwaga:** domyślnie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> ma ustawioną wartość `true`.|  
  
    > [!NOTE]
    >  Gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> lub <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> ustawiono `false`, **Menedżera sterowania usługami** spowoduje wyłączenie odpowiednich opcji menu, aby zatrzymać, wstrzymać lub kontynuować korzystanie z usługi.  
  
4.  Edytor kodu dostępu, a następnie wypełnij przetwarzania dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur.  
  
5.  Zastąpienie innych metod, dla których chcesz zdefiniować funkcji.  
  
6.  Dodanie niezbędnych instalatorów dla aplikacji usługi. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
7.  Tworzenie projektu, wybierając **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
    > [!NOTE]
    >  Nie naciśnij klawisz F5, aby uruchomić projekt — nie można uruchomić projekt usługi w ten sposób.  
  
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
