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

Aby dodać funkcjonalność do modelu aplikacji, można zastępowanie `Overridable` elementów członkowskich klasy <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Ta technika umożliwia dostosowanie zachowania modelu aplikacji i dodanie wywołań do własnych metod podczas uruchamiania i zamykania aplikacji.

## <a name="visual-overview-of-the-application-model"></a>Przegląd wizualizacji modelu aplikacji

Ta sekcja wizualnie przedstawia sekwencję wywołań funkcji w modelu aplikacji Visual Basic. W następnej sekcji opisano szczegółowo przeznaczenie poszczególnych funkcji.

Na poniższej ilustracji przedstawiono sekwencję wywołań modelu aplikacji w normalnej aplikacji Visual Basic Windows Forms. Sekwencja jest uruchamiana, gdy procedura `Sub Main` wywoła metodę <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.

![Diagram przedstawiający sekwencję wywołań modelu aplikacji.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)

Model aplikacji Visual Basic udostępnia także zdarzenia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>. Poniższa Grafika przedstawia mechanizm do wywoływania tych zdarzeń.

![Diagram przedstawiający metodę OnStartupNextInstance, która wywołuje zdarzenie StartupNextInstance.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)

![Diagram przedstawiający metodę OnUnhandledException, która wywołuje zdarzenie UnhandledException.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)

## <a name="overriding-the-base-methods"></a>Zastępowanie metod podstawowych

Metoda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> definiuje kolejność, w jakiej są uruchamiane metody `Application`. Domyślnie procedura `Sub Main` dla aplikacji Windows Forms wywołuje metodę <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.

Jeśli aplikacja jest normalną aplikacją (aplikacja o wielu wystąpieniach) lub pierwsze wystąpienie aplikacji pojedynczego wystąpienia, Metoda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> wykonuje metody `Overridable` w następującej kolejności:

1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>., Domyślnie ta metoda ustawia style wizualizacji, style wyświetlania tekstu i bieżący podmiot zabezpieczeń dla wątku głównego aplikacji (Jeśli aplikacja używa uwierzytelniania systemu Windows) i wywołuje `ShowSplashScreen`, jeśli nie `/nosplash` ani `-nosplash` nie są używane jako argumenty wiersza polecenia.

     Sekwencja uruchamiania aplikacji została anulowana, jeśli ta funkcja zwróci `False`. Może to być przydatne, jeśli istnieją sytuacje, w których aplikacja nie powinna działać.

     Metoda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> wywołuje następujące metody:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>., Określa, czy aplikacja ma zdefiniowany ekran powitalny, a jeśli tak, wyświetla ekran powitalny w osobnym wątku.

         Metoda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> zawiera kod, który wyświetla ekran powitalny przez co najmniej liczbę milisekund określoną we właściwości <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>. Aby użyć tej funkcji, należy dodać ekran powitalny do aplikacji przy użyciu **projektanta projektu** (który ustawia właściwość `My.Application.MinimumSplashScreenDisplayTime` na dwa sekundy) lub ustawić właściwość `My.Application.MinimumSplashScreenDisplayTime` w metodzie, która zastępuje metodę <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> lub <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>., Umożliwia projektantowi wyemitować kod, który inicjuje ekran powitalny.

         Domyślnie ta metoda nie wykonuje żadnych operacji. W przypadku wybrania ekranu powitalnego aplikacji w **projektancie projektu**Visual Basic, Projektant przesłania metodę <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> z metodą, która ustawia właściwość <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> na nowe wystąpienie formularza powitalnego.

2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>., Udostępnia punkt rozszerzalności do wywoływania zdarzenia `Startup`. Sekwencja uruchamiania aplikacji zostaje zatrzymana, jeśli ta funkcja zwróci `False`.

     Domyślnie ta metoda wywołuje zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>. Jeśli program obsługi zdarzeń ustawia właściwość <xref:System.ComponentModel.CancelEventArgs.Cancel> argumentu zdarzenia na `True`, metoda zwróci `False`, aby anulować uruchamianie aplikacji.

