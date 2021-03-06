---
title: Tworzenie i wdrażanie usług danych programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 7519dce8ed17bc623173f30222296ffaa42b4341
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416063"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Opracowywanie i wdrażanie Usługi danych programu WCF

Ten artykuł zawiera informacje dotyczące opracowywania i wdrażania Usługi danych programu WCF. Aby uzyskać więcej informacji na temat Usługi danych programu WCF, zobacz [wprowadzenie](getting-started-with-wcf-data-services.md) i [Przegląd](wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Opracowywanie Usługi danych programu WCF

W przypadku używania Usługi danych programu WCF do tworzenia usługi danych, która obsługuje protokół Open Data Protocol (OData), podczas programowania należy wykonać następujące podstawowe zadania:

1. **Zdefiniowanie modelu danych**

     Usługi danych programu WCF obsługuje różnych dostawców usług danych, które pozwalają definiować model danych oparty na danych z różnych źródeł danych, od relacyjnych baz danych do typów danych z późnym wiązaniem. Aby uzyskać więcej informacji, zobacz [Data Services Providers](data-services-providers-wcf-data-services.md).

2. **Utworzenie usługi danych**

     Najbardziej podstawowa usługa danych uwidacznia klasę, która dziedziczy z <xref:System.Data.Services.DataService%601> klasy, z typem, `T` który jest kwalifikowana nazwaną przestrzenią nazw kontenera jednostek. Aby uzyskać więcej informacji, zobacz [definiowanie usługi danych programu WCF](defining-wcf-data-services.md).

3. **Konfigurowanie usługi danych**

     Domyślnie Usługi danych programu WCF wyłącza dostęp do zasobów, które są udostępniane przez kontener jednostek. <xref:System.Data.Services.DataServiceConfiguration>Interfejs umożliwia skonfigurowanie dostępu do zasobów i usług, określenie obsługiwanej wersji usługi OData oraz zdefiniowanie innych zachowań obejmujących wiele usług, takich jak zachowania wsadowe lub maksymalna liczba jednostek, które mogą zostać zwrócone w ramach pojedynczego źródła odpowiedzi. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).

