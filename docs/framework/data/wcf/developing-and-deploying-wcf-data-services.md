---
title: Tworzenie i wdrażanie usług danych WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d20d4c39a6cca744ac981d1a143d2847d9b20e5a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="developing-and-deploying-wcf-data-services"></a>Tworzenie i wdrażanie usług danych WCF
Ten temat zawiera informacje o tworzeniu i wdrażaniu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Aby uzyskać więcej ogólnych informacji o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz [wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) i [omówienie](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).  
  
## <a name="developing-wcf-data-services"></a>Projektowanie usług danych programu WCF  
 Jeśli używasz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Aby utworzyć usługę danych, która obsługuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], należy wykonać następujące zadania podstawowe podczas tworzenia:  
  
1.  **Zdefiniuj modelu danych**  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje wiele różnych dostawców usług danych, które umożliwiają definiowanie na podstawie danych z różnych źródeł danych z relacyjnych baz danych do typów danych z późnym wiązaniem modelu danych. Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
2.  **Tworzenie usługi danych**  
  
     Najbardziej podstawowa usługa danych udostępnia klasy, która dziedziczy <xref:System.Data.Services.DataService%601> klasy z typem `T` czyli kwalifikowana przestrzeni nazw nazwa kontenera jednostek. Aby uzyskać więcej informacji, zobacz [definiowania usługi danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Konfigurowanie usługi danych**  
  
     Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] wyłącza dostęp do zasobów, które są dostępne w kontenerze jednostek. <xref:System.Data.Services.DataServiceConfiguration> Interfejsu można skonfigurować dostęp do zasobów i operacji usługi, określ obsługiwaną wersję [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]oraz innych zachowań usługi WWW, takich jak przetwarzanie wsadowe zachowania lub maksymalna liczba jednostek, które można określić zwracane w pojedynczą odpowiedź źródła danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 W tym temacie omówiono przede wszystkim opracowywania i wdrażania usług danych przy użyciu programu Visual Studio. Informacje o elastyczności przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] publikowania danych jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, zobacz [definiowania usługi danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
### <a name="choosing-a-development-web-server"></a>Wybór deweloperskiego serwera sieci Web  
 Podczas opracowywania usługi danych WCF jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji lub [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] witryny sieci Web za pomocą programu Visual Studio, masz do wyboru serwerów sieci Web, na którym ma być uruchamiany podczas tworzenia usługi danych. Następujące serwery sieci Web integracji z programem Visual Studio, aby ułatwić testowanie i debugowanie usług danych na komputerze lokalnym.  
  
1.  **Serwer lokalny usług IIS**  
  
     Podczas tworzenia usługi danych jest [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji lub [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] witryny sieci Web uruchomioną na Internet Information Services (IIS), zaleca się tworzenia i testowania usługi danych przy użyciu usług IIS na komputerze lokalnym. Uruchamianie usługi danych na serwerze IIS ułatwia śledzenie żądań HTTP podczas debugowania. Pozwala również wstępnie określić niezbędne uprawnienia wymagane przez program IIS przy uzyskiwaniu dostępu do plików, baz danych i innych zasobów wymaganych przez usługę danych. Przy uruchamianiu usługi danych w usługach IIS, możesz musi upewnij się, że zarówno usług IIS i [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zainstalowana i poprawnie skonfigurowana i udzielanie dostępu do kont usług IIS w systemie plików i baz danych. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych WCF działającą na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
    > [!NOTE]
    >  Możesz uruchomić program Visual Studio z uprawnieniami administratora, aby włączyć środowisko rozwoju do konfigurowania lokalnego serwera IIS.  
  
2.  **Serwera wdrożeniowego programu Visual Studio**  
  
     Visual Studio zawiera wbudowanego serwera sieci Web, serwera wdrożeniowego programu Visual Studio czyli domyślnego serwera sieci Web dla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektów. Ten serwer sieci Web jest przeznaczony do uruchamiania [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekty na komputerze lokalnym w czasie projektowania. [Szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) pokazano, jak utworzyć usługę danych, która działa w serwera wdrożeniowego programu Visual Studio.  
  
     Należy zwrócić uwagę na następujące ograniczenia używania serwera wdrożeniowego programu Visual Studio umożliwiające tworzenie usługi danych:  
  
    -   Dostęp do tego serwera można uzyskać tylko na komputerze lokalnym.  
  
    -   Ten serwer nasłuchuje na `localhost` i na określonym porcie, a nie na porcie 80, który jest domyślnym portem dla wiadomości HTTP. Aby uzyskać więcej informacji, zobacz [serwerów sieci Web w programie Visual Studio dla projektów sieci Web ASP.NET](http://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
    -   Ten serwer uruchamia usługę danych w kontekście bieżącego konta użytkownika. Na przykład jeśli uruchamiasz jako administrator na poziomie użytkownika, Usługa danych działa w serwera wdrożeniowego programu Visual Studio będzie mieć uprawnienia administratora na poziomie. Może to spowodować, że usługa danych będzie mogła uzyskać dostęp do zasobów, do których nie ma praw dostępu w przypadku jej wdrożenia na serwerze IIS.  
  
    -   Ten serwer nie oferuje dodatkowych funkcji programu IIS, takich jak uwierzytelnianie.  
  
    -   Ten serwer nie może obsłużyć fragmentarycznego HTTP strumieni, które są wysyłane jest domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta podczas uzyskiwania dostępu do dużych danych binarnych z usługi danych. Aby uzyskać więcej informacji, zobacz [przesyłania strumieniowego dostawcy](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
    -   Ten serwer ma problemy z okresu przetwarzania (`.`) znaków w adresie URL, mimo że ten znak jest obsługiwana przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] w wartości klucza.  
  
    > [!TIP]
    >  Mimo korzystania z serwera wdrożeniowego programu Visual Studio, aby przetestować usług danych podczas tworzenia, należy przetestować je ponownie po wdrożeniu na serwerze sieci Web z uruchomionymi usługami IIS.  
  
3.  **Środowisko projektowe platformy Azure z systemem Windows**  
  
     Narzędzia systemu Windows Azure dla programu Visual Studio zawiera zintegrowany zestaw narzędzi do tworzenia usług systemu Windows Azure w programie Visual Studio. Za pomocą tych narzędzi można zaprojektować usługę danych, którą będzie można wdrożyć w systemie Microsoft Azure i przed wdrożeniem można przetestować usługę danych na komputerze lokalnym. Te narzędzia używane do opracowywania usłudze danych, która działa na platformie Windows Azure przy użyciu programu Visual Studio. Możesz pobrać narzędzi systemu Windows Azure dla programu Visual Studio z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Tworzenie usłudze danych, która działa w systemie Windows Azure, zobacz wpis [wdrażanie usługi OData w systemie Windows Azure](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="development-tips"></a>Porady dotyczące projektowania  
 Podczas projektowania usługi danych należy wziąć pod uwagę następujące kwestie:  
  
-   Określ wymagania zabezpieczeń usługi danych, jeśli planujesz uwierzytelnianie użytkowników lub ograniczenie dostępu w przypadku określonych użytkowników. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usługi danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
-   Program inspekcji HTTP może być bardzo pomocny podczas debugowania usługi danych, umożliwiając inspekcję zawartości komunikatów żądań i odpowiedzi. Dowolnego analizatora pakietów sieciowych, który może wyświetlać pakiety nieprzetworzone, można używać do inspekcji żądań HTTP i odpowiedzi z usługi danych.  
  
-   Podczas debugowania usługi danych można uzyskać więcej informacji o błędzie z usługi danych niż podczas normalnej pracy. Dodatkowe informacje o błędzie można uzyskać z usługi danych, ustawiając <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> właściwości w <xref:System.Data.Services.DataServiceConfiguration> do `true` i ustawiając <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwość <xref:System.ServiceModel.Description.ServiceDebugBehavior> atrybutu dla klasy usługi danych do `true`. Aby uzyskać więcej informacji, zobacz wpis [debugowania usługi danych WCF](http://go.microsoft.com/fwlink/?LinkId=201868). Można również włączyć śledzenie w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do wyświetlania wyjątków zgłoszonych w warstwie obsługi komunikatów HTTP. Aby uzyskać więcej informacji, zobacz [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Usługi danych jest zwykle opracowany jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekt aplikacji, ale można również utworzyć należy Usługa danych jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projekt witryny sieci Web w programie Visual Studio. Informacje o różnicach między tymi dwoma typami projektów, zobacz [NIB: projekty aplikacji sieci Web i projektów witryny sieci Web w programie Visual Studio](http://msdn.microsoft.com/library/2861815e-f5a2-4378-a2f8-b8a86dc012f5).  
  
-   Podczas tworzenia usługi danych przy użyciu **Dodaj nowy element** okno dialogowe programu Visual Studio z usługą danych jest hostowana przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] w usługach IIS. Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] i usług IIS jest domyślnego hosta dla usługi danych, obsługiwane są inne opcje hostingu. Aby uzyskać więcej informacji, zobacz [obsługujący usługę danych](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).  
  
## <a name="deploying-wcf-data-services"></a>Wdrażanie usług danych programu WCF  
 Usługa danych programu WCF zapewnia elastyczność, jeśli chodzi o wybór procesu hostującego usługę danych. Za pomocą programu Visual Studio można wdrożyć usługę danych na poniższych platformach:  
  
-   **Serwer hostowanych przez usługi IIS sieci Web**  
  
     Gdy usługa danych został utworzony jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, może on wdrożony na serwerze sieci Web usług IIS przy użyciu standardu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] procesów wdrażania.  Program Visual Studio oferuje następujące technologie wdrażania do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]w zależności od rodzaju z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projektu, który obsługuje usługę danych, która jest wdrażana.  
  
    -   **Technologie wdrażania dla aplikacji sieci Web ASP.NET**  
  
        -   [Pakiet wdrożeniowy sieci Web](http://msdn.microsoft.com/library/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [Publikowania jednym kliknięciem](http://msdn.microsoft.com/library/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **Technologie wdrażania dla witryn sieci Web ASP.NET**  
  
        -   [Skopiuj narzędzie witryny sieci Web](http://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)  
  
        -   [Publikowanie witryny sieci Web narzędzia](http://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)  
  
        -   [XCopy](http://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Opcje wdrożenia dla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, zobacz [Omówienie wdrożenia sieci Web dla platformy ASP.NET i Visual Studio](http://msdn.microsoft.com/library/99bd1927-b59f-4e02-87b4-55c6ba2adbc3).  
  
    > [!TIP]
    >  Przed próbą wdrożenia usługi danych w programie IIS należy przetestować wdrożenie na serwerze sieci Web, na którym działa program IIS. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych WCF działającą na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
-   **Windows Azure**  
  
     Usługi danych systemu Windows Azure można wdrożyć przy użyciu narzędzi systemu Windows Azure dla programu Visual Studio. Możesz pobrać narzędzi systemu Windows Azure dla programu Visual Studio z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Wdrażanie usługi danych w systemie Windows Azure, zobacz wpis [wdrażanie usługi OData w systemie Windows Azure](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="deployment-considerations"></a>Uwagi dotyczące wdrażania  
 Podczas wdrażania usługi danych należy wziąć pod uwagę następujące kwestie:  
  
-   Podczas wdrażania usługi danych, który używa [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy bazy danych programu SQL Server, może być również konieczne propagację struktury danych, danych, lub wdrożenie zarówno z danymi usługi. Visual Studio może automatycznie tworzyć skrypty (pliki SQL), aby to zrobić w docelowej bazie danych, i te skrypty może być uwzględniony w pakiecie wdrożeniowym sieci Web z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [NIB: porady: Wdrażanie bazy danych z projektu aplikacji sieci Web](http://msdn.microsoft.com/library/683b33f1-8a3d-45cf-af6e-61ab50fc518b). Aby uzyskać [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] witryny sieci Web, można to zrobić pomocą **Kreator publikowania bazy danych** w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [wdrażania bazy danych przy użyciu Kreatora publikowania bazy danych](http://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7).  
  
-   Ponieważ [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obejmuje podstawowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementacji, można użyć programu Windows Server AppFabric do monitorowania usługi danych wdrożonych w programie IIS w systemie Windows Server. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] za pomocą programu Windows Server AppFabric do monitorowania usługi danych, zobacz wpis [śledzenia usług danych WCF za pomocą programu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=202005).  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting usługi danych](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 [Zabezpieczanie usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
