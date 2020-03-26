---
title: Typy obsługiwane przez serializator kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: f3eedda6c9493688680099f4b07810aebf69ff8a
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249464"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Typy obsługiwane przez serializator kontraktu danych

Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> używa jako domyślnego aparatu serializacji do konwersji danych do XML i konwersji XML z powrotem na dane. Jest <xref:System.Runtime.Serialization.DataContractSerializer> przeznaczony do serializacji typów *kontraktów danych.* Jednak obsługuje wiele innych typów, które można traktować jako o kontrakt niejawne dane. Poniżej znajduje się pełna lista typów, które mogą być serializowane:

- Wszystkie publicznie widoczne typy, które mają konstruktora, który nie ma parametrów.

- Typy kontraktów danych. Są to typy, <xref:System.Runtime.Serialization.DataContractAttribute> do których zastosowano atrybut. Nowe typy niestandardowe, które reprezentują obiekty biznesowe powinny być zwykle tworzone jako typy kontraktów danych. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) i typów [serializable](../../../../docs/framework/wcf/feature-details/serializable-types.md).

- Typy kolekcji. Są to typy, które reprezentują listy danych. Mogą to być regularne tablice typów lub <xref:System.Collections.ArrayList> typów <xref:System.Collections.Generic.Dictionary%602>kolekcji, takich jak i . Atrybut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> może służyć do dostosowywania serializacji tych typów, ale nie jest wymagane. Aby uzyskać więcej informacji, zobacz [Typy zbierania danych w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).

