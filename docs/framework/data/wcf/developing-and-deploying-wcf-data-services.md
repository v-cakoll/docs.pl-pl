---
title: Tworzenie i wdrażanie usług danych programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: 1a017267c034fa1d6ea522855b7e0e7f056637ac
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504025"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Opracowywanie i wdrażanie Usługi danych programu WCF

Ten temat zawiera informacje dotyczące opracowywania i wdrażania Usługi danych programu WCF. Aby uzyskać więcej informacji na temat Usługi danych programu WCF, zobacz [wprowadzenie](getting-started-with-wcf-data-services.md) i [Przegląd](wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Opracowywanie Usługi danych programu WCF

W przypadku używania Usługi danych programu WCF do tworzenia usługi danych, która obsługuje protokół Open Data Protocol (OData), podczas programowania należy wykonać następujące podstawowe zadania:

1. **Definiowanie modelu danych**

     Usługi danych programu WCF obsługuje różnych dostawców usług danych, które pozwalają definiować model danych oparty na danych z różnych źródeł danych, od relacyjnych baz danych do typów danych z późnym wiązaniem. Aby uzyskać więcej informacji, zobacz [Data Services Providers](data-services-providers-wcf-data-services.md).

2. **Tworzenie usługi danych**

     Najbardziej podstawowa usługa danych uwidacznia klasę, która dziedziczy z klasy <xref:System.Data.Services.DataService%601>, z typem `T`, który jest kwalifikowana nazwa przestrzeni nazw kontenera jednostek. Aby uzyskać więcej informacji, zobacz [definiowanie usługi danych programu WCF](defining-wcf-data-services.md).

3. **Konfigurowanie usługi danych**

     Domyślnie Usługi danych programu WCF wyłącza dostęp do zasobów, które są udostępniane przez kontener jednostek. Interfejs <xref:System.Data.Services.DataServiceConfiguration> umożliwia konfigurowanie dostępu do zasobów i usług, określanie obsługiwanej wersji protokołu OData oraz definiowanie innych zachowań dotyczących całej usługi, takich jak zachowania wsadowe lub maksymalna liczba jednostek, które mogą zostać zwrócone w ramach pojedynczego źródła odpowiedzi. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).

