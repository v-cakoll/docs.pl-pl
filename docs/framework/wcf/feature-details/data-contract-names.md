---
title: Nazwy kontraktów danych
description: Odkryj reguły nazewnictwa kontraktu danych i elementów członkowskich oraz domyślne zachowanie infrastruktury WCF, które obsługują komunikację przy użyciu równoważnych umów dotyczących danych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 85c533d683558520d46f259db0bdb34dcb1214c9
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247406"
---
# <a name="data-contract-names"></a>Nazwy kontraktów danych

Czasami klient i usługa nie mają tego samego typu. Mogą nadal przekazywać dane do siebie, o ile Kontrakty danych są równoważne obu stronom. [Równoważność kontraktu danych](data-contract-equivalence.md) opiera się na kontraktach danych i nazwach elementów członkowskich, w związku z czym mechanizm jest dostarczany do mapowania typów i składowych tych nazw. W tym temacie opisano reguły nazewnictwa kontraktów danych oraz domyślne zachowanie infrastruktury Windows Communication Foundation (WCF) podczas tworzenia nazw.

## <a name="basic-rules"></a>Podstawowe reguły
Podstawowe reguły dotyczące określania nazw umów dotyczących danych obejmują:

- W pełni kwalifikowana nazwa kontraktu danych składa się z przestrzeni nazw i nazwy.

- Składowe danych mają tylko nazwy, ale nie przestrzenie nazw.

- Podczas przetwarzania kontraktów danych Infrastruktura WCF jest uwzględniana w przypadku przestrzeni nazw oraz nazw kontraktów danych i elementów członkowskich danych.

## <a name="data-contract-namespaces"></a>Przestrzenie nazw kontraktu danych
Przestrzeń nazw kontraktu danych przyjmuje formę Uniform Resource Identifier (URI). Identyfikator URI może być bezwzględny lub względny. Domyślnie Kontrakty danych dla określonego typu są przypisane do przestrzeni nazw, która pochodzi z przestrzeni nazw środowiska uruchomieniowego języka wspólnego (CLR) tego typu.

Domyślnie wszystkie określone przestrzenie nazw środowiska CLR (w formacie *CLR. Namespace*) są mapowane do przestrzeni nazw `http://schemas.datacontract.org/2004/07/Clr.Namespace` . Aby zastąpić to ustawienie domyślne, Zastosuj <xref:System.Runtime.Serialization.ContractNamespaceAttribute> atrybut do całego modułu lub zestawu. Alternatywnie, aby kontrolować przestrzeń nazw kontraktu danych dla każdego typu, należy ustawić <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> Właściwość <xref:System.Runtime.Serialization.DataContractAttribute> .

> [!NOTE]
> `http://schemas.microsoft.com/2003/10/Serialization`Przestrzeń nazw jest zarezerwowana i nie może być używana jako przestrzeń nazw kontraktu danych.

> [!NOTE]
> Nie można zastąpić domyślnej przestrzeni nazw w typach kontraktu danych, które zawierają `delegate` deklaracje.

## <a name="data-contract-names"></a>Nazwy kontraktów danych
Domyślną nazwą kontraktu danych dla danego typu jest nazwa tego typu. Aby zastąpić wartość domyślną, należy ustawić <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> Właściwość <xref:System.Runtime.Serialization.DataContractAttribute> na nazwę alternatywną. Reguły specjalne dla typów ogólnych są opisane w sekcji "nazwy kontraktów danych dla typów ogólnych" w dalszej części tego tematu.

## <a name="data-member-names"></a>Nazwy elementów członkowskich danych
Domyślną nazwą elementu członkowskiego danych dla danego pola lub właściwości jest nazwa tego pola lub właściwości. Aby zastąpić domyślny, ustaw <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> Właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> na wartość alternatywną.

### <a name="examples"></a>Przykłady
Poniższy przykład pokazuje, jak można zastąpić domyślne zachowanie nazewnictwa kontraktów danych i elementów członkowskich danych.

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a>Nazwy kontraktów danych dla typów ogólnych
Istnieją specjalne reguły określania nazw kontraktów danych dla typów ogólnych. Te reguły pomagają uniknąć kolizji nazw kontraktu danych między dwoma zamkniętymi rodzajami ogólnymi tego samego typu ogólnego.

Domyślnie nazwa kontraktu danych dla typu ogólnego jest nazwą typu, po którym następuje ciąg "z", po którym następuje nazwa kontraktu danych parametrów ogólnych, a następnie *skrót* obliczony przy użyciu przestrzeni nazw kontraktu danych parametrów ogólnych. Skrót jest wynikiem funkcji matematycznej, która pełni rolę "odcisku palca", która jednoznacznie identyfikuje fragment danych. Gdy wszystkie parametry ogólne są typami pierwotnymi, skrót zostanie pominięty.

Na przykład, zobacz typy w poniższym przykładzie.

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

W tym przykładzie typ `Drawing<Square,RegularRedBrush>` ma nazwę kontraktu danych "DrawingOfSquareRedBrush5HWGAU6h", gdzie "5HWGAU6h" jest skrótem przestrzeni nazw "urn: Shapes" i "urn: default". Typ `Drawing<Square,SpecialRedBrush>` ma nazwę kontraktu danych "DrawingOfSquareRedBrushjpB5LgQ_S", gdzie "jpB5LgQ_S" jest skrótem przestrzeni nazw "urn: Shapes" i "urn: Special". Należy pamiętać, że jeśli skrót nie jest używany, te dwie nazwy są identyczne i w rezultacie występuje kolizja nazw.

## <a name="customizing-data-contract-names-for-generic-types"></a>Dostosowywanie nazw kontraktów danych dla typów ogólnych

Czasami nazwy kontraktów danych wygenerowane dla typów ogólnych, jak opisano wcześniej, są nieakceptowalne. Na przykład może być wiadomo, że nie będziesz mieć do kolizji nazw i może być konieczne usunięcie skrótu. W takim przypadku można użyć <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> właściwości, aby określić inny sposób generowania nazw. Możesz użyć liczb w nawiasach klamrowych wewnątrz właściwości, `Name` Aby odwołać się do nazw kontraktu danych parametrów ogólnych. (0 oznacza pierwszy parametr, 1 odnosi się do drugiego itd.) Możesz użyć numeru (#) w nawiasach klamrowych, aby odwołać się do skrótu. Można użyć każdego z tych odwołań wiele razy lub wcale.

Na przykład poprzedni `Drawing` typ ogólny mógł zostać zadeklarowany, jak pokazano w poniższym przykładzie.

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

W takim przypadku typ `Drawing<Square,RegularRedBrush>` ma nazwę kontraktu danych "Drawing_using_RedBrush_brush_and_Square_shape". Należy zauważyć, że ze względu na to, że w właściwości występuje "{#}" <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> , skrót nie jest częścią nazwy i w związku z tym typ jest podatny na kolizje nazw, na przykład typ `Drawing<Square,SpecialRedBrush>` będzie miał dokładnie taką samą nazwę kontraktu danych.

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [Używanie kontraktów danych](using-data-contracts.md)
- [Równoważność kontraktów danych](data-contract-equivalence.md)
- [Nazwy kontraktów danych](data-contract-names.md)
- [Przechowywanie wersji kontraktów danych](data-contract-versioning.md)
