---
title: 'Instrukcje: tworzenie kontraktu jednokierunkowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: a4996dc963c572e2aeb14b9b366af33b8f23d480
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208660"
---
# <a name="how-to-create-a-one-way-contract"></a>Instrukcje: tworzenie kontraktu jednokierunkowego
W tym temacie przedstawiono podstawowe kroki, aby utworzyć metody, które używają kontraktu jednokierunkowego. Takie metody wywoływanie operacji usługi Windows Communication Foundation (WCF) od klienta, ale nie oczekuje na odpowiedź. Ten typ kontraktu można, na przykład do publikowania liczbę subskrybentów powiadomień. Tworząc kontraktu dwukierunkowego (dwukierunkowej), umożliwiająca klientów i serwerów komunikować się ze sobą niezależnie, aby albo może zainicjować wywołania do innego, mogą używać kontraktów jednokierunkowych. Umożliwia to w szczególności serwera do wykonywania jednokierunkowe wywołań do klienta, który klient można traktować jako zdarzenia. Aby uzyskać szczegółowe informacje na temat określania metody jednokierunkowe zobacz <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości i <xref:System.ServiceModel.OperationContractAttribute> klasy.  
  
 Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej kontrakt dupleksowy, zobacz [jak: Uzyskiwanie dostępu do usług za pomocą jednokierunkowego i kontraktów "żądanie odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md). Przykładowy pracy [jednokierunkowe](../../../../docs/framework/wcf/samples/one-way.md) próbki.  
  
### <a name="to-create-a-one-way-contract"></a>Tworzenie kontraktu jednokierunkowego  
  
1.  Tworzenie kontraktu usługi, stosując <xref:System.ServiceModel.ServiceContractAttribute> klasy do interfejsu, który definiuje metody jest zaimplementowanie usługi.  
  
2.  Wywoływane przez zastosowanie wskazują, które metody w interfejsie klienta można <xref:System.ServiceModel.OperationContractAttribute> klasy do nich.  
  
3.  Wyznaczyć operacje, które musi zawierać żadnych danych wyjściowych (nie zwraca wartości i poza nie lub parametry ref) jak jednokierunkowe, ustawiając <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwość `true`. Należy pamiętać, że operacje, wykonać <xref:System.ServiceModel.OperationContractAttribute> klasy spełnia kontraktu "żądanie-odpowiedź" Domyślnie, ponieważ <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwość `false` domyślnie. Dlatego należy jawnie określić wartość właściwości atrybutu jako `true` chcącym kontraktu jednokierunkowego dla metody.  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje kontrakt dla usługi, które są dostępne różne metody jednokierunkowe. Wszystkie metody mają jednokierunkowe umowy, z wyjątkiem `Equals`, którego wartość domyślna to "żądanie-odpowiedź" i zwraca wynik.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Projektowanie i implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Instrukcje: Definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Sesja](../../../../docs/framework/wcf/samples/session.md)
- [Instrukcje: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
