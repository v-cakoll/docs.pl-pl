---
title: Typy obsługiwane przez serializator kontraktu danych
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: 9c532858ba3b93d427e5c0455f953db2499ebd6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918882"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Typy obsługiwane przez serializator kontraktu danych
Windows Communication Foundation (WCF) używa <xref:System.Runtime.Serialization.DataContractSerializer> jako jego domyślny mechanizm serializacji do konwertowania danych do formatu XML i konwertowania XML do danych. <xref:System.Runtime.Serialization.DataContractSerializer> Zaprojektowano w celu serializacji *kontraktu danych* typów. Obsługuje jednak wiele innych typów, które mogą być uważane za zawierające kontraktu danych niejawnych. Poniżej przedstawiono pełną listę typów, które można wykonywać serializację:  
  
- Publicznie widoczne typy, które mają Konstruktor, który nie ma parametrów.  
  
- Typy kontraktu danych. Są to typy, do którego <xref:System.Runtime.Serialization.DataContractAttribute> zastosowano atrybut. Nowe typy niestandardowych, które reprezentują obiektów biznesowych należy zwykle utworzyć jako dane typy kontraktu. Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) i [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
- Typy kolekcji. Są to typy, które reprezentują listy danych. Mogą to być regularnych tablic z typów, lub kolekcji, takie jak <xref:System.Collections.ArrayList> i <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atrybut można dostosować serializacji typów, ale nie jest wymagane. Aby uzyskać więcej informacji, zobacz [typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
  
- Typy wyliczeniowe. Wyliczenia, włącznie z wyliczeniami flagi są możliwe do serializacji. Opcjonalnie, mogą być oznaczone Typy wyliczeniowe <xref:System.Runtime.Serialization.DataContractAttribute> atrybut, w którym to przypadku każdy element członkowski, który uczestniczy w serializacji muszą być oznaczone <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu. Nie są szeregowane elementy członkowskie, które nie zostały oznaczone. Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
- Typy pierwotne .NET framework. Następujące typy, które są wbudowane w .NET Framework wszystkie można wykonywać serializację i są uznawane za typów pierwotnych: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, i <xref:System.String>.  
  
- Inne typy pierwotne. Te typy nie są w nim elementów podstawowych w .NET Framework, ale są traktowane jako podstawowych w formularzu serializacji XML. Te typy są <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>i tablice <xref:System.Byte>.  
  
    > [!NOTE]
    >  W przeciwieństwie do innych typów pierwotnych <xref:System.DateTimeOffset> nie jest znany typ domyślnie. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).  
  
- Typy oznaczone <xref:System.SerializableAttribute> atrybutu. Wiele typów objęte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy podstawowej biblioteki należą do tej kategorii. <xref:System.Runtime.Serialization.DataContractSerializer> Tej serializacji model programowania, który został użyty przez wywołaniem funkcji zdalnych .NET Framework, w pełni obsługuje <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, łącznie z obsługą <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
- Typy, które reprezentują pierwotne XML lub typy, które reprezentują [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] opartego na danych relacyjnych. <xref:System.Xml.XmlElement> Tablicę <xref:System.Xml.XmlNode> typy są obsługiwane jako sposób reprezentowania XML bezpośrednio. Ponadto typami, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejsu są obsługiwane, w tym powiązane <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu, a <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> typów. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataTable> Typu i <xref:System.Data.DataSet> typu (a także typizowanych klas pochodnych) implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejs i nadają się do tej kategorii. Aby uzyskać więcej informacji, zobacz [typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Tryb zaufania ograniczenia przy użyciu określonych typów w częściowym  
 Poniżej przedstawiono listę ograniczeń, korzystając z określonych typów w scenariuszach tryb częściowej relacji zaufania:  
  
- Do serializacji lub deserializacji typie, który implementuje <xref:System.Runtime.Serialization.ISerializable> w częściowo zaufanego kodu za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> wymaga <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> i <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> uprawnienia.  
  
- Podczas uruchamiania kodu usługi WCF [częściowego zaufania](../../../../docs/framework/wcf/feature-details/partial-trust.md) tryb serializacji i deserializacji `readonly` pola (zarówno `public` i `private`) nie jest obsługiwane. Jest to spowodowane wygenerowanego IL nie jest i dlatego wymaga podniesionych uprawnień.  
  
- Zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> są obsługiwane w środowisku częściowej relacji zaufania. Jednak użycie <xref:System.Runtime.Serialization.DataContractSerializer> podlega następujące warunki:  
  
    - Wszystkie możliwe do serializacji `[DataContract]` typy muszą być publiczne.  
  
    - Wszystkie możliwe do serializacji `[DataMember]` pól lub właściwości w `[DataContract]` typu muszą być publiczne i odczytu/zapisu. Serializacja i deserializacja `readonly` pola nie jest obsługiwana podczas uruchamiania usługi WCF w częściowo zaufanych aplikacji.  
  
    - `[Serializable]` / `ISerializable]` Model programowania nie jest obsługiwany w środowisku częściowej relacji zaufania.  
  
    - Znane typy muszą być określone w kodzie lub konfiguracji na poziomie komputera (`Machine.config`). Znane typy nie może być określona w konfiguracji dodatku poziomu aplikacji ze względów bezpieczeństwa.  
  
- Typami, które implementują <xref:System.Runtime.Serialization.IObjectReference> zgłosić wyjątek w środowisku częściowo zaufany, ponieważ <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> metoda wymaga uprawnienia zabezpieczeń `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.  
  
## <a name="additional-notes-on-serialization"></a>Dodatkowe uwagi dotyczące serializacji  
 Następujące reguły dotyczą również typy obsługiwane przez serializator kontraktu danych:  
  
- Typy ogólne są w pełni obsługiwane przez serializator kontraktu danych.  
  
- Typy dopuszczające wartości zerowe są w pełni obsługiwane przez serializator kontraktu danych.  
  
- Typy interfejsu są traktowane albo jako <xref:System.Object> lub, w przypadku interfejsów kolekcji, jako typy kolekcji.  
  
- Obsługiwane są zarówno struktur i klas.  
  
- <xref:System.Runtime.Serialization.DataContractSerializer> Nie obsługuje modelu programowania, używany przez <xref:System.Xml.Serialization.XmlSerializer> i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web. W szczególności, ale nie obsługuje atrybutów, takich jak <xref:System.Xml.Serialization.XmlElementAttribute> i <xref:System.Xml.Serialization.XmlAttributeAttribute>. Aby włączyć obsługę dla tego modelu programowania, WCF, muszą zostać przełączone do użycia <xref:System.Xml.Serialization.XmlSerializer> zamiast <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
- <xref:System.DBNull> Typu jest traktowana w specjalny sposób. Jest to typ pojedyncze i po deserializacji deserializacji stosuje się do ograniczeń pojedyncze i wszystkie punkty `DBNull` odwołania do pojedyncze wystąpienie. Ponieważ `DBNull` jest możliwy do serializacji typów, zażąda on <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> uprawnień.  
  
## <a name="see-also"></a>Zobacz także

- [Typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Typy z możliwością serializowania](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)
- [Typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)
