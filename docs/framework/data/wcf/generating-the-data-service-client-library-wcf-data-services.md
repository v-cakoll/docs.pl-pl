---
title: "Generowanie biblioteki klienta usługi danych (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6adbaafe170cf3f5398677d5df3b3d2ff0a95abe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Generowanie biblioteki klienta usługi danych (usługi danych WCF)
Usługi danych, który implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] może zwrócić dokument metadanych usługi, który opisuje modelu danych udostępnianych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [OData: Dokument metadanych usługi](http://go.microsoft.com/fwlink/?LinkId=186070). Można użyć **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio można dodać odwołania do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi. Jeśli używasz tego narzędzia można dodać odwołania do metadanych zwróconych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w projekcie klienta, wykonuje następujące czynności:  
  
-   Żądania dokument metadanych usługi z usługą danych i interpretowania metadane zwrócony.  
  
    > [!NOTE]
    >  Zwrócone metadane są przechowywane w projektu klienta jako plik edmx. Nie można otworzyć tego pliku edmx przy użyciu narzędzia Projektant modelu danych jednostki, ponieważ nie ma taki sam format pliku edmx, używany przez program Entity Framework. Ten plik metadanych można wyświetlić za pomocą edytora XML lub edytorze tekstu. Aby uzyskać więcej informacji, zobacz [ \[MC EDMX\]: modelu Entity Data Model danych usługi tworzenia pakietów formatu](http://go.microsoft.com/fwlink/?LinkID=178833) specyfikacji  
  
-   Generuje reprezentację usługi jako klasy kontenera jednostka, która dziedziczy <xref:System.Data.Services.Client.DataServiceContext>. Ta klasa kontenera jednostek wygenerowanego podobny do kontenera jednostek, który generuje narzędzi modelu danych jednostki. Aby uzyskać więcej informacji, zobacz [obiektu usługi — omówienie (Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
-   Generuje klasy danych do typów modelu danych, które wykryje w metadanych usługi.  
  
-   Dodanie odwołania do `System.Data.Services.Client` zestawu do projektu.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dodawanie odwołania do danych usługi](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Klasy usługi danych klienta może być również generowany przy użyciu [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzia w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [porady: ręcznie wygenerować klienta usługi klas danych](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mapowanie typu danych klienta  
 Jeśli używasz **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio lub `DataSvcUtil.exe` narzędzie do generowania klasy danych klienta, które są oparte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, typy danych .NET Framework są mapowane na typy pierwotne z model bazy danych w następujący sposób:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [OData: typy pierwotne danych](http://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