Ten temat dotyczy głównie tworzenia i wdrażania usług danych przy użyciu programu Visual Studio. Aby uzyskać informacje na temat elastyczności zapewnianej przez Usługi danych programu WCF w celu udostępnienia danych jako źródła strumieniowego OData, zobacz [definiowanie usługi danych programu WCF](defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Wybierz serwer deweloperski sieci Web

W przypadku tworzenia usługi danych programu WCF jako aplikacji ASP.NET lub witryny sieci Web ASP.NET przy użyciu programu Visual Studio 2015 można wybrać serwery sieci Web, na których będzie uruchamiana usługa danych podczas opracowywania. Poniższe serwery sieci Web integrują się z programem Visual Studio, aby ułatwić testowanie i debugowanie usług danych na komputerze lokalnym.

1. **Lokalny serwer IIS**

     Podczas tworzenia usługi danych, która jest aplikacją ASP.NET lub witryną sieci Web ASP.NET działającą na Internet Information Services (IIS), zalecamy tworzenie i testowanie usługi danych przy użyciu usług IIS na komputerze lokalnym. Uruchamianie usługi danych na serwerze IIS ułatwia śledzenie żądań HTTP podczas debugowania. Pozwala również wstępnie określić niezbędne uprawnienia wymagane przez program IIS przy uzyskiwaniu dostępu do plików, baz danych i innych zasobów wymaganych przez usługę danych. Aby uruchomić usługę danych na serwerze IIS, należy upewnić się, że zarówno program IIS, jak i Windows Communication Foundation (WCF) są zainstalowane i poprawnie skonfigurowane, oraz udzielić dostępu do kont usług IIS w systemie plików i bazach danych. Aby uzyskać więcej informacji, zobacz [How to: programowanie usługi danych programu WCF działającej w usługach IIS](how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Musisz uruchomić program Visual Studio z uprawnieniami administratora, aby umożliwić środowisku programowania skonfigurowanie lokalnego serwera usług IIS.

2. **Serwer programistyczny programu Visual Studio**

     Program Visual Studio zawiera wbudowany serwer sieci Web, serwer programistyczny programu Visual Studio, który jest domyślnym serwerem sieci Web dla projektów ASP.NET. Ten serwer sieci Web został zaprojektowany do uruchamiania projektów ASP.NET na komputerze lokalnym podczas opracowywania. [Usługi danych programu WCF przewodniku szybki start](quickstart-wcf-data-services.md) przedstawia sposób tworzenia usługi danych działającej na serwerze deweloperskim programu Visual Studio.

     W przypadku korzystania z serwera deweloperskiego programu Visual Studio w celu opracowania usługi danych należy pamiętać o następujących ograniczeniach:

    - Dostęp do tego serwera można uzyskać tylko na komputerze lokalnym.

    - Ten serwer nasłuchuje na `localhost` i na określonym porcie, a nie na porcie 80, który jest domyślnym portem dla komunikatów HTTP. Aby uzyskać więcej informacji, zobacz [serwery sieci Web w programie Visual Studio for ASP.NET — projekty sieci Web](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120)).

    - Ten serwer uruchamia usługę danych w kontekście bieżącego konta użytkownika. Na przykład jeśli korzystasz z programu jako użytkownik na poziomie administratora, usługa danych uruchomiona na serwerze deweloperskim programu Visual Studio będzie mieć uprawnienia na poziomie administratora. Może to spowodować, że usługa danych będzie mogła uzyskać dostęp do zasobów, do których nie ma praw dostępu w przypadku jej wdrożenia na serwerze IIS.

    - Ten serwer nie oferuje dodatkowych funkcji programu IIS, takich jak uwierzytelnianie.

    - Ten serwer nie obsługuje fragmentów strumieni HTTP, które są domyślnie wysyłane przez klienta Usługi danych programu WCF podczas uzyskiwania dostępu do dużych danych binarnych z usługi danych. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](streaming-provider-wcf-data-services.md).

    - Ten serwer ma problemy z przetwarzaniem znaku kropki (`.`) w adresie URL, mimo że ten znak jest obsługiwany przez Usługi danych programu WCF wartości klucza.

    > [!TIP]
    > Mimo że można użyć programu Visual Studio Development Server do testowania usług danych podczas opracowywania, należy przetestować je ponownie po wdrożeniu na serwerze sieci Web, na którym są uruchomione usługi IIS.

3. **Środowisko deweloperskie systemu Windows Azure**

     Narzędzia Microsoft Azure Tools for Visual Studio zawierają zintegrowany zestaw narzędzi do tworzenia usług systemu Windows Azure w programie Visual Studio. Za pomocą tych narzędzi można zaprojektować usługę danych, którą będzie można wdrożyć w systemie Microsoft Azure i przed wdrożeniem można przetestować usługę danych na komputerze lokalnym. Użyj tych narzędzi, gdy program Visual Studio jest używany do tworzenia usługi danych działającej na platformie Windows Azure. Narzędzia Windows Azure Tools for Visual Studio można pobrać z [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/?LinkID=201848). Aby uzyskać więcej informacji na temat tworzenia usługi danych działającej w systemie Windows Azure, zobacz po wdrożeniu [usługi OData w systemie Windows Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="development-tips"></a>Porady dotyczące projektowania

Podczas projektowania usługi danych należy wziąć pod uwagę następujące kwestie:

- Określ wymagania zabezpieczeń usługi danych, jeśli planujesz uwierzytelnianie użytkowników lub ograniczenie dostępu w przypadku określonych użytkowników. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usługi danych programu WCF](securing-wcf-data-services.md).

- Program inspekcji HTTP może być bardzo pomocny podczas debugowania usługi danych, umożliwiając inspekcję zawartości komunikatów żądań i odpowiedzi. Dowolnego analizatora pakietów sieciowych, który może wyświetlać pakiety nieprzetworzone, można używać do inspekcji żądań HTTP i odpowiedzi z usługi danych.

