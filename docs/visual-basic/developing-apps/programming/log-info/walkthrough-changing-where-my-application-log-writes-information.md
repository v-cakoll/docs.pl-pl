---
title: Zmienianie, gdzie my. Application. Log zapisuje informacje (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: 358638d50e347334487665b950b33a045b6a39f9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524409"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)

Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o zdarzeniach występujących w aplikacji. W tym instruktażu pokazano, jak zastąpić ustawienia domyślne i spowodować, że obiekt `Log` ma zapisywać w innych detektorach dzienników.

## <a name="prerequisites"></a>Wymagania wstępne

Obiekt `Log` może zapisywać informacje do kilku odbiorników dzienników. Przed zmianą konfiguracji należy określić bieżącą konfigurację odbiorników dziennika. Aby uzyskać więcej informacji, zobacz [Przewodnik: Określanie, gdzie my. Application. Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).

Warto zapoznać się z [tematem: zapisywanie informacji o zdarzeniach w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) lub [instrukcje: zapisywanie w dzienniku zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).

### <a name="to-add-listeners"></a>Aby dodać detektory

1. Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.

     \- lub-

     Jeśli nie ma pliku App. config:

    1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.

    3. Kliknij przycisk **Dodaj**.

2. Znajdź sekcję `<listeners>` w sekcji `<source>` z atrybutem `name` "DefaultSource" w sekcji `<sources>`. Sekcja `<sources>` znajduje się w sekcji `<system.diagnostics>`, w sekcji `<configuration>` najwyższego poziomu.

3. Dodaj te elementy do tej sekcji `<listeners>`.

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

4. Usuń znaczniki komentarza z odbiorników dziennika, które mają zostać odebrane `Log` komunikatów.

5. Znajdź sekcję `<sharedListeners>` w sekcji `<system.diagnostics>` w sekcji `<configuration>` najwyższego poziomu.

6. Dodaj te elementy do tej sekcji `<sharedListeners>`.

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

1. Znajdź element `<add>` odbiornika z sekcji `<sharedListeners>`.

2. @No__t_0 atrybut zawiera nazwę typu odbiornika. Ten typ musi dziedziczyć z klasy <xref:System.Diagnostics.TraceListener>. Użyj silnie nazwanego typu, aby upewnić się, że jest używany właściwy typ. Aby uzyskać więcej informacji, zobacz sekcję "Aby odwołać się do silnie nazwanego typu" poniżej.

     Niektóre typy, których można użyć, to:

    - Odbiornik <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>, który zapisuje dane w dzienniku plików.

    - Odbiornik <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>, który zapisuje informacje w dzienniku zdarzeń komputera określonym przez parametr `initializeData`.

    - @No__t_0 i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> detektory, które zapisują w pliku określonym w parametrze `initializeData`.

    - Odbiornik <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>, który zapisuje dane w konsoli wiersza polecenia.

     Aby uzyskać informacje o tym, gdzie inne typy odbiorników dzienników zapisują informacje, zapoznaj się z dokumentacją tego typu.

3. Gdy aplikacja tworzy obiekt odbiornika log, przekazuje atrybut `initializeData` jako parametr konstruktora. Znaczenie atrybutu `initializeData` zależy od odbiornika śledzenia.

4. Po utworzeniu odbiornika dziennika aplikacja ustawia właściwości odbiornika. Te właściwości są definiowane przez inne atrybuty elementu `<add>`. Aby uzyskać więcej informacji na temat właściwości określonego odbiornika, zapoznaj się z dokumentacją typu tego odbiornika.

### <a name="to-reference-a-strongly-named-type"></a>Aby odwołać się do silnie nazwanego typu

1. Aby upewnić się, że odpowiedni typ jest używany dla odbiornika dzienników, upewnij się, że używasz w pełni kwalifikowanej nazwy typu i silnie nazwanego zestawu. Składnia silnie nazwanego typu jest następująca:

     *Nazwa typu*\< >, \<*Nazwa zestawu*>, \<*numer wersji*>, \<*kultur*>, \<*silnej nazwy* 0

2. Ten przykład kodu pokazuje, jak w tym przypadku określić silnie nazwanego typu dla w pełni kwalifikowanego typu — "System. Diagnostics. FileLogTraceListener".

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     Jest to dane wyjściowe i mogą być używane do unikatowego odwoływania się do silnie nazwanego typu, tak jak w powyższej procedurze "Dodaj odbiorniki".

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
