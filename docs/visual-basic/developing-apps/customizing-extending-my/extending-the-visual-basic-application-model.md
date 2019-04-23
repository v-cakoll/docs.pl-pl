---
title: Rozszerzanie modelu aplikacji Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 6ba3f29ad0ceef7f1ea9d102743df568a32c26c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320148"
---
# <a name="extending-the-visual-basic-application-model"></a>Rozszerzanie modelu aplikacji Visual Basic
Można dodawać funkcjonalność model aplikacji poprzez zastąpienie `Overridable` członkowie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> klasy. Ta technika umożliwia dostosowywanie zachowania dotyczącego modelu aplikacji i dodawać wywołania do swoje własne metody, jak aplikacja uruchamia się i kończy pracę.  
  
## <a name="visual-overview-of-the-application-model"></a>Wizualne omówienie modelu aplikacji  
 W tej sekcji przedstawiono wizualnie sekwencję wywołań funkcji w modelu aplikacji Visual Basic. W następnej sekcji opisano przeznaczenie każdej funkcji szczegółowo.  
  
 Na poniższym rysunku przedstawiono sekwencję wywołań modelu aplikacji w normalnym aplikacji formularzy Windows w języku Visual Basic. Ciąg rozpoczyna się, kiedy `Sub Main` wywołania procedur <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metody.  
  
 ![Diagram przedstawiający sekwencję wywołań modelu aplikacji.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)  
  
 Model aplikacji Visual Basic udostępnia również <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzenia. Następujące graficznych Pokaż wywoływanie tych zdarzeń przy użyciu mechanizmu.  
  
 ![Diagram przedstawiający metodę OnStartupNextInstance podnoszonego zdarzenia StartupNextInstance.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)  
  
 ![Diagram przedstawiający metodę elemencie OnUnhandledException podnoszonego zdarzenia UnhandledException.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)  
  
## <a name="overriding-the-base-methods"></a>Nadpisywania metod bazowych  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Metoda definiuje kolejność, w którym `Application` metody uruchamiania. Domyślnie `Sub Main` wywołuje procedurę dla aplikacji Windows Forms <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metody.  
  
 Jeśli aplikacja jest aplikacją normalny (aplikacja z wieloma wystąpieniami) lub pierwsze wystąpienie pojedyncze wystąpienie aplikacji, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metoda jest wykonywana `Overridable` metod w następującej kolejności:  
  
1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Domyślnie ta metoda ustawia stylów wizualnych, style wyświetlania tekstu i bieżący podmiot zabezpieczeń dla wątku głównego aplikacji (Jeśli aplikacja używa uwierzytelniania Windows) i wywołuje `ShowSplashScreen` Jeśli żadna `/nosplash` ani `-nosplash` służy jako argument wiersza polecenia.  
  
     Sekwencja uruchamiania aplikacji została anulowana, jeśli ta funkcja zwróci `False`. Może to być przydatne, jeśli istnieją okoliczności, w których aplikacja nie powinna działać.  
  
     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Metoda wywołuje następujących metod:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Określa, czy aplikacja ma ekran powitalny zdefiniowane, a jeśli tak jest, wyświetla ekran powitalny w oddzielnym wątku.  
  
         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Metoda zawiera kod, który wyświetla powitalny ekranu do wyrażony w milisekundach czas określony przez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> właściwości. Aby używać tej funkcji, należy dodać ekran powitalny do swojej aplikacji za pomocą **projektanta projektu** (który określa `My.Application.MinimumSplashScreenDisplayTime` właściwości dwóch sekund), lub ustawić `My.Application.MinimumSplashScreenDisplayTime` właściwość w metodę, która zastępuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> lub <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metody. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Umożliwia projektanta emitować Kod, który inicjuje ekran powitalny.  
  
         Domyślnie ta metoda nie działa. Wybranie ekran powitalny dla aplikacji w języku Visual Basic **projektanta projektu**, Projektant zastępuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metodę z metodą, która ustawia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> właściwość nowe wystąpienie formularza ekran powitalny .  
  
2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Udostępnia punkt rozszerzalności dla podnoszonego `Startup` zdarzeń. Sekwencja uruchamiania aplikacji zatrzyma, jeśli ta funkcja zwróci `False`.  
  
     Domyślnie ta metoda wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzeń. Jeśli program obsługi zdarzeń ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel> właściwości argumentu zdarzenia `True`, metoda zwraca `False` do anulowania uruchomienia aplikacji.  
  
