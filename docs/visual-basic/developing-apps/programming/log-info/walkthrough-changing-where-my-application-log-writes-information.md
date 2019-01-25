---
title: Zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: b0d9e40f3f41eac5b16037a89a3cac45cbfc8c57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574449"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji. W tym instruktażu przedstawiono sposób zastępują ustawienia domyślne i spowodować, że `Log` obiektu do zapisania do innych nasłuchujących dziennika.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 `Log` Obiektu można zapisać informacji do kilku odbiorniki logu. Należy określić bieżącą konfigurację odbiorniki logu przed zmianą konfiguracji. Aby uzyskać więcej informacji, zobacz [instruktażu: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 Warto przejrzeć [jak: Zapisywanie informacji o pliku tekstowego zdarzeniach](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) lub [jak: Zapisywanie w rejestrze zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).  
  
### <a name="to-add-listeners"></a>Aby dodać obiekty nasłuchujące  
  
1.  Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.  
  
     \- lub —  
  
     Jeśli nie ma żadnego pliku app.config:  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Znajdź `<listeners>` sekcji w obszarze `<source>` sekcji z `name` atrybutu "DefaultSource" w `<sources>` sekcji. `<sources>` Znajduje się w sekcji `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.  
  
3.  Dodaj te elementy, `<listeners>` sekcji.  
  
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
  
4.  Usuń znaczniki komentarza odbiorniki logu, które chcesz otrzymywać `Log` wiadomości.  
  
5.  Znajdź `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.  
  
6.  Dodaj te elementy, `<sharedListeners>` sekcji.  
  
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
  
7.  Zawartość pliku app.config powinien wyglądać podobnie jak następujący kod XML:  
  
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
  
1.  Znajdź odbiornika `<add>` elementu z `<sharedListeners>` sekcji.  
  
2.  `type` Atrybut zawiera nazwę typu odbiornika. Ten typ musi dziedziczyć <xref:System.Diagnostics.TraceListener> klasy. Aby upewnić się, że właściwego typu jest używany, należy użyć nazwy o silnej nazwie typu. Aby uzyskać więcej informacji zobacz "Aby odwołać się do typu o silnej nazwie" sekcji poniżej.  
  
     Niektóre typy, które są dostępne są:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje je do pliku dziennika.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje informacje w dzienniku zdarzeń komputera, które są określone przez `initializeData` parametru.  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników, które zapis do pliku określonego w `initializeData` parametru.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje je w wiersza polecenia konsoli.  
  
     Uzyskać informacji o tym, gdzie innych rodzajów odbiorniki logu wpisać informacje zapoznaj się dokumentacją tego typu.  
  
3.  Gdy aplikacja tworzy obiekt odbiornika dziennika, przekazuje on `initializeData` atrybutu jako parametr konstruktora. Znaczenie `initializeData` atrybutu jest zależna od odbiornika śledzenia.  
  
4.  Po utworzeniu odbiornika dziennika, aplikacja ustawia właściwości odbiornika. Te właściwości są definiowane przez inne atrybuty `<add>` elementu. Aby uzyskać więcej informacji na właściwości określonego odbiornika zobacz dokumentację dla tego odbiornika typu.  
  
### <a name="to-reference-a-strongly-named-type"></a>Aby odwołać się do typu o silnej nazwie  
  
1.  Aby upewnić się, że właściwego typu jest używany do z odbiornikiem dziennika, upewnij się użyć w pełni kwalifikowana nazwa typu i nazwy zestawu o silnej nazwie. Składnia typu o silnej nazwie jest w następujący sposób:  
  
     \<*Nazwa typu*>, \< *nazwy zestawu*>, \< *numer wersji*>, \< *kultury*>, \< *silnej nazwy*>  
  
2.  Ten przykład kodu pokazuje, jak można ustalić nazwy typu o silnej nazwie do w pełni kwalifikowaną type—"System.Diagnostics.FileLogTraceListener" w tym przypadku.  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     Jest to dane wyjściowe i może służyć do unikatowego odwołać się do typu o silnej nazwie, jak procedury "Aby dodać obiekty nasłuchujące" powyżej.  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [Instrukcje: Zapisywanie informacji zdarzeniach w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [Instrukcje: Zapisywanie w rejestrze zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
