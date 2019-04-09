---
title: Niestandardowi dostawcy usługi danych (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: f198de20a3fa788fb8d5f2dc4ebf799989814756
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184005"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Niestandardowi dostawcy usługi danych (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obejmuje zestaw dostawcy, która pozwala na zdefiniowanie modelu danych na podstawie typów danych z późnym wiązaniem.  
  
|Dostawca|Opis|  
|--------------|-----------------|  
|Dostawca metadanych|Jest to dostawca usługi danych niestandardowych core umożliwia zdefiniowanie niestandardowego modelu danych w czasie wykonywania przez zaimplementowanie <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interfejsu.|  
|Dostawcy zapytań|Ten dostawca umożliwia wykonywanie zapytań względem modelu danych niestandardowych, która jest zdefiniowana za pomocą <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interfejsu. Dostawcy zapytań jest tworzony przez zaimplementowanie <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interfejsu.|  
|Dostawca aktualizacji|Ten dostawca pozwala na aktualizowanie typów, które są dostępne w dostawcy usług danych niestandardowych i zarządzać współbieżności. Dostawca aktualizacji jest tworzony przez zaimplementowanie <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> interfejsu|  
|Dostawca stronicowania|Ten dostawca jest używany z dostawcą usług danych niestandardowych można włączyć obsługę stronicowania opartych na serwerze. Stronicowania dostawcy usługi danych niestandardowych jest tworzony przez zaimplementowanie <xref:System.Data.Services.Providers.IDataServicePagingProvider> interfejsu.|  
|Dostawca przesyłania strumieniowego|Ten dostawca umożliwia udostępnianie duży obiekt binarny typy danych jako strumień. Dostawca przesyłania strumieniowego jest tworzony przez zaimplementowanie <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interfejsu. Dostawca przesyłania strumieniowego można również za pomocą platformy Entity Framework i odbicie dostawcy źródła danych. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
 Aby uzyskać więcej informacji, zobacz artykuł [dostawcy usługi danych niestandardowych](https://go.microsoft.com/fwlink/?LinkID=186850) i [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Toolkit dostawcy w [OData SDK](https://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [Dostawca programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
- [Dostawca odbicia](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
