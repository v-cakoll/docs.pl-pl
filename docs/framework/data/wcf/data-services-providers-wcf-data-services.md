---
title: "Usługi danych dostawców (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6f25f1f9137206c1adb3ab3f89b7c6a783aeccf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="data-services-providers-wcf-data-services"></a>Usługi danych dostawców (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje wiele modeli dostawcy udostępnianie danych jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych. Ten temat zawiera informacje umożliwiające wybranie najlepszych [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dostawcy dla źródła danych.  
  
## <a name="data-source-providers"></a>Dostawcy źródła danych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje następujących dostawców do definiowania usługi danych modelu danych.  
  
|Dostawcy|Opis|  
|--------------|-----------------|  
|Dostawcy programu Entity Framework|Ten dostawca używa programu ADO.NET Entity Framework, aby umożliwić użycia danych relacyjnych z usługą danych poprzez definiowanie modelu danych, który jest mapowany na relacyjnej bazie danych. Źródło danych może być programu SQL Server lub innego źródła danych z obsługą innego dostawcy programu Entity Framework. Jeśli masz relacyjnym źródłem danych, takich jak bazy danych programu SQL Server, należy używać dostawcy programu Entity Framework. Aby uzyskać więcej informacji, zobacz [dostawcy programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).|  
|Dostawca odbicia|Ten dostawca używa odbicia do definiowania modeli danych oparte na istniejących klas danych, które są dostępne jako wystąpień obiektu <xref:System.Linq.IQueryable%601> interfejsu. Dzięki wdrożeniu są włączone aktualizacje <xref:System.Data.Services.IUpdatable> interfejsu. Powinni używać tego dostawcy, gdy masz klas statycznych danych, które są zdefiniowane w czasie wykonywania, takich jak te generowane przez składnik LINQ to SQL lub zdefiniowany przez typizowanego obiektu DataSet. Aby uzyskać więcej informacji, zobacz [dostawcy odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).|  
|Niestandardowych dostawców usług danych|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obejmuje zestaw dostawców, które umożliwiają definiowanie dynamicznie na podstawie typów danych z późnym wiązaniem modelu danych. Te interfejsy powinny implementować, gdy podczas projektowania aplikacji nie jest znany danych przed przypadkowym lub dostawcy programu Entity Framework lub odbicia nie są wystarczające. Aby uzyskać więcej informacji, zobacz [dostawców usług danych niestandardowych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Innych dostawców usług danych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]ma następującego dostawcy usługi dodatkowe dane, które poprawia wydajność źródła danych zdefiniowany przy użyciu jednego z innych dostawców.  
  
|Dostawcy|Opis|  
|--------------|-----------------|  
|Dostawca przesyłania strumieniowego|Ten dostawca umożliwia udostępnianie typów danych dużych obiektów binarnych za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Zaimplementowanie tworzony jest dostawca przesyłania strumieniowego <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interfejsu. Ten dostawca można stosować razem z każdego dostawcy źródła danych. Aby uzyskać więcej informacji, zobacz [przesyłania strumieniowego dostawcy](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)  
 [Hosting usługi danych](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
