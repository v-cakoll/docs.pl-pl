---
title: Dostawcy Data Services (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: eb7d92b1605c6ced8319e0372c8471cd4e388cb8
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569241"
---
# <a name="data-services-providers-wcf-data-services"></a>Dostawcy Data Services (Usługi danych programu WCF)
Usługi danych programu WCF obsługuje wiele modeli dostawcy na potrzeby ujawniania danych jako strumieniowego protokołu Open Data Protocol (OData). Ten temat zawiera informacje umożliwiające wybranie najlepszego dostawcy Usługi danych programu WCF dla źródła danych.  
  
## <a name="data-source-providers"></a>Dostawcy źródła danych  
 Usługi danych programu WCF obsługuje następujących dostawców do definiowania modelu danych usługi danych.  
  
|Provider|Opis|  
|--------------|-----------------|  
|Dostawca Entity Framework|Ten dostawca używa Entity Framework ADO.NET, aby umożliwić korzystanie z danych relacyjnych z usługą danych przez zdefiniowanie modelu danych, który mapuje na dane relacyjne. Źródło danych może być SQL Server lub dowolnego innego źródła danych z obsługą dostawcy innej firmy dla Entity Framework. Dostawcy Entity Framework należy używać w przypadku relacyjnego źródła danych, takiego jak baza danych SQL Server. Aby uzyskać więcej informacji, zobacz [Entity Framework Provider](entity-framework-provider-wcf-data-services.md).|  
|Dostawca odbicia|Ten dostawca używa odbicia, aby umożliwić zdefiniowanie modelu danych opartego na istniejących klasach danych, które mogą być ujawnione jako wystąpienia interfejsu <xref:System.Linq.IQueryable%601>. Aktualizacje są włączane przez implementację interfejsu <xref:System.Data.Services.IUpdatable>. Tego dostawcy należy używać, gdy istnieją klasy danych statycznych, które są zdefiniowane w czasie wykonywania, takie jak te wygenerowane przez LINQ to SQL lub zdefiniowane przez określony zestaw danych. Aby uzyskać więcej informacji, zobacz temat [dostawca odbicia](reflection-provider-wcf-data-services.md).|  
|Niestandardowi dostawcy usługi danych|Usługi danych programu WCF obejmuje zestaw dostawców, które umożliwiają dynamiczne definiowanie modelu danych na podstawie późnych typów danych. Te interfejsy należy zaimplementować, gdy udostępniane dane nie są znane, gdy aplikacja jest zaprojektowana lub gdy Entity Framework lub dostawcy odbicia nie są wystarczające. Aby uzyskać więcej informacji, zobacz [niestandardowe dostawcy usług danych](custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Inni dostawcy usług danych  
 Usługi danych programu WCF ma następującego dodatkowego dostawcę usługi danych, który zwiększa wydajność źródła danych zdefiniowanego przy użyciu jednego z pozostałych dostawców.  
  
|Provider|Opis|  
|--------------|-----------------|  
|Dostawca przesyłania strumieniowego|Ten dostawca pozwala udostępnić binarne typy danych obiektów binarnych za pomocą Usługi danych programu WCF. Dostawca przesyłania strumieniowego jest tworzony przez implementację interfejsu <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Ten dostawca można zaimplementować razem z dowolnym dostawcą źródła danych. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md)
- [Hosting usługi danych](hosting-the-data-service-wcf-data-services.md)
