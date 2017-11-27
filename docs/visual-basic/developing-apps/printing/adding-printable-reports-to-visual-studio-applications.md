---
title: "Dodawanie drukowalnych raportów do aplikacji Visual Studio"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ce2a8b12d8202a9f201a82b0d4a571249210d48
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Dodawanie drukowalnych raportów do aplikacji Visual Studio
Program Visual Studio obsługuje różnych rozwiązań raportowych ułatwiają dodawanie sformatowanego danych raportowania do aplikacji Visual Basic. Można utworzyć i dodać raportów za pomocą kontrolki podglądu raportów, Crystal Reports lub SQL Server Reporting Services.  
  
> [!NOTE]
>  SQL Server Reporting Services jest częścią programu SQL Server 2005, a nie programu Visual Studio. Usługi Reporting Services nie są zainstalowane w systemie, chyba że został zainstalowany program SQL Server 2005.  
  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Omówienie usług Microsoft Reporting technologii w aplikacjach Visual Basic  
 Wybierz z poniższych metod raportowania technologii w aplikacji firmy Microsoft:  
  
-   Dodaj co najmniej jedno wystąpienie formantu ReportViewer do aplikacji systemu Windows w języku Visual Basic.  
  
-   Integracja usług SQL Server Reporting Services programowo przez nawiązywanie połączeń z usługą sieci Web serwera raportów.  
  
-   Użyć formantu ReportViewer i Microsoft SQL Server 2005 Reporting Services, przy użyciu kontrolki podglądu raportów i serwera raportów jako procesor raportu. (Należy pamiętać, że muszą używać wersji programu SQL Server 2005 Reporting Services, jeśli chcesz używać serwera raportów i kontrolki podglądu raportów ze sobą).  
  
## <a name="using-reportviewer-controls"></a>Korzystanie z kontrolek podglądu raportów  
 Najprostszym sposobem, aby osadzić raport funkcji do aplikacji systemu Windows w języku Visual Basic jest dodawanie do formularza w aplikacji formantu ReportViewer. Formant dodaje możliwości bezpośrednio do aplikacji przetwarzania raportów i udostępnia projektanta raportów zintegrowane, dzięki czemu można tworzyć raporty przy użyciu danych z dowolnych obiektów danych ADO.NET. Interfejs API kompletne zapewnia dostęp programistyczny do formantu i raporty tak, aby skonfigurować funkcje czasu wykonywania.  
  
 Podglądu raportów zawiera przetwarzania raportów wbudowanych oraz wyświetlanie możliwości wewnątrz formantu danych jednego, bezpłatny. Wybierz kontrolki podglądu raportów, jeśli wymagana następujące funkcje raportu:  
  
-   Raport przetwarzania w aplikacji klienta. Przetworzone raport jest wyświetlany w obszarze widoku udostępniane przez formant.  
  
-   Wiązanie danych do tabel danych ADO.NET. Możesz utworzyć raporty używające <xref:System.Data.DataTable> wystąpienia dostarczony do formantu. Może także powiązać bezpośrednio do obiektów biznesowych.  
  
-   Formanty redystrybucyjne, które można uwzględnić w aplikacji.  
  
-   Funkcjonalność aparatu plików wykonywalnych, takich jak nawigacji strony, drukowania, wyszukiwanie i eksportowanie formaty. Pasek narzędzi podglądu raportów zapewnia obsługę tych operacji.  
  
 Aby użyć kontrolki podglądu raportów, możesz przeciągnąć go z **danych** sekcji przybornika programu Visual Studio do formularza w aplikacji systemu Windows w języku Visual Basic.  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>Tworzenie raportów w programie Visual Studio dla kontrolek podglądu raportów  
 Aby utworzyć raport, który jest uruchamiany w podglądu raportów, należy dodać **raport** szablonu do projektu. Visual Studio tworzy plik definicji raportów klientów (RDLC), dodaje plik do projektu i otwiera projektanta raportów zintegrowane w obszarze roboczym programu Visual Studio.  
  
 Projektanta raportów programu Visual Studio integruje się z **źródeł danych** okna. Gdy przeciągnij pola z **źródeł danych** okna do raportu, w programie Report Designer kopiuje metadane dotyczące źródła danych do pliku definicji raportu. Te metadane jest używany przez formant podglądu raportów do automatycznego generowania kodu powiązania danych.  
  
 Projektanta raportów programu Visual Studio nie obejmuje funkcjonalności Podgląd raportu. Aby wyświetlić podgląd raportu, uruchom aplikację i wyświetlić podgląd raportu osadzonych w niej.  
  
|Aby dodać funkcje podstawowy raport do aplikacji|  
|---|    
|1.  Przeciągnij formant podglądu raportów z **danych** karcie **przybornika** na formularzu.<br />2.  Na **projektu** menu, wybierz **Dodaj nowy element**. W **Dodaj nowy element** okno dialogowe, wybierz opcję **raport** ikony, jak i kliknij przycisk **Dodaj**.<br />     Projektant raportów zostanie otwarty w środowisku programistycznym, a plik raportu (RDLC) jest dodawany do projektu.<br />3.  Przeciągnij elementy raportu z **przybornika** na układ raportu i rozmieszczenia można dowolnie.<br />4.  Przeciągnij pola z **źródeł danych** okna do elementów raportu w układ raportu.|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Przy użyciu usług raportowania w aplikacjach Visual Basic  
 Usługi Reporting Services to technologia raportowania na serwerze dołączonej do programu SQL Server. Usługi Reporting Services zawiera dodatkowe funkcje, które nie zostały znalezione w kontrolek podglądu raportów. Wybierz usług Reporting Services, jeśli potrzebna jest jedną z następujących funkcji:  
  
