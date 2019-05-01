---
title: Typy wyliczeniowe w kontraktach danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: 1837a3630424ff2a9ee4a84e9ed63f44a06bbecf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856443"
---
# <a name="enumeration-types-in-data-contracts"></a>Typy wyliczeniowe w kontraktach danych
Wyliczenia mogą być wyrażone w modelu kontraktu danych. W tym temacie przedstawiono kilka przykładów, które opisują modelu programowania.  
  
## <a name="enumeration-basics"></a>Podstawowe informacje dotyczące wyliczenia  
 Jeden ze sposobów użycia Typy wyliczeniowe w modelu kontraktu danych stosuje się <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu. Następnie należy zastosować <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu do każdego elementu członkowskiego, które muszą być zawarte w umowie dotyczącej danych.  
  
 Poniższy przykład pokazuje dwóch klas. Pierwszy używa wyliczenia, a druga definiuje wyliczenia.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Wystąpienie `Car` klasy, które mogą być wysyłane lub odbierane tylko wtedy, gdy `condition` pole jest ustawione na jedną z wartości `New`, `Used`, lub `Rental`. Jeśli `condition` jest `Broken` lub `Stolen`, <xref:System.Runtime.Serialization.SerializationException> zgłaszany.  
  
 Możesz użyć <xref:System.Runtime.Serialization.DataContractAttribute> właściwości (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> i <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) dla kontraktów danych wyliczenia.  
  
### <a name="enumeration-member-values"></a>Wartości elementów członkowskich wyliczenia  
 Ogólnie kontraktu danych zawiera nazwy elementów członkowskich wyliczenia, nie wartości liczbowe. Jednak korzystając z modelu kontraktu danych, jeśli po stronie odbierającej jest klienta WCF, wyeksportowanego schematu zachowuje wartości liczbowe. Należy pamiętać, że nie jest wymagane przy użyciu [przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
 W poprzednim przykładzie Jeśli `condition` ustawiono `Used` i danych jest serializowany do pliku XML, wynikowy kod XML jest `<condition>Used</condition>` i nie `<condition>1</condition>`. W związku z tym, następujące kontraktu danych odpowiada kontrakt danych `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Na przykład, można użyć `CarConditionEnum` po stronie wysyłania i `CarConditionWithNumbers` po stronie odbierającej. Chociaż po stronie wysyłającej korzysta z wartości "1" dla `Used` i używa po stronie odbierania, wartość "20" reprezentację XML jest `<condition>Used</condition>` dla obu stron.  
  
 Do uwzględnienia w kontraktu danych, należy najpierw zastosować <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu. W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], zawsze stosować specjalna wartość 0 (zero) do wyliczenia, która jest również wartością domyślną dla dowolnego wyliczenia. Jednak nawet ten specjalny odcinek serii nie można serializować wartość zero, chyba że jest on oznaczony wartością <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.  
  
 Istnieją dwa wyjątki od tej reguły:  
  
- Flaga wyliczenia (zostało to omówione w dalszej części tego tematu).  
  
- Elementy członkowskie danych wyliczenia z <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> właściwością `false` (w którym to przypadku wyliczenie o wartości zero jest pominięty z serializowanych danych).  
  
### <a name="customizing-enumeration-member-values"></a>Dostosowywanie wartości elementu członkowskiego wyliczenia  
 Można dostosować wartość elementu członkowskiego wyliczenia, która jest częścią kontraktu danych za pomocą <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> właściwość <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.  
  
 Na przykład, poniższy kontraktu danych również jest odpowiednikiem kontrakt danych `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Gdy serializowany wartość `PreviouslyOwned` jej reprezentacji XML `<condition>Used</condition>`.  
  
## <a name="simple-enumerations"></a>Proste wyliczenia  
 Typy wyliczeniowe, do której może serializować <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu nie zostały zastosowane. Wyliczenie, takie typy są traktowane jako dokładnie tak jak opisano wcześniej, chyba że każdy element członkowski (które nie mają <xref:System.NonSerializedAttribute> zastosowany) jest traktowana tak, jakby <xref:System.Runtime.Serialization.EnumMemberAttribute> zastosowano atrybut. Na przykład, poniższy wyliczenie niejawnie określono kontraktu danych odpowiednikiem poprzedniego `CarConditionEnum` przykład.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Można użyć prostego wyliczenia, kiedy nie trzeba dostosować wyliczenia samej nazwie kontraktu danych i przestrzeni nazw i wartości elementów członkowskich wyliczenia.  
  
#### <a name="notes-on-simple-enumerations"></a>Uwagi dotyczące prostego wyliczenia  
 Stosowanie <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut do prostych wyliczenia nie ma znaczenia.  
  
 Nie ma znaczenia czy <xref:System.SerializableAttribute> atrybut jest stosowany do wyliczenia.  
  
 Fakt, <xref:System.Runtime.Serialization.DataContractSerializer> klasy uwzględniane <xref:System.NonSerializedAttribute> zastosowany do elementów członkowskich wyliczenia różni się od zachowania <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Oba te serializatory Ignoruj <xref:System.NonSerializedAttribute> atrybutu.  
  
## <a name="flag-enumerations"></a>Flagi wyliczeń  
 Można zastosować <xref:System.FlagsAttribute> atrybutu do wyliczenia. W takim przypadku listę zero lub więcej wartości wyliczenia mogą być wysyłane lub odbierane jednocześnie.  
  
 Aby to zrobić, należy zastosować <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu do wyliczenia flag, a następnie Oznacz wszystkie elementy członkowskie z potęgi liczb z <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu. Należy pamiętać, że można używać wyliczenia flag, postęp musi być nieprzerwaną sekwencji potęgi 2 (na przykład 1, 2, 4, 8, 16, 32, 64).  
  
 Poniższe kroki dotyczą wysyłania wartość wyliczenia flag:  
  
1. Próba odnalezienia elementu członkowskiego wyliczenia (przy użyciu <xref:System.Runtime.Serialization.EnumMemberAttribute> zastosowany) która jest mapowana na wartość liczbową. Jeśli znaleziono, wysłać listę, która zawiera tylko ten element członkowski.  
  
2. Próbują przerwać wartość liczbowa do sumy w taki sposób, że istnieją elementy członkowskie wyliczenia (każdy z <xref:System.Runtime.Serialization.EnumMemberAttribute> zastosowany) mapowania każda część sumy. Wysyłanie listy wszystkich tych elementów członkowskich. Należy pamiętać, że *zachłanne algorytm* jest używana do znajdowania to suma, i w związku z tym nie ma żadnej gwarancji, który takiej sumy zostanie znaleziony, nawet jeśli jest obecny. Aby uniknąć tego problemu, upewnij się, czy uprawnień z dwóch wartości liczbowych elementów członkowskich wyliczenia.  
  
3. Jeśli dwa poprzednie kroki zakończyć się niepowodzeniem, a wartość liczbowa jest różna od zera, throw <xref:System.Runtime.Serialization.SerializationException>. Jeśli wartość liczbowa jest wartość zero, należy wysłać pustej listy.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie wyliczenie może służyć w ramach operacji flagi.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Następujące przykładowe wartości są serializowane, jak wskazano.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
