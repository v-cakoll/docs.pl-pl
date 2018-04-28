---
title: Konfigurowanie usługi danych (usługi danych WCF)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 59efd4c8-cc7a-4800-a0a4-d3f8abe6c55c
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c3c82e1e4460e82dd7e6bd88771eae96f132c8e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="configuring-the-data-service-wcf-data-services"></a>Konfigurowanie usługi danych (usługi danych WCF)
Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można utworzyć usług danych, które udostępniają [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródeł danych. Dane w tych źródeł danych mogą pochodzić z różnych źródeł danych. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] używa dostawcy danych do udostępnienia tych danych jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Tych dostawców obejmują [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy, dostawca odbicia i zestaw interfejsów dostawcy usług danych niestandardowych. Implementacja dostawcy definiuje model danych dla usługi. Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
 W [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], Usługa danych jest klasa, która dziedziczy <xref:System.Data.Services.DataService%601> klasy, których typem usługi danych jest kontenera jednostek w modelu danych. Ten kontener jednostka ma jedną lub więcej właściwości, które zwracają <xref:System.Linq.IQueryable%601>, które umożliwiają dostęp do jednostki ustawia w modelu danych.  
  
 Zachowania usługi danych są definiowane przez członków <xref:System.Data.Services.DataServiceConfiguration> klasy oraz przez członków <xref:System.Data.Services.DataServiceBehavior> klasy, która jest dostępny z <xref:System.Data.Services.DataServiceConfiguration.DataServiceBehavior%2A> właściwość <xref:System.Data.Services.DataServiceConfiguration> klasy. <xref:System.Data.Services.DataServiceConfiguration> Klasy został dostarczony do `InitializeService` metodę, która jest zaimplementowana przez usługę danych, jak poniższe implementacji usługi danych Northwind:  
  
[!code-csharp[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/Astoria Northwind Service/cs/northwind.svc.cs#dataserviceconfigcomplete)]  
[!code-vb[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/Astoria Northwind Service/vb/northwind.svc.vb#dataserviceconfigcomplete)]  
  
## <a name="data-service-configuration-settings"></a>Ustawienia konfiguracji usługi danych  
 <xref:System.Data.Services.DataServiceConfiguration> Klasy można określić następujące dane zachowania usługi:  
  
|Element członkowski|Zachowanie|  
|------------|--------------|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptCountRequests%2A>|Umożliwia wyłączenie liczba żądań, które są przesyłane do usługi danych przy użyciu `$count` segment ścieżki i `$inlinecount` opcji zapytania. Aby uzyskać więcej informacji, zobacz [OData: identyfikator URI konwencje](http://go.microsoft.com/fwlink/?LinkId=185564).|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptProjectionRequests%2A>|Umożliwia wyłączenie obsługi dla danych projekcji w żądaniach, które są przesyłane do usługi danych przy użyciu `$select` opcji zapytania. Aby uzyskać więcej informacji, zobacz [OData: identyfikator URI konwencje](http://go.microsoft.com/fwlink/?LinkId=185564).|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeAccess%2A>|Włącza typu danych mają być uwidaczniane w metadanych dla dostawcy metadanych dynamiczne zdefiniowany przy użyciu <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interfejsu.|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeConversion%2A>|Umożliwia określenie, czy dane środowisko uruchomieniowe usługi należy przekonwertować typu, która jest przechowywana w ładunku z typem właściwości rzeczywiste, który jest określony w żądaniu.|  
|<xref:System.Data.Services.DataServiceBehavior.InvokeInterceptorsOnLinkDelete%2A>|Można określić, czy zarejestrowano interceptory zmiany są wywoływane na powiązanych jednostek po usunięciu łącze relację między dwiema jednostkami.|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxBatchCount%2A>|Umożliwia ograniczenie liczby zestawów zmian i operacje, które są dozwolone w pojedynczej partii zapytań. Aby uzyskać więcej informacji, zobacz [OData: partii](http://go.microsoft.com/fwlink/?LinkId=185602) i [przetwarzanie wsadowe operacji](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxChangesetCount%2A>|Umożliwia ograniczenie liczby zmian, które można uwzględnić w zestawie jednej zmiany. Aby uzyskać więcej informacji, zobacz [porady: Włączanie stronicowania z usługi wyniki z danymi](../../../../docs/framework/data/wcf/how-to-enable-paging-of-data-service-results-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandCount%2A>|Umożliwia ograniczenie rozmiaru odpowiedzi przez ograniczenie liczby powiązanych jednostek, które mogą być włączone w ramach pojedynczego żądania przy użyciu `$expand` — operator zapytań. Aby uzyskać więcej informacji, zobacz zobacz [OData: identyfikator URI konwencje](http://go.microsoft.com/fwlink/?LinkId=185564) i [ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandDepth%2A>|Umożliwia ograniczenie rozmiaru odpowiedzi przez ograniczenie liczby wykresu powiązanych jednostek, które mogą być włączone w ramach pojedynczego żądania przy użyciu `$expand` — operator zapytań. Aby uzyskać więcej informacji, zobacz zobacz [OData: identyfikator URI konwencje](http://go.microsoft.com/fwlink/?LinkId=185564) i [ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxObjectCountOnInsert%2A>|Umożliwia ograniczenie liczby jednostek, które ma zostać wstawiony, które mogą być zawarte w jednym żądaniu POST.|  
|<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>|Definiuje wersji protokołu Atom, które jest używane przez usługę danych. Jeśli wartość <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> jest ustawiona na wartość mniejszą niż maksymalna wartość <xref:System.Data.Services.Common.DataServiceProtocolVersion>, najnowsze funkcje [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] nie jest dostępny dla klientów uzyskujących dostęp do usługi data. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxResultsPerCollection%2A>|Można ograniczyć rozmiar odpowiedzi przez ograniczenie liczby jednostek w każdym zestaw jednostek, który jest zwracany jako źródła danych.|  
|<xref:System.Data.Services.DataServiceConfiguration.RegisterKnownType%2A>|Dodaje typ danych do listy typów, które są rozpoznawane przez usługę danych.|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetAccessRule%2A>|Ustawia prawa dostępu do jednostki zestawu zasobów, które są dostępne w usłudze danych. Znak gwiazdki (`*`) można podać wartość dla parametru name ustawioną dostępu dla wszystkich pozostałych zestawów jednostek na tym samym poziomie. Zaleca się nadanie zestawy jednostek, aby zapewnić co najmniej uprawnień dostępu do danych usługi zasobów, które są wymagane przez aplikacje klienckie. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usługi danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md). Przykłady prawa dostępu minimalne wymagane dla danego identyfikatora URI i HTTP działania, zobacz tabelę w [minimalne wymagania dotyczące dostępu do zasobów](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements) sekcji.|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetPageSize%2A>|Ustawia maksymalny rozmiar strony obiektu ustawić zasobu. Aby uzyskać więcej informacji, zobacz [porady: Włączanie stronicowania z usługi wyniki z danymi](../../../../docs/framework/data/wcf/how-to-enable-paging-of-data-service-results-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.SetServiceOperationAccessRule%2A>|Ustawia prawa dostępu do operacji usługi, które są zdefiniowane w usłudze danych. Aby uzyskać więcej informacji, zobacz [operacji usługi](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md). Znak gwiazdki (`*`) można podać wartość dla parametru name ustawioną na tym samym poziomie dostępu dla wszystkich operacji usługi. Zalecane ustawienie dostępu do operacji usługi, aby zapewnić co najmniej uprawnień dostępu do danych usługi zasobów, które są wymagane przez aplikacje klienckie. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usługi danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A>|Ta właściwość konfiguracji umożliwia łatwiejsze Rozwiązywanie problemów z usługi danych, przywracając więcej informacji w komunikacie o błędzie odpowiedzi. Ta opcja nie jest przeznaczona do użycia w środowisku produkcyjnym. Aby uzyskać więcej informacji, zobacz [rozwijających się i wdrażanie usług danych WCF](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md).|  
  
<a name="accessRequirements"></a>   
## <a name="minimum-resource-access-requirements"></a>Wymagania dotyczące dostępu do zasobów minimalna  
 Następujące szczegóły tabeli minimalny zestaw jednostek, prawa, które musi otrzymać można wykonać określonej operacji. Przykłady ścieżki są oparte na usługę danych Northwind, utworzony po ukończeniu [szybkiego startu](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Ponieważ zarówno <xref:System.Data.Services.EntitySetRights> wyliczenie i <xref:System.Data.Services.ServiceOperationRights> wyliczenia są zdefiniowane przy użyciu <xref:System.FlagsAttribute>, operator logiczny OR można użyć do określenia wielu uprawnień dla operacji lub zestaw pojedynczej jednostki. Aby uzyskać więcej informacji, zobacz [porady: Włączanie dostępu do usługi Data](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).  
  
|Akcja/ścieżki|`GET`|`DELETE`|`MERGE`|`POST`|`PUT`|  
|------------------|-----------|--------------|-------------|------------|-----------|  
|`/Customers`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|Nieobsługiwane|Nieobsługiwane|<xref:System.Data.Services.EntitySetRights.WriteAppend>|Nieobsługiwane|  
|`/Customers('ALFKI')`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> I <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.ReadSingle> I <xref:System.Data.Services.EntitySetRights.WriteMerge>|n/d|<xref:System.Data.Services.EntitySetRights.ReadSingle> I <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Nieobsługiwane|Nieobsługiwane|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteMerge> lub <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> - i -<br /><br /> `Orders` `:` I <xref:System.Data.Services.EntitySetRights.WriteAppend>|Nieobsługiwane|  
|`/Customers('ALFKI')/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteDelete>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteMerge>|Nieobsługiwane|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Orders(10643)/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteDelete><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteMerge>;<br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.WriteAppend> i <xref:System.Data.Services.EntitySetRights.ReadSingle>|Nieobsługiwane|  
|`/Customers('ALFKI')/$links/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Nieobsługiwane|Nieobsługiwane|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteMerge> lub <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|Nieobsługiwane|  
|`/Customers('ALFKI')/$links/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteMerge> lub <xref:System.Data.Services.EntitySetRights.WriteReplace><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|  
|`/Orders(10643)/$links/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle>|`Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteMerge> lub <xref:System.Data.Services.EntitySetRights.WriteReplace>|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteMerge>|Nieobsługiwane|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle>;<br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadSingle> i <xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers/$count`|<xref:System.Data.Services.EntitySetRights.ReadMultiple>|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|  
|`/Customers('ALFKI')/ContactName`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|Nieobsługiwane|<xref:System.Data.Services.EntitySetRights.WriteMerge>|Nieobsługiwane|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/Address/StreetAddress/$value` <sup>1</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.WriteDelete>|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|  
|`/Customers('ALFKI')/ContactName/$value`|<xref:System.Data.Services.EntitySetRights.ReadSingle>|<xref:System.Data.Services.EntitySetRights.ReadSingle> I <xref:System.Data.Services.EntitySetRights.WriteDelete>|<xref:System.Data.Services.EntitySetRights.WriteMerge>|Nieobsługiwane|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers('ALFKI')/$value` <sup>2</sup>|<xref:System.Data.Services.EntitySetRights.ReadSingle>|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|<xref:System.Data.Services.EntitySetRights.WriteReplace>|  
|`/Customers?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Nieobsługiwane|Nieobsługiwane|`Customers`: <xref:System.Data.Services.EntitySetRights.WriteAppend>|Nieobsługiwane|  
|`/Customers('ALFKI')?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights.ReadSingle><br /><br /> - i -<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights.ReadMultiple>|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|Nieobsługiwane|  
  
 <sup>1</sup> w tym przykładzie `Address` reprezentuje właściwość typu złożonego `Customers` jednostki, która ma właściwości o nazwie `StreetAddress`. Model używany przez usługi danych Northwind nie definiuje jawnie tego typu złożonego. Jeśli model danych jest definiowana za pomocą [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] dostawcy, można użyć [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] narzędzi, aby zdefiniować typu złożonego. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i modyfikowanie typów złożonych](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).  
  
 <sup>2</sup> ten identyfikator URI jest obsługiwana, gdy właściwość, która zwraca dużego obiektu binarnego (BLOB) jest zdefiniowany jako zasób nośnika, który należy do jednostki, która jest wpisem łącza nośnika, w tym przypadku jest `Customers`. Aby uzyskać więcej informacji, zobacz [przesyłania strumieniowego dostawcy](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
<a name="versioning"></a>   
## <a name="versioning-requirements"></a>Wymagania dotyczące kontroli wersji  
 Następujące zachowania konfiguracji usług danych wymaga wersji 2 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu lub nowszy:  
  
-   Obsługa liczby żądań.  
  
-   Obsługa opcji zapytania $select dla projekcji.  
  
 Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Hosting usługi danych](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
