---
title: "Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41e41f65b82061cebc52485ed08176633c45613d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia
Przełączniki śledzenia umożliwiają włączać, wyłączać i Filtruj dane wyjściowe śledzenia.  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a>Tworzenie i Inicjowanie przełącznika śledzenia  
 Aby można było używać przełączników śledzenia, najpierw musisz je utworzyć i umieść je w kodzie. Istnieją dwie klasy wstępnie zdefiniowane, z których można utworzyć obiektów przełącznika: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> klasy i <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> klasy. Należy użyć <xref:System.Diagnostics.BooleanSwitch> Jeśli interesujących Cię tylko czy pojawi się komunikat śledzenia; użyj <xref:System.Diagnostics.TraceSwitch> Aby rozróżnić poziomy śledzenia. Jeśli używasz <xref:System.Diagnostics.TraceSwitch>, można zdefiniować debugowania wiadomości i skojarzyć je z poziomów śledzenia różne. Można używać obu typów przełączników z śledzenia i debugowania. Domyślnie <xref:System.Diagnostics.BooleanSwitch> jest wyłączona i <xref:System.Diagnostics.TraceSwitch> jest ustawiony poziom <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. Przełączniki śledzenia można tworzyć i umieszczane w dowolnej części swój kod, który może używać ich.  
  
 Mimo że można ustawić poziomy śledzenia i inne opcje konfiguracji w kodzie, zalecane jest użycie pliku konfiguracji do zarządzania stanem przełączników. Jest to spowodowane zarządzania konfiguracją przełączników w systemie konfiguracji zapewnia większą elastyczność — można włączać i wyłączać różnych przełączników i zmienianie poziomów bez konieczności ponownego kompilowania aplikacji.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Aby utworzyć i zainicjować przełącznika śledzenia  
  
1.  Zdefiniuj przełącznikiem jako dowolnego typu <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> lub typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> i ustaw nazwę i opis przełącznika.  
  
