---
title: Data Services — dostawcy (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: 7a870eb0c85fa6ed208341a3ac10dce8bb0724bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164427"
---
# <a name="data-services-providers-wcf-data-services"></a>Data Services — dostawcy (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje wiele modeli dostawcy do udostępniania danych jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych. Ten temat zawiera informacje umożliwiające wybranie najlepszej [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dostawcy dla źródła danych.  
  
## <a name="data-source-providers"></a>Dostawcy źródła danych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje następujących dostawców na potrzeby definiowania modelu danych usługi danych.  
  
|Dostawca|Opis|  
|--------------|-----------------|  
|Dostawca programu Entity Framework|Ten dostawca używa ADO.NET Entity Framework, aby umożliwić do użycia w relacyjnej bazie danych za pomocą usługi danych przez zdefiniowanie modelu danych, który jest mapowany do opartego na danych relacyjnych. Źródło danych może być program SQL Server lub dowolnego innego źródła danych z obsługą innych dostawców dla programu Entity Framework. W przypadku źródła danych relacyjnych, takich jak bazy danych programu SQL Server, należy używać dostawcy środowiska Entity Framework. Aby uzyskać więcej informacji, zobacz [dostawcy Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).|  
|Dostawcy odbicia|Ten dostawca używa odbicia w celu umożliwiają zdefiniowanie modelu danych, w oparciu o istniejące klasy danych, które są dostępne jako wystąpień obiektu <xref:System.Linq.IQueryable%601> interfejsu. Aktualizacje są włączone przez zaimplementowanie <xref:System.Data.Services.IUpdatable> interfejsu. W przypadku danych statycznych klas, które są zdefiniowane w czasie wykonywania, takich jak te generowane w składniku LINQ to SQL lub zdefiniowany przez typizowany zestaw danych, należy używać tego dostawcy. Aby uzyskać więcej informacji, zobacz [dostawcy odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).|  
|Niestandardowi dostawcy usługi danych|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zawiera zestaw dostawców, którzy umożliwiają zdefiniowanie dynamicznie na podstawie typów danych z późnym wiązaniem modelu danych. Te interfejsy powinny implementować, gdy dane są udostępniane nie jest znany, podczas projektowania aplikacji lub dostawcy programu Entity Framework lub odbicia nie są wystarczające. Aby uzyskać więcej informacji, zobacz [dostawcy usługi danych niestandardowych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Innych dostawców usług danych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ma następującego dostawcy usługi dodatkowe dane, które poprawia wydajność źródła danych, zdefiniowane przy użyciu jednego z innych dostawców.  
  
|Dostawca|Opis|  
|--------------|-----------------|  
|Dostawca przesyłania strumieniowego|Ten dostawca umożliwia udostępnianie duży obiekt binarny typy danych przy użyciu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Dostawca przesyłania strumieniowego jest tworzony przez zaimplementowanie <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interfejsu. Ten dostawca może być implementowany wraz z dowolnego dostawcy źródła danych. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
- [Hosting usługi danych](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