- Typy wyliczenia. Wyliczenia, w tym wyliczenia flagi, są serializable. Opcjonalnie typy wyliczenia mogą <xref:System.Runtime.Serialization.DataContractAttribute> być oznaczone atrybutem, w którym to przypadku każdy element <xref:System.Runtime.Serialization.EnumMemberAttribute> członkowski, który uczestniczy w serializacji musi być oznaczony atrybutem. Elementy członkowskie, które nie są oznaczone nie są serializowane. Aby uzyskać więcej informacji, zobacz [Typy wyliczenia w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- .NET Framework typów pierwotnych. Następujące typy wbudowane w .NET Framework mogą być serializowane i <xref:System.Byte>są <xref:System.SByte> <xref:System.Int16>uważane <xref:System.Int32> <xref:System.Int64>za <xref:System.UInt16> <xref:System.UInt32>typy pierwotne: , , , , , , , <xref:System.UInt64>, <xref:System.Single>, , <xref:System.Double>, , <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, , <xref:System.Object>, , i <xref:System.String>.

- Inne typy pierwotne. Te typy nie są elementów pierwotnych w .NET Framework, ale są traktowane jako elementów pierwotnych w formie seryjny XML. Te typy <xref:System.DateTimeOffset> <xref:System.TimeSpan>to <xref:System.Guid> <xref:System.DateTime> <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>, , <xref:System.Byte>, i tablice .

  > [!NOTE]
  > W przeciwieństwie do innych <xref:System.DateTimeOffset> typów pierwotnych, nie jest znany typ domyślnie. Aby uzyskać więcej informacji, zobacz [Znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).

- Typy oznaczone <xref:System.SerializableAttribute> atrybutem. Wiele typów zawartych w bibliotece klas podstawowych programu .NET Framework należy do tej kategorii. W <xref:System.Runtime.Serialization.DataContractSerializer> pełni obsługuje ten model programowania serializacji, który był <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>używany przez <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.NET Framework <xref:System.Runtime.Serialization.ISerializable> komunikacji zdalnej, , i , w tym obsługi interfejsu.

- Typy reprezentujące nieprzetworzony kod XML lub typy reprezentujące ADO.NET dane relacyjne. I <xref:System.Xml.XmlElement> tablica <xref:System.Xml.XmlNode> typów są obsługiwane jako sposób reprezentowania XML bezpośrednio. Ponadto typy, które <xref:System.Xml.Serialization.IXmlSerializable> implementują interfejs są <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> obsługiwane, w <xref:System.Xml.Linq.XDocument> tym <xref:System.Xml.Linq.XElement> powiązanego atrybutu i i typów. Typ ADO.NET<xref:System.Data.DataTable> i <xref:System.Data.DataSet> typ (a także jego typizowane klasy pochodne) <xref:System.Xml.Serialization.IXmlSerializable> wszystkie implementują interfejs i dlatego pasują do tej kategorii. Aby uzyskać więcej informacji, zobacz [XML i ADO.NET typy w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Ograniczenia korzystania z niektórych typów w trybie częściowego zaufania

Poniżej znajduje się lista ograniczeń podczas korzystania z niektórych typów w scenariuszach trybu częściowego zaufania:

- Aby serializować lub deserialize <xref:System.Runtime.Serialization.ISerializable> typu, który implementuje <xref:System.Runtime.Serialization.DataContractSerializer> w <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> częściowo <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> zaufany kod przy użyciu wymaga i uprawnienia.

- Podczas uruchamiania kodu WCF w trybie [częściowego](../../../../docs/framework/wcf/feature-details/partial-trust.md) `readonly` zaufania serializacji i deserializacji pól (zarówno `public` i) `private`nie jest obsługiwany. Dzieje się tak, ponieważ wygenerowany IL jest niemożliwy do zweryfikowania i dlatego wymaga podwyższonych uprawnień.

- Zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> są obsługiwane w środowisku częściowego zaufania. Jednakże korzystanie <xref:System.Runtime.Serialization.DataContractSerializer> z nich podlega następującym warunkom:

  - Wszystkie typy `[DataContract]` serializable muszą być publiczne.

  - Wszystkie pola `[DataMember]` lub właściwości serializowalne w typie `[DataContract]` muszą być publiczne i odczytywać/zapisywać. Serializacji i deserializacji `readonly` pól nie jest obsługiwany podczas uruchamiania WCF w aplikacji częściowo zaufanych.

  - `[Serializable]` / Model `ISerializable]` programowania nie jest obsługiwany w środowisku częściowego zaufania.

  - Znane typy muszą być określone w`Machine.config`konfiguracji kodu lub na poziomie maszyny ( ). Znane typy nie można określić w konfiguracji na poziomie aplikacji ze względów bezpieczeństwa.

- Typy, <xref:System.Runtime.Serialization.IObjectReference> które implementują zgłaszają wyjątek w <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> środowisku częściowo `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`zaufanym, ponieważ metoda wymaga uprawnień zabezpieczeń.

## <a name="additional-notes-on-serialization"></a>Dodatkowe uwagi dotyczące serializacji

Następujące reguły mają również zastosowanie do typów obsługiwanych przez serializator kontraktu danych:

- Typy ogólne są w pełni obsługiwane przez serializator kontraktu danych.

- Typy wartości nullable są w pełni obsługiwane przez serializator umowy danych.

- Typy interfejsu są traktowane <xref:System.Object> jako lub, w przypadku interfejsów kolekcji, jako typy kolekcji.

- Obsługiwane są zarówno struktury, jak i klasy.

- Nie <xref:System.Runtime.Serialization.DataContractSerializer> obsługuje modelu programowania używanego <xref:System.Xml.Serialization.XmlSerializer> przez usługi sieci Web i ASP.NET. W szczególności nie obsługuje atrybutów takich jak <xref:System.Xml.Serialization.XmlElementAttribute> i <xref:System.Xml.Serialization.XmlAttributeAttribute>. Aby włączyć obsługę tego modelu programowania, WCF musi <xref:System.Xml.Serialization.XmlSerializer> być włączony <xref:System.Runtime.Serialization.DataContractSerializer>do używania zamiast .

- Typ <xref:System.DBNull> jest traktowany w sposób szczególny. Jest typem singleton, a po deserializacji deserializer przestrzega ograniczenia `DBNull` singleton i wskazuje wszystkie odwołania do wystąpienia singleton. Ponieważ `DBNull` jest typu serializable, <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> wymaga uprawnień.

## <a name="see-also"></a>Zobacz też

- [Typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Typy z możliwością serializowania](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)
- [Typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)
