---
title: 'Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia'
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
ms.openlocfilehash: 8bf3b974ff0ef9f719274ab684b3dce85295c917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181824"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia
Przełączniki śledzenia umożliwiają włączanie, wyłączanie i filtrowanie danych wyjściowych.  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a>Tworzenie i inicjowanie przełącznika śledzenia  
 Aby użyć przełączników śledzenia, należy je najpierw utworzyć i umieścić je w kodzie. Istnieją dwie wstępnie zdefiniowane klasy, z których można <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> tworzyć <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> obiekty switch: klasę i klasę. <xref:System.Diagnostics.BooleanSwitch> Użyjesz, jeśli zależy Ci tylko na tym, czy pojawi się komunikat śledzenia; <xref:System.Diagnostics.TraceSwitch> jeśli chcesz rozróżnić poziomy śledzenia. Jeśli używasz <xref:System.Diagnostics.TraceSwitch>programu , można zdefiniować własne komunikaty debugowania i skojarzyć je z różnymi poziomami śledzenia. Można użyć obu typów przełączników z śledzenia lub debugowania. Domyślnie a <xref:System.Diagnostics.BooleanSwitch> jest wyłączona i a jest ustawiona <xref:System.Diagnostics.TraceSwitch> na poziom <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>. Przełączniki śledzenia można utworzyć i umieścić w dowolnej części kodu, która może ich używać.  
  
 Chociaż można ustawić poziomy śledzenia i inne opcje konfiguracji w kodzie, zaleca się użycie pliku konfiguracyjnego do zarządzania stanem przełączników. Dzieje się tak, ponieważ zarządzanie konfiguracją przełączników w systemie konfiguracyjnym zapewnia większą elastyczność — można włączać i wyłączać różne przełączniki i zmieniać poziomy bez ponownego komppilowania aplikacji.  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>Aby utworzyć i zainicjować przełącznik śledzenia  
  
1. Zdefiniuj przełącznik <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> jako <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> typ lub typ i ustaw nazwę i opis przełącznika.  
  
