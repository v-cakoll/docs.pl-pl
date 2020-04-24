---
title: Rozszerzanie modelu aplikacji Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 46c18ab540c90c4147514685c2acc824755b435f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976863"
---
# <a name="extending-the-visual-basic-application-model"></a>Rozszerzanie modelu aplikacji Visual Basic

Aby dodać funkcjonalność do modelu aplikacji, można zastępowanie `Overridable` elementów członkowskich <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> klasy. Ta technika umożliwia dostosowanie zachowania modelu aplikacji i dodanie wywołań do własnych metod podczas uruchamiania i zamykania aplikacji.

## <a name="visual-overview-of-the-application-model"></a>Przegląd wizualizacji modelu aplikacji

Ta sekcja wizualnie przedstawia sekwencję wywołań funkcji w modelu aplikacji Visual Basic. W następnej sekcji opisano szczegółowo przeznaczenie poszczególnych funkcji.

Na poniższej ilustracji przedstawiono sekwencję wywołań modelu aplikacji w normalnej aplikacji Visual Basic Windows Forms. Sekwencja zaczyna się, gdy `Sub Main` procedura wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metodę.

![Diagram przedstawiający sekwencję wywołań modelu aplikacji.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)

Model aplikacji Visual Basic udostępnia także zdarzenia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> i. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> Poniższa Grafika przedstawia mechanizm do wywoływania tych zdarzeń.

![Diagram przedstawiający metodę OnStartupNextInstance, która wywołuje zdarzenie StartupNextInstance.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)

![Diagram przedstawiający metodę OnUnhandledException, która wywołuje zdarzenie UnhandledException.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)

## <a name="overriding-the-base-methods"></a>Zastępowanie metod podstawowych

<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Metoda definiuje kolejność, w jakiej są `Application` uruchamiane metody. Domyślnie `Sub Main` procedura dla Windows Forms aplikacji wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metodę.

Jeśli aplikacja jest zwykłą aplikacją (aplikacja o wielu wystąpieniach) lub pierwsze wystąpienie aplikacji pojedynczego wystąpienia, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Metoda wykonuje `Overridable` metody w następującej kolejności:

1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Domyślnie ta metoda ustawia style wizualizacji, style wyświetlania tekstu i bieżący podmiot zabezpieczeń dla wątku głównego aplikacji (Jeśli aplikacja używa uwierzytelniania systemu Windows) i wywołuje `ShowSplashScreen` , jeśli nie `/nosplash` `-nosplash` jest ani nie jest używany jako argument wiersza polecenia.

     Sekwencja uruchamiania aplikacji została anulowana, jeśli ta funkcja `False`zwróci wartość. Może to być przydatne, jeśli istnieją sytuacje, w których aplikacja nie powinna działać.

     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Metoda wywołuje następujące metody:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Określa, czy aplikacja ma zdefiniowany ekran powitalny, a jeśli tak, wyświetla ekran powitalny w osobnym wątku.

         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Metoda zawiera kod, który wyświetla ekran powitalny przez co najmniej liczbę milisekund określoną przez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> właściwość. Aby użyć tej funkcji, należy dodać ekran powitalny do aplikacji przy użyciu **projektanta projektu** ( `My.Application.MinimumSplashScreenDisplayTime` który ustawia właściwość na dwa sekundy) lub `My.Application.MinimumSplashScreenDisplayTime` ustawić właściwość w metodzie, która zastępuje metodę <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> lub. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Umożliwia projektantowi wyemitować kod, który inicjuje ekran powitalny.

         Domyślnie ta metoda nie wykonuje żadnych operacji. W przypadku wybrania ekranu powitalnego aplikacji w **projektancie projektu**Visual Basic Projektant zastępuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metodę metodą, która ustawia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> właściwość na nowe wystąpienie formularza powitalnego.

2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Udostępnia punkt rozszerzalności do wywoływania `Startup` zdarzenia. Sekwencja uruchamiania aplikacji zostaje zatrzymana, jeśli ta `False`funkcja zwróci wartość.

     Domyślnie ta metoda podnosi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzenie. Jeśli program obsługi zdarzeń ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel> właściwość argumentu zdarzenia na `True`, metoda zwraca `False` , aby anulować uruchamianie aplikacji.

