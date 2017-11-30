---
title: "Porady: uruchamianie usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e4f93da8a2a5be00d798d64caba0f54bfd71ceb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-start-services"></a>Porady: uruchamianie usług
Po zainstalowaniu usługi musi być uruchomiona. Uruchamianie wywołania <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody w klasie usługi. Zazwyczaj <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda definiuje przydatne pracę, wykona usługi. Po uruchomieniu usługi pozostanie aktywne do czasu jest ręcznie wstrzymana lub zatrzymana.  
  
 Usługi można zainstalowane do uruchamiania automatycznie lub ręcznie. Usługa, która jest uruchamiana automatycznie zostanie uruchomiony, gdy komputer, na którym jest zainstalowany jest ponowny rozruch lub włączany po raz pierwszy. Użytkownik musi uruchomić usługę, która jest uruchamiana ręcznie.  
  
> [!NOTE]
>  Domyślnie usługi utworzone za pomocą [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] są ustawione na uruchamianie ręczne.  
  
 Istnieje kilka sposobów, można ręcznie uruchomić usługę — od **Eksploratora serwera**, z **Menedżera sterowania usługami**, lub z kodu za pomocą składnika o nazwie <xref:System.ServiceProcess.ServiceController>.  
  
 Możesz ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość <xref:System.ServiceProcess.ServiceInstaller> klasę, aby określić, czy należy uruchomić usługę ręcznie lub automatycznie.  
  
### <a name="to-specify-how-a-service-should-start"></a>Aby określić, jak powinna zaczynać się usługi  
  
1.  Po utworzeniu usługi, należy dodać wymagane pliki instalacyjne dla niego. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  W Projektancie kliknij Instalatora usługi dla usługi, którą użytkownik pracuje z.  
  
3.  W **właściwości** ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwości do jednej z następujących czynności:  
  
    |Aby zainstalować usługi|Ustaw tę wartość|  
    |----------------------------------|--------------------|  
    |Po ponownym uruchomieniu komputera|**Automatyczne**|  
    |Po uruchomieniu usługi przez jawną akcję użytkownika|**Ręcznie**|  
  
    > [!TIP]
    >  Aby zapobiec ogóle uruchomić usługi, można ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwości **wyłączone**. Można to zrobić, jeśli mają być ponownego rozruchu serwera i aby zaoszczędzić czas, zapobiegając usług, które zwykle zaczyna się od uruchamiania.  
  
    > [!NOTE]
    >  Po zainstalowaniu usługi można zmienić tych i innych właściwości.  
  
     Istnieje kilka sposobów, można uruchomić usługę, która ma jego <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> procesu ustawioną **ręcznego** — od **Eksploratora serwera**, z **Menedżera sterowania usługami systemu Windows**, lub z kodu. Należy pamiętać, nie wszystkie z tych metod faktycznie uruchomić usługę w kontekście jest **Menedżera sterowania usługami**; **Eksploratora serwera** i programowe metody uruchamiania usługi faktycznie manipulowania kontrolera.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>Aby ręcznie uruchomić usługę z Eksploratora serwera  
  
1.  W **Eksploratora serwera**, dodać serwer, jeśli go nie ma już na liście. Aby uzyskać więcej informacji, zobacz porady: dostęp i zainicjować Eksploratora bazy danych Eksploratora serwera.  
  
2.  Rozwiń węzeł **usług** węzeł, a następnie zlokalizuj usługi chcesz uruchomić.  
  
3.  Kliknij prawym przyciskiem myszy nazwę usługi, a następnie kliknij przycisk **Start**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>Aby ręcznie uruchomić usługę od menedżera kontroli usług  
  
1.  Otwórz **Menedżera sterowania usługami** wykonując jedną z następujących czynności:  
  
    -   W systemach Windows XP i 2000 Professional, kliknij prawym przyciskiem myszy **Mój komputer** na pulpicie, a następnie kliknij **Zarządzaj**. W oknie dialogowym Rozwiń **usługi i aplikacje** węzła.  
  
         \-lub -  
  
    -   W systemie Windows Server 2003 i Windows 2000 Server kliknij **Start**, wskaż **programy**, kliknij przycisk **narzędzia administracyjne**, a następnie kliknij przycisk **usług**.  
  
        > [!NOTE]
        >  W systemie Windows NT 4.0, możesz otworzyć to okno dialogowe z **Panelu sterowania**.  
  
     Powinien zostać wyświetlony na liście usługi **usług** okna.  
  
2.  Wybierz usługę na liście, kliknij go prawym przyciskiem myszy, a następnie kliknij przycisk **Start**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Aby ręcznie uruchomić usługę z kodu  
  
1.  Utwórz wystąpienie <xref:System.ServiceProcess.ServiceController> klasy, a następnie skonfigurować go do interakcji z usługą, którą chcesz administrować.  
  
2.  Wywołanie <xref:System.ServiceProcess.ServiceController.Start%2A> metodę, aby uruchomić usługę.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Porady: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Porady: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
