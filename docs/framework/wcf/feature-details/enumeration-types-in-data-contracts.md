---
title: Typy wyliczeniowe w kontraktach danych
description: Dowiedz się, jak model kontraktu danych wyraża Wyliczenie w ramach modelu programowania WFC.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: ff3184a285e88d47d4545a38a6c74b2f209827fb
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247302"
---
# <a name="enumeration-types-in-data-contracts"></a>Typy wyliczeniowe w kontraktach danych
Wyliczenia mogą być wyrażone w modelu kontraktu danych. Ten temat zawiera kilka przykładów objaśniających model programowania.  
  
## <a name="enumeration-basics"></a>Podstawowe informacje dotyczące wyliczania  
 Jednym ze sposobów używania typów wyliczeniowych w modelu kontraktu danych jest zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu do typu. Następnie należy zastosować <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut do każdego elementu członkowskiego, który musi być uwzględniony w umowie dotyczącej danych.  
  
 Poniższy przykład przedstawia dwie klasy. Pierwszy używa wyliczenia, a drugi definiuje wyliczenie.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Wystąpienie `Car` klasy może być wysyłane lub odbierane tylko wtedy, gdy `condition` pole jest ustawione na jedną z wartości `New` , `Used` lub `Rental` . Jeśli `condition` jest `Broken` generowane lub `Stolen` , <xref:System.Runtime.Serialization.SerializationException> jest generowany.  
  
 Można użyć <xref:System.Runtime.Serialization.DataContractAttribute> właściwości ( <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> i <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> ) jako zwykłych dla kontraktów danych wyliczenia.  
  
### <a name="enumeration-member-values"></a>Wartości elementu członkowskiego wyliczenia  
 Ogólnie rzecz biorąc kontrakt dotyczący danych zawiera nazwy elementów członkowskich wyliczenia, a nie wartości numeryczne. Jednak w przypadku korzystania z modelu kontraktu danych, jeśli strona otrzymująca jest klientem WCF, wyeksportowany schemat zachowuje wartości liczbowe. Należy zauważyć, że nie jest to przypadek w przypadku używania [klasy XmlSerializer](using-the-xmlserializer-class.md).  
  
 W poprzednim przykładzie, jeśli `condition` jest ustawiona na, `Used` a dane są serializowane do kodu XML, otrzymany kod XML to, `<condition>Used</condition>` a nie `<condition>1</condition>` . W związku z tym następująca umowa dotycząca danych jest równoznaczna z umową danych `CarConditionEnum` .  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Na przykład można użyć po `CarConditionEnum` stronie wysyłającej i po `CarConditionWithNumbers` stronie odbiorczej. Mimo że po stronie wysyłającej jest stosowana wartość "1" `Used` , a po stronie otrzymującej jest stosowana wartość "20", Reprezentacja XML jest `<condition>Used</condition>` dla obu stron.  
  
 Aby uwzględnić je w kontrakcie danych, należy zastosować <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut. W .NET Framework można zawsze zastosować specjalną wartość 0 (zero) do wyliczenia, która jest również wartością domyślną dla dowolnego wyliczenia. Jednak nawet tej specjalnej wartości zerowej nie można serializować, chyba że jest oznaczona przy użyciu <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.  
  
 Istnieją dwa wyjątki:  
  
- Wyliczenia flag (omówione w dalszej części tego tematu).  
  
- Elementy członkowskie danych wyliczenia z <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> właściwością ustawioną na `false` (w takim przypadku Wyliczenie o wartości zero jest pomijane w przypadku serializowanych danych).  
  
### <a name="customizing-enumeration-member-values"></a>Dostosowywanie wartości elementów członkowskich wyliczenia  
 Można dostosować wartość elementu członkowskiego wyliczenia, który stanowi część kontraktu danych przy użyciu <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> właściwości <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.  
  
 Na przykład następująca umowa dotycząca danych jest również równoważna z kontraktem danych `CarConditionEnum` .  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Podczas serializacji wartość `PreviouslyOwned` ma reprezentację XML `<condition>Used</condition>` .  
  
