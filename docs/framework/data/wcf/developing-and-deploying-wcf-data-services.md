---
title: Tworzenie i wdrażanie usług danych programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 4591175da5078a194bfe69884701e5432a0c38a3
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389726"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Opracowywanie i wdrażanie usług danych WCF

Ten artykuł zawiera informacje dotyczące tworzenia i wdrażania usług danych WCF. Aby uzyskać bardziej podstawowe informacje na temat usług danych WCF, zobacz [Wprowadzenie](getting-started-with-wcf-data-services.md) i [Omówienie](wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Tworzenie usług danych WCF

Podczas tworzenia usługi danych usługi OData za pomocą usług WCF data Services należy wykonać następujące podstawowe zadania podczas opracowywania:

1. **Zdefiniowanie modelu danych**

     Usługi WCF Data Services obsługuje różnych dostawców usług danych, które umożliwiają definiowanie modelu danych na podstawie danych z różnych źródeł danych, z relacyjnych baz danych do późno związanych typów danych. Aby uzyskać więcej informacji, zobacz [Dostawcy usług danych](data-services-providers-wcf-data-services.md).

2. **Utworzenie usługi danych**

     Najbardziej podstawowa usługa danych udostępnia klasę, <xref:System.Data.Services.DataService%601> która dziedziczy `T` z klasy, z typem, który jest nazwą kwalifikowaną obszaru nazw kontenera jednostki. Aby uzyskać więcej informacji, zobacz [Definiowanie usług danych WCF](defining-wcf-data-services.md).

3. **Konfigurowanie usługi danych**

     Domyślnie usługi danych WCF wyłącza dostęp do zasobów, które są udostępniane przez kontener jednostki. Interfejs <xref:System.Data.Services.DataServiceConfiguration> umożliwia skonfigurowanie dostępu do zasobów i operacji usługi, określić obsługiwaną wersję OData i zdefiniować inne zachowania całej usługi, takie jak zachowania przetwarzania wsadowego lub maksymalna liczba jednostek, które mogą być zwracane w jednym źródle odpowiedzi. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).

