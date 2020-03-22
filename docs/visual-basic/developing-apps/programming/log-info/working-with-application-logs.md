---
title: Praca z dziennikami aplikacji
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 617b940d2cf15779ae3c10e4663b63c9771d44b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345899"
---
# <a name="working-with-application-logs-in-visual-basic"></a>Praca z dziennikami aplikacji w Visual Basic

Obiekty `My.Application.Log` `My.Log` i ułatwiają zapisywanie rejestrowania i śledzenia informacji do dzienników.

## <a name="how-messages-are-logged"></a>Jak rejestrowane są wiadomości

Po pierwsze ważności wiadomości jest sprawdzany <xref:System.Diagnostics.TraceSource.Switch%2A> z właściwości log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> właściwości. Domyślnie tylko komunikaty o ważności "Informacje" i wyższe są przekazywane do odbiorników `TraceListener` śledzenia, określone w kolekcji dziennika. Następnie każdy odbiornik porównuje ważność wiadomości do właściwości odbiornika. <xref:System.Diagnostics.TraceSource.Switch%2A> Jeśli ważność wiadomości jest wystarczająco wysoka, odbiornik zapisuje komunikat.

Na poniższym diagramie pokazano, `WriteEntry` jak komunikat napisany `WriteLine` do metody przechodzi do metod detektorów śledzenia dziennika:

![Diagram, który pokazuje moje wywołanie dziennika.](./media/working-with-application-logs/my-log-call-messages.png)

Można zmienić zachowanie dziennika i odbiorników śledzenia, zmieniając plik konfiguracyjny aplikacji. Na poniższym diagramie przedstawiono zgodność między częściami dziennika a plikiem konfiguracji.

![Diagram przedstawiający konfigurację mojego dziennika.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a>Gdzie rejestrowane są wiadomości

Jeśli zestaw nie ma pliku `My.Application.Log` `My.Log` konfiguracji, i obiekty zapisu do danych <xref:System.Diagnostics.DefaultTraceListener> wyjściowych debugowania aplikacji (za pośrednictwem klasy). Ponadto `My.Application.Log` obiekt zapisuje do pliku dziennika zestawu (za <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> pośrednictwem klasy), podczas gdy `My.Log` obiekt zapisuje do ASP.NET danych <xref:System.Web.WebPageTraceListener> wyjściowych strony sieci Web (za pośrednictwem klasy).

Dane wyjściowe debugowania można wyświetlić w oknie **dane wyjściowe** programu Visual Studio podczas uruchamiania aplikacji w trybie debugowania. Aby otworzyć okno **Dane wyjściowe,** kliknij element menu **Debugowanie,** wskaż polecenie **Windows**, a następnie kliknij pozycję **Wyjście**. W oknie **Dane wyjściowe** wybierz **debugowanie** z pola **Pokaż dane wyjściowe.**

Domyślnie `My.Application.Log` zapisuje plik dziennika w ścieżce dla danych aplikacji użytkownika. Ścieżkę można uzyskać <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> z właściwości <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> obiektu. Format tej ścieżki jest następujący:

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

Typowa wartość `BasePath` jest następująca.

C:\Dokumenty i\\`username`ustawienia \Dane aplikacji

Wartości , `CompanyName` `ProductName`i `ProductVersion` pochodzą z informacji o zestawie aplikacji. Formą nazwy pliku dziennika jest *AssemblyName*.log, gdzie *Nazwa zestawu* jest nazwą pliku zestawu bez rozszerzenia. Jeśli potrzebny jest więcej niż jeden plik dziennika, na przykład gdy oryginalny dziennik jest niedostępny, gdy aplikacja próbuje zapisać w dzienniku, formularz `Integer`dla nazwy pliku dziennika to *AssemblyName*-*iteration*.log, gdzie `iteration` jest dodatni .

Domyślne zachowanie można zastąpić, dodając lub zmieniając pliki konfiguracyjne komputera i aplikacji. Aby uzyskać więcej informacji, zobacz [Przewodnik: Zmiana miejsca, w którym my.application.log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).

## <a name="configuring-log-settings"></a>Konfigurowanie ustawień dziennika

Obiekt `Log` ma domyślną implementację, która działa bez pliku konfiguracji aplikacji, app.config. Aby zmienić ustawienia domyślne, należy dodać plik konfiguracyjny z nowymi ustawieniami. Aby uzyskać więcej informacji, zobacz [Instruktaż: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

Sekcje konfiguracji dziennika znajdują `<system.diagnostics>` się w `<configuration>` węźle w głównym węźle pliku app.config. Informacje dziennika są zdefiniowane w kilku węzłach:

- Detektory `Log` obiektu są zdefiniowane `<sources>` w węźle o nazwie DefaultSource.

- Filtr ważności `Log` obiektu jest zdefiniowany `<switches>` w węźle o nazwie DefaultSwitch.

- Odbiorniki dziennika są zdefiniowane w węźle. `<sharedListeners>`

 Przykłady `<sources>`, `<switches>`i `<sharedListeners>` węzły są wyświetlane w następującym kodzie:

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a>Zmiana ustawień dziennika po wdrożeniu

Podczas tworzenia aplikacji jej ustawienia konfiguracji są przechowywane w pliku app.config, jak pokazano w powyższych przykładach. Po wdrożeniu aplikacji można skonfigurować dziennik, edytując plik konfiguracyjny. W aplikacji opartej na systemie Windows nazwa tego pliku to *nazwa pliku .* exe.config i musi znajdować się w tym samym folderze co plik wykonywalny. W przypadku aplikacji sieci Web jest to plik Web.config skojarzony z projektem.

Gdy aplikacja wykonuje kod, który tworzy wystąpienie klasy po raz pierwszy, sprawdza plik konfiguracji pod kątem informacji o obiekcie. W `Log` przypadku obiektu dzieje się `Log` to przy pierwszym wejściu do obiektu. System sprawdza plik konfiguracyjny tylko raz dla dowolnego konkretnego obiektu — przy pierwszym uruchomieniu obiektu przez aplikację. W związku z tym może być konieczne ponowne uruchomienie aplikacji, aby zmiany zostały wprowadzone.

W wdrożonej aplikacji można włączyć kod śledzenia przez ponowne skonfigurowanie obiektów przełącznika przed uruchomieniem aplikacji. Zazwyczaj wiąże się to z włączaniem i wyłączaniem obiektów przełącznika lub zmienianiem poziomów śledzenia, a następnie ponownym uruchomieniem aplikacji.

## <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami

Podczas zapisywania danych w dzienniku należy wziąć pod uwagę następujące kwestie:

- **Unikaj wycieku informacji o użytkowniku.** Upewnij się, że aplikacja zapisuje tylko zatwierdzone informacje w dzienniku. Na przykład może być dopuszczalne dla dziennika aplikacji zawierają nazwy użytkowników, ale nie hasła użytkownika.

- **Zabezpiecz lokalizacje dzienników.** Każdy dziennik zawierający potencjalnie poufne informacje powinny być przechowywane w bezpiecznej lokalizacji.

- **Unikaj wprowadzających w błąd informacji.** Ogólnie rzecz biorąc aplikacja powinna sprawdzić poprawność wszystkich danych wprowadzonych przez użytkownika przed użyciem tych danych. Obejmuje to zapisywanie danych w dzienniku aplikacji.

- **Unikaj odmowy usługi.** Jeśli aplikacja zapisuje zbyt wiele informacji w dzienniku, może wypełnić dziennik lub utrudnić znalezienie ważnych informacji.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Rejestrowanie informacji z aplikacji](../../../../visual-basic/developing-apps/programming/log-info/index.md)