3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>., Udostępnia punkt początkowy, gdy główna aplikacja jest gotowa do uruchomienia, po zakończeniu inicjalizacji.

     Domyślnie, przed wprowadzeniem Windows Forms pętli komunikatów, ta metoda wywołuje `OnCreateMainForm` (aby utworzyć formularz główny aplikacji) i `HideSplashScreen` (aby zamknąć ekran powitalny):

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>., Udostępnia sposób, w jaki Projektant może emitować kod, który inicjuje formularz główny.

         Domyślnie ta metoda nie wykonuje żadnych operacji. Jednak po wybraniu formularza głównego dla aplikacji w **projektancie projektu**Visual Basic Projektant zastępuje metodę <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodą, która ustawia właściwość <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> na nowe wystąpienie formularza głównego.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>., Jeśli aplikacja ma zdefiniowany ekran powitalny, a jest otwarta, ta metoda zamyka ekran powitalny.

         Domyślnie ta metoda zamyka ekran powitalny.

4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>., Umożliwia dostosowanie sposobu, w jaki aplikacja o pojedynczym wystąpieniu działa po uruchomieniu innego wystąpienia aplikacji.

     Domyślnie ta metoda wywołuje zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>.

5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>., Udostępnia punkt rozszerzalności do wywoływania zdarzenia `Shutdown`. Ta metoda nie jest uruchamiana, jeśli wystąpił nieobsługiwany wyjątek w aplikacji głównej.

     Domyślnie ta metoda wywołuje zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>.

6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>., Wykonywane, jeśli wystąpił nieobsługiwany wyjątek w którejkolwiek z powyższych metod wymienionych na liście.

     Domyślnie ta metoda wywołuje zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>, o ile debuger nie jest dołączony, a aplikacja obsługuje zdarzenie `UnhandledException`.

 Jeśli aplikacja jest aplikacją o pojedynczym wystąpieniu, a aplikacja jest już uruchomiona, kolejne wystąpienie aplikacji wywołuje metodę <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> w oryginalnym wystąpieniu aplikacji, a następnie kończy działanie.

 Konstruktor <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> wywołuje właściwość <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>, aby określić, który aparat renderowania tekstu ma być używany dla formularzy aplikacji. Domyślnie właściwość <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> zwraca `False`, co oznacza, że używany jest aparat renderowania tekstu GDI, który jest domyślny w Visual Basic 2005 i nowszych wersjach. Można zastąpić Właściwość <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>, aby zwracała `True`, co oznacza, że używany jest aparat renderowania tekstu GDI+, który jest wartością domyślną w Visual Basic .NET 2002 i Visual Basic .NET 2003.

## <a name="configuring-the-application"></a>Konfigurowanie aplikacji

 W ramach modelu aplikacji Visual Basic Klasa <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> udostępnia chronione właściwości, które konfigurują aplikację. Te właściwości należy ustawić w konstruktorze klasy implementującej.

 W domyślnym projekcie Windows Forms **Projektant projektu** tworzy kod służący do ustawiania właściwości przy użyciu ustawień projektanta. Właściwości są używane tylko wtedy, gdy aplikacja jest uruchamiana. ustawienie ich po uruchomieniu aplikacji nie ma żadnego wpływu.

|Właściwość|Leżą|Ustawienie w okienku aplikacji projektanta projektu|
|---|---|---|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Czy aplikacja działa jako aplikacja pojedynczego wystąpienia, czy z wieloma wystąpieniami.|Zaznacz pole wyboru **aplikacji z pojedynczym wystąpieniem**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Jeśli aplikacja będzie używać stylów wizualnych, które pasują do systemu Windows XP.|Pole wyboru **włączania stylów wizualnych XP**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Jeśli aplikacja automatycznie zapisuje zmiany ustawień użytkownika aplikacji po zakończeniu działania aplikacji.|Pole wyboru **Zapisz moje ustawienia przy zamykaniu**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Co powoduje przerwanie działania aplikacji, na przykład gdy zostanie zamknięty formularz startowy lub gdy ostatni formularz zostanie zamknięty.|Lista **trybów zamykania**|

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Omówienie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
