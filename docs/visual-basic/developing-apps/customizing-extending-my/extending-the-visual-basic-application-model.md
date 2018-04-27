---
title: Rozszerzanie modelu aplikacji Visual Basic
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ffd882c2a1d04c29483d380e972d6ce70bdb5c4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="extending-the-visual-basic-application-model"></a>Rozszerzanie modelu aplikacji Visual Basic
Można dodać funkcje do modelu aplikacji przez zastąpienie `Overridable` członkami <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> klasy. Ta technika pozwala dostosować zachowanie aplikacji modelu, a następnie dodaj wywołania metod własnych aplikacji uruchamiania i wyłączania.  
  
## <a name="visual-overview-of-the-application-model"></a>Omówienie modelu aplikacji Visual  
 W tej sekcji przedstawiono wizualnie sekwencję wywołań funkcji w modelu aplikacji Visual Basic. W następnej sekcji opisano przeznaczenie każdej funkcji szczegółowo.  
  
 Na poniższym rysunku przedstawiono sekwencję wywołań modelu aplikacji w normalnym aplikacji formularzy systemu Windows w języku Visual Basic. Sekwencja uruchamiania, kiedy `Sub Main` wywołań procedur <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metody.  
  
 ![Model aplikacji Visual Basic &#45; &#45; Uruchom](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelrun.gif "VB_ModelRun")  
  
 Udostępnia Model aplikacji Visual Basic <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> i <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzenia. Poniższej grafice zawierają mechanizm wywoływanie tych zdarzeń.  
  
 ![Model aplikacji Visual Basic &#45; &#45; następne wystąpienie](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelnext.gif "VB_ModelNext")  
  
 ![Model aplikacji Visual Basic nieobsłużony wyjątek](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_unhandex.gif "VB_UnhandEx")  
  
## <a name="overriding-the-base-methods"></a>Nadpisywania metod bazowych  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Metoda definiuje kolejność, w którym `Application` metody uruchamiania. Domyślnie `Sub Main` wywołuje procedurę dla aplikacji Windows Forms <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metody.  
  
 Jeśli aplikacja jest normalne aplikacji (wiele wystąpień aplikacji) lub pierwszego wystąpienia jednego wystąpienia aplikacji, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> wykonuje metodę `Overridable` metod w następującej kolejności:  
  
1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Domyślnie ta metoda ustawia stylów wizualnych, style wyświetlania tekstu i bieżący podmiot zabezpieczeń dla wątku głównego aplikacji (Jeśli aplikacja używa uwierzytelniania systemu Windows) i wywołania `ShowSplashScreen` Jeśli żadna `/nosplash` ani `-nosplash` jest używany jako argument wiersza polecenia.  
  
     Sekwencja uruchamiania aplikacji zostało anulowane, jeśli ta funkcja zwraca `False`. Może to być przydatne, jeśli istnieją okoliczności, w których nie należy uruchamiać aplikacji.  
  
     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Metoda wywołuje następujących metod:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Określa, czy aplikacja ma ekran powitalny zdefiniowane, a jeśli tak, wyświetla ekran powitalny w oddzielnym wątku.  
  
         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Metoda zawiera kod, który wyświetla to pozostawienie ekranu powitalnego ekranu dla wyrażony w milisekundach czas określony przez <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> właściwości. Aby używać tej funkcji, należy dodać do swojej aplikacji za pomocą ekranu powitalnego **projektanta projektu** (który określa `My.Application.MinimumSplashScreenDisplayTime` właściwości do dwóch sekund), lub ustaw `My.Application.MinimumSplashScreenDisplayTime` właściwość w metodę, która zastępuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> lub <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metody. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Umożliwia projektanta na emitowanie kodu, który inicjuje ekranu powitalnego.  
  
         Domyślnie ta metoda nie działa. Wybranie ekranu powitalnego aplikacji w języku Visual Basic **projektanta projektu**, zastępuje projektanta <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metodę za pomocą metody, która ustawia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> właściwości do nowego wystąpienia formularz ekranu powitalnego .  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Udostępnia punkt rozszerzalności dla wywoływanie `Startup` zdarzeń. Zatrzymuje sekwencja uruchamiania aplikacji, jeśli ta funkcja zwraca `False`.  
  
     Domyślnie ta metoda zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzeń. Jeśli program obsługi zdarzeń ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel> właściwości argument zdarzenia `True`, metoda zwraca `False` anulować uruchamiania aplikacji.  
  
3.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Zapewnia punkt początkowy podczas aplikacji głównej jest gotowy do uruchomienia, uruchomiona po ukończeniu inicjowania.  
  
     Domyślnie przed uśpieniem pętli komunikatów formularzy systemu Windows, ta metoda wywołuje `OnCreateMainForm` (Aby utworzyć formularz główny aplikacji) i `HideSplashScreen` (aby zamknąć ekran powitalny) metod:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Umożliwia projektanta na emitowanie kodu, który inicjuje formularz główny.  
  
         Domyślnie ta metoda nie działa. Jednak po wybraniu formularz główny aplikacji w języku Visual Basic **projektanta projektu**, zastępuje projektanta <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodę za pomocą metody, która ustawia <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> właściwości nowe wystąpienie klasy głównym formularza.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Jeśli aplikacja ma ekran powitalny zdefiniowany i jest otwarty, ta metoda powoduje zamknięcie ekranu powitalnego.  
  
         Domyślnie ta metoda powoduje zamknięcie ekranu powitalnego.  
  
4.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Umożliwia dostosowanie zachowania pojedyncze wystąpienie aplikacji podczas uruchamiania inne wystąpienie aplikacji.  
  
     Domyślnie ta metoda zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> zdarzeń.  
  
5.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Udostępnia punkt rozszerzalności dla wywoływanie `Shutdown` zdarzeń. Ta metoda nie działa, jeśli wystąpi nieobsługiwany wyjątek w aplikacji głównej.  
  
     Domyślnie ta metoda zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzeń.  
  
6.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Należy wykonać, jeśli wystąpi nieobsługiwany wyjątek w dowolnej z metod wymienionych powyżej.  
  
     Domyślnie ta metoda zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> tak długo, jak nie jest dołączony debuger, a aplikacja jest obsługa zdarzeń `UnhandledException` zdarzeń.  
  
 Jeśli aplikacja jest pojedyncze wystąpienie aplikacji, a aplikacja jest już uruchomiona, kolejne wystąpienie aplikacji wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> metody w oryginalnym wystąpieniu aplikacji, a następnie zamyka.  
 
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> Wywołania konstruktora <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> właściwości w celu określenia aparat renderowania tekstu stosowanie w formularzach aplikacji. Domyślnie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> zwraca `False`, wskazującą, czy można używać aparatu renderowania tekstu GDI, co jest ustawieniem domyślnym w [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]. Można zastąpić <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> właściwości do zwrócenia `True`, która wskazuje, że używane aparat renderowania tekstu GDI +, co jest ustawieniem domyślnym w Visual Basic .NET 2002 i Visual Basic .NET 2003.  
  
## <a name="configuring-the-application"></a>Konfigurowanie aplikacji  
 W ramach modelu aplikacji Visual Basic <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering> klasa udostępnia właściwości chronionego, służące do konfiguracji aplikacji. Te właściwości należy ustawić w konstruktorze klasy implementującej.  
  
 W projekcie domyślny program Windows Forms **projektanta projektu** tworzy kod, aby ustawić właściwości przy użyciu projektanta ustawień. Te właściwości są używane tylko wtedy, gdy aplikacja jest uruchamiana; Po uruchomieniu aplikacji ich ustawienie nie ma znaczenia.  
  
|Właściwość|Określa|Ustawienia w okienku aplikacji projektanta projektu|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Określa, czy aplikacja zostanie uruchomiona jako aplikacja wystąpienia jednego lub wielu wystąpień.|**Aplikacja pojedynczego wystąpienia** pole wyboru|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Jeśli aplikacja będzie używać stylów wizualnych, zgodne z systemem Windows XP.|**Włącz style wizualne XP** pole wyboru|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Jeśli aplikacja automatycznie zapisze zmiany ustawienia użytkownika aplikacji, po zamknięciu aplikacji.|**Zapisz My.Settings podczas zamykania** pole wyboru|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Co powoduje zamknięcie, np. gdy zamknie się formularz startowy lub gdy zostanie zamknięty ostatni formularz aplikacji.|**Tryb zamykania** listy|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 [Omówienie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
