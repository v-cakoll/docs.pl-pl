---
title: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: bdee0a91360580b156c1734ef4c82139b18ce2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74336735"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)

Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji. W tym przewodniku pokazano, jak zastąpić ustawienia domyślne i spowodować, że obiekt do zapisu `Log` do innych detektorów dziennika.

## <a name="prerequisites"></a>Wymagania wstępne

Obiekt `Log` może zapisywać informacje do kilku odbiorników dziennika. Przed zmianą konfiguracji należy określić bieżącą konfigurację odbiorników dziennika. Aby uzyskać więcej informacji, zobacz [Przewodnik: Określanie, gdzie my.application.log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

Możesz przejrzeć [jak: Zapis informacji o zdarzeniu w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) lub [Jak: Zapis w dzienniku zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).

### <a name="to-add-listeners"></a>Aby dodać słuchaczy

1. Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**.

     \-lub -

     Jeśli nie ma pliku app.config:

    1. W menu **Projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Znajdź `<listeners>` sekcję w `<source>` sekcji `name` z atrybutem "DefaultSource" w `<sources>` sekcji. Sekcja `<sources>` znajduje się `<system.diagnostics>` w sekcji, w `<configuration>` sekcji najwyższego poziomu.

3. Dodaj te elementy `<listeners>` do tej sekcji.

    ```xml
    <!-- Uncomment to connect the application file log. -->
    <!-- <add name="FileLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="EventLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="Delimited" /> -->
    <!-- Uncomment to connect the XML log. -->
    <!-- <add name="XmlWriter" /> -->
    <!-- Uncomment to connect the console log. -->
    <!-- <add name="Console" /> -->
    ```

4. Odkomentuj detektory dziennika, `Log` które chcesz odbierać wiadomości.

5. Zlokalizuj `<sharedListeners>` `<system.diagnostics>` sekcję w sekcji `<configuration>` w sekcji najwyższego poziomu.

6. Dodaj te elementy `<sharedListeners>` do tej sekcji.

    ```xml
    <add name="FileLog"
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
               Microsoft.VisualBasic, Version=8.0.0.0,
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
         initializeData="FileLogWriter" />
    <add name="EventLog"
         type="System.Diagnostics.EventLogTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="sample application"/>
    <add name="Delimited"
         type="System.Diagnostics.DelimitedListTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleDelimitedFile.txt"
         traceOutputOptions="DateTime" />
    <add name="XmlWriter"
         type="System.Diagnostics.XmlWriterTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleLogFile.xml" />
    <add name="Console"
         type="System.Diagnostics.ConsoleTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="true" />
    ```

7. Zawartość pliku app.config powinna być podobna do następującej opcji XML:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Uncomment to connect the application file log. -->
              <!-- <add name="FileLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="EventLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="Delimited" /> -->
              <!-- Uncomment to connect the XML log. -->
              <!-- <add name="XmlWriter" /> -->
              <!-- Uncomment to connect the console log. -->
              <!-- <add name="Console" /> -->
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
               initializeData="FileLogWriter" />
          <add name="EventLog"
               type="System.Diagnostics.EventLogTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="sample application"/>
          <add name="Delimited"
               type="System.Diagnostics.DelimitedListTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleDelimitedFile.txt"
               traceOutputOptions="DateTime" />
          <add name="XmlWriter"
               type="System.Diagnostics.XmlWriterTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleLogFile.xml" />
          <add name="Console"
               type="System.Diagnostics.ConsoleTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="true" />
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

### <a name="to-reconfigure-a-listener"></a>Aby ponownie skonfigurować odbiornik

1. Znajdź element odbiornika `<add>` z `<sharedListeners>` sekcji.

2. Atrybut `type` podaje nazwę typu odbiornika. Ten typ musi <xref:System.Diagnostics.TraceListener> dziedziczyć z klasy. Użyj silnie nazwanej nazwy nazwy typu, aby upewnić się, że używany jest odpowiedni typ. Aby uzyskać więcej informacji, zobacz sekcję "Aby odwołać się do typu o silnie nazwanej" poniżej.

     Niektóre typy, których można użyć, to:

    - Odbiornik, <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> który zapisuje do dziennika plików.

    - Odbiornik, <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> który zapisuje informacje do dziennika zdarzeń `initializeData` komputera określonych przez parametr.

    - I <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników, które zapisują do `initializeData` pliku określonego w parametrze.

    - Odbiornik, <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> który zapisuje do konsoli wiersza polecenia.

     Aby uzyskać informacje o tym, gdzie inne typy detektorów dziennika zapisują informacje, zapoznaj się z dokumentacją tego typu.

3. Gdy aplikacja tworzy obiekt detektora dziennika, `initializeData` przekazuje atrybut jako parametr konstruktora. Znaczenie atrybutu `initializeData` zależy od odbiornika śledzenia.

4. Po utworzeniu odbiornika dziennika aplikacja ustawia właściwości odbiornika. Te właściwości są definiowane przez `<add>` inne atrybuty w elemencie. Aby uzyskać więcej informacji na temat właściwości dla określonego odbiornika, zobacz dokumentację dla tego typu odbiornika.

### <a name="to-reference-a-strongly-named-type"></a>Aby odwołać się do typu o silnie nazwanym

1. Aby upewnić się, że odpowiedni typ jest używany dla odbiornika dziennika, upewnij się, że używa się w pełni kwalifikowanej nazwy typu i silnie nazwanej nazwy zestawu. Składnia typu o silnie nazwanym typie jest następująca:

     \<*nazwa typu* \<>, *> nazwy zestawu,* \< *> numeru wersji,* \<> *kultury,* \< *nazwa*>

2. W tym przykładzie kodu pokazano, jak określić nazwę typu o silnie nazwanej dla w pełni kwalifikowanego typu — "System.Diagnostics.FileLogTraceListener" w tym przypadku.

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     Jest to dane wyjściowe i może służyć do unikatowego odwoływania się do typu o silnie nazwanych, jak w procedurze "Aby dodać odbiorniki" powyżej.

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
