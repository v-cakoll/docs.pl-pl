---
title: Omówienie modelu aplikacji Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 02cc71dbda47d078284d9a2ec07538dfa063ac75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014153"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Omówienie modelu aplikacji Visual Basic
Dobrze zdefiniowany model zapewnia Visual Basic sterujące zachowaniem aplikacji Windows Forms: model aplikacji Visual Basic. Ten model zawiera zdarzenia do obsługi aplikacji uruchamiania i zamykania, a także zdarzenia dla połowowe nieobsłużonych wyjątków. Zapewnia również obsługę do tworzenia aplikacji w jednym wystąpieniu. Model aplikacji jest rozszerzalny, dzięki czemu deweloperzy, którzy potrzebują więcej kontroli można dostosować jego możliwym do zastąpienia metody.  
  
## <a name="uses-for-the-application-model"></a>Zastosowań Model aplikacji  
 Typowa aplikacja potrzebuje do wykonywania zadań uruchamiania i zamykania. Na przykład podczas uruchamiania, aplikacja może wyświetlić ekran powitalny, tworzenie połączeń bazy danych, obciążenia zapisanego stanu i tak dalej. Po zamknięciu aplikacji go zamknąć połączenia z bazą danych, zapisanie bieżącego stanu i tak dalej. Ponadto aplikacja może wykonać określonego kodu aplikacji w sytuacji nagłego wyłączenia dół nieoczekiwanie, takie jak podczas nieobsługiwany wyjątek.  
  
 Model aplikacji Visual Basic można łatwo utworzyć *jednego wystąpienia* aplikacji. Aplikacja o pojedynczym wystąpieniu różni się w z normalnym aplikacji, w tym tylko jedno wystąpienie aplikacji może działać w danym momencie. Próby uruchomienia inne wystąpienie aplikacji jednego wystąpienia powoduje w oryginalnym wystąpieniu bycia powiadamianym — poprzez `StartupNextInstance` zdarzeń — zgłaszający kolejna próba uruchomienia. Powiadomienie zawiera argumenty wiersza polecenia kolejne wystąpienia. Następnie zamknięto kolejne wystąpienie aplikacji, zanim nastąpi inicjowanie.  
  
 Aplikacja o pojedynczym wystąpieniu rozpoczyna się i sprawdza, czy jest pierwsze wystąpienie lub kolejne wystąpienie aplikacji:  
  
- Jeśli jest pierwsze wystąpienie, rozpoczyna się w zwykły sposób.  
  
- Każda próba uruchomienia aplikacji, podczas pierwszego wystąpienia powoduje zachowanie bardzo różnią się. Kolejna próba powiadamia pierwszego wystąpienia o argumenty wiersza polecenia, a następnie natychmiast kończy działanie. Uchwyty pierwszego wystąpienia `StartupNextInstance` zdarzenie, aby określić, co kolejne wystąpienie argumenty wiersza polecenia zostały i kontynuuje działanie.  
  
     Ten diagram przedstawia, jak kolejne wystąpienie sygnalizuje pierwsze wystąpienie:  
  
     ![Diagram przedstawiający obrazu aplikacji pojedynczego wystąpienia.](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 Obsługa `StartupNextInstance` zdarzenia, można kontrolować, jak działa aplikacja o pojedynczym wystąpieniu. Na przykład program Microsoft Outlook jest zazwyczaj uruchamiany jako pojedyncze wystąpienie aplikacji; gdy program Outlook jest uruchomiony, a próba uruchomienia programu Outlook ponownie, otrzymuje fokus do oryginalnego wystąpienia, ale nie można otworzyć inne wystąpienie.  
  
## <a name="events-in-the-application-model"></a>Zdarzenia w modelu aplikacji  
 W modelu aplikacji znajdują się następujące zdarzenia:  
  
- **Uruchamianie aplikacji**. Wywołuje aplikację <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzenia podczas jego uruchamiania. Dzięki obsłudze to zdarzenie, możesz dodać kod, który inicjuje aplikację przed załadowaniem formularza głównego. `Startup` Zdarzenia są także anulowanie wykonanie aplikacji w tej fazie procesu uruchamiania w razie potrzeby.  
  
     Można skonfigurować aplikację, aby wyświetlić ekran powitalny, podczas wykonywania kodu uruchamiania aplikacji. Domyślnie ten model aplikacji pomija powitalny ekranu, gdy albo `/nosplash` lub `-nosplash` argument wiersza polecenia jest używany.  
  
- **Aplikacje w jednym wystąpieniu**. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> Zdarzenie jest wywoływane, gdy rozpoczyna się kolejne wystąpienie aplikacja o pojedynczym wystąpieniu. Zdarzenie przekazuje argumenty wiersza polecenia, kolejne wystąpienia.  
  
- **Nieobsługiwane wyjątki**. Jeśli aplikacja napotkał nieobsługiwany wyjątek, zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzeń. Programu obsługi dla tego zdarzenia można zbadać wyjątek i ustalenia, czy należy kontynuować wykonywanie.  
  
     `UnhandledException` Zdarzeń nie jest zgłaszany w pewnych okolicznościach. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
- **Zmiany łączność sieciową**. Jeśli zmieni się dostępności sieci komputera, aplikacja zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> zdarzeń.  
  
     `NetworkAvailabilityChanged` Zdarzeń nie jest zgłaszany w pewnych okolicznościach. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
- **Zamknij aplikację**. Aplikacja udostępnia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzeń w celu sygnalizowania, że po około, aby zamknąć. W takim przypadku program obsługi, możesz upewnić się, że operacje Twoja aplikacja potrzebuje do wykonywania — zamykania i zapisywania, na przykład — są wykonywane. Można skonfigurować aplikację do zamykania po zamknięciu formularza głównego lub do zamykania zamykać tylko wtedy, gdy wszystkie formularze.  
  
## <a name="availability"></a>Dostępność  
 Domyślnie model aplikacji Visual Basic jest dostępne dla projektów Windows Forms. Jeśli Konfigurowanie aplikacji do korzystania z obiektu uruchamiania różnych, lub uruchomić kod aplikacji niestandardowej `Sub Main`, następnie obiekt lub klasa może być konieczne podanie implementację <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> klasy modelu aplikacji. Aby uzyskać informacje o zmianie obiekt początkowy, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Rozszerzanie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
