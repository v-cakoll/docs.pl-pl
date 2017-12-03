---
title: Typy wyliczeniowe w kontraktach danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 13b3d19c8e71d7bd6a37362b1ac1b5e23e8ff24a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="enumeration-types-in-data-contracts"></a>Typy wyliczeniowe w kontraktach danych
Wyliczenia mogą być wyrażone w modelu kontraktu danych. W tym temacie przedstawiono kilka przykładów objaśniające modelu programowania.  
  
## <a name="enumeration-basics"></a>Podstawy — wyliczenie  
 Sposób użycia Typy wyliczeniowe w modelu kontraktu danych ma zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu. Następnie należy zastosować <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu do każdego elementu członkowskiego, który musi być uwzględniona w kontraktu danych.  
  
 W poniższym przykładzie przedstawiono dwie klasy. Wyliczenia używa pierwszego i drugiego definiuje wyliczenia.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Wystąpienie `Car` klasy, które mogą być wysyłane lub odbierane tylko wtedy, gdy `condition` pole jest ustawione na jedną z wartości `New`, `Used`, lub `Rental`. Jeśli `condition` jest `Broken` lub `Stolen`, <xref:System.Runtime.Serialization.SerializationException> jest generowany.  
  
 Można użyć <xref:System.Runtime.Serialization.DataContractAttribute> właściwości (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> i <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) dla kontraktów danych wyliczenia.  
  
### <a name="enumeration-member-values"></a>Wartości elementu członkowskiego wyliczenia  
 Kontrakt danych obejmuje zazwyczaj wyliczenie nazwy elementów członkowskich, nie wartości liczbowe. Jednak jeśli przy użyciu danych kontraktu modelu, jeśli po stronie odbierającej jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, wyeksportowanego schematu zachowuje wartości liczbowe. Należy pamiętać, że to nie jest to przy użyciu [przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
 W poprzednim przykładzie Jeśli `condition` ustawiono `Used` i jest serializowany danych do pliku XML, wynikowy kod XML jest `<condition>Used</condition>` i nie `<condition>1</condition>`. W związku z tym następujące kontrakt danych jest odpowiednikiem z kontraktem danych `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Na przykład można użyć `CarConditionEnum` po stronie wysyłającej i `CarConditionWithNumbers` po stronie odbierającej. Chociaż po stronie wysyłającej korzysta z wartości "1" dla `Used` i używa po stronie odbierania, wartość "20" reprezentację XML jest `<condition>Used</condition>` po obu stronach.  
  
 Do uwzględnienia w kontraktu danych, należy najpierw zastosować <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu. W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], zawsze można zastosować specjalna wartość 0 (zero) do wyliczenia, która jest również wartością domyślną dla dowolnego wyliczenia. Jednak nawet to specjalne wartości zerowej nie można serializować, chyba że jest on oznaczony <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.  
  
 Istnieją dwa wyjątki od tej reguły:  
  
-   Flaga wyliczenia (omówione w dalszej części tego tematu).  
  
-   Elementy członkowskie danych wyliczenia z <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ustawioną właściwość `false` (w takim przypadku wyliczenie o wartości zero pominięto w danych serializacji).  
  
### <a name="customizing-enumeration-member-values"></a>Dostosowywanie wartości elementu członkowskiego wyliczenia  
 Można dostosować wartość elementu członkowskiego wyliczenia, która jest częścią kontraktu danych przy użyciu <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> właściwość <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.  
  
 Na przykład następujące kontraktu danych również jest odpowiednikiem z kontraktem danych `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Podczas serializacji wartości `PreviouslyOwned` jej reprezentacji XML `<condition>Used</condition>`.  
  
## <a name="simple-enumerations"></a>Proste wyliczenia  
 Można również serializacji typów wyliczenia, do którego <xref:System.Runtime.Serialization.DataContractAttribute> nie zastosowano atrybutu. Takie wyliczenie typy są traktowane dokładnie jak opisano wcześniej, z wyjątkiem każdy członek (, która nie ma <xref:System.NonSerializedAttribute> atrybut zastosowany) jest traktowana tak, jakby <xref:System.Runtime.Serialization.EnumMemberAttribute> zastosowano atrybut. Na przykład następujące wyliczenie niejawnie określono kontraktu danych odpowiednikiem poprzedniego `CarConditionEnum` przykład.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Można użyć prostego wyliczenia, gdy nie chcesz dostosować nazwy kontraktu danych wyliczenia i przestrzeni nazw i wartości elementu członkowskiego wyliczenia.  
  
#### <a name="notes-on-simple-enumerations"></a>Uwagi dotyczące prostego wyliczenia  
 Stosowanie <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut do prostych wyliczenia nie ma znaczenia.  
  
 Nie ma różnicy czy <xref:System.SerializableAttribute> atrybut jest stosowany do wyliczenia.  
  
 Fakt który <xref:System.Runtime.Serialization.DataContractSerializer> klasy uwzględniane są <xref:System.NonSerializedAttribute> atrybut zastosowany do elementy członkowskie wyliczenia różni się od zachowania <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Oba te serializatorów Ignoruj <xref:System.NonSerializedAttribute> atrybutu.  
  
## <a name="flag-enumerations"></a>Flaga wyliczenia  
 Możesz zastosować <xref:System.FlagsAttribute> atrybutu do wyliczenia. W takim przypadku listę zero lub więcej wartości wyliczenia mogą być wysyłane lub odbierane jednocześnie.  
  
 Aby to zrobić, należy zastosować <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu wyliczanie flag, a następnie Oznacz wszystkie elementy członkowskie, które są potęgami liczby dwa z <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu. Należy pamiętać, że aby użyć wyliczanie flag, postęp musi być nieprzerwaną sekwencji potęgami liczby 2 (na przykład 1, 2, 4, 8, 16, 32, 64).  
  
 Poniższe kroki dotyczą wysyłania wartości wyliczenia flagi:  
  
1.  Próba odnalezienia elementu członkowskiego wyliczenia (z <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut zastosowany) która jest mapowana na wartość liczbową. Jeśli znaleziono, Wyślij listę, która zawiera tylko ten element członkowski.  
  
2.  Próba Podziel wartość liczbową na sumę w taki sposób, że istnieją elementy członkowskie wyliczenia (każde z nich <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut zastosowany) mapowania każdej części suma. Wysyłanie listy wszystkich tych elementów członkowskich. Należy pamiętać, że *zachłanne algorytm* jest używana do znajdowania tych sum i w związku z tym nie ma gwarancji, że takie Suma zostanie znaleziony, nawet jeśli jest obecny. Aby uniknąć tego problemu, upewnij się, że wartości liczbowych elementy członkowskie wyliczenia są potęgami liczby dwa.  
  
3.  Jeśli dwa poprzednie kroki zakończyć się niepowodzeniem, a wartość liczbowa jest różna od zera, throw <xref:System.Runtime.Serialization.SerializationException>. Jeśli wartość liczbowa jest zero, należy wysłać pustej listy.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie wyliczenie można użyć w operacji flagi.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Następujące przykładowe wartości są serializowane wskazane.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
