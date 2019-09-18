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
ms.openlocfilehash: 13f89af41520fa023d8841d6dc6d7766e2abe6da
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052710"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia
Przełączniki śledzenia umożliwiają włączenie, wyłączenie i filtrowanie danych wyjściowych śledzenia.  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a>Tworzenie i Inicjowanie przełącznika śledzenia  
 Aby można było używać przełączników śledzenia, należy najpierw je utworzyć i umieścić w kodzie. Istnieją dwie wstępnie zdefiniowane klasy, z których można tworzyć obiekty przełącznika: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> klasy <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> i klasy. Należy użyć <xref:System.Diagnostics.BooleanSwitch> , jeśli chcesz się dowiedzieć, czy jest wyświetlany komunikat śledzenia, <xref:System.Diagnostics.TraceSwitch> Jeśli chcesz rozróżnić poziomy śledzenia. W przypadku korzystania z <xref:System.Diagnostics.TraceSwitch>programu można definiować własne komunikaty debugowania i kojarzyć je z różnymi poziomami śledzenia. Można użyć obu typów przełączników z funkcją śledzenia lub debugowania. Domyślnie <xref:System.Diagnostics.BooleanSwitch> jest wyłączona <xref:System.Diagnostics.TraceSwitch> i jest ustawiona na poziom <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. Przełączniki śledzenia można tworzyć i umieszczać w dowolnej części kodu, który może z nich korzystać.  
  
 Chociaż można ustawić poziomy śledzenia i inne opcje konfiguracji w kodzie, zalecamy użycie pliku konfiguracji do zarządzania stanem przełączników. Jest to spowodowane tym, że zarządzanie konfiguracją przełączników w systemie konfiguracji zapewnia większą elastyczność — można włączyć i wyłączyć różne przełączniki i zmienić poziomy bez konieczności ponownego kompilowania aplikacji.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Aby utworzyć i zainicjować przełącznik śledzenia  
  
1. Zdefiniuj przełącznik jako typ <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> lub typ <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> , a następnie ustaw nazwę i opis przełącznika.  
  
