---
title: 'Instrukcje: Uruchamianie usług'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: db66e8a264bc0381a2ff4689c4427047a158eb32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336840"
---
# <a name="how-to-start-services"></a>Instrukcje: Uruchamianie usług
Po zainstalowaniu usługi musi być uruchomiona. Początkowo wywołań <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody w klasie usługi. Zazwyczaj <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda definiuje przydatnej pracy, wykona usługi. Po uruchomieniu usługi pozostaje aktywne do czasu jest ręcznie wstrzymana lub zatrzymana.  
  
 Usługi można skonfigurować do uruchamiania automatycznie lub ręcznie. Usługa, która jest uruchamiana automatycznie zostanie uruchomiony, gdy komputer, na którym jest zainstalowany, jest ponownie uruchamiany lub najpierw jest włączona. Użytkownik musi uruchomić usługę, która jest uruchamiana ręcznie.  
  
> [!NOTE]
>  Domyślnie usługi utworzone za pomocą programu Visual Studio są ustawione na uruchamianie ręczne.  
  
 Istnieje kilka sposobów, można ręcznie uruchomić usługę — od **Eksploratora serwera**, z **Menedżera sterowania usługami**, lub z kodu za pomocą składnika o nazwie <xref:System.ServiceProcess.ServiceController>.  
  
 Możesz ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość <xref:System.ServiceProcess.ServiceInstaller> klasę, aby określić, czy należy uruchomić usługę ręcznie lub automatycznie.  
  
### <a name="to-specify-how-a-service-should-start"></a>Aby określić, jak usługa powinna być uruchamiana  
  
1. Po utworzeniu usługi, dodanie niezbędnych instalatorów dla niego. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2. W Projektancie kliknij Instalatora usługi dla usługi, którą pracujesz.  
  
3. W **właściwości** oknie <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwości do jednej z następujących czynności:  
  
    |Aby zainstalować usługę|Ustaw tę wartość|  
    |----------------------------------|--------------------|  
    |Po ponownym uruchomieniu komputera|**Automatyczne**|  
    |Po uruchomieniu usługi w jawna Akcja użytkownika|**Ręcznie**|  
  
    > [!TIP]
    >  Aby zapobiec sytuacji, w której usługa jest uruchomiona na wszystkich, możesz ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwości **wyłączone**. Możesz to zrobić, jeśli chcesz ponownie uruchomić serwer, a chcesz zaoszczędzić czas, co uniemożliwia usług, które zwykle zaczyna się od uruchamiania.  
  
    > [!NOTE]
    >  Po zainstalowaniu usługi można zmienić tych i innych właściwości.  
  
     Istnieje kilka sposobów, które można uruchomić usługi, która ma jego <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> zestawu procesu **ręczne** — od **Eksploratora serwera**, z **Menedżera sterowania usługami systemu Windows**, lub z kodu. Ważne jest, aby należy pamiętać, nie wszystkie te metody faktycznie uruchomić usługi w kontekście **Menedżera sterowania usługami**; **Eksploratora serwera** i programowe metod uruchamiania usługi faktycznie manipulowania kontrolera.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>Aby ręcznie uruchomić usługę z poziomu Eksploratora serwera  
  
1. W **Eksploratora serwera**, dodać serwer, jeśli go nie ma już na liście. Aby uzyskać więcej informacji, zobacz jak: Uzyskiwanie dostępu oraz inicjowanie Eksploratora bazy danych Eksploratora serwera.  
  
2. Rozwiń **usług** węzła, a następnie znajdź odpowiednią usługę, aby uruchomić.  
  
3. Kliknij prawym przyciskiem myszy nazwę usługi, a następnie kliknij przycisk **Start**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>Aby ręcznie uruchomić usługę z Menedżera sterowania usługami  
  
1. Otwórz **Menedżera sterowania usługami** , wykonując jedną z następujących czynności:  
  
    -   Windows XP lub 2000 Professional, kliknij prawym przyciskiem myszy **Mój komputer** na pulpicie, a następnie kliknij **Zarządzaj**. W oknie dialogowym Rozwiń **usługi i aplikacje** węzła.  
  
         \- lub —  
  
    -   W systemie Windows Server 2003 i Windows 2000 Server, kliknij przycisk **Start**, wskaż polecenie **programy**, kliknij przycisk **narzędzia administracyjne**, a następnie kliknij przycisk **usług**.  
  
        > [!NOTE]
        >  W Windows NT 4.0, możesz otworzyć to okno dialogowe z **Panelu sterowania**.  
  
     Powinien zostać wyświetlony na liście usługi **usług** okna.  
  
2. Wybierz usługę na liście, kliknij go prawym przyciskiem myszy, a następnie kliknij **Start**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Aby ręcznie uruchomić usługę z kodu  
  
1. Utwórz wystąpienie obiektu <xref:System.ServiceProcess.ServiceController> klasy, a następnie skonfigurować go do interakcji z usługą, którą chcesz administrować.  
  
2. Wywołaj <xref:System.ServiceProcess.ServiceController.Start%2A> metodę, aby uruchomić usługę.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Instrukcje: Tworzenie usług Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Instrukcje: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
