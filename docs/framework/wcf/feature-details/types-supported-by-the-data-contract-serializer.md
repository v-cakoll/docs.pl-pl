---
title: "Typy obsługiwane przez serializator kontraktu danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b6d9ed91e71b7d3f3f214a862389b8ba5316760
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Typy obsługiwane przez serializator kontraktu danych
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]używa <xref:System.Runtime.Serialization.DataContractSerializer> jako jego domyślny aparat serializacji, aby przekonwertować danych XML i przekonwertować do danych XML. <xref:System.Runtime.Serialization.DataContractSerializer> Jest przeznaczony do serializacji *kontraktu danych* typów. Obsługuje jednak wiele innych typów, które mogą być uważane za zawierające niejawnych danych kontraktu. Poniżej znajduje się pełna lista typów, które można serializować:  
  
-   Wszystkie typy widocznego publicznie, które ma konstruktora bez parametrów.  
  
-   Typy kontraktu danych. Są to typy, do których <xref:System.Runtime.Serialization.DataContractAttribute> zastosowano atrybut. Nowe niestandardowe typy, które reprezentują obiektów biznesowych zwykle należy utworzyć jako dane typy kontraktu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) i [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
-   Typy kolekcji. Są to typy, które reprezentują listę danych. Mogą to być regularne tablice typów, lub kolekcji, takie jak <xref:System.Collections.ArrayList> i <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atrybut może służyć do dostosowania serializacji typy, ale nie jest wymagane. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
  
-   Typy wyliczeniowe. Wyliczenia, łącznie z wyliczenia flag, jest możliwy do serializacji. Opcjonalnie, Typy wyliczeniowe może być oznaczony przez <xref:System.Runtime.Serialization.DataContractAttribute> atrybutów, w którym to przypadku każdy członek, który uczestniczy w serializacji muszą być oznaczone <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu. Elementy członkowskie, które nie są oznaczone nie są serializowane. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   Typy pierwotne .NET framework. Następujące typy wbudowane w programie .NET Framework wszystkie można serializować i są traktowane jako typy pierwotne: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, i <xref:System.String>.  
  
-   Inne typy pierwotne. Te typy nie są w nim elementów podstawowych w programie .NET Framework, ale są traktowane jako typów podstawowych w formularzu serializacji XML. Te typy są <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>i tablice <xref:System.Byte>.  
  
    > [!NOTE]
    >  W odróżnieniu od innych typów pierwotnych <xref:System.DateTimeOffset> nie jest znanym typem domyślnie. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).  
  
-   Typy oznaczone <xref:System.SerializableAttribute> atrybutu. Wiele typów objęte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy podstawowej biblioteki obniżenia do tej kategorii. <xref:System.Runtime.Serialization.DataContractSerializer> w pełni obsługuje ten serializacji modelu programowania, który był używany przez usługi zdalne środowiska .NET Framework, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, wprowadzając obsługę <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
-   Typy, które reprezentują raw XML ani typów, które reprezentują [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] relacyjnej bazie danych. <xref:System.Xml.XmlElement> i tablica <xref:System.Xml.XmlNode> typy są obsługiwane jako sposób bezpośrednio reprezentacji XML. Ponadto typy, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejsu są obsługiwane w tym pokrewny <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu i <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> typów. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataTable> Typu i <xref:System.Data.DataSet> typu (a także typu klasy pochodnej) wszystkie wdrożenia <xref:System.Xml.Serialization.IXmlSerializable> interfejsu i nadają się do tej kategorii. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Ograniczenia używania niektórych typów w częściowym tryb zaufania  
 Poniżej znajduje się lista ograniczeń, korzystając z określonych typów w scenariuszach trybie częściowej relacji zaufania:  
  
-   Do serializacji lub deserializacji typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> w częściowo zaufanego kodu za pomocą <xref:System.Runtime.Serialization.DataContractSerializer> wymaga <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> i <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> uprawnienia.  
  
-   Podczas uruchamiania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kod w [zaufania częściowego](../../../../docs/framework/wcf/feature-details/partial-trust.md) tryb, serializacji i deserializacji `readonly` pola (zarówno `public` i `private`) nie jest obsługiwana. Jest to spowodowane wygenerowanego IL jest niemożliwy i dlatego wymaga podwyższonym poziomem uprawnień.  
  
-   Zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> są obsługiwane w środowisku częściowej relacji zaufania. Jednak użycie <xref:System.Runtime.Serialization.DataContractSerializer> podlega następujące warunki:  
  
    -   Wszystkie serializacji `[DataContract]` typy muszą być publiczne.  
  
    -   Wszystkie serializacji `[DataMember]` pola lub właściwości w `[DataContract]` typu musi być publiczny i odczytu/zapisu. Serializacja i deserializacja `readonly` pola nie jest obsługiwane podczas uruchamiania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w częściowo zaufanych aplikacji.  
  
    -   `[Serializable]` / `ISerializable]` Model programowania nie jest obsługiwany w środowisku częściowej relacji zaufania.  
  
    -   Znane typy muszą być określone w kodu lub konfiguracji na poziomie maszyny (`Machine.config`). W aplikacjach na poziomie konfiguracji ze względów bezpieczeństwa nie można określić znanych typów.  
  
-   Typy, które implementują <xref:System.Runtime.Serialization.IObjectReference> Zgłoś wyjątek w środowisku częściowo zaufane, ponieważ <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> metoda wymaga uprawnień zabezpieczeń `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.  
  
## <a name="additional-notes-on-serialization"></a>Dodatkowe uwagi o serializacji  
 Następujące reguły dotyczą również typy obsługiwane przez serializator kontraktu danych:  
  
-   Typy ogólne są w pełni obsługiwane przez serializator kontraktu danych.  
  
-   Typy dopuszczające wartości null są w pełni obsługiwane przez serializator kontraktu danych.  
  
-   Typy interfejsów są traktowane albo jako <xref:System.Object> lub, w przypadku interfejsy kolekcji jako typy kolekcji.  
  
-   Obsługiwane są zarówno struktur i klas.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Nie obsługuje modelu programowania używany przez <xref:System.Xml.Serialization.XmlSerializer> i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web. W szczególności nie obsługuje atrybutów, takich jak <xref:System.Xml.Serialization.XmlElementAttribute> i <xref:System.Xml.Serialization.XmlAttributeAttribute>. Aby włączyć obsługę programowania modelu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] muszą zostać przełączone do używania <xref:System.Xml.Serialization.XmlSerializer> zamiast <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   <xref:System.DBNull> Typu jest traktowana w specjalny sposób. Jest to typ singleton, a po deserializacji Deserializator szanuje Ograniczenie singleton i wszystkie punkty `DBNull` odwołania do pojedyncze wystąpienie. Ponieważ `DBNull` jest typem umożliwiającym serializację go wymaga <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> uprawnienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [Typy kolekcji w kontraktach danych](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)  
 [Typy wyliczeniowe w kontraktach danych](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)
