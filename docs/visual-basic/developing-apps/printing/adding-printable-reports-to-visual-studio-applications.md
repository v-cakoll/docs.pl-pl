---
title: Dodawanie drukowalnych raportów do aplikacji Visual Studio
ms.date: 07/20/2015
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
ms.openlocfilehash: 65264deea3aeff1a633ea6888b3f175031b7fba5
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212017"
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Dodawanie drukowalnych raportów do aplikacji Visual Studio
Program Visual Studio obsługuje wiele różnych rozwiązań raportowych ułatwiają dodawania danych raportowania do aplikacji w języku Visual Basic. Można tworzyć i Dodaj raporty za pomocą kontrolek podglądu raportów, raportów Crystal Reports lub SQL Server Reporting Services.  

  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Omówienie usług Microsoft Reporting technologii w aplikacjach Visual Studio  
 Użyj usług Microsoft reporting technologii w aplikacji, wybierając spośród następujących metod:  
  
-   Dodaj co najmniej jednego wystąpienia kontrolki podglądu raportów do aplikacji w języku Visual Basic Windows.  
  
-   Integracja programu SQL Server Reporting Services programowo przez wykonywanie wywołań do usługi sieci Web serwera raportów.  
  
-   Użyj formantu ReportViewer i Microsoft SQL Server 2005 Reporting Services ze sobą za pomocą kontrolki podglądu raportów i serwera raportów jako podmiot przetwarzający raportu. (Zwróć uwagę, należy użyć wersji programu SQL Server 2005 Reporting Services, jeśli chcesz używać serwera raportów i kontrolki ReportViewer ze sobą).  
  
## <a name="using-reportviewer-controls"></a>Korzystanie z kontrolek podglądu raportów  
 Najprostszym sposobem osadzania funkcji raportu w aplikacji Windows w języku Visual Basic jest dodać formant podglądu raportów do formularza w Twojej aplikacji. Kontrolka dodaje możliwości bezpośrednio do aplikacji przetwarzania raportu i zapewnia opłat licencyjnych projektanta raportów zintegrowanego, dzięki czemu można tworzyć raporty przy użyciu danych z dowolnych obiektów danych ADO.NET. Interfejs API w pełni funkcjonalne zapewnia dostęp programistyczny do kontrolki i raporty, dzięki czemu można skonfigurować funkcji wykonawczej.  
  
 Podglądu raportów zawiera przetwarzania raportów wbudowanych oraz wyświetlanie możliwości kontroli danych w jednym, bezpłatny. Wybierz ReportViewer kontrolki, jeśli wymagane są następujące funkcje raportu:  
  
-   Raport przetwarzania w aplikacji klienckiej. Przetworzone raport jest wyświetlany w obszarze widoku, dostarczone przez kontrolkę.  
  
-   Powiązywanie danych do tabel danych ADO.NET. Możesz tworzyć raporty, które mogą korzystać <xref:System.Data.DataTable> wystąpień dostarczone do formantu. Możesz również powiązać bezpośrednio do obiektów biznesowych.  
  
-   Pakiet redystrybucyjny kontrolki, które można uwzględnić w aplikacji.  
  
-   Funkcjonalność aparatu plików wykonywalnych, takich jak nawigowania po stronach, drukowanie, wyszukiwanie i formaty eksportu. Pasek narzędzi podglądu raportów zapewnia obsługę tych operacji.  
  
 Aby użyć kontrolki ReportViewer, można przeciągnąć go z **danych** części programu Visual Studio Toolbox w formularzu w aplikacji Windows w języku Visual Basic.  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>Tworzenie raportów w programie Visual Studio dla kontrolek podglądu raportów  
 Aby utworzyć raport, który jest uruchamiany w podglądu raportów, dodawania **raportu** szablon do projektu. Visual Studio tworzy plik definicji raportu (.rdlc) klienta, dodaje plik do projektu i zostanie otwarty projektant raportów zintegrowane w obszarze roboczym programu Visual Studio.  
  
 Projektanta raportów w usłudze Visual Studio integruje się z **źródeł danych** okna. Podczas przeciągania pola z **źródeł danych** okna do raportu, Projektant raportów kopiuje metadane dotyczące źródła danych do pliku definicji raportu. Te metadane jest używany przez kontrolkę ReportViewer do automatycznego generowania kodu powiązanie danych.  
  
 Projektanta raportów w usłudze Visual Studio nie zawiera funkcji podglądu raportu. Aby wyświetlić podgląd raportu, należy uruchomić aplikację i wyświetlić podglądu raportu osadzone w nim.  
  
|Aby dodać funkcję podstawowego raportu na aplikację|  
|---|    
|1.  Przeciągnij formant podglądu raportów z **danych** karcie **przybornika** do formularza.<br />2.  Na **projektu** menu, wybierz **Dodaj nowy element**. W **Dodaj nowy element** okno dialogowe, wybierz opcję **raportu** ikonę i kliknij przycisk **Dodaj**.<br />     Zostanie otwarty projektant raportów w środowisku deweloperskim, a plik raportu (.rdlc) zostanie dodany do projektu.<br />3.  Przeciągnij elementy raportu z **przybornika** na układ raportu i zorganizować je, jak chcesz.<br />4.  Przeciągnij pola z **źródeł danych** okna do elementów raportu w układzie raportu.|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Korzystanie z usług Reporting Services w aplikacji Visual Basic  
 Usługi Reporting Services to oparte na serwerze raportowania technologia, która jest dołączana do programu SQL Server. Usługi Reporting Services zawiera dodatkowe funkcje, które nie znajdują się w kontrolek podglądu raportów. Wybierz usługi Reporting Services, jeśli potrzebujesz żadnego z następujących funkcji:  
  
