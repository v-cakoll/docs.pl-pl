---
title: Generowanie biblioteki klienta usługi danych (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 170f9714f3cfbf2350423f28316d665d427fd56e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862254"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Generowanie biblioteki klienta usługi danych (WCF Data Services)
Usługi danych, który implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] może zwrócić dokument metadanych usług, który opisuje model danych udostępnianych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [OData: Dokument metadanych usługi](https://go.microsoft.com/fwlink/?LinkId=186070). Możesz użyć **Dodaj odwołanie do usługi** w programie Visual Studio można dodać odwołania do okna dialogowego [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi. Kiedy używać tego narzędzia można dodać odwołania do metadanych zwróconych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w projekcie klienta, wykonuje następujące czynności:  
  
-   Żądanie dokumentu metadanych usługi z usługi danych, a następnie interpretuje zwróconych metadanych.  
  
    > [!NOTE]
    >  Zwróconych metadanych znajduje się w projekcie klienta jako pliku edmx. Nie można otworzyć tego pliku edmx przy użyciu projektanta modelu Entity Data Model, ponieważ nie ma taki sam format pliku edmx używane przez program Entity Framework. Ten plik metadanych można wyświetlić za pomocą edytora XML lub dowolnego edytora tekstów. Aby uzyskać więcej informacji, zobacz [ \[MC EDMX\]: model Entity Data Model do formatu pakietu usług danych](https://go.microsoft.com/fwlink/?LinkID=178833) specyfikacji  
  
-   Generuje reprezentację usługi jako klasa kontenera jednostki, która dziedziczy <xref:System.Data.Services.Client.DataServiceContext>. Ta klasa kontenera jednostki wygenerowanego przypomina kontener jednostek, które generują narzędzia modelu Entity Data Model. Aby uzyskać więcej informacji, zobacz [obiektu usługi — omówienie (Entity Framework)](https://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
-   Generuje klasy danych dla typów modelu danych, które wykryje w metadanych usługi.  
  
-   Dodanie odwołania do `System.Data.Services.Client` zestawu do projektu.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dodawanie odwołania usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Klas usługi danych klienta mogą być też generowane przy użyciu [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzia w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [porady: ręczne Generowanie klas usługi danych klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mapowanie typu danych klienta  
 Kiedy używasz **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio lub `DataSvcUtil.exe` narzędzie do generowania klasy danych klienta, które są oparte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanału informacyjnego, typów danych programu .NET Framework są mapowane na typy pierwotne z modelu danych w następujący sposób:  
  
|Typ modelu danych|Typ danych .NET framework|  
|---------------------|------------------------------|  
|`Edm.Binary`|<xref:System.Byte>`[]`|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 Aby uzyskać więcej informacji, zobacz [OData: typów danych pierwotnych](https://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
