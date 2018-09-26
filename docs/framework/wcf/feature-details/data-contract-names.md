---
title: Nazwy kontraktów danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: cd878452f3ec99627507334a26873a004e5b5314
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47072530"
---
# <a name="data-contract-names"></a>Nazwy kontraktów danych

Czasami klienta, jak i usługi nie mają te same typy. Można nadal przekazują dane ze sobą tak długo, jak kontrakty danych są równoważne po obu stronach. [Równoważność kontraktów danych](data-contract-equivalence.md) opiera się na kontrakt danych i nazwy elementów członkowskich danych, i w związku z tym mechanizm jest dostarczany do mapowania typów i elementów członkowskich tych nazw. W tym temacie opisano reguły dotyczące nazw kontraktów danych, a także domyślne zachowanie infrastruktury usług Windows Communication Foundation (WCF), podczas tworzenia nazwy.

## <a name="basic-rules"></a>Podstawowe zasady
Podstawowe zasady dotyczące nazewnictwa dane, które obejmują zamówień:

- Nazwa kontraktu danych w pełni kwalifikowaną składa się z przestrzeni nazw i nazwę.

- Elementy członkowskie danych mają tylko nazwy, ale nie przestrzeni nazw.

- Podczas przetwarzania kontraktów danych, infrastruktura WCF jest rozróżniana wielkość liter do przestrzeni nazw i nazwy kontraktów danych i elementy członkowskie danych.

## <a name="data-contract-namespaces"></a>Przestrzenie nazw kontraktu danych
Przestrzeń nazw kontraktu danych ma postać z jednolite zasobów identyfikator (URI). Identyfikator URI może być bezwzględny lub względny. Domyślnie kontraktów danych do określonego typu są przypisywane przestrzeni nazw, który pochodzi z wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) przestrzeń nazw tego typu.

Domyślnie w dowolnym danym przestrzeń nazw środowiska CLR (w formacie *Clr.Namespace*) jest zamapowana na przestrzeń nazw `http://schemas.datacontract.org/2004/07/Clr.Namespace`. Aby zastąpić to ustawienie domyślne, zastosuj <xref:System.Runtime.Serialization.ContractNamespaceAttribute> atrybutu cały moduł lub zestawu. Alternatywnie, aby kontrolować przestrzeń nazw kontraktu danych dla każdego typu, należy ustawić <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> właściwość <xref:System.Runtime.Serialization.DataContractAttribute>.

> [!NOTE]
> `http://schemas.microsoft.com/2003/10/Serialization` Przestrzeni nazw jest zarezerwowany i nie można użyć jako przestrzeń nazw kontraktu danych.

> [!NOTE]
> Nie można zastąpić domyślny obszar nazw w typy kontraktu danych, które zawierają `delegate` deklaracji.

## <a name="data-contract-names"></a>Nazwy kontraktów danych
Domyślna nazwa kontraktu danych dla danego typu jest nazwą tego typu. Aby zastąpić domyślne, należy ustawić <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> właściwość <xref:System.Runtime.Serialization.DataContractAttribute> do alternatywnej nazwy. Reguły specjalne dla typów ogólnych są opisane w "Typy kontraktu danych nazwy dla ogólnego" w dalszej części tego tematu.

## <a name="data-member-names"></a>Nazwy elementów członkowskich danych
Nazwa domyślny element członkowski danych dla określonego pola lub właściwości jest nazwa tego pola lub właściwości. Aby zastąpić domyślne, należy ustawić <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> alternatywne wartości.

### <a name="examples"></a>Przykłady
Poniższy przykład pokazuje, jak można zastąpić domyślny nazewnictwa zachowanie kontraktów danych i elementy członkowskie danych.

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a>Nazwy kontraktów danych do typów ogólnych
Istnieją specjalne reguły dla określania nazwy kontraktów danych do typów ogólnych. Te zasady pomagają uniknąć konfliktów nazw kontraktu danych między dwa ogólne zamknięte tego samego typu ogólnego.

Domyślnie, Nazwa kontraktu danych dla typu ogólnego jest nazwą typu, w którym następuje ciąg "", a następnie nazwy kontraktów danych ogólnych parametrów, a następnie *skrótu* obliczane przy użyciu przestrzeni nazw kontraktu danych z Parametry ogólne. Skrót jest wynikiem funkcji matematycznych, który działa jako "odciskiem palca" który unikatowo identyfikuje element danych. W przypadku wszystkich parametrów ogólnych typów pierwotnych, skrót zostanie pominięty.

Na przykład wyświetlić typy w poniższym przykładzie.

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

W tym przykładzie typ `Drawing<Square,RegularRedBrush>` ma nazwie kontraktu danych "DrawingOfSquareRedBrush5HWGAU6h", gdzie "5HWGAU6h" to skrót przestrzeni nazw "urn: kształty" i "urn: default". Typ `Drawing<Square,SpecialRedBrush>` ma nazwie kontraktu danych "DrawingOfSquareRedBrushjpB5LgQ_S", gdzie "jpB5LgQ_S" to skrót "urn: kształty" i przestrzeni nazw "urn: specjalne". Należy pamiętać, że jeśli skrót nie jest używany, dwie nazwy są identyczne i dlatego występuje kolizja nazw.

## <a name="customizing-data-contract-names-for-generic-types"></a>Dostosowywanie nazwy kontraktów danych do typów ogólnych

Czasami nazwy kontraktu danych, które są generowane dla typów ogólnych, jak opisano wcześniej, są nie do przyjęcia. Na przykład może znasz wcześniej nie będzie działać do konfliktów nazw, a następnie usunąć wartości mieszania. W takim przypadku można użyć <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> właściwość `DataContractAttribute` atrybutu, aby określić inny sposób na potrzeby generowania nazw. Liczby można użyć w nawiasach klamrowych wewnątrz `Name` właściwości do odwoływania się do danych kontraktu nazwy parametrów ogólnych. (0, który odnosi się do pierwszego parametru, 1, który odwołuje się do drugiej i tak dalej). Znak numeru (#) wewnątrz nawiasów klamrowych służy do odwoływania się do mieszania. Możesz użyć każdej z tych odwołań wiele razy lub wcale.

Na przykład poprzednim ogólny `Drawing` typu można zadeklarowano jak pokazano w poniższym przykładzie.

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

W tym przypadku typ `Drawing<Square,RegularRedBrush>` o nazwie kontraktu danych "Drawing_using_RedBrush_brush_and_Square_shape". Należy pamiętać, że ponieważ "{#}" w <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> właściwości skrót nie jest częścią nazwy, i dlatego typu są podatne na nazewnictwa kolizji, na przykład typ `Drawing<Square,SpecialRedBrush>` musi dokładnie takiej samej nazwie kontraktu danych.

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [Używanie kontraktów danych](using-data-contracts.md)
- [Równoważność kontraktów danych](data-contract-equivalence.md)
- [Nazwy kontraktów danych](data-contract-names.md)
- [Przechowywanie wersji kontraktów danych](data-contract-versioning.md)