- Podczas debugowania usługi danych warto uzyskać więcej informacji o błędzie z usługi danych niż podczas zwykłej operacji. Aby uzyskać dodatkowe informacje o błędzie z usługi danych, należy ustawić właściwość <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> w <xref:System.Data.Services.DataServiceConfiguration> na `true` i ustawiając właściwość <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> atrybutu <xref:System.ServiceModel.Description.ServiceDebugBehavior> w klasie usługi danych na `true`. Aby uzyskać więcej informacji, zobacz [usługi danych programu WCF debugowania](https://docs.microsoft.com/archive/blogs/phaniraj/debugging-wcf-data-services). Możesz również włączyć śledzenie w programie WCF, aby wyświetlić wyjątki wywoływane w warstwie komunikatów HTTP. Aby uzyskać więcej informacji, zobacz [Konfigurowanie śledzenia](../../wcf/diagnostics/tracing/configuring-tracing.md).

- Usługa danych jest zazwyczaj opracowana jako projekt aplikacji ASP.NET, ale można również utworzyć usługę danych jako projekt witryny sieci Web ASP.NET w programie Visual Studio. Aby uzyskać informacje o różnicach między dwoma typami projektów, zobacz [projekty aplikacji sieci Web a projekty witryn sieci Web w programie Visual Studio](https://docs.microsoft.com/previous-versions/aspnet/dd547590(v=vs.110)).

- Podczas tworzenia usługi danych przy użyciu okna dialogowego **Dodaj nowy element** w programie Visual Studio usługa danych jest hostowana przez ASP.NET w usługach IIS. Chociaż ASP.NET i IIS jest domyślnym hostem dla usługi danych, obsługiwane są inne opcje hostingu. Aby uzyskać więcej informacji, zobacz [hosting usługi danych](hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Wdróż Usługi danych programu WCF

Usługa danych programu WCF zapewnia elastyczność, jeśli chodzi o wybór procesu hostującego usługę danych. Za pomocą programu Visual Studio można wdrożyć usługę danych na następujących platformach:

- **Serwer sieci Web hostowany przez usługi IIS**

    Po opracowaniu usługi danych jako projektu ASP.NET można ją wdrożyć na serwerze sieci Web usług IIS przy użyciu standardowych procesów wdrażania ASP.NET.  Program Visual Studio udostępnia następujące technologie wdrażania ASP.NET, w zależności od rodzaju projektu ASP.NET, który obsługuje wdrożoną usługę danych.

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

- **System Windows Azure**

     Usługę danych można wdrożyć w systemie Windows Azure przy użyciu narzędzi Windows Azure Tools for Visual Studio. Narzędzia Windows Azure Tools for Visual Studio można pobrać z [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/?LinkID=201848). Aby uzyskać więcej informacji na temat wdrażania usługi danych w systemie Windows Azure, zobacz po wdrożeniu [usługi OData w systemie Windows Azure](https://docs.microsoft.com/archive/blogs/astoriateam/deploying-an-odata-service-in-windows-azure).

### <a name="deployment-considerations"></a>Uwagi dotyczące wdrażania

Podczas wdrażania usługi danych należy wziąć pod uwagę następujące kwestie:

- Podczas wdrażania usługi danych, która używa dostawcy Entity Framework w celu uzyskania dostępu do bazy danych SQL Server, może być również konieczne propagowanie struktur danych, danych lub obu w ramach wdrożenia usługi danych. Program Visual Studio może automatycznie tworzyć skrypty (pliki SQL) w celu wykonania tej czynności w docelowej bazie danych. te skrypty można dołączać do pakietu wdrożeniowego sieci Web aplikacji ASP.NET. Aby uzyskać więcej informacji, zobacz [jak: Wdrażanie bazy danych za pomocą projektu aplikacji sieci Web](https://docs.microsoft.com/previous-versions/dd465343(v=vs.100)). W przypadku witryny sieci Web ASP.NET można to zrobić za pomocą **Kreatora publikowania bazy danych** w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [publikowanie SQL Database](https://docs.microsoft.com/previous-versions/aspnet/bb907585(v=vs.100)).

- Ponieważ Usługi danych programu WCF zawiera podstawową implementację programu WCF, można użyć programu Windows Server AppFabric do monitorowania usługi danych wdrożonej w usługach IIS uruchomionych w systemie Windows Server. Aby uzyskać więcej informacji o używaniu programu Windows Server AppFabric do monitorowania usługi danych, zobacz [śledzenie po stronie śledzenia usługi danych programu WCF z systemem Windows Server AppFabric](https://docs.microsoft.com/archive/blogs/rjacobs/tracking-wcf-data-services-with-windows-server-appfabric).

## <a name="see-also"></a>Zobacz też

- [Hosting usługi danych](hosting-the-data-service-wcf-data-services.md)
- [Zabezpieczanie usług danych WCF](securing-wcf-data-services.md)
- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
