---
title: Omówienie modelu aplikacji Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 5194810574f594e2c117fef8d8998b7ecebbc981
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591602"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Omówienie modelu aplikacji Visual Basic
Visual Basic udostępnia model dobrze zdefiniowany sterujące zachowaniem aplikacji formularzy systemu Windows: model aplikacji Visual Basic. Ten model zawiera zdarzenia do obsługi aplikacji uruchomienia i zamknięcia, a także zdarzenia połowowe nieobsługiwanych wyjątków. Zapewnia również obsługę do opracowywania aplikacji w jednym wystąpieniu. Model aplikacji jest otwarty, więc deweloperów, które muszą mieć większą kontrolę, można dostosować jego nadpisywalnych metod.  
  
## <a name="uses-for-the-application-model"></a>Używa modelu aplikacji  
 Typowa aplikacja musi wykonać zadania uruchamiania i wyłączania. Na przykład podczas uruchamiania, aplikacji można wyświetlić ekranu powitalnego, nawiązywać połączenia bazy danych, załaduj zapisany stan itd. Po zamknięciu aplikacji go zamknąć połączenia bazy danych, zapisanie bieżącego stanu i tak dalej. Ponadto aplikacji może uruchomić kod z określonych aplikacji przebiega w dół nieoczekiwanie, takie jak podczas nieobsługiwany wyjątek.  
  
 Model aplikacji Visual Basic ułatwia tworzenie *jednego wystąpienia* aplikacji. Pojedyncze wystąpienie aplikacji różni się od normalnego aplikacji w tym tylko jedno wystąpienie aplikacji może być uruchomiony w czasie. Próby uruchomienia inne wystąpienie aplikacji jednego wystąpienia powoduje w oryginalnym wystąpieniu zgłoszonego — za pomocą klasy `StartupNextInstance` zdarzeń — wprowadzone kolejna próba uruchomienia. Powiadomienie zawiera wystąpienie kolejne argumenty wiersza polecenia. Kolejne wystąpienie aplikacji są zamykane, zanim nastąpi inicjowanie.  
  
 Pojedyncze wystąpienie aplikacji uruchamia i sprawdza, czy jest początkowo lub kolejne wystąpienie aplikacji:  
  
-   Jeśli jest pierwsze wystąpienie rozpoczyna się w zwykły sposób.  
  
-   Każda próba uruchomienia aplikacji, podczas wykonywania pierwszego wystąpienia powoduje zachowanie bardzo różnią się. Kolejna próba powiadamia pierwszego wystąpienia o argumenty wiersza polecenia, a następnie natychmiast kończy działanie. Uchwyty pierwszego wystąpienia `StartupNextInstance` zdarzenia w celu określenia co argumenty wiersza polecenia kolejne wystąpienie było i kontynuuje działanie.  
  
     Ten diagram przedstawia, jak kolejne wystąpienia sygnały pierwszego wystąpienia.  
  
     ![Pojedyncze wystąpienie aplikacji obrazu](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 Obsługa `StartupNextInstance` zdarzeń, można kontrolować zachowanie aplikacji jednego wystąpienia. Na przykład program Microsoft Outlook jest zazwyczaj uruchamiany jako pojedyncze wystąpienie aplikacji; gdy program Outlook jest uruchomiony i spróbować ponownie uruchomić program Outlook ponownie, otrzymuje fokus do oryginalnego wystąpienia, ale nie można otworzyć inne wystąpienie.  
  
## <a name="events-in-the-application-model"></a>Zdarzenia w modelu aplikacji  
 W modelu aplikacji znajdują się następujące zdarzenia:  
  
-   **Uruchamianie aplikacji**. Generuje aplikacji <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzeń podczas jej uruchamiania. Dzięki obsłudze tego zdarzenia, możesz dodać kod, który inicjuje aplikacji przed załadowaniem formularza głównego. `Startup` Zdarzeń umożliwia również anulowanie wykonywania aplikacji w tej fazie procesu uruchamiania, w razie potrzeby.  
  
     Można skonfigurować aplikację do wyświetlenia ekranu powitalnego podczas wykonywania kodu uruchamiania aplikacji. Domyślnie model aplikacji pomija to pozostawienie ekranu powitalnego ekranu, gdy albo `/nosplash` lub `-nosplash` zostanie użyty argument wiersza polecenia.  
  
-   **Aplikacje jednego wystąpienia**. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> Zdarzenie jest zgłaszane, gdy rozpoczyna się kolejne wystąpienie pojedyncze wystąpienie aplikacji. Zdarzenie przekazuje argumenty wiersza polecenia kolejne wystąpienia.  
  
-   **Nieobsługiwane wyjątki**. Gdy aplikacja napotka nieobsługiwany wyjątek, zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzeń. Sprawdzić wyjątek i określanie, czy do kontynuowania wykonywania programu obsługi dla tego zdarzenia.  
  
     `UnhandledException` Zdarzenie nie jest wywoływane w pewnych okolicznościach. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
-   **Zmiany łączność sieciową**. W przypadku zmiany dostępności sieci komputera, aplikacja zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> zdarzeń.  
  
     `NetworkAvailabilityChanged` Zdarzenie nie jest wywoływane w pewnych okolicznościach. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
-   **Zamknij aplikację**. Aplikacja udostępnia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzenia sygnalizują, gdy ma zamknięta. W takim przypadku program obsługi, można upewnić się, że operacje aplikacji powinien przeprowadzać — zamykania i zapisywania, na przykład — zostały zakończone. Możesz skonfigurować aplikację po zamknięciu formularza głównego lub zamknąć zamykać tylko wtedy, gdy wszystkich formularzy.  
  
## <a name="availability"></a>Dostępność  
 Domyślnie model aplikacji Visual Basic jest dostępne dla projektów formularzy systemu Windows. Jeśli Konfigurowanie aplikacji w celu użycia obiektu uruchomienia różnych, lub uruchomić kod aplikacji niestandardowej `Sub Main`, następnie obiekt lub klasa może być konieczne podanie implementacja <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> klasy do korzystania z modelu aplikacji. Informacje o zmianie obiektu uruchamiania, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Rozszerzanie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
