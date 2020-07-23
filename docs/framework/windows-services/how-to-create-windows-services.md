---
title: 'Instrukcje: Tworzenie usług systemu Windows'
description: Aby utworzyć usługę, użyj szablonu projektu usługi systemu Windows. Ustaw właściwość ServiceName, Utwórz Instalatory i Zastąp metody OnStart i OnStop.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 6918225e39c15a52710fd0d56342aae869b42325
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925777"
---
# <a name="how-to-create-windows-services"></a>Instrukcje: Tworzenie usług systemu Windows
Podczas tworzenia usługi można użyć szablonu projektu programu Visual Studio o nazwie **Usługa systemu Windows**. Ten szablon automatycznie wykonuje większość pracy za Ciebie, odwołując się do odpowiednich klas i przestrzeni nazw, konfigurując dziedziczenie z klasy podstawowej dla usług i zastępując kilka metod, które mogą zostać przesłonięte.  
  
> [!WARNING]
> Szablon projektu usług systemu Windows nie jest dostępny w wersji Express programu Visual Studio.  
  
 Aby utworzyć usługę funkcjonalną, należy co najmniej:  
  
- Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Właściwość.  
  
- Utwórz niezbędne Instalatory dla aplikacji usługi.  
  
- Przesłoń i określ kod dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metod i, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> Aby dostosować sposób zachowania usługi.  
  
### <a name="to-create-a-windows-service-application"></a>Aby utworzyć aplikację usługi systemu Windows  
  
1. Utwórz projekt **usługi systemu Windows** .  
  
    > [!NOTE]
    > Aby uzyskać instrukcje dotyczące pisania usługi bez użycia szablonu, zobacz [jak: programowe pisanie usług](how-to-write-services-programmatically.md).  
  
2. W oknie **Właściwości** Ustaw <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Właściwość usługi.  
  
     ![Ustaw właściwość ServiceName.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    > Wartość <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> właściwości musi zawsze odpowiadać nazwie zarejestrowanej w klasach Instalatora. W przypadku zmiany tej właściwości należy <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> również zaktualizować Właściwość klas Instalatora.  
  
3. Ustaw dowolne z następujących właściwości, aby określić, jak będzie działać usługa.  
  
    |Właściwość|Ustawienie|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True`, aby wskazać, że usługa będzie akceptować żądania zatrzymania działania; `false`, aby zapobiec zatrzymaniu usługi.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True`, aby wskazać, że usługa chce otrzymywać powiadomienie, gdy komputer, na którym się znajduje, jest zamykana, umożliwiając mu wywołanie <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedury.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True`, aby wskazać, że usługa będzie akceptować żądania wstrzymania lub wznowienia działania. `false`Aby zapobiec wstrzymaniu i wznowieniu usługi.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True`Aby wskazać, że usługa może obsługiwać powiadomienia o zmianach stanu zasilacza komputera; `false`Aby zapobiec powiadamianiu usługi o tych zmianach.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True`w celu zapisania wpisów informacyjnych w dzienniku zdarzeń aplikacji, gdy usługa wykonuje akcję; `false`Aby wyłączyć tę funkcję. Aby uzyskać więcej informacji, zobacz [jak: rejestrować informacje o usługach](how-to-log-information-about-services.md). **Uwaga:**  Domyślnie <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> jest ustawiony na `true` .|  
  
    > [!NOTE]
    > Gdy <xref:System.ServiceProcess.ServiceBase.CanStop%2A> lub <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jest ustawiona na `false` , **Menedżer sterowania usługami** wyłącza odpowiednie opcje menu, aby zatrzymać, wstrzymać lub kontynuować usługę.  
  
4. Uzyskaj dostęp do edytora kodu i Wypełnij odpowiednie przetwarzanie dla <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur i.  
  
5. Zastąp wszystkie inne metody, dla których chcesz zdefiniować funkcję.  
  
6. Dodanie niezbędnych instalatorów dla aplikacji usługi. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów do aplikacji usługi](how-to-add-installers-to-your-service-application.md).  
  
7. Skompiluj projekt, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .  
  
    > [!NOTE]
    > Nie należy naciskać klawisza F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.  
  
8. Zainstaluj usługę. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
- [Instrukcje: Programowane pisanie usług](how-to-write-services-programmatically.md)
- [Instrukcje: Dodawanie instalatorów od aplikacji usług](how-to-add-installers-to-your-service-application.md)
- [Instrukcje: Rejestrowanie informacji o usługach](how-to-log-information-about-services.md)
- [Instrukcje: Uruchamianie usług](how-to-start-services.md)
- [Instrukcje: Określanie kontekstu zabezpieczeń dla usług](how-to-specify-the-security-context-for-services.md)
- [Instrukcje: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md)
- [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