W tym artykule opisano przede wszystkim rozwój i wdrażanie usług danych przy użyciu programu Visual Studio. Aby uzyskać informacje na temat elastyczności zapewnianej przez usługi WCF Data Services w zakresie ujawniania danych w stanie źródła danych OData, zobacz [Definiowanie usług danych WCF](defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Wybieranie programu Rozwoju serwera sieci Web

Podczas tworzenia usługi danych WCF jako ASP.NET aplikacji lub ASP.NET witryny sieci Web przy użyciu programu Visual Studio 2015, masz do wyboru serwery sieci Web, na których można uruchomić usługę danych podczas tworzenia. Następujące serwery sieci Web integrują się z programem Visual Studio, aby ułatwić testowanie i debugowanie usług danych na komputerze lokalnym.

1. **Lokalny serwer usług IIS**

     Podczas tworzenia usługi danych, która jest ASP.NET aplikacji lub ASP.NET witryny sieci Web, która działa w internetowych usługach informacyjnych (IIS), zaleca się opracowanie i przetestowanie usługi danych przy użyciu usług IIS na komputerze lokalnym. Uruchamianie usługi danych na serwerze IIS ułatwia śledzenie żądań HTTP podczas debugowania. Pozwala również wstępnie określić niezbędne uprawnienia wymagane przez program IIS przy uzyskiwaniu dostępu do plików, baz danych i innych zasobów wymaganych przez usługę danych. Aby uruchomić usługę danych w usługach IIS, upewnij się, że zarówno usługi IIS, jak i Windows Communication Foundation (WCF) są poprawnie zainstalowane i skonfigurowane, a także udziel dostępu do kont usług IIS w systemie plików i bazach danych. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie usługi danych WCF uruchomionej na usługach IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Należy uruchomić program Visual Studio z uprawnieniami administratora, aby umożliwić środowisku programistycznemu konfigurowanie lokalnego serwera usług IIS.

2. **Visual Studio Development Server**

     Program Visual Studio zawiera wbudowany serwer sieci Web, program Visual Studio Development Server, który jest domyślnym serwerem sieci Web dla projektów ASP.NET. Ten serwer sieci Web jest przeznaczony do uruchamiania projektów ASP.NET na komputerze lokalnym podczas tworzenia. [WCF Data Services Szybki start](quickstart-wcf-data-services.md) pokazuje, jak utworzyć usługę danych, która jest uruchamiana w programie Visual Studio Development Server.

     Należy pamiętać o następujących ograniczeniach podczas korzystania z programu Visual Studio Development Server do tworzenia usługi danych:

    - Dostęp do tego serwera można uzyskać tylko na komputerze lokalnym.

    - Ten serwer nasłuchuje na `localhost` i na określonym porcie, a nie na porcie 80, który jest domyślnym portem dla wiadomości HTTP. Aby uzyskać więcej informacji, zobacz [Serwery sieci Web w programie Visual Studio dla ASP.NET projektów sieci Web](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - Ten serwer uruchamia usługę danych w kontekście bieżącego konta użytkownika. Na przykład jeśli jesteś uruchomiony jako użytkownik na poziomie administratora, usługa danych uruchomiona na serwerze programu Visual Studio Development Server będzie miała uprawnienia na poziomie administratora. Może to spowodować, że usługa danych będzie mogła uzyskać dostęp do zasobów, do których nie ma praw dostępu w przypadku jej wdrożenia na serwerze IIS.

    - Ten serwer nie oferuje dodatkowych funkcji programu IIS, takich jak uwierzytelnianie.

    - Ten serwer nie może obsługiwać fragmentowanych strumieni HTTP, które są domyślnie wysyłane przez klienta usług danych WCF podczas uzyskiwania dostępu do dużych danych binarnych z usługi danych. Aby uzyskać więcej informacji, zobacz [Dostawca przesyłania strumieniowego](streaming-provider-wcf-data-services.md).

    - Ten serwer ma problemy z`.`przetwarzaniem znaku kropki ( ) w adresie URL, mimo że ten znak jest obsługiwany przez usługi danych WCF w wartościach klucza.

    > [!TIP]
    > Mimo że można użyć programu Visual Studio Development Server do testowania usług danych podczas tworzenia, należy przetestować je ponownie po wdrożeniu na serwerze sieci Web z uruchomionymi usługami IIS.

3. **Środowisko programistyczne systemu Windows Azure**

     Narzędzia platformy Windows Azure dla programu Visual Studio zawierają zintegrowany zestaw narzędzi do tworzenia usług systemu Windows Azure w programie Visual Studio. Za pomocą tych narzędzi można zaprojektować usługę danych, którą będzie można wdrożyć w systemie Microsoft Azure i przed wdrożeniem można przetestować usługę danych na komputerze lokalnym. Użyj tych narzędzi podczas korzystania z programu Visual Studio do tworzenia usługi danych, która działa na platformie Windows Azure. Aby uzyskać informacje dotyczące instalowania tych narzędzi, zobacz [Narzędzia platformy Azure dla programu Visual Studio 2015](../../../azure/sdk/vs2015-install.md). Aby uzyskać więcej informacji na temat tworzenia usługi danych, która działa w systemie Windows Azure, zobacz wpis [Wdrażanie usługi OData w systemie Windows Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="development-tips"></a>Porady dotyczące projektowania

Podczas tworzenia usługi danych należy wziąć pod uwagę następujące kwestie:

- Jeśli planujesz uwierzytelnić użytkowników lub ograniczyć dostęp dla określonych użytkowników, należy określić wymagania dotyczące zabezpieczeń usługi danych. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usług danych WCF](securing-wcf-data-services.md).

- Program inspekcji HTTP może być przydatny podczas debugowania usługi danych, umożliwiając sprawdzanie zawartości komunikatów żądania i odpowiedzi. Dowolnego analizatora pakietów sieciowych, który może wyświetlać pakiety nieprzetworzone, można używać do inspekcji żądań HTTP i odpowiedzi z usługi danych.

- Podczas debugowania usługi danych, można uzyskać więcej informacji o błędzie z usługi danych niż podczas normalnej operacji. Dodatkowe informacje o błędzie można uzyskać z <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> usługi <xref:System.Data.Services.DataServiceConfiguration> danych, ustawiając właściwość w do `true` i ustawiając <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwość <xref:System.ServiceModel.Description.ServiceDebugBehavior> atrybutu w klasie usługi danych na . `true` Aby uzyskać więcej informacji, zobacz post [Debugowanie usług danych WCF](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services). Można również włączyć śledzenie w WCF, aby wyświetlić wyjątki wywoływane w warstwie wiadomości HTTP. Aby uzyskać więcej informacji, zobacz [Konfigurowanie śledzenia](../../wcf/diagnostics/tracing/configuring-tracing.md).

- Usługa danych jest zwykle rozwijany jako projekt aplikacji ASP.NET, ale można również utworzyć usługę danych jako projekt witryny sieci Web ASP.NET w programie Visual Studio. Aby uzyskać informacje na temat różnic między tymi dwoma typami projektów, zobacz [Projekty aplikacji sieci Web a projekty witryn sieci Web w programie Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- Podczas tworzenia usługi danych przy użyciu okna dialogowego **Dodawanie nowego elementu** w programie Visual Studio usługa danych jest obsługiwana przez ASP.NET w usługach IIS. Podczas gdy ASP.NET i usługi IIS są domyślnym hostem dla usługi danych, obsługiwane są inne opcje hostingu. Aby uzyskać więcej informacji, zobacz [Hostowanie usługi danych](hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Wdrażanie usług danych WCF

Usługa danych programu WCF zapewnia elastyczność, jeśli chodzi o wybór procesu hostującego usługę danych. Za pomocą programu Visual Studio można wdrożyć usługę danych na następujących platformach:

- **Serwer sieci Web hostowany przez usługi IIS**

    Gdy usługa danych jest rozwijana jako projekt ASP.NET, można ją wdrożyć na serwerze sieci Web usług IIS przy użyciu standardowych procesów wdrażania ASP.NET.  Visual Studio udostępnia następujące technologie wdrażania dla ASP.NET, w zależności od rodzaju projektu ASP.NET, który obsługuje wdrażaną usługę danych.

  - **Technologie wdrażania ASP.NET aplikacji sieci Web**

    - [Jak: Tworzenie pakietu wdrażania sieci Web w programie Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Jak: Wdrażanie projektu sieci Web przy użyciu publikowania jednym kliknięciem w programie Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **Technologie wdrażania ASP.NET witryn sieci Web**

    - [Jak: Kopiowanie plików witryny sieci Web za pomocą narzędzia Kopiowanie witryny sieci Web](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Jak: Publikowanie witryn sieci Web](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [Przewodnik: Wdrażanie ASP.NET aplikacji sieci Web przy użyciu xcopy](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Aby uzyskać więcej informacji na temat opcji wdrażania aplikacji ASP.NET, zobacz [Omówienie wdrażania sieci Web dla programu Visual Studio i ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Przed próbą wdrożenia usługi danych w programie IIS należy przetestować wdrożenie na serwerze sieci Web, na którym działa program IIS. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie usługi danych WCF uruchomionej na usługach IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

- **System Microsoft Azure**

     Usługę danych można wdrożyć w systemie Windows Azure przy użyciu narzędzi windows azure dla programu Visual Studio. Narzędzia platformy Windows Azure dla programu Visual Studio można pobrać z [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/?LinkID=201848). Aby uzyskać więcej informacji na temat wdrażania usługi danych w systemie Windows Azure, zobacz wpis [Wdrażanie usługi OData w systemie Windows Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="deployment-considerations"></a>Uwagi dotyczące wdrażania

Podczas wdrażania usługi danych należy wziąć pod uwagę następujące kwestie:

- Podczas wdrażania usługi danych, która używa dostawcy entity framework do uzyskiwania dostępu do bazy danych programu SQL Server, może być również konieczności propagacji struktur danych, danych lub obu z wdrożenia usługi danych. Visual Studio może automatycznie tworzyć skrypty (.sql plików), aby to zrobić w docelowej bazie danych, a skrypty te mogą być zawarte w pakiecie wdrażania sieci Web aplikacji ASP.NET. Aby uzyskać więcej informacji, zobacz [Jak: Wdrażanie bazy danych za pomocą projektu aplikacji sieci Web](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). W przypadku ASP.NET witryny sieci Web można to zrobić za pomocą **Kreatora publikowania bazy danych** w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Publikowanie bazy danych SQL](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- Ponieważ usługi WCF Data Services zawierają podstawową implementację WCF, można użyć aplikacji AppFabric systemu Windows Server do monitorowania usługi danych wdrożonej w usługach IIS uruchomionych w systemie Windows Server. Aby uzyskać więcej informacji na temat używania aplikacji AppFabric systemu Windows Server do monitorowania usługi danych, zobacz wpis [Śledzenie usług danych WCF w systemie Windows Server AppFabric](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric).

## <a name="see-also"></a>Zobacz też

- [Hosting usługi danych](hosting-the-data-service-wcf-data-services.md)
- [Zabezpieczanie usług danych WCF](securing-wcf-data-services.md)
- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
