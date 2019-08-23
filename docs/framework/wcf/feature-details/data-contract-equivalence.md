---
title: Równoważność kontraktów danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: 448c47d8687aa32671ade016f9b48cd763f87dfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945361"
---
# <a name="data-contract-equivalence"></a>Równoważność kontraktów danych
Aby Klient pomyślnie wysłał dane określonego typu do usługi lub usługa, która pomyślnie wyśle dane do klienta, wysłany typ nie musi istnieć na końcu odbioru. Jedyny wymóg polega na tym, że kontrakty danych obu typów są równoważne. (Czasami ścisła równoważność nie jest wymagana, zgodnie z opisem w sekcji [przechowywanie wersji kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)).  
  
 Aby Kontrakty danych były równoważne, muszą mieć tę samą przestrzeń nazw i nazwę. Ponadto każdy element członkowski danych na jednej stronie musi mieć odpowiedni element członkowski danych po drugiej stronie.  
  
 Aby elementy członkowskie danych były równoważne, muszą mieć taką samą nazwę. Ponadto muszą one reprezentować ten sam typ danych; oznacza to, że ich Kontrakty danych muszą być równoważne.  
  
> [!NOTE]
> Należy zauważyć, że nazwy kontraktu danych i przestrzenie nazw, a także nazwy składowych danych, w których jest rozróżniana wielkość liter.  
  
 Aby uzyskać więcej informacji na temat nazw kontraktów danych i przestrzeni nazw, a także nazw elementów członkowskich danych, zobacz [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Jeśli dwa typy znajdują się na tej samej stronie (nadawcy lub odbiornik), a ich Kontrakty danych nie są równoważne (na przykład mają różne elementy członkowskie danych), nie należy dawać im tej samej nazwy i przestrzeni nazw. Wykonanie tej operacji może spowodować wystąpienie wyjątków.  
  
 Kontrakty danych dla następujących typów są równoważne:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Kolejność elementów członkowskich danych i równoważności kontraktu danych  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> Użycie właściwości <xref:System.Runtime.Serialization.DataMemberAttribute> klasy może wpłynąć na równoważność kontraktu danych. Kontrakty danych muszą mieć elementy członkowskie, które są wyświetlane w tej samej kolejności, aby były równoważne. Kolejność domyślna jest alfabetyczna. Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Na przykład poniższy kod skutkuje odpowiednikiem umów dotyczących danych.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Niemniej jednak w przypadku tego samego kontraktu danych nie są zgodne.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Dziedziczenie, interfejsy i równoważność kontraktu danych  
 Podczas określania równoważności, kontrakt danych, który dziedziczy z innego kontraktu danych, jest traktowany jak w przypadku tylko jednego kontraktu danych, który zawiera wszystkie elementy członkowskie danych z typu podstawowego. Należy pamiętać, że kolejność elementów członkowskich danych musi być zgodna i składowe typu podstawowego poprzedzają elementy członkowskie typu pochodnego w kolejności. Ponadto, jeśli, jak w poniższym przykładzie kodu, dwa elementy członkowskie danych mają tę samą wartość kolejności, kolejność dla tych elementów członkowskich danych jest alfabetyczna. Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 W poniższym przykładzie kontrakt danych dla typu `Employee` jest odpowiednikiem kontraktu danych dla tego typu. `Worker`  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Podczas przekazywania parametrów i zwracanych wartości między klientem a usługą nie można wysyłać kontraktu danych z klasy bazowej, gdy punkt końcowy otrzymywania oczekuje kontraktu danych z klasy pochodnej. Jest to zgodne z założenia programowanie zorientowane obiektowo. W poprzednim przykładzie obiekt typu `Person` nie może być wysyłany, `Employee` gdy jest oczekiwany.  
  
 Kontrakt danych z klasy pochodnej może być wysyłany, gdy oczekiwano kontraktu danych z klasy bazowej, ale tylko wtedy, gdy punkt końcowy odbioru "wie" typu pochodnego przy użyciu <xref:System.Runtime.Serialization.KnownTypeAttribute>. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). W poprzednim przykładzie obiekt typu `Employee` może być wysyłany, `Person` gdy jest oczekiwany, ale tylko wtedy, gdy kod <xref:System.Runtime.Serialization.KnownTypeAttribute> odbiorcy wykorzystuje do dołączenia do listy znanych typów.  
  
 W przypadku przekazywania parametrów i zwracanych wartości między aplikacjami, jeśli oczekiwany typ jest interfejsem, jest równoważne oczekiwanemu typowi <xref:System.Object>typu. Ze względu na to, <xref:System.Object>że każdy typ ostatecznie pochodzi od, każdy kontrakt danych ostatecznie <xref:System.Object>pochodzi z kontraktu danych dla. W ten sposób każdy typ kontraktu danych może zostać przesłany, gdy oczekiwany jest interfejs. Dodatkowe kroki są wymagane do pomyślnej pracy z interfejsami; Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Znane typy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
