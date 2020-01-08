---
title: Niestandardowi dostawcy usług danych (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: a5041b04151a288f9c6c1a567dacec8da8c80a42
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346134"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Niestandardowi dostawcy usług danych (Usługi danych programu WCF)
Usługi danych programu WCF obejmuje zestaw dostawców, który umożliwia zdefiniowanie modelu danych na podstawie późnych typów danych.  
  
|Provider|Opis|  
|--------------|-----------------|  
|Dostawca metadanych|Jest to podstawowy dostawca usługi danych niestandardowych, który umożliwia zdefiniowanie niestandardowego modelu danych w środowisku uruchomieniowym przez implementację interfejsu <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>.|  
|Dostawca zapytań|Ten dostawca umożliwia wykonywanie zapytań dotyczących niestandardowego modelu danych, który jest definiowany przy użyciu interfejsu <xref:System.Data.Services.Providers.IDataServiceMetadataProvider>. Dostawca zapytań jest tworzony przez implementację interfejsu <xref:System.Data.Services.Providers.IDataServiceQueryProvider>.|  
|Aktualizuj dostawcę|Ten dostawca umożliwia Dokonywanie aktualizacji typów, które są widoczne w niestandardowym dostawcy usług danych i Zarządzanie współbieżnością. Dostawca aktualizacji jest tworzony przez implementację interfejsu <xref:System.Data.Services.Providers.IDataServiceUpdateProvider>|  
|Dostawca stronicowania|Ten dostawca jest używany z niestandardowym dostawcą usług danych w celu włączenia obsługi stronicowania opartego na serwerze. Dostawca stronicowania dla niestandardowej usługi danych jest tworzony przez implementację interfejsu <xref:System.Data.Services.Providers.IDataServicePagingProvider>.|  
|Dostawca przesyłania strumieniowego|Ten dostawca pozwala udostępnić binarne typy danych typu binary jako strumień. Dostawca przesyłania strumieniowego jest tworzony przez implementację interfejsu <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Dostawca przesyłania strumieniowego może być również używany z dostawcami źródeł danych Entity Framework i odbicia. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Zobacz także

- [Dostawcy usług danych](data-services-providers-wcf-data-services.md)
- [Dostawca programu Entity Framework](entity-framework-provider-wcf-data-services.md)
- [Dostawca odbicia](reflection-provider-wcf-data-services.md)
