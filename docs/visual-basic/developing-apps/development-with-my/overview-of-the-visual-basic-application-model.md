---
title: Omówienie modelu aplikacji Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: aa47304cf2bded93bdb95ffe7dfa35bb37d9a643
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976461"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Omówienie modelu aplikacji Visual Basic

Visual Basic udostępnia dobrze zdefiniowany model służący do kontrolowania zachowania aplikacji Windows Forms: model aplikacji Visual Basic. Ten model zawiera zdarzenia do obsługi uruchamiania i zamykania aplikacji oraz zdarzenia dotyczące przechwytywania nieobsłużonych wyjątków. Zapewnia również obsługę tworzenia aplikacji z pojedynczym wystąpieniem. Model aplikacji jest rozszerzalny, dlatego deweloperzy, którzy potrzebują większej kontroli, mogą dostosować swoje metody zamiarowe.  
  
## <a name="uses-for-the-application-model"></a>Używa modelu aplikacji  

 Typowa aplikacja musi wykonywać zadania podczas uruchamiania i zamykania. Na przykład po uruchomieniu aplikacji może być wyświetlany ekran powitalny, tworzenie połączeń z bazą danych, załadowanie zapisanego stanu i tak dalej. Po zamknięciu aplikacji może ona zamykać połączenia z bazą danych, zapisywać bieżący stan i tak dalej. Ponadto aplikacja może wykonywać określony kod w przypadku nieoczekiwanego zamknięcia aplikacji, na przykład podczas nieobsługiwanego wyjątku.  
  
 Visual Basic model aplikacji ułatwia tworzenie aplikacji o *pojedynczym wystąpieniu* . Aplikacja o pojedynczym wystąpieniu różni się od zwykłej aplikacji, która może działać jednocześnie tylko w jednym wystąpieniu aplikacji. Próba uruchomienia innego wystąpienia aplikacji o pojedynczym wystąpieniu spowoduje powiadomienie oryginalnego wystąpienia o wystąpieniu zdarzenia `StartupNextInstance` — od momentu wykonania innej próby uruchomienia. Powiadomienie zawiera argumenty wiersza polecenia kolejnego wystąpienia. Kolejne wystąpienie aplikacji jest następnie zamykane przed wystąpieniem dowolnego inicjalizacji.  
  
 Aplikacja o pojedynczym wystąpieniu jest uruchamiana i sprawdza, czy jest to pierwsze wystąpienie lub następne wystąpienie aplikacji:  
  
- Jeśli jest to pierwsze wystąpienie, rozpocznie się w zwykły sposób.  
  
- Każda kolejna próba uruchomienia aplikacji podczas pierwszego wystąpienia powoduje bardzo inne zachowanie. Kolejna próba powiadamia pierwsze wystąpienie o argumentach wiersza polecenia, a następnie natychmiast kończy pracę. Pierwsze wystąpienie obsługuje zdarzenie `StartupNextInstance`, aby określić, jakie argumenty wiersza polecenia dla kolejnych wystąpień były i nadal działają.  
  
     Ten diagram pokazuje, jak kolejne wystąpienie sygnalizuje pierwsze wystąpienie:  
  
     ![Diagram przedstawiający obraz aplikacji o pojedynczym wystąpieniu.](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 Dzięki obsłudze zdarzenia `StartupNextInstance` można kontrolować działanie aplikacji o pojedynczym wystąpieniu. Na przykład program Microsoft Outlook zazwyczaj działa jako aplikacja pojedynczego wystąpienia; gdy program Outlook jest uruchomiony i próbujesz ponownie uruchomić program Outlook, fokus jest przenoszony do oryginalnego wystąpienia, ale inne wystąpienie nie jest otwarte.  
  
## <a name="events-in-the-application-model"></a>Zdarzenia w modelu aplikacji  

 W modelu aplikacji znaleziono następujące zdarzenia:  
  
- **Uruchamianie aplikacji**. Aplikacja wywołuje zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> podczas jego uruchamiania. Obsługując to zdarzenie, można dodać kod inicjujący aplikację przed załadowaniem formularza głównego. Zdarzenie `Startup` umożliwia również anulowanie wykonywania aplikacji w tej fazie procesu uruchamiania, jeśli jest to konieczne.  
  
     Można skonfigurować aplikację tak, aby wyświetlała ekran powitalny podczas uruchamiania kodu uruchomienia aplikacji. Domyślnie model aplikacji pomija ekran powitalny, gdy jest używany `/nosplash` lub `-nosplash` argument wiersza polecenia.  
  
- **Aplikacje o pojedynczym wystąpieniu**. Zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> jest zgłaszane, gdy zostanie uruchomione kolejne wystąpienie aplikacji o jednym wystąpieniu. Zdarzenie przekazuje argumenty wiersza polecenia kolejnego wystąpienia.  
  
- **Nieobsłużone wyjątki**. Jeśli aplikacja napotka nieobsługiwany wyjątek, wywołuje zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>. Program obsługi dla tego zdarzenia może sprawdzić wyjątek i określić, czy kontynuować wykonywanie.  
  
     Zdarzenie `UnhandledException` nie zostanie zgłoszone w pewnych okolicznościach. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
- **Zmiany łączności sieciowej**. Jeśli zmieni się dostępność sieci komputera, aplikacja zgłasza zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
     Zdarzenie `NetworkAvailabilityChanged` nie zostanie zgłoszone w pewnych okolicznościach. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
- **Zamykanie aplikacji**. Aplikacja udostępnia zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>, aby sygnalizować, gdy zostanie zamknięte. W tym obsłudze zdarzeń można upewnić się, że operacje wymagane przez aplikację są wykonywane — zamknięcie i zapisanie — na przykład — zostało zakończone. Można skonfigurować aplikację do zamykania, gdy główny formularz zostanie zamknięty lub aby zamknąć tylko wtedy, gdy wszystkie formularze zostały zamknięte.  
  
## <a name="availability"></a>Dostępność  

 Domyślnie model aplikacji Visual Basic jest dostępny dla Windows Forms projektów. W przypadku skonfigurowania aplikacji tak, aby korzystała z innego obiektu startowego, lub uruchomić kod aplikacji z niestandardowym `Sub Main`, ten obiekt lub Klasa może wymagać dostarczenia implementacji klasy <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> w celu użycia modelu aplikacji. Aby uzyskać informacje na temat zmiany obiektu uruchomieniowego, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Rozszerzanie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