2. Skonfiguruj przełącznik śledzenia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie przełączników śledzenia](#configure).  
  
     Poniższy kod tworzy dwa przełączniki, po jednym z każdego typu:  
  
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
 Po rozesłaniu aplikacji nadal można włączyć lub wyłączyć dane wyjściowe śledzenia, konfigurując przełączniki śledzenia w aplikacji. Konfigurowanie przełącznika oznacza zmianę jego wartości ze źródła zewnętrznego po jego zainicjowaniu. Za pomocą pliku konfiguracyjnego można zmienić wartości obiektów przełącznika. Można skonfigurować przełącznik śledzenia, aby go włączyć i wyłączyć lub ustawić jego poziom, określając ilość i typ wiadomości przekazuje do odbiorników.  
  
 Przełączniki są konfigurowane przy użyciu pliku .config. W przypadku aplikacji sieci Web jest to plik Web.config skojarzony z projektem. W aplikacji systemu Windows ten plik nosi nazwę (nazwa aplikacji).exe.config. W wdrożonej aplikacji ten plik musi znajdować się w tym samym folderze co plik wykonywalny.  
  
 Gdy aplikacja wykonuje kod, który tworzy wystąpienie przełącznika po raz pierwszy, sprawdza plik konfiguracji pod kątem informacji na poziomie śledzenia o nazwanym przełączniku. System śledzenia sprawdza plik konfiguracyjny tylko raz dla dowolnego konkretnego przełącznika — po raz pierwszy aplikacja tworzy przełącznik.  
  
 W wdrożonej aplikacji można włączyć kod śledzenia przez ponowne skonfigurowanie obiektów przełącznika, gdy aplikacja nie jest uruchomiona. Zazwyczaj wiąże się to z włączaniem i wyłączaniem obiektów przełącznika lub zmienianiem poziomów śledzenia, a następnie ponownym uruchomieniem aplikacji.  
  
 Podczas tworzenia wystąpienia przełącznika, należy również zainicjować go, określając dwa argumenty: *argument displayName* i argument *opisu.* Argument *displayName* konstruktora <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> ustawia właściwość wystąpienia <xref:System.Diagnostics.Switch> klasy. *DisplayName* to nazwa używana do konfigurowania przełącznika w pliku .config, a argument *opisu* powinien zwracać krótki opis przełącznika i jakie wiadomości steruje.  
  
 Oprócz określania nazwy przełącznika do skonfigurowania, należy również określić wartość przełącznika. Ta wartość jest całkowitej liczby. Dla <xref:System.Diagnostics.BooleanSwitch>, wartość 0 odpowiada **Off**, a każda wartość niezerowa odpowiada **On**. Dla <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3 i 4 odpowiadają **Off**, **Błąd**, **Ostrzeżenie**, **Info**i **Pełne**, odpowiednio. Dowolna liczba większa niż 4 jest traktowana jako **szczegółowa,** a dowolna liczba mniejsza niż zero jest traktowana jako **Wyłącz.**  
  
> [!NOTE]
> W .NET Framework w wersji 2.0 można użyć tekstu, aby określić wartość przełącznika. Na przykład `true` dla <xref:System.Diagnostics.BooleanSwitch> tekstu lub tekstu reprezentującego wartość wyliczenia, taką jak `Error` dla <xref:System.Diagnostics.TraceSwitch>pliku . Linia `<add name="myTraceSwitch" value="Error" />` jest równoważna `<add name="myTraceSwitch" value="1" />`.  
  
 Aby użytkownicy końcowi mogli skonfigurować przełączniki śledzenia aplikacji, należy dostarczyć szczegółową dokumentację dotyczącą przełączników w aplikacji. Należy szczegółowo, które przełączniki kontrolować, co i jak je włączyć i wyłączyć. Należy również podać użytkownikowi końcowemu plik .config, który ma odpowiednią Pomoc w komentarzach.  
  
#### <a name="to-configure-trace-switches"></a>Aby skonfigurować przełączniki śledzenia  
  
1. Aby użyć przełączników śledzenia, należy je najpierw utworzyć i umieścić w kodzie zgodnie z opisem w sekcji [Tworzenie i inicjowanie przełącznika śledzenia](#create).  
  
2. Jeśli projekt nie zawiera pliku konfiguracyjnego (app.config lub Web.config), z menu **Projekt** wybierz polecenie **Dodaj nowy element**.  
  
    - **Visual Basic:** W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.  
  
         Plik konfiguracji aplikacji jest tworzony i otwierany. Jest to dokument XML, którego element główny jest`<configuration>.`  
  
    - **Visual C#:** W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik **XML**. Nazwij ten plik **app.config**. W edytorze XML po deklaracji XML dodaj następujący kod XML:  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         Podczas kompilowania projektu plik app.config jest kopiowany do folderu wyjściowego projektu i zmienia nazwę *nazwy aplikacji*.exe.config.  
  
3. Po `<configuration>` tagu, `</configuration>` ale przed tagiem, dodaj odpowiedni kod XML, aby skonfigurować przełączniki. Poniższe przykłady pokazują **przełącznik logiczny** z właściwością `DataMessageSwitch` **DisplayName** i **przełącznikiem TraceSwitch** z właściwością **DisplayName** . `TraceLevelSwitch`  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     W tej konfiguracji oba przełączniki są wyłączone.  
  
4. Jeśli chcesz włączyć **przełącznik logiczny,** na przykład `DataMessagesSwitch` w poprzednim przykładzie, zmień **wartość** na dowolną liczę całkowitą inną niż 0.  
  
5. Jeśli chcesz włączyć **przełącznik TraceS,** na `TraceLevelSwitch` przykład w poprzednim przykładzie, zmień **wartość** na odpowiednie ustawienie poziomu (1 na 4).  
  
6. Dodaj komentarze do pliku .config, aby użytkownik końcowy miał jasną wiedzę na temat wartości, które należy zmienić, aby odpowiednio skonfigurować przełączniki.  
  
     W poniższym przykładzie pokazano, jak może wyglądać ostateczny kod, w tym komentarze:  
  
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

- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
- [Porady: dodawanie instrukcji śledzenia do kodu aplikacji](how-to-add-trace-statements-to-application-code.md)
- [Przełączniki śledzenia](trace-switches.md)
- [Schemat ustawień śledzenia i debugowania](../configure-apps/file-schema/trace-debug/index.md)
