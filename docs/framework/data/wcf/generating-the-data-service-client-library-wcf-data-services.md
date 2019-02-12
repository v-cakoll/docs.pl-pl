---
title: Generowanie biblioteki klienta usługi danych (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 41f4e7cd633cf6175b6b167937cf53ceb4d9ec59
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092101"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Generowanie biblioteki klienta usługi danych (WCF Data Services)
Usługi danych, który implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] może zwrócić dokument metadanych usług, który opisuje model danych udostępnianych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [OData: Dokument metadanych usługi](https://go.microsoft.com/fwlink/?LinkId=186070). Możesz użyć **Dodaj odwołanie do usługi** w programie Visual Studio można dodać odwołania do okna dialogowego [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi. Kiedy używać tego narzędzia można dodać odwołania do metadanych zwróconych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w projekcie klienta, wykonuje następujące czynności:  
  
-   Żądanie dokumentu metadanych usługi z usługi danych, a następnie interpretuje zwróconych metadanych.  
  
    > [!NOTE]
    >  Zwróconych metadanych znajduje się w projekcie klienta jako pliku edmx. Nie można otworzyć tego pliku edmx przy użyciu projektanta modelu Entity Data Model, ponieważ nie ma taki sam format pliku edmx używane przez program Entity Framework. Ten plik metadanych można wyświetlić za pomocą edytora XML lub dowolnego edytora tekstów. Aby uzyskać więcej informacji, zobacz [ \[MC EDMX\]: Model Entity Data Model do formatu pakietu usług danych](https://go.microsoft.com/fwlink/?LinkID=178833) specyfikacji  
  
-   Generuje reprezentację usługi jako klasa kontenera jednostki, która dziedziczy <xref:System.Data.Services.Client.DataServiceContext>. Ta klasa kontenera jednostki wygenerowanego przypomina kontener jednostek, które generują narzędzia modelu Entity Data Model. Aby uzyskać więcej informacji, zobacz [obiektu usługi — omówienie (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
-   Generuje klasy danych dla typów modelu danych, które wykryje w metadanych usługi.  
  
-   Dodanie odwołania do `System.Data.Services.Client` zestawu do projektu.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dodaj odwołanie do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Klas usługi danych klienta mogą być też generowane przy użyciu [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzia w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [jak: Ręczne Generowanie klas usługi danych klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
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
  
 Aby uzyskać więcej informacji, zobacz [OData: Pierwotne typy danych](https://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Zobacz także
- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
