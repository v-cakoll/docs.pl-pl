---
title: Dostawcy Data Services (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: 7623c2b743d6a61362c8cf0e1228b4663c9e7d48
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780388"
---
# <a name="data-services-providers-wcf-data-services"></a>Dostawcy Data Services (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje wiele modeli dostawcy na potrzeby ujawniania danych [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] jako źródła strumieniowego. Ten temat zawiera informacje umożliwiające wybranie najlepszego [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dostawcy dla źródła danych.  
  
## <a name="data-source-providers"></a>Dostawcy źródła danych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Program obsługuje następujących dostawców do definiowania modelu danych usługi danych.  
  
|Dostawca|Opis|  
|--------------|-----------------|  
|Dostawca Entity Framework|Ten dostawca używa Entity Framework ADO.NET, aby umożliwić korzystanie z danych relacyjnych z usługą danych przez zdefiniowanie modelu danych, który mapuje na dane relacyjne. Źródło danych może być SQL Server lub dowolnego innego źródła danych z obsługą dostawcy innej firmy dla Entity Framework. Dostawcy Entity Framework należy używać w przypadku relacyjnego źródła danych, takiego jak baza danych SQL Server. Aby uzyskać więcej informacji, zobacz [Entity Framework Provider](entity-framework-provider-wcf-data-services.md).|  
|Dostawca odbicia|Ten dostawca używa odbicia, aby umożliwić zdefiniowanie modelu danych opartego na istniejących klasach danych, które mogą być ujawnione <xref:System.Linq.IQueryable%601> jako wystąpienia interfejsu. Aktualizacje są włączane przez implementację <xref:System.Data.Services.IUpdatable> interfejsu. Tego dostawcy należy używać, gdy istnieją klasy danych statycznych, które są zdefiniowane w czasie wykonywania, takie jak te wygenerowane przez LINQ to SQL lub zdefiniowane przez określony zestaw danych. Aby uzyskać więcej informacji, zobacz temat [dostawca odbicia](reflection-provider-wcf-data-services.md).|  
|Niestandardowi dostawcy usługi danych|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zawiera zestaw dostawców, które umożliwiają dynamiczne definiowanie modelu danych na podstawie późnych typów danych. Te interfejsy należy zaimplementować, gdy udostępniane dane nie są znane, gdy aplikacja jest zaprojektowana lub gdy Entity Framework lub dostawcy odbicia nie są wystarczające. Aby uzyskać więcej informacji, zobacz [niestandardowe dostawcy usług danych](custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Inni dostawcy usług danych  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]ma następującego dodatkowego dostawcę usługi danych, który zwiększa wydajność źródła danych zdefiniowanego przy użyciu jednego z pozostałych dostawców.  
  
|Dostawca|Opis|  
|--------------|-----------------|  
|Dostawca przesyłania strumieniowego|Ten dostawca pozwala udostępnić binarne typy danych obiektów binarnych za pomocą polecenia [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Dostawca przesyłania strumieniowego jest tworzony przez implementację <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interfejsu. Ten dostawca można zaimplementować razem z dowolnym dostawcą źródła danych. Aby uzyskać więcej informacji, zobacz [dostawca przesyłania strumieniowego](streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md)
- [Hosting usługi danych](hosting-the-data-service-wcf-data-services.md)
