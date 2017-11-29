---
title: "Porady: dodawanie instalatorów od aplikacji usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 8137e41f92335849916dfc9e9ce72afeb186e73c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-installers-to-your-service-application"></a>Porady: dodawanie instalatorów od aplikacji usług
Program Visual Studio jest dostarczany instalacji składników, które można zainstalować zasoby skojarzone z usługi aplikacji. Instalacja składników zarejestrować poszczególnych usług w systemie, do której jest instalowany i umożliwić Menedżera sterowania usługami wiedzieć, czy Usługa istnieje. Podczas pracy z aplikacją usługi, możesz wybrać link w oknie właściwości można automatycznie dodać odpowiednie pliki instalacyjne do projektu.  
  
> [!NOTE]
>  Wartości właściwości dla usługi są kopiowane z klasy usługi do klasy Instalatora. Po aktualizacji wartości właściwości w klasie usługi, nie są one automatycznie aktualizowane w Instalatorze.  
  
 Po dodaniu Instalatora do projektu, nową klasę (, która domyślnie nosi nazwę `ProjectInstaller`) jest tworzony w projekcie i wystąpień instalacji odpowiednie składniki są tworzone w niej. Ta klasa działa jako centralny punkt dla wszystkich składników instalacji musi projektu. Na przykład jeśli dodać drugi usług do aplikacji i kliknij link Dodaj Instalatora, drugi klasa Instalatora nie jest tworzona; Zamiast tego składnika niezbędne dodatkowe instalacji drugiego usługi jest dodawany do istniejącej klasy.  
  
 Nie trzeba wykonać specjalne pisania kodu w ramach programów instalacyjnych, aby poprawnie zainstalować usługi. Jednak czasami konieczne może być modyfikować zawartość pliki instalacyjne, jeśli konieczne jest dodanie specjalne funkcje do procesu instalacji.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-installers-to-your-service-application"></a>Aby dodać instalatorów od aplikacji usług  
  
1.  W **Eksploratora rozwiązań**, dostępu **projekt** widoku dla usługi, dla której chcesz dodać składnik instalacji.  
  
2.  Kliknij przycisk tła projektanta, aby wybrać usługi, a nie wszystkich jego zawartość.  
  
3.  Przy użyciu projektanta fokus, kliknij prawym przyciskiem myszy, a następnie kliknij polecenie **dodać Instalatora**.  
  
     Nowa klasa `ProjectInstaller`i dwa składniki instalacji <xref:System.ServiceProcess.ServiceProcessInstaller> i <xref:System.ServiceProcess.ServiceInstaller>, zostaną dodane do projektu i wartości właściwości dla usługi są kopiowane do składników.  
  
4.  Kliknij przycisk <xref:System.ServiceProcess.ServiceInstaller> składnika i sprawdź, czy wartość <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwość ma ustawioną taką samą wartość jak <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> właściwości na samą usługę.  
  
5.  Aby określić, jak można uruchomić usługi, kliknij przycisk <xref:System.ServiceProcess.ServiceInstaller> składnika i ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> na odpowiednią wartość.  
  
    |Wartość|Wynik|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Usługa musi być uruchomiona ręcznie po zakończeniu instalacji. Aby uzyskać więcej informacji, zobacz [porady: Uruchom usługi](../../../docs/framework/windows-services/how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Przy każdym ponownym uruchomieniu komputera, usługa zostanie uruchomiona przez samego siebie.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Nie można uruchomić usługi.|  
  
6.  Aby ustalić kontekst zabezpieczeń, w którym będzie uruchamiany usługi, kliknij przycisk <xref:System.ServiceProcess.ServiceProcessInstaller> składnika i ustawianie wartości odpowiednich właściwości. Aby uzyskać więcej informacji, zobacz [porady: Określanie kontekstu zabezpieczeń dla usług](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).  
  
7.  Zastąp wszystkie metody, dla których należy wykonać czynności niestandardowe.  
  
8.  Wykonaj kroki od 1 do 7 dla każdej dodatkowej usługi w projekcie.  
  
    > [!NOTE]
    >  Dla każdej dodatkowej usługi w projekcie, należy dodać dodatkowe <xref:System.ServiceProcess.ServiceInstaller> składnika w projekcie `ProjectInstaller` klasy. <xref:System.ServiceProcess.ServiceProcessInstaller> Element został dodany w kroku 3 współdziała z wszystkich instalatorów poszczególnych usług w projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Porady: uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Porady: Określanie kontekstu zabezpieczeń dla usług](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
