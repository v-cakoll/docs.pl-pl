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

Obiekty `My.Application.Log` i `My.Log` ułatwiają zapisywanie informacji o rejestrowaniu i śledzeniu w dziennikach.

## <a name="how-messages-are-logged"></a>Jak są rejestrowane komunikaty

Po pierwsze ważność komunikatu jest sprawdzana z <xref:System.Diagnostics.TraceSource.Switch%2A> właściwością <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> właściwości log. Domyślnie tylko wiadomości o ważności "Information" i wyższych są przesyłane do odbiorników śledzenia określonych w `TraceListener` kolekcji dzienników. Następnie każdy odbiornik porównuje ważność komunikatu z <xref:System.Diagnostics.TraceSource.Switch%2A> właściwością odbiornika. Jeśli ważność komunikatu jest wystarczająco wysoka, odbiornik zapisuje komunikat.

Na poniższym diagramie przedstawiono sposób, w jaki komunikat zapisany `WriteEntry` w metodzie jest przesyłany do `WriteLine` metod detektorów śledzenia dziennika:

![Diagram przedstawiający moje wywołanie dziennika.](./media/working-with-application-logs/my-log-call-messages.png)

Można zmienić zachowanie dziennika i detektorów śledzenia, zmieniając plik konfiguracyjny aplikacji. Na poniższym diagramie przedstawiono zgodność między częściami dziennika i pliku konfiguracji.

![Diagram przedstawiający moją konfigurację dziennika.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a>Gdzie są rejestrowane komunikaty

Jeśli zestaw nie ma pliku konfiguracji, `My.Application.Log` a obiekty i `My.Log` zapisują w danych wyjściowych debugowania aplikacji (za pomocą <xref:System.Diagnostics.DefaultTraceListener> klasy). Ponadto `My.Application.Log` obiekt zapisuje w pliku dziennika zestawu (za pomocą <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy), podczas gdy `My.Log` obiekt zapisuje do danych wyjściowych strony sieci Web ASP.NET (za pomocą <xref:System.Web.WebPageTraceListener> klasy).

Dane wyjściowe debugowania można wyświetlić w oknie **danych wyjściowych** programu Visual Studio podczas uruchamiania aplikacji w trybie debugowania. Aby otworzyć okno **dane wyjściowe** , kliknij element menu **Debuguj** , wskaż polecenie **Windows**, a następnie kliknij pozycję **dane wyjściowe**. W oknie **dane wyjściowe** wybierz pozycję **Debuguj** w polu **Pokaż dane wyjściowe z** .

Domyślnie program `My.Application.Log` zapisuje plik dziennika w ścieżce dla danych aplikacji użytkownika. Ścieżkę można pobrać z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> właściwości <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> obiektu. Format tej ścieżki jest następujący:

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

Typowa wartość dla `BasePath` jest następująca.

C:\Dokumenty i ustawienia\\`username`\Dane danych

Wartości `CompanyName`, `ProductName`i `ProductVersion` pochodzą z informacji o zestawie aplikacji. Nazwa pliku dziennika to *AssemblyName*. log, gdzie *AssemblyName* jest nazwą pliku zestawu bez rozszerzenia. Jeśli jest wymagany więcej niż jeden plik dziennika, na przykład gdy oryginalny dziennik jest niedostępny, gdy aplikacja próbuje zapisać w dzienniku, formularz dla nazwy pliku dziennika to *AssemblyName*-*iteracji*. log, gdzie `iteration` jest wartością dodatnią. `Integer`

Zachowanie domyślne można zastąpić przez dodanie lub zmianę plików konfiguracyjnych komputera i aplikacji. Aby uzyskać więcej informacji, zobacz [Przewodnik: Zmienianie, gdzie my. Application. Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).

## <a name="configuring-log-settings"></a>Konfigurowanie ustawień dziennika

`Log` Obiekt ma domyślną implementację, która działa bez pliku konfiguracji aplikacji App. config. Aby zmienić wartości domyślne, należy dodać plik konfiguracji z nowymi ustawieniami. Aby uzyskać więcej informacji, zobacz [Przewodnik: filtrowanie danych wyjściowych my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

Sekcje konfiguracji dziennika znajdują się w `<system.diagnostics>` węźle głównym `<configuration>` pliku App. config. Informacje dziennika są zdefiniowane w kilku węzłach:

- Detektory dla `Log` obiektu są zdefiniowane w `<sources>` węźle o nazwie DefaultSource.

- Filtr ważności dla `Log` obiektu jest zdefiniowany w `<switches>` węźle o nazwie DefaultSwitch.

- Odbiorniki dzienników są zdefiniowane w `<sharedListeners>` węźle.

 Przykłady `<sources>`, `<switches>`i `<sharedListeners>` węzłów są pokazane w następującym kodzie:

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

Podczas tworzenia aplikacji jego ustawienia konfiguracji są przechowywane w pliku App. config, jak pokazano w powyższym przykładzie. Po wdrożeniu aplikacji można nadal skonfigurować dziennik, edytując plik konfiguracji. W aplikacji opartej na systemie Windows nazwa tego pliku to *ApplicationName*. exe. config i musi znajdować się w tym samym folderze co plik wykonywalny. W przypadku aplikacji sieci Web jest to plik Web. config skojarzony z projektem.

Gdy aplikacja wykonuje kod, który tworzy wystąpienie klasy po raz pierwszy, sprawdza plik konfiguracji w celu uzyskania informacji na temat obiektu. Dla `Log` obiektu, dzieje się to podczas pierwszego uzyskiwania dostępu `Log` do obiektu. System analizuje plik konfiguracyjny tylko raz dla każdego określonego obiektu — podczas pierwszego tworzenia obiektu przez aplikację. W związku z tym może być konieczne ponowne uruchomienie aplikacji, aby zmiany zaczęły obowiązywać.

W wdrożonej aplikacji należy włączyć kod śledzenia przez ponowne skonfigurowanie obiektów Switch przed uruchomieniem aplikacji. Zazwyczaj obejmuje to włączenie i wyłączenie obiektów przełącznika lub zmianę poziomów śledzenia, a następnie ponowne uruchomienie aplikacji.

## <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami

Podczas zapisywania danych do dziennika należy wziąć pod uwagę następujące kwestie:

- **Unikaj przecieku informacji o użytkownikach.** Upewnij się, że aplikacja zapisuje tylko zatwierdzone informacje w dzienniku. Na przykład może być to możliwe, aby dziennik aplikacji zawierał nazwy użytkowników, ale nie hasła użytkowników.

- **Ustaw lokalizacje dzienników jako bezpieczne.** Wszystkie dzienniki zawierające potencjalnie poufne informacje powinny być przechowywane w bezpiecznej lokalizacji.

- **Unikaj mylących informacji.** Ogólnie rzecz biorąc, aplikacja powinna sprawdzać poprawność wszystkich danych wprowadzonych przez użytkownika przed użyciem tych danych. Obejmuje to zapisywanie danych w dzienniku aplikacji.

- **Unikaj odmowy usługi.** Jeśli aplikacja zapisuje zbyt dużo informacji w dzienniku, może wypełnić dziennik lub utrudnić znalezienie ważnych informacji.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Rejestrowanie informacji z aplikacji](../../../../visual-basic/developing-apps/programming/log-info/index.md)
