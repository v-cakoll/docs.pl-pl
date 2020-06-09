---
title: Typy obsługiwane przez serializator kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: 15c3cda8329682fcbaa36609647ec49de7eb3c37
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595105"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Typy obsługiwane przez serializator kontraktu danych

Windows Communication Foundation (WCF) używa <xref:System.Runtime.Serialization.DataContractSerializer> jako domyślnego aparatu serializacji, aby przekonwertować dane do formatu XML i przekonwertować kod XML z powrotem na dane. <xref:System.Runtime.Serialization.DataContractSerializer>Jest przeznaczony do serializacji typów *kontraktu danych* . Jednak obsługuje ona wiele innych typów, które można traktować jako niejawny kontrakt danych. Poniżej znajduje się kompletna lista typów, które mogą być serializowane:

- Wszystkie publicznie widoczne typy, które mają konstruktora, który nie ma parametrów.

- Typy kontraktów danych. Są to typy, do których <xref:System.Runtime.Serialization.DataContractAttribute> zastosowano atrybut. Nowe typy niestandardowe, które reprezentują obiekty biznesowe, powinny być zwykle tworzone jako typy kontraktu danych. Aby uzyskać więcej informacji, zobacz [Używanie kontraktów danych](using-data-contracts.md) i [typów możliwych do serializacji](serializable-types.md).

- Typy kolekcji. Są to typy reprezentujące listy danych. Mogą to być regularne tablice typów lub typy kolekcji, takie jak <xref:System.Collections.ArrayList> i <xref:System.Collections.Generic.Dictionary%602> . Ten <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut może służyć do dostosowywania serializacji tych typów, ale nie jest to wymagane. Aby uzyskać więcej informacji, zobacz [typy kolekcji w kontraktach danych](collection-types-in-data-contracts.md).

- Typy wyliczeniowe. Wyliczenia, w tym wyliczenia flag, można serializować. Opcjonalnie typy wyliczeniowe mogą być oznaczone <xref:System.Runtime.Serialization.DataContractAttribute> atrybutem. w takim przypadku każdy element członkowski, który uczestniczy w serializacji, musi być oznaczony <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutem. Elementy członkowskie, które nie są oznaczone, nie są serializowane. Aby uzyskać więcej informacji, zobacz [typy wyliczeniowe w kontraktach danych](enumeration-types-in-data-contracts.md).

- .NET Framework typy pierwotne. Następujące typy wbudowane w .NET Framework mogą być serializowane i są uznawane za typy pierwotne:,,,,,,,,,, <xref:System.Byte> <xref:System.SByte> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> <xref:System.Single> <xref:System.Double> <xref:System.Boolean> , <xref:System.Char> ,, <xref:System.Decimal> <xref:System.Object> , i <xref:System.String> .

- Inne typy pierwotne. Te typy nie są pierwotne w .NET Framework ale są traktowane jako elementy pierwotne w serializowanym formularzu XML. Te typy to,,,, <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.TimeSpan> <xref:System.Guid> <xref:System.Uri> <xref:System.Xml.XmlQualifiedName> i tablice <xref:System.Byte> .

  > [!NOTE]
  > W przeciwieństwie do innych typów pierwotnych, <xref:System.DateTimeOffset> nie jest domyślnie znanym typem. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](data-contract-known-types.md)).

- Typy oznaczone <xref:System.SerializableAttribute> atrybutem. Wiele typów uwzględnionych w bibliotece klas podstawowych .NET Framework należy do tej kategorii. W <xref:System.Runtime.Serialization.DataContractSerializer> pełni obsługuje ten model programowania serializacji, który był używany przez .NET Framework komunikacji zdalnej, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> , w tym obsługę <xref:System.Runtime.Serialization.ISerializable> interfejsu.

- Typy, które reprezentują nieprzetworzony kod XML lub typy reprezentujące dane relacyjne ADO.NET. <xref:System.Xml.XmlElement>Tablica i <xref:System.Xml.XmlNode> typy są obsługiwane jako sposób bezpośredniego reprezentowania kodu XML. Ponadto typy implementujące <xref:System.Xml.Serialization.IXmlSerializable> interfejs są obsługiwane, w tym powiązane z nimi <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybuty i <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> typy i. Typ ADO.NET <xref:System.Data.DataTable> i <xref:System.Data.DataSet> Typ (a także jej klasy pochodne) implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejs i dlatego mieszczą się w tej kategorii. Aby uzyskać więcej informacji, zobacz [Typy XML i ADO.NET w kontraktach danych](xml-and-ado-net-types-in-data-contracts.md).

## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Ograniczenia dotyczące używania niektórych typów w trybie częściowego zaufania

Poniżej znajduje się lista ograniczeń w przypadku korzystania z określonych typów w scenariuszach częściowego trybu zaufania:

- Aby serializować lub deserializować typ, który implementuje <xref:System.Runtime.Serialization.ISerializable> kod częściowo zaufany przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> wymaganych <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> uprawnień i.

- Podczas uruchamiania kodu WCF w trybie [częściowego zaufania](partial-trust.md) , serializacja i deserializacja `readonly` pól (zarówno `public` i `private` ) nie jest obsługiwana. Wynika to z faktu, że wygenerowany kod IL jest niemożliwy do sprawdzenia i w związku z tym wymaga podniesionych uprawnień.

- Zarówno, <xref:System.Runtime.Serialization.DataContractSerializer> jak i <xref:System.Xml.Serialization.XmlSerializer> są obsługiwane w środowisku częściowej relacji zaufania. Jednak użycie programu <xref:System.Runtime.Serialization.DataContractSerializer> podlega następującym warunkom:

  - Wszystkie `[DataContract]` typy możliwe do serializacji muszą być publiczne.

  - Wszystkie możliwe do serializacji `[DataMember]` pola lub właściwości w `[DataContract]` typie muszą być publiczne i odczytywane i zapisywane. Serializacja i deserializacja `readonly` pól nie jest obsługiwana w przypadku uruchamiania programu WCF w częściowo zaufanej aplikacji.

  - `[Serializable]` / `ISerializable]` Model programowania nie jest obsługiwany w środowisku częściowej relacji zaufania.

  - Znane typy muszą być określone w kodzie lub konfiguracji na poziomie komputera ( `Machine.config` ). Nie można określić znanych typów w konfiguracji na poziomie aplikacji ze względów bezpieczeństwa.

- Typy, które implementują <xref:System.Runtime.Serialization.IObjectReference> zgłoszenie wyjątku w środowisku częściowo zaufanym, ponieważ <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> Metoda wymaga uprawnienia zabezpieczeń `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]` .

## <a name="additional-notes-on-serialization"></a>Dodatkowe uwagi dotyczące serializacji

Poniższe reguły mają zastosowanie również do typów obsługiwanych przez serializator kontraktu danych:

- Typy ogólne są w pełni obsługiwane przez serializator kontraktu danych.

- Typy wartości null są w pełni obsługiwane przez serializator kontraktu danych.

- Typy interfejsów są traktowane jako <xref:System.Object> lub, w przypadku interfejsów kolekcji, jako typy kolekcji.

- Obsługiwane są zarówno struktury, jak i klasy.

- Program <xref:System.Runtime.Serialization.DataContractSerializer> nie obsługuje modelu programowania używanego przez <xref:System.Xml.Serialization.XmlSerializer> usługi i ASP.NET sieci Web. W szczególności nie obsługuje atrybutów takich jak <xref:System.Xml.Serialization.XmlElementAttribute> i <xref:System.Xml.Serialization.XmlAttributeAttribute> . Aby włączyć obsługę tego modelu programowania, należy przełączyć WCF w celu użycia <xref:System.Xml.Serialization.XmlSerializer> zamiast <xref:System.Runtime.Serialization.DataContractSerializer> .

- <xref:System.DBNull>Typ jest traktowany w specjalny sposób. Jest to typ pojedynczy, a po deserializacji deserializowany odnosi się do ograniczenia singleton i wskazuje wszystkie `DBNull` odwołania do pojedynczego wystąpienia. Ponieważ `DBNull` jest typem możliwym do serializacji, wymaga <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> uprawnień.

## <a name="see-also"></a>Zobacz też

- [Typy XML i ADO.NET w kontraktach danych](xml-and-ado-net-types-in-data-contracts.md)
- [Używanie kontraktów danych](using-data-contracts.md)
- [Typy z możliwością serializowania](serializable-types.md)
- [Typy kolekcji w kontraktach danych](collection-types-in-data-contracts.md)
- [Typy wyliczeniowe w kontraktach danych](enumeration-types-in-data-contracts.md)
