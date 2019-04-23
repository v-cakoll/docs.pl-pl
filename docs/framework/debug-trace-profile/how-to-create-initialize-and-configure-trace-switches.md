---
title: 'Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia'
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87170035df47e7605d25531df4b0759bf121ad80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325712"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia
Przełączniki śledzenia umożliwiają włączać, wyłączać i filtrować dane wyjściowe śledzenia.  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a>Tworzenie i Inicjowanie przełącznikiem śledzenia  
 Aby można było używać przełączników śledzenia, należy najpierw utworzyć je i umieścić je w kodzie. Istnieją dwie klasy wstępnie zdefiniowanych, z których możesz tworzyć obiekty przełącznika: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> klasy i <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> klasy. Należy użyć <xref:System.Diagnostics.BooleanSwitch> interesujące Cię tylko czy pojawi się komunikat śledzenia; należy użyć <xref:System.Diagnostics.TraceSwitch> Aby rozróżnić poziomy śledzenia. Jeśli używasz <xref:System.Diagnostics.TraceSwitch>, można zdefiniować własne komunikatów debugowania i skojarzyć je z różnymi poziomami śledzenia. Można użyć obu rodzajów przełączników przy użyciu śledzenia i debugowania. Domyślnie <xref:System.Diagnostics.BooleanSwitch> jest wyłączona i <xref:System.Diagnostics.TraceSwitch> jest ustawiona na poziomie <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. Przełączniki śledzenia można tworzyć i umieszczane w dowolnej części swój kod, który może ich używać.  
  
 Mimo że w kodzie, można ustawić poziomu śledzenia i inne opcje konfiguracji, zaleca się użyć pliku konfiguracji do zarządzania stanem przełączników. Jest to spowodowane zarządzania konfiguracją przełączników w systemie konfiguracji zapewnia większą elastyczność — można włączać i wyłączać różnych przełączników i zmieniać poziomy bez konieczności ponownego kompilowania aplikacji.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Aby utworzyć i zainicjować przełącznikiem śledzenia  
  
1. Przełącznik jest definiowana jako dowolnego typu <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> lub typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> i ustaw nazwę i opis przełącznika.  
  