3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Zapewnia punkt początkowy podczas aplikacji głównej jest gotowy do uruchomienia, uruchomione po zakończeniu inicjowania.  
  
     Domyślnie przed uśpieniem pętli komunikatów Windows Forms, ta metoda wywołuje `OnCreateMainForm` (w celu utworzenia aplikacji formularza głównego) i `HideSplashScreen` (tak, aby zamknąć ekran powitalny) metody:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Zapewnia sposób projektanta emitować Kod, który inicjuje formularza głównego.  
  
         Domyślnie ta metoda nie działa. Jednak po wybraniu formularza głównego dla aplikacji w języku Visual Basic **projektanta projektu**, Projektant zastępuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodę z metodą, która ustawia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> właściwości do nowego wystąpienia formularza głównego.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Jeśli aplikacja ma ekran powitalny zdefiniowany i jest otwarty, ta metoda zamyka ekran powitalny.  
  
         Domyślnie ta metoda zamyka ekran powitalny.  
  
4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Zapewnia sposób dostosowywania, jak aplikacja o pojedynczym wystąpieniu zachowuje się podczas uruchamiania inne wystąpienie aplikacji.  
  
     Domyślnie ta metoda wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> zdarzeń.  
  
5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Udostępnia punkt rozszerzalności dla podnoszonego `Shutdown` zdarzeń. Ta metoda nie działa, jeśli wystąpi nieobsługiwany wyjątek w głównej aplikacji.  
  
     Domyślnie ta metoda wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzeń.  
  
6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Wykonywane, jeśli wystąpił nieobsługiwany wyjątek wystąpi w żadnej z wymienionych powyżej metod.  
  
     Domyślnie ta metoda wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> tak długo, jak nie jest dołączony debuger i aplikacji jest obsługa zdarzeń `UnhandledException` zdarzeń.  
  
 Jeśli aplikacja jest aplikacją pojedynczego wystąpienia, a aplikacja jest już uruchomiona, kolejne wystąpienie aplikacji wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> metody w oryginalnym wystąpieniu aplikacji, a następnie zamyka.  
 
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> Konstruktor wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> właściwości w celu określenia aparat renderowania tekstu do użycia dla aplikacji formularzy. Domyślnie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> właściwość zwraca `False`, wskazując, że aparat renderowania GDI tekstu można użyć, co jest ustawieniem domyślnym w [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]. Można zastąpić <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> właściwości do zwrócenia `True`, która wskazuje, że używane tekstu aparat renderowania GDI +, co jest ustawieniem domyślnym w Visual Basic .NET 2002 i Visual Basic .NET 2003.  
  
## <a name="configuring-the-application"></a>Konfigurowanie aplikacji  
 Jako część modelu aplikacji Visual Basic <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering> klasy zawiera właściwości chronionego, skonfigurowanych aplikacji. Te właściwości należy ustawić w konstruktorze klasy implementującej.  
  
 W domyślny projekt Windows Forms **projektanta projektu** tworzy kod, aby ustawić właściwości przy użyciu projektanta ustawień. Właściwości są używane tylko wtedy, gdy aplikacja jest uruchamiana; Po uruchomieniu aplikacji ich ustawienie nie ma znaczenia.  
  
|Właściwość|Określa|Ustawienia w okienku aplikacji projektanta projektu|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Czy aplikacja działa jako aplikacja pojedynczego wystąpienia lub wieloma wystąpieniami.|**Pojedyncze wystąpienie aplikacji** pola wyboru|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Jeśli aplikacja będzie używać stylów wizualnych, które odpowiadają Windows XP.|**Włączyć style wizualne XP** pola wyboru|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Jeśli aplikacja automatycznie zapisuje zmiany ustawień użytkownika aplikacji, gdy aplikacja kończy działanie.|**Zapisz My.Settings podczas zamykania** pola wyboru|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Co powoduje, że aplikacja zakończyć, np. gdy zamyka formularz początkowy lub po zamknięciu ostatniego formularza.|**Tryb zamykania** listy|  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Omówienie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
