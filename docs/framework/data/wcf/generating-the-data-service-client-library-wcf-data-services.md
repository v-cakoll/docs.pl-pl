---
title: Generowanie biblioteki klienta usługi danych (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: d53f2d209d6fb0a6f3cadb96245338060ece87db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780285"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Generowanie biblioteki klienta usługi danych (Usługi danych programu WCF)
Usługa danych implementująca [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] może zwrócić dokument metadanych usługi, który opisuje model danych uwidoczniony [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] przez kanał informacyjny. Aby uzyskać więcej informacji, [zobacz OData: Dokument](https://go.microsoft.com/fwlink/?LinkId=186070)metadanych usługi. Możesz użyć okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio, aby dodać odwołanie do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]usługi opartej na usłudze. W przypadku użycia tego narzędzia do dodania odwołania do metadanych zwracanych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródło danych w projekcie klienta wykonywane są następujące akcje:  
  
- Żąda dokumentu metadanych usługi z usługi danych i interpretuje zwrócone metadane.  
  
    > [!NOTE]
    > Zwrócone metadane są przechowywane w projekcie klienta jako plik. edmx. Nie można otworzyć tego pliku edmx przy użyciu projektanta Entity Data Model, ponieważ nie ma on tego samego formatu pliku. edmx, który jest używany przez Entity Framework. Ten plik metadanych można wyświetlić za pomocą edytora XML lub dowolnego edytora tekstu. Aby uzyskać więcej informacji, zobacz [ \[MC-edmx\]: Entity Data Model specyfikacji formatu](https://go.microsoft.com/fwlink/?LinkID=178833) pakowania Data Services  
  
- Generuje reprezentację usługi jako klasę kontenera jednostek, która dziedziczy z <xref:System.Data.Services.Client.DataServiceContext>. Ta klasa kontenerów jednostek jest podobna do kontenera jednostek wygenerowanego przez narzędzia Entity Data Model. Aby uzyskać więcej informacji, zobacz temat [usługi obiektów — omówienie (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
- Generuje klasy danych dla typów modeli danych odnajdywanych w metadanych usługi.  
  
- Dodaje odwołanie do `System.Data.Services.Client` zestawu do projektu.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dodaj odwołanie](how-to-add-a-data-service-reference-wcf-data-services.md)do usługi danych.  
  
 Klasy usługi danych klienta mogą być również generowane za pomocą narzędzia [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [jak: Generuj ręcznie klasy](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)usługi danych klienta.  
  
## <a name="client-data-type-mapping"></a>Mapowanie typu danych klienta  
 W przypadku korzystania z okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio `DataSvcUtil.exe` lub narzędzia do generowania klas danych klienta, które [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] są oparte na źródle danych, typy danych .NET Framework są mapowane na typy pierwotne z modelu dane w następujący sposób:  
  
|Typ modelu danych|Typ danych .NET Framework|  
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
  
 Aby uzyskać więcej informacji, [zobacz OData: Typy](https://go.microsoft.com/fwlink/?LinkId=186072)danych pierwotnych.  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Szybki start](quickstart-wcf-data-services.md)