2. Skonfiguruj na przełączniku śledzenia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](#configure).  
  
     Poniższy kod tworzy dwa przełączniki, jeden dla każdego typu.  
  
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
 Po aplikacji został rozesłany, nadal można włączyć lub wyłączyć dane wyjściowe śledzenia przez skonfigurowanie przełączników śledzenia w aplikacji. Konfigurowanie przełącznika oznacza, zmieniając jego wartość z zewnętrznego źródła, po jego zainicjowaniu. Można zmienić wartości obiektów przełącznika, przy użyciu pliku konfiguracji. Skonfiguruj przełącznikiem śledzenia, aby go włączyć i wyłączyć lub ustawić jego poziom Określanie wielkość i typ wiadomości przekazywane wraz z do odbiorników.  
  
 Przełączniki są skonfigurowane przy użyciu pliku Config. Dla aplikacji sieci Web jest skojarzony z projektem pliku Web.config. W aplikacji Windows, ten plik ma nazwę (nazwa aplikacji). exe.config. We wdrożonej aplikacji ten plik musi znajdować się w tym samym folderze co plik wykonywalny.  
  
 Gdy aplikacja wykonuje kod, który tworzy wystąpienie przełącznika po raz pierwszy, sprawdza plik konfiguracyjny dla poziomu śledzenia informacji o przełącznikiem o nazwie. System śledzenia sprawdza plik konfiguracyjny tylko raz dla dowolnego określonego przełącznika — aplikacja tworzy przełącznik po raz pierwszy.  
  
 Ponowne skonfigurowanie obiektami przełącznika, gdy aplikacja nie jest uruchomiona, we wdrożonej aplikacji włączyć kod śledzenia. Zazwyczaj ten proces obejmuje Włączanie obiektami przełącznika i wyłączyć lub zmieniając poziomy śledzenia, a następnie ponownie uruchomić aplikację.  
  
 Podczas tworzenia wystąpienia przełącznika również jej inicjalizację, określając dwa argumenty: *displayName* argumentu i *opis* argumentu. *DisplayName* argument zestawy Konstruktor <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> właściwość <xref:System.Diagnostics.Switch> wystąpienia klasy. *DisplayName* jest nazwa, która służy do konfigurowania przełącznika w pliku config i *opis* argument powinien zwrócić krótki opis przełącznika i jakie komunikaty kontrolki.  
  
 Oprócz określenia nazwy przełącznika w celu skonfigurowania, należy także określić wartość dla przełącznika. Ta wartość jest liczbą całkowitą. Dla <xref:System.Diagnostics.BooleanSwitch>, wartości 0 odpowiada **poza**, i odpowiada dowolną wartość różną od zera **na**. Dla <xref:System.Diagnostics.TraceSwitch>0,1,2,3 oraz 4 odpowiadają **poza**, **błąd**, **ostrzeżenie**, **informacje**, i **pełne**, odpowiednio. Wszystkie liczby większe niż 4 jest traktowany jako **pełne**oraz numer mniej niż zero jest traktowany jako **poza**.  
  
> [!NOTE]
>  W .NET Framework w wersji 2.0 można użyć tekstu, aby określić wartość dla przełącznika. Na przykład `true` dla <xref:System.Diagnostics.BooleanSwitch> lub tekstu, takie jak reprezentujących wartości wyliczenia `Error` dla <xref:System.Diagnostics.TraceSwitch>. Wiersz `<add name="myTraceSwitch" value="Error" />` jest odpowiednikiem `<add name="myTraceSwitch" value="1" />`.  
  
 Aby użytkownicy końcowi mogli Konfigurowanie przełączników śledzenia aplikacji musisz podać szczegółową dokumentację na temat parametrów w aplikacji. Należy szczegółowo, które przełączniki kontrolować, co oraz sposób ich włączać i wyłączać. Należy również podać użytkownikowi końcowemu przy użyciu pliku .config zawierającej odpowiednią pomoc w komentarzach.  
  
#### <a name="to-configure-trace-switches"></a>Aby skonfigurować przełączniki śledzenia  
  
1. Aby można było używać przełączników śledzenia, najpierw należy je utworzyć i umieść je w swoim kodzie, zgodnie z opisem w sekcji [tworzenie i Inicjowanie przełącznikiem śledzenia](#create).  
  
2. Jeśli projekt nie zawiera pliku konfiguracji (app.config lub Web.config), następnie z **projektu** menu, wybierz opcję **Dodaj nowy element**.  
  
    -   **Visual Basic:** W **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.  
  
         Plik konfiguracji aplikacji zostanie utworzony i otwarty. To jest którego element główny dokumentu XML `<configuration>.`  
  
    -   **Wizualne C#:** W **Dodaj nowy element** okna dialogowego wybierz **pliku XML**. Nazwij ten plik **app.config**. W edytorze XML, po deklaracji XML, Dodaj następujący kod XML:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Podczas kompilowania projektu pliku app.config jest kopiowany do folderu wyjściowego projektu i została zmieniona *applicationname*. exe.config.  
  
3. Po `<configuration>` tagu, ale przed `</configuration>` tag, Dodaj odpowiedni kod XML do skonfigurowania przełączników. W poniższych przykładach pokazano **BooleanSwitch** z **DisplayName** właściwość `DataMessageSwitch` i **TraceSwitch** z **DisplayName**  właściwość `TraceLevelSwitch`.  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     W tej konfiguracji oba przełączniki są wyłączone.  
  
4. Jeśli konieczne jest włączenie **BooleanSwitch**, takich jak `DataMessagesSwitch` pokazano w poprzednim przykładzie, zmień **wartość** do dowolnej liczby całkowitej, innym niż 0.  
  
5. Jeśli konieczne jest włączenie **TraceSwitch**, takich jak `TraceLevelSwitch` pokazano w poprzednim przykładzie, zmień **wartość** odpowiednie ustawienie poziomie (od 1 do 4).  
  
6. Aby użytkownik końcowy miał świadomość, jakich wartości można zmienić na odpowiednio skonfigurować przełączniki, dodać komentarze do pliku Config.  
  
     Poniższy przykład pokazuje, jak może wyglądać końcowego kodu, w tym komentarzy:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Schemat ustawień śledzenia i debugowania](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
