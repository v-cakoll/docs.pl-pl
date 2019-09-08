---
title: Niestandardowi dostawcy usług danych (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: 4a6079db5e969154c4a9bb6451dd7c698c6d2088
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780370"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Niestandardowi dostawcy usług danych (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zawiera zestaw dostawców, które umożliwiają zdefiniowanie modelu danych na podstawie późnych typów danych.  
  
|Dostawca|Opis|  
|--------------|-----------------|  
|Dostawca metadanych|Jest to podstawowy dostawca usługi danych niestandardowych, który umożliwia zdefiniowanie niestandardowego modelu danych w środowisku uruchomieniowym przez implementację <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interfejsu.|  
|Dostawca zapytań|Ten dostawca umożliwia wykonywanie zapytań względem niestandardowego modelu danych, który jest definiowany przy użyciu <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interfejsu. Dostawca zapytań jest tworzony przez implementację <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interfejsu.|  
|Aktualizuj dostawcę|Ten dostawca umożliwia Dokonywanie aktualizacji typów, które są widoczne w niestandardowym dostawcy usług danych i Zarządzanie współbieżnością. Dostawca aktualizacji jest tworzony przez implementację <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> interfejsu|  
|Dostawca stronicowania|Ten dostawca jest używany z niestandardowym dostawcą usług danych w celu włączenia obsługi stronicowania opartego na serwerze. Dostawca stronicowania dla niestandardowej usługi danych jest tworzony przez implementację <xref:System.Data.Services.Providers.IDataServicePagingProvider> interfejsu.|  
|Dostawca przesyłania strumieniowego|Ten dostawca pozwala udostępnić binarne typy danych typu binary jako strumień. Dostawca przesyłania strumieniowego jest tworzony przez implementację <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interfejsu. Dostawca przesyłania strumieniowego może być również używany z dostawcami źródeł danych Entity Framework i odbicia. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](streaming-provider-wcf-data-services.md).|  
  
 Aby uzyskać więcej informacji, zapoznaj się z artykułami [Custom Data Service Providers](https://go.microsoft.com/fwlink/?LinkID=186850) and [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] The Provider Toolkit w [zestawie SDK OData](https://go.microsoft.com/fwlink/?LinkId=186069).  
  
## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Dostawca programu Entity Framework](entity-framework-provider-wcf-data-services.md)
- [Dostawca odbicia](reflection-provider-wcf-data-services.md)
