---
title: "Typy z możliwością serializowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e368472db3bdca73661586821106174e13d4d24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="serializable-types"></a>Typy z możliwością serializowania
Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje wszystkich typów publicznie widoczna. Wszystkie właściwości publiczne odczytu/zapisu i pól typu są serializowane.  
  
 Domyślne zachowanie można zmienić, stosując <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty dla typów i członków tej funkcji mogą być przydatne w sytuacjach, w których mają typy, które nie są pod kontrolą i nie można zmodyfikować, aby dodać atrybuty. <xref:System.Runtime.Serialization.DataContractSerializer> Rozpoznaje takie typy "nieoznaczone".  
  
## <a name="serialization-defaults"></a>Ustawienia domyślne serializacji  
 Możesz zastosować <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty jawnie kontrolować lub dostosowanie serializacji typów i członków. Ponadto można stosować te atrybuty do pól prywatnych. Jednak nawet typy, które nie są oznaczone ikoną z tych atrybutów są serializacji i deserializacji. Zastosuj poniższe reguły i wyjątków:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje bez atrybutów przy użyciu domyślnych właściwości nowo utworzone typy z typów kontraktu danych.  
  
-   Wszystkie publiczne pola i właściwości z publicznych `get` i `set` metody są serializowane, jeśli nie zostanie zastosowana <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atrybutu do tego elementu członkowskiego.  
  
-   Semantyka podobne do serializacji <xref:System.Xml.Serialization.XmlSerializer>.  
  
-   Nieoznaczone typy serializacji są tylko typy publiczne z konstruktorów bez parametrów. Wyjątkiem od tej reguły jest <xref:System.Runtime.Serialization.ExtensionDataObject> używane z <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu.  
  
-   Pola tylko do odczytu, właściwości bez `get` lub `set` metody i właściwości z wewnętrznego lub prywatnego `set` lub `get` metod nie są serializowane. Tych właściwości są ignorowane, a nie wyjątek, chyba że w przypadku kolekcji tylko do pobrania.  
  
-   <xref:System.Xml.Serialization.XmlSerializer>atrybuty (takich jak `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`i tak dalej), są ignorowane.  
  
-   Jeśli nie mają zastosowania <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do danego typu serializatora ignoruje członków w danym typie, do którego <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut jest stosowany.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> Właściwość jest obsługiwana w typach nie oznaczony atrybutem <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu. Obejmuje to obsługę <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu nieoznaczone typy.  
  
-   "Wykluczyć" procesu serializacji dla publicznych elementów członkowskich, właściwości lub pól, zastosuj <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atrybutu do tego elementu członkowskiego.  
  
## <a name="inheritance"></a>Dziedziczenie  
 Nieoznaczone typy (typy bez <xref:System.Runtime.Serialization.DataContractAttribute> atrybut) może dziedziczyć z typów, które mają atrybut; jednak odwrotnej nie jest dozwolona: typy z atrybutem nie może dziedziczyć po nieoznaczone typy. Ta reguła jest wymuszone głównie w celu zapewnienia zgodności z poprzednimi wersjami z kod napisany w starszych wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