2. Skonfiguruj przełącznik śledzenia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](#configure).  
  
     Poniższy kod tworzy dwa przełączniki, jeden z każdego typu:  
  
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
 Po rozpoczęciu dystrybuowania aplikacji nadal można włączać lub wyłączać dane wyjściowe śledzenia przez skonfigurowanie przełączników śledzenia w aplikacji. Skonfigurowanie przełącznika oznacza zmianę jego wartości ze źródła zewnętrznego po jego zainicjowaniu. Można zmienić wartości obiektów przełącznika przy użyciu pliku konfiguracji. Można skonfigurować przełącznik śledzenia, aby go włączyć i wyłączyć, lub ustawić jego poziom, określając wielkość i typ komunikatów przesyłanych wraz z odbiornikami.  
  
 Przełączniki są konfigurowane przy użyciu pliku. config. W przypadku aplikacji sieci Web jest to plik Web. config skojarzony z projektem. W aplikacji systemu Windows ten plik ma nazwę (nazwa aplikacji). exe. config. W wdrożonej aplikacji ten plik musi znajdować się w tym samym folderze co plik wykonywalny.  
  
 Gdy aplikacja wykonuje kod, który tworzy wystąpienie przełącznika po raz pierwszy, sprawdza plik konfiguracji dla informacji na poziomie śledzenia o nazwanym przełączniku. System śledzenia analizuje plik konfiguracji tylko raz dla każdego określonego przełącznika — podczas pierwszego tworzenia przełącznika przez aplikację.  
  
 W wdrożonej aplikacji należy włączyć kod śledzenia przez ponowne skonfigurowanie obiektów Switch, gdy aplikacja nie jest uruchomiona. Zazwyczaj obejmuje to włączenie i wyłączenie obiektów przełącznika lub zmianę poziomów śledzenia, a następnie ponowne uruchomienie aplikacji.  
  
 Podczas tworzenia wystąpienia przełącznika, można go również zainicjować przez określenie dwóch argumentów: argumentu *DisplayName* i argumentu *Description* . Argument *DisplayName* konstruktora ustawia <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> Właściwość <xref:System.Diagnostics.Switch> wystąpienia klasy. *DisplayName* jest nazwą, która jest używana do konfigurowania przełącznika w pliku. config, a argument *Description* powinien zwrócić krótki opis przełącznika i komunikaty, które kontroluje.  
  
 Oprócz określenia nazwy przełącznika do skonfigurowania należy również określić wartość dla przełącznika. Ta wartość jest liczbą całkowitą. Dla <xref:System.Diagnostics.BooleanSwitch>, wartość 0 odpowiada **off**, a każda wartość różna od zera odpowiada wartości **on**. Dla <xref:System.Diagnostics.TraceSwitch>, 0, 1, 2, 3 i **4 odpowiadają**odpowiednio wartościom, **błędom**, **ostrzeżeniem**, **informacjom**i **pełnym**. Każda liczba większa niż 4 jest traktowana jako **pełna**, a każda liczba mniejsza od zera jest traktowana jako **wyłączona**.  
  
> [!NOTE]
> W .NET Framework w wersji 2,0 można użyć tekstu, aby określić wartość dla przełącznika. Na przykład `true` `Error` dla lub tekst reprezentujący wartość wyliczenia, na przykład dla elementu <xref:System.Diagnostics.TraceSwitch>. <xref:System.Diagnostics.BooleanSwitch> Wiersz `<add name="myTraceSwitch" value="Error" />` jest`<add name="myTraceSwitch" value="1" />`odpowiednikiem.  
  
 Aby użytkownicy końcowi mogli konfigurować przełączniki śledzenia aplikacji, należy dostarczyć szczegółowej dokumentacji dotyczącej przełączników w aplikacji. Należy szczegółowo określić, które przełączniki kontrolują sposób i sposób włączania i wyłączania. Należy również udostępnić użytkownikowi końcowemu plik. config, który ma odpowiednią pomoc w komentarzach.  
  
#### <a name="to-configure-trace-switches"></a>Aby skonfigurować przełączniki śledzenia  
  
1. Aby można było korzystać z przełączników śledzenia, najpierw należy je utworzyć i umieścić w kodzie zgodnie z opisem w sekcji [Tworzenie i Inicjowanie przełącznika śledzenia](#create).  
  
2. Jeśli projekt nie zawiera pliku konfiguracji (App. config lub Web. config), w menu **projekt** wybierz polecenie **Dodaj nowy element**.  
  
    - **Visual Basic:** W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.  
  
         Plik konfiguracji aplikacji zostanie utworzony i otwarty. Jest to dokument XML, którego element główny to`<configuration>.`  
  
    - **Wizualizacja C#:** W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik XML**. Nazwij ten plik **App. config**. W edytorze XML, po deklaracji XML, Dodaj następujący kod XML:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Po skompilowaniu projektu plik App. config jest kopiowany do folderu wyjściowego projektu i ma nazwę *ApplicationName*. exe. config.  
  
3. Po tagu, ale przed tagiem, Dodaj odpowiedni kod XML, aby skonfigurować przełączniki. `</configuration>` `<configuration>` W poniższych przykładach przedstawiono **BooleanSwitch** z właściwością `DataMessageSwitch` **DisplayName** i **TraceSwitch** z właściwością `TraceLevelSwitch` **DisplayName** .  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     W tej konfiguracji oba przełączniki są wyłączone.  
  
4. Jeśli musisz włączyć **BooleanSwitch**, jak `DataMessagesSwitch` pokazano w poprzednim przykładzie, Zmień **wartość** na dowolną liczbę całkowitą inną niż 0.  
  
5. Jeśli musisz włączyć **TraceSwitch**, jak pokazano w poprzednim przykładzie, `TraceLevelSwitch` Zmień **wartość** na odpowiednie ustawienie na poziomie (od 1 do 4).  
  
6. Dodaj komentarze do pliku config, aby użytkownik końcowy miał jasno zrozumieć, jakie wartości należy zmienić, aby odpowiednio skonfigurować przełączniki.  
  
     Poniższy przykład pokazuje, jak kod końcowy, w tym komentarze, może wyglądać następująco:  
  
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

- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
- [Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji](how-to-add-trace-statements-to-application-code.md)
- [Przełączniki śledzenia](trace-switches.md)
- [Schemat ustawień śledzenia i debugowania](../configure-apps/file-schema/trace-debug/index.md)
