---
title: "Nazwy kontraktów danych"
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
helpviewer_keywords: data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da7cb5e30cd4c8c5bf59c45b5e38d766990275b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="data-contract-names"></a>Nazwy kontraktów danych
Czasami klientem a usługą nie mają takich samych typach. One nadal przekazują dane do siebie, tak długo, jak kontraktów danych są równoważne po obu stronach. [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md) opiera się na kontrakt danych i nazwy elementów członkowskich danych, i w związku z tym mechanizm jest dostępne do mapowania typów i członków tych nazw. W tym temacie opisano reguły dotyczące nazw kontraktów danych, a także domyślne zachowanie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infrastruktury podczas tworzenia nazwy.  
  
## <a name="basic-rules"></a>Podstawowe zasady  
 Podstawowe zasady dotyczące nazewnictwa dane, które obejmują kontraktów:  
  
-   Nazwa kontraktu danych pełni kwalifikowanymi składa się z przestrzeni nazw i nazwę.  
  
-   Elementy członkowskie danych mają tylko nazwy, ale nie przestrzeni nazw.  
  
-   Podczas przetwarzania kontraktów danych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury jest rozróżniana wielkość liter, zarówno w przestrzeni nazw, jak i nazwy kontraktów danych i elementy członkowskie danych.  
  
## <a name="data-contract-namespaces"></a>Przestrzeni nazw kontraktów danych  
 Przestrzeń nazw kontraktu danych ma postać z zasobów identyfikator URI (Uniform). Identyfikator URI może być bezwzględny lub względny. Domyślnie kontraktów danych dla określonego typu są przypisywane przestrzeni nazw, która pochodzi z wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) przestrzeni nazw tego typu.  
  
 Domyślnie w danej przestrzeni nazw CLR (w formacie *Clr.Namespace*) jest zamapowany do przestrzeni nazw "http://schemas.datacontract.org/2004/07/Clr.Namespace". Aby zastąpić to ustawienie domyślne, należy zastosować <xref:System.Runtime.Serialization.ContractNamespaceAttribute> atrybutu cały moduł lub zestaw. Alternatywnie w celu kontroli przestrzeń nazw kontraktu danych dla każdego typu należy ustawić <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> właściwość <xref:System.Runtime.Serialization.DataContractAttribute>.  
  
> [!NOTE]
>  Przestrzeń nazw "http://schemas.microsoft.com/2003/10/Serialization" jest zarezerwowany i nie można użyć jako przestrzeń nazw kontraktu danych.  
  
> [!NOTE]
>  Nie można zastąpić domyślną przestrzeń nazw w typach kontraktu danych, które zawierają `delegate` deklaracji.  
  
## <a name="data-contract-names"></a>Nazwy kontraktów danych  
 Domyślna nazwa kontraktu danych dla danego typu jest nazwą danego typu. Aby zastąpić domyślną, ustaw <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> właściwość <xref:System.Runtime.Serialization.DataContractAttribute> do alternatywnej nazwy. Reguły specjalne dla typów ogólnych opisanym w "Typy kontraktu danych nazwy dla ogólnego" w dalszej części tego tematu.  
  
## <a name="data-member-names"></a>Nazwy elementów członkowskich danych  
 Nazwa domyślnego elementu członkowskiego danych dla danego pola lub właściwości jest nazwa tego pola lub właściwości. Aby zastąpić domyślną, ustaw <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> alternatywną wartość.  
  
### <a name="examples"></a>Przykłady  
 W poniższym przykładzie pokazano, jak można zastąpić domyślną nazw kontraktów danych i elementy członkowskie danych.  
  
 [!code-csharp[C_DataContractNames#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
 [!code-vb[C_DataContractNames#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]  
  
## <a name="data-contract-names-for-generic-types"></a>Nazwy kontraktów danych do typów ogólnych  
 Reguły specjalne istnieje określania nazwy kontraktów danych do typów ogólnych. Te reguły uniknąć konfliktów nazw kontraktu danych między dwa ogólne zamkniętego tego samego typu ogólnego.  
  
 Domyślnie nazwa kontraktu danych dla typu ogólnego jest nazwa typu, a następnie ciąg "", a następnie według nazwy kontraktów danych ogólnych parametrów, a następnie *skrótu* obliczane przy użyciu przestrzeni nazw kontraktów danych z Parametry ogólne. Skrót jest wynikiem funkcji matematycznych, która działa jako "odcisk palca" który unikatowo identyfikuje element danych. Gdy wszystkie parametry ogólne są typy pierwotne, skrót zostanie pominięty.  
  
 Na przykład Zobacz typy w poniższym przykładzie.  
  
 [!code-csharp[C_DataContractNames#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
 [!code-vb[C_DataContractNames#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]  
  
 W tym przykładzie typ `Drawing<Square,RegularRedBrush>` ma nazwę kontraktu danych "DrawingOfSquareRedBrush5HWGAU6h", gdzie "5HWGAU6h" to skrót przestrzeni nazw "urn: kształty" i "urn: domyślny". Typ `Drawing<Square,SpecialRedBrush>` ma nazwę kontraktu danych "DrawingOfSquareRedBrushjpB5LgQ_S", gdzie "jpB5LgQ_S" to skrót "urn: kształty" i przestrzeni nazw "urn: special". Zauważ, że jeśli skrót nie jest używany, dwie nazwy są identyczne, i w związku z tym występuje kolizja nazw.  
  
## <a name="customizing-data-contract-names-for-generic-types"></a>Dostosowywanie nazwy kontraktów danych do typów ogólnych  
 Czasami nazwy kontraktów danych, które są generowane dla typów ogólnych, jak opisano wcześniej, jest nie do przyjęcia. Na przykład może znasz z wyprzedzeniem nie zostaną uruchomione w konflikty nazw i może być konieczne usunięcie skrót. W takim przypadku można użyć <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> właściwość `DataContractAttribute` atrybutu, aby określić inną metodę generowania nazw. Liczby można użyć w nawiasach klamrowych wewnątrz `Name` właściwości odwoływać się do danych nazwy parametrów ogólnych. (0 odnosi się do pierwszego parametru, 1 odwołuje się do drugiego i tak dalej). Można użyć znaku numeru (#) wewnątrz nawiasów klamrowych do odwoływania się do skrótu. Można użyć każdego z tych wiele razy lub wcale.  
  
 Na przykład poprzedniego ogólnego `Drawing` typu można zadeklarowano jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[c_DataContractNames#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
 [!code-vb[c_DataContractNames#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]  
  
 W takim przypadku typ `Drawing<Square,RegularRedBrush>` o nazwie kontraktu danych "Drawing_using_RedBrush_brush_and_Square_shape". Należy pamiętać, że ponieważ brakuje "{#}" w <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> właściwości, skrót nie jest częścią nazwy, a w związku z tym typem jest podatny na nazewnictwa kolizji, na przykład typ `Drawing<Square,SpecialRedBrush>` musi dokładnie takiej samej nazwie kontraktu danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.ContractNamespaceAttribute>  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