2.  Skonfiguruj przełącznik śledzenia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](#configure).  
  
     Poniższy kod tworzy dwa przełączniki, jeden z każdego typu.  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =   
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =   
       new System.Diagnostics.TraceSwitch("General",   
       "Entire application");  
    ```  
  
<a name="configure"></a>   
## <a name="configuring-trace-switches"></a>Konfigurowanie przełączników śledzenia  
 Po aplikacji został rozesłany, nadal można włączyć lub wyłączyć dane wyjściowe śledzenia przez skonfigurowanie przełączników śledzenia w aplikacji. Konfigurowanie przełącznikiem oznacza, że zmiany jego wartość z zewnętrznego źródła po została zainicjowana. Można zmienić wartości obiektu przełącznika, przy użyciu pliku konfiguracji. Skonfiguruj przełącznika śledzenia, aby ją włączyć lub wyłączyć, lub jego poziom określania wielkości i typ wiadomości przekazuje do odbiorników.  
  
 Przełączniki są skonfigurowane przy użyciu pliku Config. Dla aplikacji sieci Web jest to plik Web.config skojarzony z projektem. W aplikacji systemu Windows, ten plik ma nazwę (nazwa aplikacji). exe.config. We wdrożonej aplikacji ten plik musi znajdować się w tym samym folderze co plik wykonywalny.  
  
 Podczas aplikacji kod, który tworzy wystąpienie przełącznika po raz pierwszy, sprawdza plik konfiguracji poziom śledzenia informacji o nazwanych przełącznika. Śledzenie system sprawdza pliku konfiguracji tylko raz dla dowolnego określonego przełącznika — aplikacja tworzy przełącznika po raz pierwszy.  
  
 We wdrożonej aplikacji możesz włączyć kod śledzenia za ponownej konfiguracji przełącznika obiektów, kiedy aplikacja nie jest uruchomiona. Zazwyczaj wiąże się to Włączanie obiektami przełącznika i wyłączyć lub zmieniając poziomy śledzenia, a następnie ponowne uruchomienie aplikacji.  
  
 Podczas tworzenia wystąpienia przełącznika można również zainicjować go przez określenie dwa argumenty: *displayName* argumentu i *opis* argumentu. *DisplayName* argument zestawów konstruktora <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> właściwość <xref:System.Diagnostics.Switch> wystąpienie klasy. *DisplayName* to nazwa, która jest używana do konfigurowania przełącznika w pliku .config i *opis* argument powinien zwrócić krótki opis przełączników i jakie komunikaty kontrolki.  
  
 Oprócz określenia nazwy przełącznika można skonfigurować, należy określić wartość dla tego przełącznika. Ta wartość jest liczbą całkowitą. Dla <xref:System.Diagnostics.BooleanSwitch>, wartość 0 odpowiada **poza**, i odpowiada dowolną wartość niezerową **na**. Dla <xref:System.Diagnostics.TraceSwitch>0,1,2,3 i 4 odpowiada **poza**, **błąd**, **ostrzeżenie**, **informacji**, i **pełne**odpowiednio. Wszystkie liczby większe niż 4 jest traktowany jako **pełne**oraz numer mniej niż zero jest traktowany jako **poza**.  
  
> [!NOTE]
>  W programie .NET Framework w wersji 2.0 tekst można użyć do określenia wartości dla przełącznika. Na przykład `true` dla <xref:System.Diagnostics.BooleanSwitch> lub tekst reprezentujący wartości wyliczenia, takich jak `Error` dla <xref:System.Diagnostics.TraceSwitch>. Wiersz `<add name="myTraceSwitch" value="Error" />` jest odpowiednikiem `<add name="myTraceSwitch" value="1" />`.  
  
 Aby użytkownicy końcowi mogli Konfigurowanie przełączników śledzenia aplikacji musisz podać szczegółowa dokumentacja na temat parametrów w aplikacji. Należy szczegółowo, które przełączniki kontroli co oraz jak je włączyć i wyłączyć. Należy również podać użytkownikowi końcowemu z pliku .config, który ma odpowiednie pomocy w komentarzach.  
  
#### <a name="to-configure-trace-switches"></a>Aby skonfigurować przełączniki śledzenia  
  
1.  Aby można było używać przełączników śledzenia, najpierw musisz je utworzyć i umieść je w kodzie, zgodnie z opisem w sekcji [tworzenie i Inicjowanie przełącznika śledzenia](#create).  
  
2.  Jeśli projekt zawiera plik konfiguracji (app.config lub Web.config), następnie z **projektu** menu, wybierz opcję **Dodaj nowy element**.  
  
    -   **Visual Basic:** w **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.  
  
         Plik konfiguracji aplikacji jest utworzony i otwarty. To jest dokument XML, którego element główny jest`<configuration>.`  
  
    -   **Visual C#:** w **Dodaj nowy element** oknie dialogowym wybierz **pliku XML**. Nazwij ten plik **app.config**. W edytorze XML po deklaracji XML, Dodaj następujący kod XML:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Podczas kompilowania projektu pliku app.config jest kopiowany do folderu wyjściowego projektu i zostanie zmieniona nazwa *applicationname*. exe.config.  
  
3.  Po `<configuration>` tagów, ale przed wysłaniem `</configuration>` tagów, Dodaj odpowiednie XML do skonfigurowania przełączników. W poniższych przykładach pokazano **BooleanSwitch** z **DisplayName** właściwość `DataMessageSwitch` i **TraceSwitch** z **Nazwa wyświetlana**  właściwość `TraceLevelSwitch`.  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     W tej konfiguracji obu przełączniki są wyłączone.  
  
4.  Jeśli konieczne jest włączenie **BooleanSwitch**, takich jak `DataMessagesSwitch` pokazano w poprzednim przykładzie, zmień **wartość** do dowolnej liczby całkowitej niż 0.  
  
5.  Jeśli konieczne jest włączenie **TraceSwitch**, takich jak `TraceLevelSwitch` pokazano w poprzednim przykładzie, zmień **wartość** odpowiednich ustawień poziomu (od 1 do 4).  
  
6.  Dodawanie komentarzy do pliku .config, aby użytkownik końcowy miał przejrzysty jakie wartości, aby zmienić odpowiednio skonfigurować przełączników.  
  
     W poniższym przykładzie pokazano, jak może wyglądać końcowego kodu, w tym komentarzy:  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Schemat ustawień śledzenia i debugowania](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