3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Udostępnia punkt początkowy, gdy główna aplikacja jest gotowa do uruchomienia, po zakończeniu inicjalizacji.

     Domyślnie, przed wprowadzeniem Windows Forms pętli komunikatów, ta metoda wywołuje `OnCreateMainForm` (aby utworzyć formularz główny aplikacji) i `HideSplashScreen` (aby zamknąć ekran powitalny):

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Udostępnia sposób, w jaki Projektant może emitować kod, który inicjuje formularz główny.

         Domyślnie ta metoda nie wykonuje żadnych operacji. Jednak po wybraniu formularza głównego dla aplikacji w **projektancie projektu**Visual Basic Projektant zastępuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodę metodą, która ustawia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> właściwość na nowe wystąpienie formularza głównego.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Jeśli aplikacja ma zdefiniowany ekran powitalny, a jest otwarta, ta metoda zamyka ekran powitalny.

         Domyślnie ta metoda zamyka ekran powitalny.

4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Umożliwia dostosowanie sposobu, w jaki aplikacja o pojedynczym wystąpieniu działa po uruchomieniu innego wystąpienia aplikacji.

     Domyślnie ta metoda podnosi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> zdarzenie.

5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Udostępnia punkt rozszerzalności do wywoływania `Shutdown` zdarzenia. Ta metoda nie jest uruchamiana, jeśli wystąpił nieobsługiwany wyjątek w aplikacji głównej.

     Domyślnie ta metoda podnosi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzenie.

6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Wykonywane, jeśli wystąpił nieobsługiwany wyjątek w którejkolwiek z powyższych metod wymienionych na liście.

     Domyślnie ta metoda podnosi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzenie, o ile debuger nie jest dołączony i aplikacja obsługuje `UnhandledException` zdarzenie.

 Jeśli aplikacja jest aplikacją o pojedynczym wystąpieniu, a aplikacja jest już uruchomiona, kolejne wystąpienie aplikacji wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> metodę w oryginalnym wystąpieniu aplikacji, a następnie kończy działanie.

 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> Konstruktor wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> właściwość, aby określić, który aparat renderowania tekstu ma być używany dla formularzy aplikacji. Domyślnie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> Właściwość zwraca `False`, wskazując, że używany jest aparat renderowania tekstu GDI, który jest domyślny w Visual Basic 2005 i nowszych wersjach. Można przesłonić <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> właściwość na wartość `True`Return, co oznacza, że używany jest aparat renderowania tekstu GDI+, który jest domyślny w Visual Basic .NET 2002 i Visual Basic .NET 2003.

## <a name="configuring-the-application"></a>Konfigurowanie aplikacji

 W ramach modelu aplikacji Visual Basic <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Klasa zawiera chronione właściwości, które konfigurują aplikację. Te właściwości należy ustawić w konstruktorze klasy implementującej.

 W domyślnym projekcie Windows Forms **Projektant projektu** tworzy kod służący do ustawiania właściwości przy użyciu ustawień projektanta. Właściwości są używane tylko wtedy, gdy aplikacja jest uruchamiana. ustawienie ich po uruchomieniu aplikacji nie ma żadnego wpływu.

|Właściwość|Leżą|Ustawienie w okienku aplikacji projektanta projektu|
|---|---|---|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Czy aplikacja działa jako aplikacja pojedynczego wystąpienia, czy z wieloma wystąpieniami.|Zaznacz pole wyboru **aplikacji z pojedynczym wystąpieniem**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Jeśli aplikacja będzie używać stylów wizualnych, które pasują do systemu Windows XP.|Pole wyboru **włączania stylów wizualnych XP**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Jeśli aplikacja automatycznie zapisuje zmiany ustawień użytkownika aplikacji po zakończeniu działania aplikacji.|Pole wyboru **Zapisz moje ustawienia przy zamykaniu**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Co powoduje przerwanie działania aplikacji, na przykład gdy zostanie zamknięty formularz startowy lub gdy ostatni formularz zostanie zamknięty.|Lista **trybów zamykania**|

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Omówienie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
