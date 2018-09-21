---
title: Tworzenie i wdrażanie usług danych WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: cf1782eaf54701f0cf93576325b3d46e8bc4d3f1
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46517691"
---
# <a name="develop-and-deploy-wcf-data-services"></a>Tworzenie i wdrażanie usług danych WCF

Ten temat zawiera informacje dotyczące projektowania i wdrażania usług danych WCF. Aby uzyskać bardziej podstawowe informacje na temat usług danych WCF zobacz [wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) i [Przegląd](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).

## <a name="develop-wcf-data-services"></a>Tworzenie usługi danych WCF

Kiedy używasz usług danych WCF utworzyć usługę danych, która obsługuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], należy wykonać następujące podstawowe zadania podczas projektowania:

1.  **Zdefiniowanie modelu danych**

     Usługi danych WCF obsługuje wiele różnych dostawców usług danych, które umożliwiają zdefiniowanie modelu danych na podstawie danych z różnych źródeł danych z relacyjnej bazy danych do typów danych z późnym wiązaniem. Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).

2.  **Tworzenie usługi danych**

     Najbardziej podstawowa usługa danych uwidacznia klasę, która dziedziczy po elemencie <xref:System.Data.Services.DataService%601> klasy o typie `T` czyli przestrzeni nazw kwalifikowana nazwa kontenera jednostek. Aby uzyskać więcej informacji, zobacz [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

3.  **Konfigurowanie usługi danych**

     Domyślnie usługi danych WCF powoduje wyłączenie dostępu do zasobów, które są uwidaczniane przez kontener jednostek. <xref:System.Data.Services.DataServiceConfiguration> Interfejs umożliwia skonfigurowanie dostępu do zasobów i operacji usług, określenie obsługiwanej wersji OData oraz zdefiniowanie innych zachowań całej usługi, takie jak przetwarzanie wsadowe zachowania lub maksymalna liczba jednostek, które mogą być zwracane w kanale informacyjnym pojedynczą odpowiedź. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

W tym temacie omówiono przede wszystkim tworzenia i wdrażania usługi danych przy użyciu programu Visual Studio. Aby uzyskać informacji na temat elastyczności zapewnianej przez usługi danych WCF chodzi o Uwidacznianie danych jako źródeł danych OData, zobacz [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

### <a name="choose-a-development-web-server"></a>Wybierz serwer sieci Web Development

Podczas tworzenia usługi danych programu WCF jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji lub [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] witryny sieci Web za pomocą programu Visual Studio 2015, masz do wyboru, serwery sieci Web, na którym ma być uruchamiana usługa danych podczas programowania. Poniższe serwery sieci Web integrują się z programem Visual Studio, aby ułatwić testowanie i debugowanie usług danych na komputerze lokalnym.

1.  **Lokalny serwer IIS**

     Podczas tworzenia usługi danych jest [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji lub [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] witryny sieci Web, która jest uruchamiana w Internet Information Services (IIS), zaleca się projektowanie i testowanie usługi danych przy użyciu usług IIS na komputerze lokalnym. Uruchamianie usługi danych na serwerze IIS ułatwia śledzenie żądań HTTP podczas debugowania. Pozwala również wstępnie określić niezbędne uprawnienia wymagane przez program IIS przy uzyskiwaniu dostępu do plików, baz danych i innych zasobów wymaganych przez usługę danych. Aby uruchamiać usługę danych na serwerze IIS, należy upewnić się, zarówno w przypadku usług IIS, jak i Windows Communication Foundation (WCF) są zainstalowane i poprawnie skonfigurowane i udzielić dostępu do kont usług IIS w systemie plików i baz danych. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych WCF działającej na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).

    > [!NOTE]
    > Możesz uruchomić program Visual Studio z uprawnieniami administratora, aby włączyć środowisko deweloperskie w celu skonfigurowania lokalnego serwera IIS.

2.  **Serwer deweloperski programu Visual Studio**

     Program Visual Studio obejmuje wbudowanego serwera sieci Web serwera wdrożeniowego programu Visual Studio czyli domyślnego serwera sieci Web dla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektów. Ten serwer sieci Web jest przeznaczony do działania [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekty na komputerze lokalnym podczas projektowania. [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) pokazuje, jak utworzyć usługę danych, która działa w serwera wdrożeniowego programu Visual Studio.

     Należy pamiętać o następujących ograniczeniach, gdy używasz serwera wdrożeniowego programu Visual Studio do projektowania usługi danych:

    -   Dostęp do tego serwera można uzyskać tylko na komputerze lokalnym.

    -   Ten serwer nasłuchuje na `localhost` i na określonym porcie, a nie na porcie 80, który jest domyślnym portem dla komunikatów HTTP. Aby uzyskać więcej informacji, zobacz [serwerów sieci Web w programie Visual Studio dla projektów sieci Web platformy ASP.NET](https://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).

    -   Ten serwer uruchamia usługę danych w kontekście bieżącego konta użytkownika. Na przykład jeśli używasz jako użytkownik na poziomie administratora, Usługa danych uruchomiona w serwera wdrożeniowego programu Visual Studio mają uprawnienia na poziomie administratora. Może to spowodować, że usługa danych będzie mogła uzyskać dostęp do zasobów, do których nie ma praw dostępu w przypadku jej wdrożenia na serwerze IIS.

    -   Ten serwer nie oferuje dodatkowych funkcji programu IIS, takich jak uwierzytelnianie.

    -   Ten serwer nie obsługuje fragmentarycznych strumieni HTTP, które są wysyłane jest domyślnie przez klienta usługi danych WCF, podczas uzyskiwania dostępu do dużych danych binarnych z usługi danych. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).

    -   Ten serwer ma problemy z przetworzeniem okres (`.`) znak w adresie URL, mimo że ten znak jest obsługiwany przez usługi danych WCF w wartościach klucza.

    > [!TIP]
    > Mimo że serwera wdrożeniowego programu Visual Studio można użyć do testowania usług danych podczas projektowania, należy przetestować je ponownie po wdrożeniu na serwerze sieci Web, na którym są uruchomione usługi IIS.

3.  **Środowisko deweloperskie platformy Azure Windows**

     Windows Azure Tools dla programu Visual Studio obejmują zintegrowany zestaw narzędzi do tworzenia usług Windows Azure w programie Visual Studio. Za pomocą tych narzędzi można zaprojektować usługę danych, którą będzie można wdrożyć w systemie Microsoft Azure i przed wdrożeniem można przetestować usługę danych na komputerze lokalnym. W przypadku używania programu Visual Studio do projektowania usługi danych, które jest uruchamiane na platformie Windows Azure, należy użyć tych narzędzi. Możesz pobrać program Windows Azure Tools dla programu Visual Studio z [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=201848). Aby uzyskać więcej informacji na temat tworzenia usługi danych, która działa na platformie Windows Azure, zobacz wpis [wdrażanie usługi OData w systemie Windows Azure](https://go.microsoft.com/fwlink/?LinkId=201847).

### <a name="development-tips"></a>Porady dotyczące projektowania

Podczas projektowania usługi danych należy wziąć pod uwagę następujące kwestie:

-   Określ wymagania zabezpieczeń usługi danych, jeśli planujesz uwierzytelnianie użytkowników lub ograniczenie dostępu w przypadku określonych użytkowników. Aby uzyskać więcej informacji, zobacz [zabezpieczania usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).

-   Program inspekcji HTTP może być bardzo pomocny podczas debugowania usługi danych, umożliwiając inspekcję zawartości komunikatów żądań i odpowiedzi. Dowolnego analizatora pakietów sieciowych, który może wyświetlać pakiety nieprzetworzone, można używać do inspekcji żądań HTTP i odpowiedzi z usługi danych.

-   Podczas debugowania usługi danych można uzyskać więcej informacji o błędzie z usługi danych niż podczas normalnej pracy. Dodatkowe informacje o błędzie można uzyskać z usługi danych, ustawiając <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> właściwość <xref:System.Data.Services.DataServiceConfiguration> do `true` i ustawiając <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwość <xref:System.ServiceModel.Description.ServiceDebugBehavior> atrybut w klasie usługi danych `true`. Aby uzyskać więcej informacji, zobacz wpis [debugowanie usług danych WCF](https://go.microsoft.com/fwlink/?LinkId=201868). Możesz również włączyć śledzenie w programie WCF, aby wyświetlić wyjątki wywoływane w warstwie obsługi komunikatów HTTP. Aby uzyskać więcej informacji, zobacz [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).

-   Usługa danych zazwyczaj projektuje się jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekt aplikacji, ale można również utworzyć usługę danych jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu witryny sieci Web w programie Visual Studio. Aby uzyskać informacje o różnicach między dwoma typami projektów, zobacz [NIB: Web Application Projects versus projektów witryny sieci Web w programie Visual Studio](https://msdn.microsoft.com/library/2861815e-f5a2-4378-a2f8-b8a86dc012f5).

-   Podczas tworzenia usługi danych przy użyciu **Dodaj nowy element** okno dialogowe w programie Visual Studio, Usługa danych jest hostowana przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] w usługach IIS. Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] i IIS są domyślnym hostem dla usługi danych, obsługiwane są inne opcje hostingu. Aby uzyskać więcej informacji, zobacz [Hosting usługi danych](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).

## <a name="deploy-wcf-data-services"></a>Wdrażanie usług danych WCF

Usługa danych programu WCF zapewnia elastyczność, jeśli chodzi o wybór procesu hostującego usługę danych. Visual Studio można użyć do wdrożenia usługi danych na następujących platformach:

-   **Serwer sieci Web obsługiwane przez usługi IIS**

     Jeśli usługa danych jest opracowana jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, można je było wdrożyć do serwera sieci Web usług IIS przy użyciu standardu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] procesów wdrażania.  Program Visual Studio zapewnia Poniższe technologie wdrażania programu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], w zależności od używanego z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, który hostuje usługę danych, w której przeprowadzasz wdrożenie.

    -   **Technologie wdrażania dla aplikacji sieci Web ASP.NET**

        -   [Pakiet wdrażania sieci Web](https://msdn.microsoft.com/library/1f9713c8-9540-494c-b80d-9893b970ad6f)

        -   [Publikowanie jednym kliknięciem](https://msdn.microsoft.com/library/59226246-99ad-4aec-975d-7c61e8a8911c)

    -   **Technologie wdrażania witryn sieci Web platformy ASP.NET**

        -   [Narzędzia kopiowania witryny internetowej](https://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)

        -   [Publikowanie witryny sieci Web narzędzia](https://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)

        -   [XCopy](https://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)

     Aby uzyskać więcej informacji o opcjach wdrażania [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, zobacz [Przegląd wdrażania sieci Web dla programu Visual Studio i platformy ASP.NET](https://msdn.microsoft.com/library/99bd1927-b59f-4e02-87b4-55c6ba2adbc3).

    > [!TIP]
    > Przed próbą wdrożenia usługi danych w programie IIS należy przetestować wdrożenie na serwerze sieci Web, na którym działa program IIS. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych WCF działającej na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).

-   **Windows Azure**

     Usługi danych można wdrożyć na platformie Windows Azure przy użyciu narzędzia Windows Azure Tools dla programu Visual Studio. Możesz pobrać program Windows Azure Tools dla programu Visual Studio z [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=201848). Aby uzyskać więcej informacji na temat wdrażania usługi danych na platformie Windows Azure, zobacz wpis [wdrażanie usługi OData w systemie Windows Azure](https://go.microsoft.com/fwlink/?LinkId=201847).

### <a name="deployment-considerations"></a>Uwagi dotyczące wdrażania

Podczas wdrażania usługi danych należy wziąć pod uwagę następujące kwestie:

-   Podczas wdrażania usługi danych, która używa [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy bazy danych programu SQL Server, może być również konieczne rozpropagowanie struktur danych, dane, lub obu z danymi wdrożenie usługi. Program Visual Studio może automatycznie tworzyć skrypty (pliki SQL), aby to zrobić w docelowej bazie danych i skrypty te mogą być zawarte w pakiet wdrażania sieci Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [jak: wdrożyć bazę danych z projektu aplikacji sieci Web](https://msdn.microsoft.com/library/683b33f1-8a3d-45cf-af6e-61ab50fc518b). Aby uzyskać [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] witryny sieci Web, można to zrobić pomocą **Database Publishing Wizard** w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [wdrażania bazy danych za pomocą Kreatora publikacji w bazie danych](https://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7).

-   Ponieważ WCF Data Services zawierają podstawową implementację programu WCF, można użyć programu Windows Server AppFabric do monitorowania usługi danych wdrożonej w programie IIS działającym w systemie Windows Server. Aby uzyskać więcej informacji o używaniu programu Windows Server AppFabric do monitorowania usługi danych, zobacz wpis [śledzenia usług danych WCF za pomocą programu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=202005).

## <a name="see-also"></a>Zobacz też

- [Hosting usługi danych](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
- [Zabezpieczanie usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)
- [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
