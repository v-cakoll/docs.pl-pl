---
title: Generowanie biblioteki klienta usługi danych (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: f73ea93fe76f31c81935dbfb29183c247e41d8cd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975285"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Generowanie biblioteki klienta usługi danych (Usługi danych programu WCF)
Usługa danych, która implementuje protokół Open Data Protocol (OData), może zwrócić dokument metadanych usługi, który opisuje model danych uwidoczniony przez kanał informacyjny OData. Aby uzyskać więcej informacji, zobacz [dokument metadanych usługi OData: Service](https://go.microsoft.com/fwlink/?LinkId=186070). Możesz użyć okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio, aby dodać odwołanie do usługi opartej na protokole OData. W przypadku użycia tego narzędzia do dodania odwołania do metadanych zwracanych przez źródło danych OData w projekcie klienta wykonywane są następujące akcje:  
  
- Żąda dokumentu metadanych usługi z usługi danych i interpretuje zwrócone metadane.  
  
    > [!NOTE]
    > Zwrócone metadane są przechowywane w projekcie klienta jako plik. edmx. Nie można otworzyć tego pliku edmx przy użyciu projektanta Entity Data Model, ponieważ nie ma on tego samego formatu pliku. edmx, który jest używany przez Entity Framework. Ten plik metadanych można wyświetlić za pomocą edytora XML lub dowolnego edytora tekstu. Aby uzyskać więcej informacji, zobacz [\[MC-EDMX\]: Entity Data Model dla specyfikacji formatu pakowania Data Services](https://go.microsoft.com/fwlink/?LinkID=178833)  
  
- Generuje reprezentację usługi jako klasę kontenera jednostek, która dziedziczy po <xref:System.Data.Services.Client.DataServiceContext>. Ta klasa kontenerów jednostek jest podobna do kontenera jednostek wygenerowanego przez narzędzia Entity Data Model. Aby uzyskać więcej informacji, zobacz temat [usługi obiektów — omówienie (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
- Generuje klasy danych dla typów modeli danych odnajdywanych w metadanych usługi.  
  
- Dodaje odwołanie do zestawu `System.Data.Services.Client` do projektu.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie odwołania do usługi danych](how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 Klasy usługi danych klienta mogą być również generowane za pomocą narzędzia [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [jak: ręczne generowanie klas usługi danych klienta](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>Mapowanie typu danych klienta  
 W przypadku korzystania z okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio lub narzędzia `DataSvcUtil.exe` do generowania klas danych klienta opartych na strumieniowym źródle danych OData, typy danych .NET Framework są mapowane na typy pierwotne z modelu dane w następujący sposób:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [typy danych OData: pierwotne](https://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
- [Szybki start](quickstart-wcf-data-services.md)
