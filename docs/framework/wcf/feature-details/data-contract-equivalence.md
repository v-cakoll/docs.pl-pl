---
title: Równoważność kontraktów danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: a526a58ef801e91775756e6a84a94a066d32d284
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857236"
---
# <a name="data-contract-equivalence"></a>Równoważność kontraktów danych
Klient pomyślnie wysyłać danych określonego typu usługi lub Usługa pomyślnie wysyłać dane do klienta wysłane typu nie zawsze musi istnieć po stronie odbiorczej. Jedynym wymaganiem jest równoważne kontraktów danych obu typów. (Czasami równoważności ograniczeniami nie jest wymagane, zgodnie z opisem w [przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Dla kontraktów danych jako równoważne muszą mieć ten sam obszar nazw i nazwę. Ponadto każdy element członkowski danych na jednej stronie musi mieć element członkowski danych równoważne z drugiej strony.  
  
 Składowych danych jako równoważne muszą mieć taką samą nazwę. Ponadto musi reprezentować ten sam typ danych. oznacza to musi być równoważna ich kontraktów danych.  
  
> [!NOTE]
>  Należy pamiętać, że kontraktu danych, nazwy i przestrzenie nazw, a także nazwy elementów członkowskich danych, jest rozróżniana wielkość liter.  
  
 Aby uzyskać więcej informacji na temat nazw kontraktu danych i przestrzeni nazw, a także nazwy elementów członkowskich danych zobacz [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Jeśli istnieją dwa typy na tej samej stronie (nadawcy i adresata), a ich kontraktów danych nie są równoważne (na przykład mają różnych składowych danych), nie należy nadawać im taką samą nazwę i przestrzeń nazw. Może to spowodować wyjątki zostanie wygenerowany.  
  
 Kontrakty danych dla następujących typów są równoważne:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Równoważność kolejność elementów członkowskich danych i kontrakt danych  
 Za pomocą <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> klasa może mieć wpływ na równoważność kontraktów danych. Kontrakty danych musi mieć elementy członkowskie, które pojawiają się w tej samej kolejności jako równoważne. Kolejnością domyślną jest porządek alfabetyczny. Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Na przykład poniższy kod powoduje kontraktów danych równoważne.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Jednak poniżej nie powoduje kontraktu danych równoważne.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Dziedziczenie, interfejsy i równoważność kontraktów danych  
 Przy określaniu równoważności, kontraktu danych, która dziedziczy inny kontrakt danych jest traktowany tak, jakby była tylko jeden kontraktu danych, który obejmuje wszystkie elementy członkowskie danych z typu podstawowego. Należy pamiętać, że kolejność elementów członkowskich danych muszą być zgodne, oraz że poprzedzać członków typu podstawowego uzyskane elementy członkowskie typu w kolejności. Ponadto jeśli, tak jak w poniższym przykładzie kodu, elementy członkowskie danych dwa mają taką samą wartość kolejności, kolejność elementów członkowskich tych danych jest porządek alfabetyczny. Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 W poniższym przykładzie kontraktu danych dla typu `Employee` jest odpowiednikiem kontraktu danych dla typu `Worker`.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Podczas przekazywania parametrów i zwracanych wartości między klientem a usługą, nie można wysłać kontraktu danych z klasy bazowej, podczas odbierania punkt końcowy oczekuje kontraktu danych z klasy pochodnej. Jest to zgodne z założenia programowania obiektowego. W poprzednim przykładzie obiekt typu `Person` nie mogą być wysyłane po `Employee` oczekuje.  
  
 Kontrakt danych z klasy pochodnej mogą być wysyłane, gdy kontrakt danych z klasy bazowej jest oczekiwany, ale tylko wtedy, gdy odbieranie punktu końcowego "wie" przy użyciu typu pochodnego <xref:System.Runtime.Serialization.KnownTypeAttribute>. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). W poprzednim przykładzie obiekt typu `Employee` mogą być wysyłane po `Person` jest oczekiwany, ale tylko wtedy, gdy kod odbiorcy stosuje <xref:System.Runtime.Serialization.KnownTypeAttribute> się go włączyć do listy znanych typów.  
  
 Podczas przekazywania parametrów i zwracanych wartości między aplikacjami, jeśli oczekiwany typ jest interfejsem, jest równoważne z oczekiwanym typem jest typ <xref:System.Object>. Ponieważ każdy typ ostatecznie jest pochodną <xref:System.Object>, kontraktu danych, co ostatecznie pochodzi z kontraktu danych dla <xref:System.Object>. W związku z tym dowolnego typu kontraktu danych mogą być przekazywane, gdy oczekiwano interfejsu. Dodatkowe kroki są wymagane do pomyślnie pracy z interfejsami; Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Znane typy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
