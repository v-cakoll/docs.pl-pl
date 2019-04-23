---
title: Typy z możliwością serializowania
ms.date: 03/30/2017
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
ms.openlocfilehash: 44fc538ccb69296b91c94d2b9ae497be599c0c7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160852"
---
# <a name="serializable-types"></a>Typy z możliwością serializowania
Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje wszystkich typów publicznie widoczne. Wszystkie właściwości publiczne odczytu/zapisu i pola tego typu są serializowane.  
  
 Można zmienić domyślne zachowanie, stosując <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty do typów i członków tej funkcji mogą być przydatne w sytuacjach, w których mają typy, które nie są pod Twoją kontrolą i nie można zmodyfikować, aby dodać atrybuty. <xref:System.Runtime.Serialization.DataContractSerializer> Rozpoznaje typy takie "nieoznaczone".  
  
## <a name="serialization-defaults"></a>Serializacja wartości domyślne  
 Można zastosować <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów, aby jawnie kontrolować lub dostosować serializacji typów i elementów członkowskich. Ponadto te atrybuty można zastosować do pól prywatnych. Jednak nawet typy, które nie są oznaczone przez te atrybuty są serializacji i deserializacji. Obowiązują następujące reguły i wyjątków:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje kontraktu danych z typów bez przy użyciu domyślnych właściwości nowo utworzonej typy atrybutów.  
  
-   Wszystkie publiczne pola i właściwości z publicznych `get` i `set` metody są serializowane, o ile nie zostanie zastosowana <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atrybutu tego elementu członkowskiego.  
  
-   Semantyka serializacji jest podobne do występujących dla <xref:System.Xml.Serialization.XmlSerializer>.  
  
-   Nieoznaczone typy tylko typy publiczne konstruktory, które nie mają parametrów są serializowane. Wyjątkiem od tej reguły jest <xref:System.Runtime.Serialization.ExtensionDataObject> używane z <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu.  
  
-   Pola tylko do odczytu, właściwości bez `get` lub `set` metody i właściwości za pomocą wewnętrznego lub prywatnego `set` lub `get` metod nie są serializowane. Tych właściwości są ignorowane i jest zgłaszany żaden wyjątek, z wyjątkiem kolekcji tylko do get.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> atrybuty (takie jak `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`i tak dalej), są ignorowane.  
  
-   Jeśli nie zastosujesz <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do danego typu serializator ignoruje wszystkich elementów członkowskich tego typu, do którego <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut jest stosowany.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> Właściwość jest obsługiwana w typach oznaczone nie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu. Obejmuje to obsługę <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu nieoznaczone typy.  
  
-   Aby "zrezygnować" nad procesem serializacji dla pola, właściwości lub publiczne elementy członkowskie, zastosuj <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atrybutu tego elementu członkowskiego.  
  
## <a name="inheritance"></a>Dziedziczenie  
 Nieoznaczone typy (typy bez <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu) może dziedziczyć z typów, które mają atrybut; Jednakże, odwrotna nie jest dozwolony: typy z atrybutem nie może dziedziczyć z nieoznaczone typy. Ta zasada jest wymuszana głównie w celu zapewnienia zgodności z poprzednimi wersjami przy użyciu kodu napisanego w starszych wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
