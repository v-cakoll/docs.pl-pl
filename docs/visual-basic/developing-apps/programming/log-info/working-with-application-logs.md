---
title: Praca z dziennikami aplikacji w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 00c54a59ccfe2a49dcf35b322ca077a10a48ae7d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839642"
---
# <a name="working-with-application-logs-in-visual-basic"></a>Praca z dziennikami aplikacji w Visual Basic

`My.Application.Log` i `My.Log` obiektów ułatwiają zapisu rejestrowania i śledzenia informacji w dziennikach.

## <a name="how-messages-are-logged"></a>Jak komunikaty są rejestrowane.

Najpierw ważności komunikatu został sprawdzony i <xref:System.Diagnostics.TraceSource.Switch%2A> właściwości dziennika <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> właściwości. Przez domyślne, tylko komunikaty o ważności "Informacje" i nowszej są przekazywane do detektorów śledzenia określony w dzienniku `TraceListener` kolekcji. Następnie każdego odbiornika porównuje ważność wiadomości do odbiornika <xref:System.Diagnostics.TraceSource.Switch%2A> właściwości. Jeśli ważność komunikatu jest wystarczająco wysoka, odbiornik zapisuje się komunikatu.

Na poniższym diagramie przedstawiono, w jaki sposób wiadomość zapisywane `WriteEntry` przekazywane do metody `WriteLine` obiekty nasłuchujące śledzenia metody dziennika:

![Diagram przedstawiający Moje wywołania dziennika.](./media/working-with-application-logs/my-log-call-messages.png)

Możesz zmienić zachowanie dziennika i śledzenia słuchaczy, zmieniając pliku konfiguracji aplikacji. Na poniższym diagramie przedstawiono związek między częściami dziennika i pliku konfiguracji.

![Diagram przedstawiający konfigurację dziennika.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a>Gdzie są rejestrowane komunikaty

Jeśli zestaw ma plik konfiguracji nie `My.Application.Log` i `My.Log` obiektów zapisywać dane wyjściowe debugowania aplikacji (za pośrednictwem <xref:System.Diagnostics.DefaultTraceListener> klasy). Ponadto `My.Application.Log` obiekt zapisuje do pliku dziennika zestawu (za pośrednictwem <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> klasy), gdy `My.Log` obiekt zapisuje dane wyjściowe strony sieci Web platformy ASP.NET (za pośrednictwem <xref:System.Web.WebPageTraceListener> klasy).

Dane wyjściowe debugowania mogą być wyświetlane w programie Visual Studio **dane wyjściowe** okna podczas uruchamiania aplikacji w trybie debugowania. Aby otworzyć **dane wyjściowe** okna, kliknij przycisk **debugowania** elementu menu, wskaż **Windows**, a następnie kliknij przycisk **dane wyjściowe**. W **dane wyjściowe** wybierz **debugowania** z **Pokaż dane wyjściowe z** pole.

Domyślnie `My.Application.Log` zapisuje plik dziennika w ścieżce dla danych aplikacji użytkownika. Możesz uzyskać ścieżkę z <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> właściwość <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> obiektu. Format tej ścieżki jest następująca:

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

Typowa wartość dla `BasePath` jest następujący.

C:\Documents and Settings\\`username`\Application danych

Wartości `CompanyName`, `ProductName`, i `ProductVersion` pochodzą z informacjami o zestawie aplikacji. Nazwa pliku dziennika jest *AssemblyName*.log, gdzie *AssemblyName* jest nazwą pliku zestawu bez rozszerzenia. Jeśli potrzebna jest więcej niż jeden plik dziennika, np. gdy oryginalny plik dziennika jest niedostępny podczas aplikacja próbuje zapisać w dzienniku, formularz dla nazwy pliku dziennika jest *AssemblyName*-*iteracji* .log, gdzie `iteration` jest dodatni `Integer`.

Zachowanie domyślne można przesłonić, przez dodanie lub zmiana plik konfiguracji komputera i aplikacji. Aby uzyskać więcej informacji, zobacz [instruktażu: Zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).

## <a name="configuring-log-settings"></a>Konfigurowanie ustawień dziennika

`Log` Obiekt ma domyślną implementację, która działa bez pliku konfiguracji aplikacji, pliku app.config. Aby zmienić ustawienia domyślne, należy dodać plik konfiguracji z nowymi ustawieniami. Aby uzyskać więcej informacji, zobacz [instruktażu: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

W sekcjach konfiguracji dziennika znajdują się w `<system.diagnostics>` węzła w głównym `<configuration>` węzła pliku app.config. Informacje w dzienniku jest zdefiniowana w kilka węzłów:

- Detektory `Log` obiektu są zdefiniowane w `<sources>` węzeł o nazwie DefaultSource.

- Filtr ważność `Log` obiekt jest zdefiniowany w `<switches>` węzeł o nazwie DefaultSwitch.

- Odbiorniki logu są zdefiniowane w `<sharedListeners>` węzła.

 Przykłady `<sources>`, `<switches>`, i `<sharedListeners>` węzły są wyświetlane w następującym kodzie:

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

Podczas opracowywania aplikacji, jego ustawienia konfiguracji są przechowywane w pliku app.config, jak pokazano w przykładach. Po wdrożeniu aplikacji będzie możliwe skonfigurowanie dziennika, edytując plik konfiguracji. W przypadku aplikacji z systemem Windows jest nazwę tego pliku *applicationName*. exe.config i musi znajdować się w tym samym folderze co plik wykonywalny. Dla aplikacji sieci Web jest skojarzony z projektem pliku Web.config.

Gdy aplikacja wykonuje kod, który tworzy wystąpienie klasy po raz pierwszy, sprawdza plik konfiguracji, aby uzyskać informacje o obiekcie. Aby uzyskać `Log` obiektu, dzieje się po raz pierwszy `Log` dostępu do obiektu. System sprawdza, czy plik konfiguracyjny tylko raz dla każdego określonego obiektu — aplikacja tworzy obiekt po raz pierwszy. Dlatego może być konieczne ponowne uruchomienie aplikacji, aby zmiany zaczęły obowiązywać.

We wdrożonej aplikacji włączysz kod śledzenia przez ponowne skonfigurowanie obiektami przełącznika, przed uruchomieniem aplikacji. Zazwyczaj ten proces obejmuje Włączanie obiektami przełącznika i wyłączyć lub zmieniając poziomy śledzenia, a następnie ponownie uruchomić aplikację.

## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń

Podczas zapisywania danych w dzienniku, należy wziąć pod uwagę następujące czynności:

- **Wyciekiem informacje o użytkowniku.** Upewnij się, że zapisów aplikacji tylko zatwierdzone informacji w dzienniku. Na przykład może być możliwa do dziennika aplikacji, które ma zawierać nazwy użytkownika, ale nie hasło użytkownika.

- **Lokalizacje dziennika zapewnić bezpieczeństwo.** Żadnych dzienników, która zawiera potencjalnie poufne informacje powinny być przechowywane w bezpiecznej lokalizacji.

- **Należy unikać mylących informacji.** Ogólnie rzecz biorąc aplikację należy zweryfikować wszystkie dane wprowadzane przez użytkownika przed rozpoczęciem korzystania z tych danych. Obejmuje to zapisywanie danych w dzienniku aplikacji.

- **Należy unikać "odmowa usługi".** Jeśli aplikacja zapisuje zbyt dużej ilości informacji w dzienniku, jest wypełnienie dziennika lub ułatwić znajdowanie trudne do ważnych informacji.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Rejestrowanie informacji z aplikacji](../../../../visual-basic/developing-apps/programming/log-info/index.md)