-   Wdrażanie skalowalnego w poziomie i przetwarzania raportu po stronie serwera, który zapewnia lepszą wydajność, złożonych lub długotrwałe raportów oraz raport dużych działania.  
  
-   Zintegrowane danych i przetwarzania raportu o obsługę formantów raport niestandardowy i sformatowanego renderowania formatów.  
  
-   Zaplanowane przetwarzania raportów, dzięki czemu można określić dokładnie, jeśli raporty są uruchamiane.  
  
-   Raport na podstawie subskrybenta dystrybucji za pośrednictwem poczty e-mail lub do lokalizacji udziału plików.  
  
-   Raportowanie ad hoc, tak aby użytkownicy biznesowi mogą tworzyć raporty, zgodnie z potrzebami.  
  
-   Subskrypcje oparte na danych, które kierować dostosowane raportu wyjściowego do dynamicznej listy adresatów.  
  
-   Niestandardowe rozszerzenia przetwarzania danych, dostarczenia raportu niestandardowego uwierzytelniania i renderowania raportu.  
  
 Serwer raportów jest implementowany jako usługi sieci Web. Kod aplikacji może zawierać wywołania usługi sieci Web dostęp do raportów i innych metadanych. Usługa sieci Web zapewnia pełny dostęp programistyczny do wystąpienia serwera raportów.  
  
 Ponieważ usług Reporting Services to technologia raportowania oparte na sieci Web, domyślnej przeglądarki zawiera raporty, które mają być renderowane w formacie HTML. Jeśli nie chcesz używać HTML jako domyślny format prezentacji raport, należy zapisać Podgląd raportu niestandardowego dla aplikacji.  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Tworzenie raportów w programie Visual Studio dla usług raportowania  
 Do tworzenia raportów, które są uruchamiane na serwerze raportów, można tworzyć definicji raportu (RDL) pliki w programie Visual Studio za pośrednictwem Business Intelligence Development Studio, który jest dołączony do programu SQL Server 2005.  
  
> [!NOTE]
>  Musisz mieć zainstalowany, aby można było używać programu SQL Server Reporting Services i Business Intelligence Development Studio programu SQL Server 2005.  
  
 Business Intelligence Development Studio dodaje szablony projektów, które są specyficzne dla składników programu SQL Server. Aby utworzyć raporty, można wybrać **Projekt serwera raportów** lub **Kreator projektu serwera raportów** szablonów. Można określić połączeń ze źródłem danych i zapytania do różnych typów źródła danych, w tym programu SQL Server, Oracle usług Analysis Services, XML i SQL Server Integration Services. A **danych** karcie **układu** karcie i **Podgląd** kartę umożliwiają definiowanie danych, Utwórz układ raportu i wyświetlić podgląd raportu, w tym samym obszarze roboczym.  
  
 Definicje raportów, które kompilacji dla serwera raportów lub formantu mogą być ponownie używane w obu technologii.  
  
|Aby utworzyć raport, który jest uruchamiany na serwerze raportów|  
|---|    
|1.  Na **pliku** menu, wybierz **nowy**.<br />     **Nowy projekt** zostanie otwarte okno dialogowe.<br />2.  W **typy projektów** okienku, kliknij przycisk **projektów analizy biznesowej**.<br />3.  W okienku szablonów wybierz **Projekt serwera raportów** lub **Kreator projektu serwera raportów**.|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>Za pomocą kontrolek podglądu raportów i SQL Server Reporting Services razem  
 Kontrolek podglądu raportów i SQL Server 2005 Reporting Services mogą być używane razem w tej samej aplikacji.  
  
-   Formant podglądu raportów zawiera przeglądarkę, która jest używana do wyświetlania raportów w aplikacji.  
  
-   Usługi Reporting Services udostępnia raporty i wykonuje wszystkie przetwarzania na serwerze zdalnym.  
  
 Formant podglądu raportów można skonfigurować do wyświetlania raportów, które są przechowywane i przetwarzane na zdalnym serwerze raportów usług Reporting Services. Konfiguracja tego typu jest nazywana *tryb przetwarzania zdalnego*. W trybie przetwarzania zdalnego kontrolki raportu, który jest przechowywany na serwerze zdalnym raportu. Serwer raportów wykonuje wszystkie operacje przetwarzania raportu, przetwarzanie danych i renderowania raportu. Zakończono, wyrenderowany raport jest zwracana do formantu i wyświetlane w obszarze widoku.  
  
 Raporty uruchamiane na obsługę serwera raportów dodatkowe eksportowanie formatów, implementacją parametryzacja innego raportu, użyj typy źródeł danych są obsługiwane przez serwer raportów, które są dostępne za pośrednictwem modelu autoryzacji opartej na rolach na Serwer raportów.  
  
 Do używania trybu przetwarzania zdalnego, określ adres URL i ścieżkę do raportu server podczas konfigurowania formantu ReportViewer.