W tym artykule opisano głównie opracowywanie i wdrażanie usług danych przy użyciu programu Visual Studio. Aby uzyskać informacje na temat elastyczności zapewnianej przez Usługi danych programu WCF w celu udostępnienia danych jako źródła strumieniowego OData, zobacz [definiowanie usługi danych programu WCF](defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Wybierz serwer deweloperski sieci Web

W przypadku tworzenia usługi danych programu WCF jako aplikacji ASP.NET lub witryny sieci Web ASP.NET przy użyciu programu Visual Studio 2015 można wybrać serwery sieci Web, na których będzie uruchamiana usługa danych podczas opracowywania. Poniższe serwery sieci Web integrują się z programem Visual Studio, aby ułatwić testowanie i debugowanie usług danych na komputerze lokalnym.

1. **Lokalny serwer IIS**

     Podczas tworzenia usługi danych, która jest aplikacją ASP.NET lub witryną sieci Web ASP.NET działającą na Internet Information Services (IIS), zalecamy tworzenie i testowanie usługi danych przy użyciu usług IIS na komputerze lokalnym. Uruchamianie usługi danych na serwerze IIS ułatwia śledzenie żądań HTTP podczas debugowania. Pozwala to również wstępnie określić niezbędne prawa wymagane przez usługi IIS do uzyskiwania dostępu do plików, baz danych i innych zasobów wymaganych przez usługę danych. Aby uruchomić usługę danych na serwerze IIS, upewnij się, że zarówno program IIS, jak i Windows Communication Foundation (WCF) są zainstalowane i poprawnie skonfigurowane, a następnie Udziel dostępu do kont usług IIS w systemie plików i bazach danych. Aby uzyskać więcej informacji, zobacz [How to: programowanie usługi danych programu WCF działającej w usługach IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Musisz uruchomić program Visual Studio z uprawnieniami administratora, aby umożliwić środowisku programowania skonfigurowanie lokalnego serwera usług IIS.

2. **Serwer programistyczny programu Visual Studio**

     Program Visual Studio zawiera wbudowany serwer sieci Web, serwer programistyczny programu Visual Studio, który jest domyślnym serwerem sieci Web dla projektów ASP.NET. Ten serwer sieci Web został zaprojektowany do uruchamiania projektów ASP.NET na komputerze lokalnym podczas opracowywania. [Usługi danych programu WCF przewodniku szybki start](quickstart-wcf-data-services.md) przedstawia sposób tworzenia usługi danych działającej na serwerze deweloperskim programu Visual Studio.

     Podczas tworzenia usługi danych należy pamiętać o następujących ograniczeniach:

    - Dostęp do tego serwera można uzyskać tylko na komputerze lokalnym.

    - Ten serwer nasłuchuje na `localhost` określonym porcie, a nie na porcie 80, który jest domyślnym portem dla komunikatów http. Aby uzyskać więcej informacji, zobacz [serwery sieci Web w programie Visual Studio for ASP.NET — projekty sieci Web](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - Ten serwer uruchamia usługę danych w kontekście bieżącego konta użytkownika. Na przykład jeśli korzystasz z programu jako użytkownik na poziomie administratora, usługa danych uruchomiona na serwerze deweloperskim programu Visual Studio będzie mieć uprawnienia na poziomie administratora. Może to spowodować, że usługa danych będzie mogła uzyskać dostęp do zasobów, do których nie ma praw dostępu w przypadku jej wdrożenia na serwerze IIS.

    - Ten serwer nie oferuje dodatkowych funkcji programu IIS, takich jak uwierzytelnianie.

    - Ten serwer nie obsługuje fragmentarycznych strumieni HTTP, które są domyślnie wysyłane przez klienta Usługi danych programu WCF podczas uzyskiwania dostępu do dużych danych binarnych z usługi danych. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](streaming-provider-wcf-data-services.md).

    - Ten serwer ma problemy z przetwarzaniem znaku kropki ( `.` ) w adresie URL, mimo że ten znak jest obsługiwany przez usługi danych programu WCF w wartościach klucza.

    > [!TIP]
    > Mimo że można użyć programu Visual Studio Development Server do testowania usług danych podczas opracowywania, należy przetestować je ponownie po wdrożeniu na serwerze sieci Web, na którym są uruchomione usługi IIS.

3. **Środowisko deweloperskie platformy Azure**

     Narzędzia systemu Azure dla programu Visual Studio obejmują zintegrowany zestaw narzędzi do tworzenia usług platformy Azure w programie Visual Studio. Za pomocą tych narzędzi można opracowywać usługi danych, które można wdrożyć na platformie Azure, i można przetestować usługę danych na komputerze lokalnym przed wdrożeniem. Użyj tych narzędzi podczas korzystania z programu Visual Studio do tworzenia usługi danych działającej na platformie Azure. Aby uzyskać informacje na temat instalowania narzędzi, zobacz [Azure Tools for Visual Studio 2015](../../../azure/vs2015-install.md). Aby uzyskać więcej informacji na temat tworzenia usługi danych działającej na platformie Azure, zobacz po wdrożeniu [usługi OData na platformie Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="development-tips"></a>Porady dotyczące projektowania

Podczas tworzenia usługi danych należy wziąć pod uwagę następujące kwestie:

- Jeśli planujesz uwierzytelnianie użytkowników lub ograniczasz dostęp dla określonych użytkowników, ustal wymagania dotyczące zabezpieczeń usługi danych. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usługi danych programu WCF](securing-wcf-data-services.md).

- Program inspekcji HTTP może być przydatny podczas debugowania usługi danych, umożliwiając inspekcję zawartości komunikatów żądania i odpowiedzi. Dowolnego analizatora pakietów sieciowych, który może wyświetlać pakiety nieprzetworzone, można używać do inspekcji żądań HTTP i odpowiedzi z usługi danych.

- Podczas debugowania usługi danych warto uzyskać więcej informacji o błędzie z usługi danych niż podczas zwykłej operacji. Możesz uzyskać dodatkowe informacje o błędzie z usługi danych, ustawiając <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> Właściwość w <xref:System.Data.Services.DataServiceConfiguration> na `true` i ustawiając <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwość atrybutu w <xref:System.ServiceModel.Description.ServiceDebugBehavior> klasie usługi danych na `true` . Aby uzyskać więcej informacji, zobacz [usługi danych programu WCF debugowania](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services). Możesz również włączyć śledzenie w programie WCF, aby wyświetlić wyjątki wywoływane w warstwie komunikatów HTTP. Aby uzyskać więcej informacji, zobacz [Konfigurowanie śledzenia](../../wcf/diagnostics/tracing/configuring-tracing.md).

- Usługa danych jest zazwyczaj opracowana jako projekt aplikacji ASP.NET, ale można również utworzyć usługę danych jako projekt witryny sieci Web ASP.NET w programie Visual Studio. Aby uzyskać informacje o różnicach między dwoma typami projektów, zobacz [projekty aplikacji sieci Web a projekty witryn sieci Web w programie Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- Podczas tworzenia usługi danych przy użyciu okna dialogowego **Dodaj nowy element** w programie Visual Studio usługa danych jest hostowana przez ASP.NET w usługach IIS. Chociaż ASP.NET i IIS jest domyślnym hostem dla usługi danych, obsługiwane są inne opcje hostingu. Aby uzyskać więcej informacji, zobacz [hosting usługi danych](hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Wdróż Usługi danych programu WCF

Usługa danych programu WCF zapewnia elastyczność, jeśli chodzi o wybór procesu hostującego usługę danych. Za pomocą programu Visual Studio można wdrożyć usługę danych na następujących platformach:

- **Serwer sieci Web hostowany przez usługi IIS**

    Po opracowaniu usługi danych jako projektu ASP.NET można ją wdrożyć na serwerze sieci Web usług IIS przy użyciu standardowych procesów wdrażania ASP.NET. Program Visual Studio udostępnia następujące technologie wdrażania ASP.NET, w zależności od rodzaju projektu ASP.NET, który obsługuje wdrożoną usługę danych.

  - **Technologie wdrażania aplikacji sieci Web ASP.NET**

    - [Instrukcje: Tworzenie pakietu wdrożeniowego sieci Web w programie Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465323(v=vs.110))

    - [Instrukcje: wdrażanie projektu sieci Web przy użyciu jednego kliknięcia przycisku Publikuj w programie Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd465337(v=vs.110))

  - **Technologie wdrażania dla witryn sieci Web ASP.NET**

    - [Instrukcje: kopiowanie plików witryny sieci Web za pomocą narzędzia kopiowania witryny sieci Web](https://docs.microsoft.com/previous-versions/aspnet/c95809c0(v=vs.100))

    - [Instrukcje: publikowanie witryn sieci Web](https://docs.microsoft.com/previous-versions/aspnet/20yh9f1b(v=vs.100))

    - [Przewodnik: wdrażanie aplikacji sieci Web ASP.NET przy użyciu polecenia XCOPY](https://docs.microsoft.com/previous-versions/aspnet/f735abw9(v=vs.100))

     Aby uzyskać więcej informacji o opcjach wdrażania dla aplikacji ASP.NET, zobacz [Omówienie wdrażania w sieci Web dla programu Visual Studio i ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/dd394698(v=vs.110)).

    > [!TIP]
    > Przed próbą wdrożenia usługi danych w programie IIS należy przetestować wdrożenie na serwerze sieci Web, na którym działa program IIS. Aby uzyskać więcej informacji, zobacz [How to: programowanie usługi danych programu WCF działającej w usługach IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

- **Azure**

     Usługę danych można wdrożyć na platformie Azure przy użyciu [narzędzi platformy Azure dla programu Visual Studio](../../../azure/vs2015-install.md). Aby uzyskać więcej informacji na temat wdrażania usługi danych na platformie Azure, zobacz [wdrażanie usługi OData na platformie Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="deployment-considerations"></a>Uwagi dotyczące wdrażania

Podczas wdrażania usługi danych należy wziąć pod uwagę następujące kwestie:

- Podczas wdrażania usługi danych, która używa dostawcy Entity Framework w celu uzyskania dostępu do bazy danych SQL Server, może być również konieczne propagowanie struktur danych, danych lub obu w ramach wdrożenia usługi danych. Program Visual Studio może automatycznie tworzyć skrypty (pliki SQL) w celu wykonania tej czynności w docelowej bazie danych. te skrypty można dołączać do pakietu wdrożeniowego sieci Web aplikacji ASP.NET. Aby uzyskać więcej informacji, zobacz [jak: Wdrażanie bazy danych za pomocą projektu aplikacji sieci Web](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). W przypadku witryny sieci Web ASP.NET można to zrobić za pomocą **Kreatora publikowania bazy danych** w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [publikowanie SQL Database](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- Ponieważ Usługi danych programu WCF zawiera podstawową implementację programu WCF, można użyć programu Windows Server AppFabric do monitorowania usługi danych wdrożonej w usługach IIS uruchomionych w systemie Windows Server. Aby uzyskać więcej informacji o używaniu programu Windows Server AppFabric do monitorowania usługi danych, zobacz [śledzenie po stronie śledzenia usługi danych programu WCF z systemem Windows Server AppFabric](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric).

## <a name="see-also"></a>Zobacz także

- [Hosting usługi danych](hosting-the-data-service-wcf-data-services.md)
- [Zabezpieczanie usług danych WCF](securing-wcf-data-services.md)
- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
