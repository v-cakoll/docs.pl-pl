---
title: 'Porady: dodawanie instalatorów od aplikacji usług'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
author: ghogen
manager: douge
ms.openlocfilehash: 77f41e696fed3d33282b6437e99129fda9e209e9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553345"
---
# <a name="how-to-add-installers-to-your-service-application"></a>Porady: dodawanie instalatorów od aplikacji usług
Program Visual Studio jest dostarczany składników instalacji, które można zainstalować zasoby skojarzone ze swoimi aplikacjami usługi. Składniki instalacyjne zarejestrować pojedynczą usługę w systemie, do którego jest w trakcie instalacji i umożliwić Menedżera sterowania usługami wiedzieć, że Usługa istnieje. Podczas pracy z aplikacją usługi, możesz wybrać link w oknie dialogowym właściwości, aby automatycznie dodać odpowiednie pliki instalacyjne do projektu.  
  
> [!NOTE]
>  Wartości właściwości dla usługi są kopiowane z klasy usługi do klasy Instalatora. Po aktualizacji wartości właściwości w klasie usługi, nie są one automatycznie aktualizowane w Instalatorze.  
  
 Po dodaniu Instalatora do projektu nową klasę (która domyślnie jest o nazwie `ProjectInstaller`) jest tworzony w projekcie i wystąpienia instalacji odpowiednie składniki są tworzone w obrębie tej. Ta klasa działa jako centralny punkt dla wszystkich składników instalacji wymaga projektu. Na przykład jeśli dodać drugą usługę do aplikacji i kliknij łącze Dodaj Instalatora, nie jest tworzony drugi klasa Instalatora; Zamiast tego składnika instalacyjnymi dodatkowe usługi drugi zostanie dodany do istniejącej klasy.  
  
 Nie musisz wykonać specjalne pisania w ramach programów instalacyjnych, aby poprawnie zainstalować usług. Jednak czasami konieczne może być zmodyfikowania zawartości pliki instalacyjne, jeśli trzeba dodać specjalne funkcje do procesu instalacji.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-installers-to-your-service-application"></a>Aby dodać instalatorów od aplikacji usług  
  
1.  W **Eksploratora rozwiązań**, dostępu **projektowania** widoku dla usługi, dla którego chcesz dodać jako składnik instalacji.  
  
2.  Kliknij tło projektanta aby wybrać usługę, a nie jakąkolwiek jej zawartość.  
  
3.  Za pomocą projektanta w fokus, kliknij prawym przyciskiem myszy, a następnie kliknij **Dodaj Instalatora**.  
  
     Nowa klasa `ProjectInstaller`i dwa składniki: Instalacja <xref:System.ServiceProcess.ServiceProcessInstaller> i <xref:System.ServiceProcess.ServiceInstaller>, są dodawane do projektu i wartości właściwości dla usługi są kopiowane do składników.  
  
4.  Kliknij przycisk <xref:System.ServiceProcess.ServiceInstaller> składnika i sprawdź, czy wartość <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość jest ustawiona na taką samą wartość jak <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość samą usługę.  
  
5.  Aby określić, jak można uruchomić usługi, kliknij przycisk <xref:System.ServiceProcess.ServiceInstaller> składnika i ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość odpowiednią wartość.  
  
    |Wartość|Wynik|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Usługę można ręcznie uruchomić po zakończeniu instalacji. Aby uzyskać więcej informacji, zobacz [porady: uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Usługa zostanie uruchomiona przez siebie przy każdym ponownym uruchomieniu komputera.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Nie można uruchomić usługi.|  
  
6.  Aby ustalić kontekstu zabezpieczeń, w którym będzie uruchamiany usługi, kliknij przycisk <xref:System.ServiceProcess.ServiceProcessInstaller> składnika i ustawianie wartości odpowiednich właściwości. Aby uzyskać więcej informacji, zobacz [porady: Określanie kontekstu zabezpieczeń dla usług](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).  
  
7.  Zastąp wszystkie metody, dla których trzeba wykonać niestandardowych.  
  
8.  Wykonaj kroki od 1 do 7 dla każdego dodatkowe usługi w projekcie.  
  
    > [!NOTE]
    >  Dla każdej dodatkowej usługi w projekcie, należy dodać kolejny <xref:System.ServiceProcess.ServiceInstaller> składnika w projekcie `ProjectInstaller` klasy. <xref:System.ServiceProcess.ServiceProcessInstaller> Składnika dodanej w kroku 3 pracuje ze wszystkimi programów instalacyjnych poszczególnych usług w projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Instrukcje: uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Instrukcje: określanie kontekstu zabezpieczeń dla usług](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
