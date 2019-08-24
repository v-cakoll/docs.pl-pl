---
title: 'Instrukcje: Tworzenie usług systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 960d30f4e484238e9e7c23741578650a8c3005c8
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987147"
---
# <a name="how-to-create-windows-services"></a>Instrukcje: Tworzenie usług systemu Windows
Podczas tworzenia usługi można użyć szablonu projektu programu Visual Studio o nazwie **Usługa systemu Windows**. Ten szablon automatycznie wykonuje większość pracy za Ciebie, odwołując się do odpowiednich klas i przestrzeni nazw, konfigurując dziedziczenie z klasy podstawowej dla usług i zastępując kilka metod, które mogą zostać przesłonięte.  
  
> [!WARNING]
> Szablon projektu usług systemu Windows nie jest dostępny w wersji Express programu Visual Studio.  
  
 Aby utworzyć usługę funkcjonalną, należy co najmniej:  
  
- <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Ustaw właściwość.  
  
- Utwórz niezbędne Instalatory dla aplikacji usługi.  
  
- Przesłoń i określ kod dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metod <xref:System.ServiceProcess.ServiceBase.OnStop%2A> i, aby dostosować sposób zachowania usługi.  
  
### <a name="to-create-a-windows-service-application"></a>Aby utworzyć aplikację usługi systemu Windows  
  
1. Utwórz projekt **usługi systemu Windows** .  
  
    > [!NOTE]
    > Aby uzyskać instrukcje dotyczące pisania usługi bez użycia szablonu, zobacz [How to: Programowo](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)pisać usługi.  
  
2. W oknie **Właściwości** Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwość usługi.  
  
     ![Ustaw właściwość ServiceName.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    > Wartość <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości musi zawsze odpowiadać nazwie zarejestrowanej w klasach Instalatora. W przypadku zmiany tej właściwości należy również zaktualizować <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Właściwość klas Instalatora.  
  
3. Ustaw dowolne z następujących właściwości, aby określić, jak będzie działać usługa.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True`, aby wskazać, że usługa będzie akceptować żądania zatrzymania działania; `false` , aby zapobiec zatrzymaniu usługi.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True`, aby wskazać, że usługa chce otrzymywać powiadomienie, gdy komputer, na którym się znajduje, jest zamykana, umożliwiając mu wywołanie <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedury.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True`, aby wskazać, że usługa będzie akceptować żądania wstrzymania lub wznowienia działania. `false` aby zapobiec wstrzymaniu i wznowieniu usługi.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True`Aby wskazać, że usługa może obsługiwać powiadomienia o zmianach stanu zasilacza komputera; `false` aby zapobiec powiadamianiu usługi o tych zmianach.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True`w celu zapisania wpisów informacyjnych w dzienniku zdarzeń aplikacji, gdy usługa wykonuje akcję; `false` aby wyłączyć tę funkcję. Aby uzyskać więcej informacji, zobacz [jak: Rejestruj informacje o usługach](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Uwaga:**  Domyślnie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> jest ustawiony na `true`.|  
  
    > [!NOTE]
    > Gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> `false`lub <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jest ustawiona na, **Menedżer sterowania usługami** wyłącza odpowiednie opcje menu, aby zatrzymać, wstrzymać lub kontynuować usługę.  
  
4. Uzyskaj dostęp do edytora kodu i Wypełnij odpowiednie przetwarzanie dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> procedur i. <xref:System.ServiceProcess.ServiceBase.OnStop%2A>  
  
5. Zastąp wszystkie inne metody, dla których chcesz zdefiniować funkcję.  
  
6. Dodanie niezbędnych instalatorów dla aplikacji usługi. Aby uzyskać więcej informacji, zobacz [jak: Dodaj Instalatory do aplikacji](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)usługi.  
  
7. Skompiluj projekt, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .  
  
    > [!NOTE]
    > Nie należy naciskać klawisza F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.  
  
8. Zainstaluj usługę. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)usług.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Instrukcje: Programistyczne zapisywanie usług](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)
- [Instrukcje: Dodawanie instalatorów do aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Instrukcje: Rejestruj informacje o usługach](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [Instrukcje: Uruchom usługi](../../../docs/framework/windows-services/how-to-start-services.md)
- [Instrukcje: Określanie kontekstu zabezpieczeń dla usług](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
- [Instrukcje: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Przewodnik: Tworzenie aplikacji usługi systemu Windows w projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