-   Wdrażanie skalowalnego w poziomie i przetwarzania raportu po stronie serwera, który zapewnia lepszą wydajność dla złożonych i długotrwałych raportów oraz działania mocno obciążające raportu.  
  
-   Zintegrowane przetwarzania danych i raportów, dzięki obsłudze kontrolek niestandardowych raportów i bogate renderowania formaty danych wyjściowych.  
  
-   Zaplanowane przetwarzania raportu, dzięki czemu można określić dokładnie w przypadku, gdy są uruchamiane w raportach.  
  
-   Raport na podstawie subskrybenta dystrybucji za pośrednictwem poczty e-mail lub do lokalizacji udziału plików.  
  
-   Raportowanie ad hoc, tak aby użytkownicy biznesowi mogą tworzyć raporty, zgodnie z potrzebami.  
  
-   Subskrypcje oparte na danych, które trasy dostosowany raport, dane wyjściowe do dynamicznej listy adresatów.  
  
-   Niestandardowe rozszerzenia do przetwarzania danych, dostarczenia raportu, uwierzytelnianie niestandardowe i renderowania raportu.  
  
 Serwer raportów jest implementowany jako usługę sieci Web. Kod aplikacji musi zawierać wywołania usługi sieci Web dostęp do raportów i innych metadanych. Usługa sieci Web zapewnia pełny dostęp programowy do wystąpienia serwera raportów.  
  
 Ponieważ usług Reporting Services to technologia raportowania opartego na sieci Web, domyślna przeglądarka zawiera raporty, które mają być renderowane w formacie HTML. Jeśli nie chcesz używać HTML jako domyślny format prezentacji raportu, należy napisać podglądu raportu niestandardowego w aplikacji.  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Tworzenie raportów w programie Visual Studio dla usług raportowania  
 Możesz tworzyć raporty, które są uruchamiane na serwerze raportów, utworzysz definicji raportu (RDL) plików w programie Visual Studio za pośrednictwem Business Intelligence Development Studio, który jest dołączony do programu SQL Server 2005.  
  
 Business Intelligence Development Studio dodaje szablony projektów, które są specyficzne dla składników programu SQL Server. Aby utworzyć raporty, możesz korzystać z **projektu serwera raportów** lub **Kreator projektu serwera raportów** szablonów. Można określić połączeń ze źródłami danych i zapytań na różne typy źródeł danych, w tym programu SQL Server, Oracle, usług Analysis Services, XML i SQL Server Integration Services. A **danych** karcie **układ** karcie i **(wersja zapoznawcza)** karta pozwala na zdefiniowanie danych, Utwórz układ raportu i wyświetlić podglądu raportu, w tym samym obszarze roboczym.  
  
 Definicje, które są kompilowane dla formantu lub na serwerze raportów mogą być ponownie używane w obu technologii.  
  
|Aby utworzyć raport, który jest uruchamiany na serwerze raportów|  
|---|    
|1.  Na **pliku** menu, wybierz **New**.<br />     **Nowy projekt** zostanie otwarte okno dialogowe.<br />2.  W **typów projektów** okienku kliknij **projekty Business Intelligence**.<br />3.  W okienku szablonów zaznacz **projektu serwera raportów** lub **Kreator projektu serwera raportów**.|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>Używanie kontrolek ReportViewer i SQL Server Reporting Services razem  
 Kontrolek ReportViewer i SQL Server 2005 Reporting Services mogą być używane razem w tej samej aplikacji.  
  
-   Formant podglądu raportów zapewnia viewer, który służy do wyświetlania raportów w aplikacji.  
  
-   Usługi Reporting Services zawiera raporty, a następnie wykonuje całego procesu przetwarzania na serwerze zdalnym.  
  
 Kontrolki podglądu raportów można skonfigurować tak, aby wyświetlić raporty, które są przechowywane i przetwarzane na zdalnym serwerze raportów usług Reporting Services. Ten typ konfiguracji jest nazywany *trybu przetwarzania zdalnego*. W trybie przetwarzania zdalnego kontrolka żąda raportu, który jest przechowywany na serwerze raportów zdalnego. Serwer raportów wykonuje przetwarzanie raportu, przetwarzanie danych i renderowania raportu. Zakończono, wyrenderowany raport został zwrócony do formantu, a następnie wyświetlana w obszarze widoku.  
  
 Raporty uruchamiane na temat obsługi serwera raportów dodatkowe formaty eksportu, implementacją parametryzacji inny raport, użyj typów źródeł danych, które są obsługiwane przez serwer raportów i są dostępne za pośrednictwem modelu autoryzacji opartej na rolach na Serwer raportów.  
  
 Aby użyć trybu przetwarzania zdalnego, określ adres URL i ścieżki do raportu server podczas konfigurowania formantu ReportViewer.
