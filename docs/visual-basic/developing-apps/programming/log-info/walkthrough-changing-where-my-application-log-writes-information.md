---
title: Zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: ab46f192f2e9549d0568737236742a366ce7b3a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592213"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a>Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji. W tym przewodniku przedstawiono sposób zastępują ustawienia domyślne i spowodować `Log` obiektu do zapisania do innych odbiorniki dzienników.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 `Log` Obiektu można zapisać informacji do kilku odbiorniki dzienników. Musisz określić bieżącą konfigurację odbiorników dziennika przed zmianą konfiguracji. Aby uzyskać więcej informacji, zobacz [wskazówki: Ustalanie gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 Warto przejrzeć [porady: zapis informacji o zdarzeniu do pliku tekstowego](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) lub [jak: zapisu do dziennika zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).  
  
### <a name="to-add-listeners"></a>Aby dodać obiekty nasłuchujące  
  
1.  Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.  
  
     \- lub -  
  
     Jeśli plik app.config, nie istnieje:  
  
    1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
    2.  Z **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku konfiguracji aplikacji**.  
  
    3.  Kliknij przycisk **Dodaj**.  
  
2.  Zlokalizuj `<listeners>` w obszarze `<source>` sekcji z `name` atrybutu "DefaultSource" w `<sources>` sekcji. `<sources>` Znajduje się w sekcji `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
3.  Dodaj te elementy w tym `<listeners>` sekcji.  
  
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
  
4.  Usuń znaczniki komentarza odbiorniki dzienników, które chcesz otrzymywać `Log` wiadomości.  
  
5.  Zlokalizuj `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.  
  
6.  Dodaj te elementy w tym `<sharedListeners>` sekcji.  
  
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
  
7.  Zawartość pliku app.config powinny być podobne do następującego kodu XML:  
  
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
  
1.  Zlokalizuj odbiornika `<add>` element z `<sharedListeners>` sekcji.  
  
2.  `type` Atrybut nadaje nazwę typu odbiornika. Ten typ musi dziedziczyć z <xref:System.Diagnostics.TraceListener> klasy. Aby upewnić się, że jest używany nieprawidłowy typ, użyj nazwy typu o silnej nazwie. Aby uzyskać więcej informacji zobacz "Aby odwoływać się do typu o silnej nazwie" sekcji poniżej.  
  
     Niektóre typy, które są dostępne są:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje do pliku dziennika.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje informacje w dzienniku zdarzeń komputera określona przez `initializeData` parametru.  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników, które zapisać do pliku określonego w `initializeData` parametru.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje do wiersza polecenia konsoli.  
  
     Aby dowiedzieć się, w którym innych typów odbiorniki logu zapisywać informacje zapoznaj się dokumentacją tego typu.  
  
3.  Gdy aplikacja tworzy obiekt dziennika odbiornika, przekazuje `initializeData` atrybut jako parametru konstruktora. Znaczenie `initializeData` atrybutu jest zależny od obiektu nasłuchującego śledzenia.  
  
4.  Po utworzeniu odbiornika dziennika, aplikacja ustawia właściwości odbiornika. Te właściwości są definiowane przez inne atrybuty w `<add>` elementu. Więcej informacji dotyczących właściwości dla określonego odbiornika w dokumentacji dla tego odbiornika typu.  
  
### <a name="to-reference-a-strongly-named-type"></a>Aby odwołać się do typu o silnej nazwie  
  
1.  Aby upewnić się, że nieprawidłowy typ jest używany przez odbiornik sieci dziennika, upewnij się, że nazwa FQDN typu i nazwa zestawu o silnej nazwie. O silnej nazwie typu ma następującą składnię:  
  
     \<*Nazwa typu*>, \< *nazwy zestawu*>, \< *numer wersji*>, \< *kultury*>, \< *silnej nazwy*>  
  
2.  Ten przykładowy kod przedstawia sposób określić nazwę typu o silnej nazwie FQDN type—"System.Diagnostics.FileLogTraceListener" w tym przypadku.  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     Jest to dane wyjściowe, i może służyć do unikatowego odwoływać się do typu o silnej nazwie, jak procedury "Aby dodać odbiorników" powyżej.  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>  
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>  
 [Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)  
 [Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