## <a name="simple-enumerations"></a>Proste wyliczenia  
 Można również serializować typy wyliczeniowe, do których <xref:System.Runtime.Serialization.DataContractAttribute> atrybut nie został zastosowany. Takie typy wyliczeniowe są traktowane dokładnie zgodnie z wcześniejszym opisem, z tą różnicą, że każdy element członkowski (który nie ma <xref:System.NonSerializedAttribute> zastosowania atrybutu) jest traktowany jak gdyby <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut został zastosowany. Na przykład następujące Wyliczenie niejawnie ma umowę danych odpowiadającą poprzedniemu `CarConditionEnum` przykładowi.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Można użyć prostych wyliczeń, gdy nie trzeba dostosowywać nazwy i przestrzeni nazw kontraktu danych wyliczenia oraz wartości elementów członkowskich wyliczenia.  
  
#### <a name="notes-on-simple-enumerations"></a>Uwagi dotyczące prostych wyliczeń  
 Zastosowanie <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu do prostych wyliczeń nie ma żadnego wpływu.  
  
 Nie ma żadnej różnicy niezależnie od tego, czy <xref:System.SerializableAttribute> atrybut jest stosowany do wyliczenia.  
  
 Fakt, że <xref:System.Runtime.Serialization.DataContractSerializer> Klasa uznaje <xref:System.NonSerializedAttribute> atrybut zastosowany do elementów członkowskich wyliczenia, różni się od zachowania <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . Oba te serializatory ignorują <xref:System.NonSerializedAttribute> atrybut.  
  
## <a name="flag-enumerations"></a>Wyliczenia flag  
 Można zastosować <xref:System.FlagsAttribute> atrybut do wyliczenia. W takim przypadku można jednocześnie wysłać lub odebrać listę wartości wyliczenia zero lub więcej.  
  
 W tym celu należy zastosować <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do wyliczenia flag, a następnie oznaczyć wszystkie elementy członkowskie, które mają uprawnienia dwóch przy użyciu <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu. Należy pamiętać, że aby użyć wyliczenia flag, postęp musi być nieprzerwaną sekwencją uprawnień 2 (na przykład 1, 2, 4, 8, 16, 32, 64).  
  
 Poniższe kroki dotyczą wysyłania wartości wyliczenia flagi:  
  
1. Próba znalezienia elementu członkowskiego wyliczenia (z <xref:System.Runtime.Serialization.EnumMemberAttribute> zastosowanym atrybutem), który jest mapowany na wartość liczbową. Jeśli zostanie znaleziona, Wyślij listę zawierającą tylko ten element członkowski.  
  
2. Podjęto próbę przerwania wartości liczbowej w sumie, w taki sposób, że istnieją elementy członkowskie wyliczenia (z których każdy ma <xref:System.Runtime.Serialization.EnumMemberAttribute> przypisany atrybut), które są mapowane na każdą część sum. Wyślij listę wszystkich tych członków. Należy zauważyć, że *algorytm zachłanne* jest używany do znajdowania takich sum i dlatego nie ma gwarancji, że taka suma jest znaleziona, nawet jeśli jest obecna. Aby uniknąć tego problemu, upewnij się, że wartości liczbowe elementów członkowskich wyliczenia to uprawnienia dwóch.  
  
3. Jeśli powyższe dwa kroki zakończą się niepowodzeniem, a wartość liczbowa jest różna od zera, throw a <xref:System.Runtime.Serialization.SerializationException> . Jeśli wartość liczbowa jest równa zero, Wyślij pustą listę.  
  
### <a name="example"></a>Przykład  
 W operacji flagi można użyć następującego przykładu wyliczenia.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Następujące przykładowe wartości są serializowane zgodnie z podanym opisem.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Używanie kontraktów danych](using-data-contracts.md)
- [Określanie transferu danych w kontraktach usług](specifying-data-transfer-in-service-contracts.md)
