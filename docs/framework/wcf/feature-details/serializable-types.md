---
title: Typy z możliwością serializowania
ms.date: 03/30/2017
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
ms.openlocfilehash: e65fcb93c5c36bb289b825cef58b3adc6f5155f5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586107"
---
# <a name="serializable-types"></a>Typy z możliwością serializowania
Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializacji wszystkie publicznie widoczne typy. Wszystkie publiczne właściwości odczytu/zapisu i pola typu są serializowane.  
  
 Zachowanie domyślne można zmienić, stosując <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty i do typów i składowych, których ta funkcja może być przydatna w sytuacjach, w których masz typy, które nie znajdują się pod kontrolą i nie można ich modyfikować w celu dodania atrybutów. <xref:System.Runtime.Serialization.DataContractSerializer>Rozpoznaje takie typy "nieoznaczone".  
  
## <a name="serialization-defaults"></a>Wartości domyślne serializacji  
 Można zastosować <xref:System.Runtime.Serialization.DataContractAttribute> atrybuty i, <xref:System.Runtime.Serialization.DataMemberAttribute> Aby jawnie kontrolować lub dostosowywać serializacji typów i elementów członkowskich. Ponadto te atrybuty można zastosować do pól prywatnych. Jednak typy, które nie są oznaczone tymi atrybutami, są serializowane i deserializowane. Mają zastosowanie następujące reguły i wyjątki:  
  
- <xref:System.Runtime.Serialization.DataContractSerializer>Wnioskuje o umowę danych z typów bez atrybutów przy użyciu domyślnych właściwości nowo utworzonych typów.  
  
- Wszystkie pola publiczne i właściwości z `get` `set` metodami publicznymi są serializowane, chyba że stosujesz <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atrybut do tego elementu członkowskiego.  
  
- Semantyka serializacji jest podobna do właściwości <xref:System.Xml.Serialization.XmlSerializer> .  
  
- W przypadku typów nieoznaczonych tylko typy publiczne z konstruktorów, które nie mają parametrów są serializowane. Wyjątek od tej reguły jest <xref:System.Runtime.Serialization.ExtensionDataObject> używany z <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsem.  
  
- Pola tylko do odczytu, właściwości bez `get` metody lub `set` i właściwości z wewnętrznymi lub prywatnymi `set` `get` metodami nie są serializowane. Takie właściwości są ignorowane i nie jest zgłaszany żaden wyjątek, chyba że w przypadku kolekcji tylko do pobrania.  
  
- <xref:System.Xml.Serialization.XmlSerializer>atrybuty (takie jak `XmlElement` ,,, `XmlAttribute` `XmlIgnore` `XmlInclude` i tak dalej) są ignorowane.  
  
- Jeśli nie zastosujesz <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu do danego typu, serializator zignoruje dowolny element członkowski w tym typie, do którego <xref:System.Runtime.Serialization.DataMemberAttribute> zastosowano atrybut.  
  
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>Właściwość jest obsługiwana w typach, które nie są oznaczone <xref:System.Runtime.Serialization.DataContractAttribute> atrybutem. Obejmuje to obsługę atrybutu dla <xref:System.Runtime.Serialization.KnownTypeAttribute> nieoznaczonych typów.  
  
- Aby zrezygnować z procesu serializacji dla publicznych elementów członkowskich, właściwości lub pól, Zastosuj <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atrybut do tego elementu członkowskiego.  
  
## <a name="inheritance"></a>Dziedziczenie  
 Typy nieoznaczone (typy bez <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu) mogą dziedziczyć po typach, które mają ten atrybut, ale odwrotnie nie jest dozwolone: typy z atrybutem nie mogą dziedziczyć po typach nieoznaczonych. Ta reguła jest wymuszana głównie w celu zapewnienia zgodności z poprzednimi wersjami przy użyciu kodu pisanego we wcześniejszych wersjach .NET Framework.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Typy obsługiwane przez serializator kontraktu danych](types-supported-by-the-data-contract-serializer.md)
