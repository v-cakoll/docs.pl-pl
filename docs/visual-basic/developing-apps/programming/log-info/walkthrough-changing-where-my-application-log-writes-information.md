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

Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o zdarzeniach występujących w aplikacji. W tym instruktażu pokazano, jak zastąpić ustawienia domyślne i spowodować `Log` , że obiekt ma być zapisany w innych detektorach dzienników.

## <a name="prerequisites"></a>Wymagania wstępne

`Log` Obiekt może zapisywać informacje w kilku detektorach dzienników. Przed zmianą konfiguracji należy określić bieżącą konfigurację odbiorników dziennika. Aby uzyskać więcej informacji, zobacz [Przewodnik: Określanie, gdzie my. Application. Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

Warto zapoznać się z [tematem: zapisywanie informacji o zdarzeniach w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) lub [instrukcje: zapisywanie w dzienniku zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).

### <a name="to-add-listeners"></a>Aby dodać detektory

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

     \-oraz

     Jeśli nie ma pliku App. config:

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij pozycję **Add** (Dodaj).

2. Znajdź `<listeners>` sekcję `<source>` w sekcji z `name` atrybutem "DefaultSource" w `<sources>` sekcji. `<sources>` Sekcja znajduje się w `<system.diagnostics>` sekcji najwyższego poziomu `<configuration>` .

3. Dodaj te elementy do tej `<listeners>` sekcji.

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

4. Usuń znaczniki komentarza z odbiorników dziennika, dla `Log` których chcesz otrzymywać wiadomości.

5. Znajdź `<sharedListeners>` sekcję `<system.diagnostics>` w sekcji, w sekcji najwyższego poziomu `<configuration>` .

6. Dodaj te elementy do tej `<sharedListeners>` sekcji.

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

7. Zawartość pliku App. config powinna wyglądać podobnie do następującego kodu XML:

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

### <a name="to-reconfigure-a-listener"></a>Aby zmienić konfigurację odbiornika

1. Znajdź `<add>` element odbiornika z `<sharedListeners>` sekcji.

2. `type` Atrybut zawiera nazwę typu odbiornika. Ten typ musi dziedziczyć po <xref:System.Diagnostics.TraceListener> klasie. Użyj silnie nazwanego typu, aby upewnić się, że jest używany właściwy typ. Aby uzyskać więcej informacji, zobacz sekcję "Aby odwołać się do silnie nazwanego typu" poniżej.

     Niektóre typy, których można użyć, to:

    - <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> Odbiornik, który zapisuje dane w dzienniku plików.

    - <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> Odbiornik, który zapisuje informacje do dziennika zdarzeń komputera określonego przez `initializeData` parametr.

    - <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Detektory <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> i, które zapisują w pliku określonym w `initializeData` parametrze.

    - <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> Odbiornik, który zapisuje dane w konsoli wiersza polecenia.

     Aby uzyskać informacje o tym, gdzie inne typy odbiorników dzienników zapisują informacje, zapoznaj się z dokumentacją tego typu.

3. Gdy aplikacja tworzy obiekt odbiornika log, przekazuje `initializeData` atrybut jako parametr konstruktora. Znaczenie `initializeData` atrybutu zależy od odbiornika śledzenia.

4. Po utworzeniu odbiornika dziennika aplikacja ustawia właściwości odbiornika. Te właściwości są definiowane przez inne atrybuty w `<add>` elemencie. Aby uzyskać więcej informacji na temat właściwości określonego odbiornika, zapoznaj się z dokumentacją typu tego odbiornika.

### <a name="to-reference-a-strongly-named-type"></a>Aby odwołać się do silnie nazwanego typu

1. Aby upewnić się, że odpowiedni typ jest używany dla odbiornika dzienników, upewnij się, że używasz w pełni kwalifikowanej nazwy typu i silnie nazwanego zestawu. Składnia silnie nazwanego typu jest następująca:

     \<*Nazwa typu*>, \< *Nazwa zestawu*>, \< *numer wersji*>, \< *kultura*>, \< *silna nazwa*>

2. Ten przykład kodu pokazuje, jak w tym przypadku określić silnie nazwanego typu dla w pełni kwalifikowanego typu — "System. Diagnostics. FileLogTraceListener".

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     Jest to dane wyjściowe i mogą być używane do unikatowego odwoływania się do silnie nazwanego typu, tak jak w powyższej procedurze "Dodaj odbiorniki".

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
