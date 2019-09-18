---
title: 'Instrukcje: Dodawanie instalatorów od aplikacji usług'
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
ms.openlocfilehash: 99e2376c50f0b47cc21002b2926818707188805e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053652"
---
# <a name="how-to-add-installers-to-your-service-application"></a>Instrukcje: Dodawanie instalatorów od aplikacji usług
Program Visual Studio jest dostarczany ze składnikami instalacji, które mogą instalować zasoby skojarzone z aplikacjami usługi. Składniki instalacji rejestrują poszczególne usługi w systemie, w którym jest instalowana, i pozwalają menedżerowi sterowania usługami znać, że usługa istnieje. Podczas pracy z aplikacją usługi można wybrać łącze w okno Właściwości, aby automatycznie dodać odpowiednie Instalatory do projektu.  
  
> [!NOTE]
> Wartości właściwości usługi są kopiowane z klasy usługi do klasy Instalatora. W przypadku zaktualizowania wartości właściwości w klasie usług nie są one automatycznie aktualizowane w instalatorze.  
  
 Po dodaniu Instalatora do projektu w projekcie zostanie utworzona nowa klasa (która domyślnie nosi nazwę `ProjectInstaller`), a w nim zostaną utworzone wystąpienia odpowiednich składników instalacyjnych. Ta klasa działa jako punkt centralny dla wszystkich składników instalacji potrzebnych przez projekt. Jeśli na przykład dodasz drugą usługę do aplikacji i klikniesz link Dodaj Instalatora, nie zostanie utworzona druga Klasa Instalatora; Zamiast tego niezbędny dodatkowy składnik instalacyjny dla drugiej usługi jest dodawany do istniejącej klasy.  
  
 Nie trzeba wykonywać żadnych specjalnych kodowania w ramach instalatorów, aby zapewnić prawidłowe działanie usług. Jednak czasami trzeba zmodyfikować zawartość instalatorów, jeśli trzeba dodać specjalną funkcjonalność do procesu instalacji.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-installers-to-your-service-application"></a>Aby dodać Instalatory do aplikacji usługi  
  
1. W **Eksplorator rozwiązań**dostęp do widoku **projektu** dla usługi, dla której chcesz dodać składnik instalacji.  
  
2. Kliknij tło projektanta, aby wybrać samą usługę, a nie jej zawartość.  
  
3. Korzystając z projektanta w fokusie, kliknij prawym przyciskiem myszy, a następnie kliknij polecenie **Dodaj Instalatora**.  
  
     Nowa klasa, `ProjectInstaller`i dwa składniki instalacyjne, <xref:System.ServiceProcess.ServiceProcessInstaller> i <xref:System.ServiceProcess.ServiceInstaller>, są dodawane do projektu, a wartości właściwości usługi są kopiowane do składników programu.  
  
4. Kliknij składnik i sprawdź, czy wartość <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwości jest ustawiona na taką samą wartość jak <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość w samej usłudze. <xref:System.ServiceProcess.ServiceInstaller>  
  
5. Aby określić, jak zostanie uruchomiona usługa, kliknij <xref:System.ServiceProcess.ServiceInstaller> składnik i <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> ustaw właściwość na odpowiednią wartość.  
  
    |Wartość|Wynik|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Usługa musi zostać uruchomiona ręcznie po zakończeniu instalacji. Aby uzyskać więcej informacji, zobacz [jak: Uruchom usługi](how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Usługa rozpocznie się za każdym razem, gdy komputer zostanie uruchomiony ponownie.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Nie można uruchomić usługi.|  
  
6. Aby określić kontekst zabezpieczeń, w którym zostanie uruchomiona usługa, kliknij <xref:System.ServiceProcess.ServiceProcessInstaller> składnik i ustaw odpowiednie wartości właściwości. Aby uzyskać więcej informacji, zobacz [jak: Określ kontekst zabezpieczeń usług](how-to-specify-the-security-context-for-services.md).  
  
7. Zastąp wszystkie metody, dla których należy wykonać przetwarzanie niestandardowe.  
  
8. Wykonaj kroki od 1 do 7 dla każdej dodatkowej usługi w projekcie.  
  
    > [!NOTE]
    > Dla każdej dodatkowej usługi w projekcie należy dodać dodatkowy <xref:System.ServiceProcess.ServiceInstaller> składnik do `ProjectInstaller` klasy projektu. <xref:System.ServiceProcess.ServiceProcessInstaller> Składnik dodany w kroku 3 współdziała ze wszystkimi instalacjami poszczególnych usług w projekcie.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
- [Instrukcje: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md)
- [Instrukcje: Uruchom usługi](how-to-start-services.md)
- [Instrukcje: Określanie kontekstu zabezpieczeń dla usług](how-to-specify-the-security-context-for-services.md)
