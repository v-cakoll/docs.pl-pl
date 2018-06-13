---
title: Równoważność kontraktów danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: b6461ffe6525b377e7f836a686a401033d344a4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492802"
---
# <a name="data-contract-equivalence"></a>Równoważność kontraktów danych
Klient pomyślnie wysyłania danych określonego typu usługi lub usług pomyślnie wysyłać dane do klienta wysłane typu nie zawsze musi istnieje po stronie odbiorczej. Jedynym wymaganiem jest równoważne kontraktów danych obu typów. (Czasami strict równoważność nie jest wymagana, zgodnie z opisem w [przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Dla kontraktów danych jako równoważne muszą mieć taką samą przestrzeń nazw i nazwę. Ponadto każdy element członkowski danych na jednej stronie musi mieć element członkowski danych równoważne z drugiej strony.  
  
 Elementów członkowskich danych jako równoważne muszą mieć taką samą nazwę. Ponadto musi reprezentować ten sam typ danych. oznacza to, że ich kontraktów danych musi być taka sama.  
  
> [!NOTE]
>  Należy pamiętać, że kontraktu danych, nazwy i przestrzeni nazw, jak również nazwy elementów członkowskich danych, jest rozróżniana wielkość liter.  
  
 Aby uzyskać więcej informacji na temat nazw kontraktu danych i przestrzenie nazw, jak również nazwy elementów członkowskich danych, zobacz [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Jeśli istnieją dwa typy na tej samej stronie (nadawcy i adresata) i ich kontraktów danych nie są równoważne (na przykład użytkownicy mają elementy członkowskie danych różnych), nie należy nadawać je taką samą nazwę i przestrzeń nazw. W ten sposób może spowodować wyjątki zostanie wygenerowany.  
  
 Kontrakty danych dla następujących typów są równoważne:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Równoważność kolejność elementów członkowskich danych i kontraktu danych  
 Przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> klasy może mieć wpływ na równoważność kontraktów danych. Kontrakty danych musi mieć elementy członkowskie, które pojawiają się w tej samej kolejności równoważne. Domyślna kolejność to alfabetycznym. Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Na przykład następujący kod powoduje kontraktów danych równoważne.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 Jednak następujące nie powoduje kontraktu danych równoważne.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Dziedziczenie, interfejsów i równoważność kontraktów danych  
 Podczas określania równoważność, kontraktu danych, która dziedziczy inny kontrakt danych jest traktowana tak, jakby była tylko jeden kontrakt danych obejmuje wszystkie elementy członkowskie danych z typu podstawowego. Należy pamiętać, że kolejność elementów członkowskich danych muszą być zgodne oraz że poprzedzają elementów członkowskich typu podstawowego uzyskane elementy członkowskie typu w kolejności. Ponadto jeśli jak w poniższym przykładzie kodu, elementy członkowskie danych dwa mają taką samą wartość kolejności, kolejność elementów członkowskich tych danych jest alfabetycznym. Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 W poniższym przykładzie dla typu kontraktu danych `Employee` jest odpowiednikiem kontraktu danych dla typu `Worker`.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Podczas przekazywania parametrów i zwracanych wartości między klientem a usługą, kontrakt danych z klasy podstawowej nie można wysłać podczas odbierania punkt końcowy oczekuje kontraktu danych z klasy pochodnej. Jest to zgodne z zorientowane obiektowo programowania rozwiązań. W poprzednim przykładzie, typu obiektu `Person` nie mogą być wysyłane podczas `Employee` jest oczekiwany.  
  
 Kontrakt danych z klasy pochodnej mogą być wysyłane, gdy kontrakt danych z klasy podstawowej jest oczekiwany, ale tylko w przypadku odbierania punktu końcowego "wie" użycia typu pochodnego <xref:System.Runtime.Serialization.KnownTypeAttribute>. Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). W poprzednim przykładzie, typu obiektu `Employee` mogą być wysyłane podczas `Person` jest oczekiwany, ale tylko wtedy, gdy kod odbiornika wykorzystuje <xref:System.Runtime.Serialization.KnownTypeAttribute> należeć listy znanych typów.  
  
 Podczas przekazywania parametrów i zwracanych wartości między aplikacjami, jeśli oczekiwany typ to interfejs, jest odpowiednikiem oczekiwanym typem jest typu <xref:System.Object>. Ponieważ każdy typ ostatecznie pochodną <xref:System.Object>, kontrakt danych, co ostatecznie pochodną kontraktu danych dla <xref:System.Object>. W związku z tym dowolnego typu kontraktu danych mogą być przekazywane, gdy interfejs. Dodatkowe kroki są wymagane do pomyślnie pracy z interfejsami; Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [Znane typy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
