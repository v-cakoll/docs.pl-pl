---
title: 'Instrukcje: Tworzenie kontraktu jednokierunkowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 42c056c9b56ed1245290cd66833cc6565f517b66
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593454"
---
# <a name="how-to-create-a-one-way-contract"></a>Instrukcje: Tworzenie kontraktu jednokierunkowego
W tym temacie przedstawiono podstawowe kroki tworzenia metod, które korzystają z kontraktu jednokierunkowego. Takie metody wywołują operacje w usłudze Windows Communication Foundation (WCF) z klienta, ale nie oczekują odpowiedzi. Tego typu kontraktu można użyć na przykład w celu opublikowania powiadomień dla wielu subskrybentów. Kontrakty jednokierunkowe można także używać podczas tworzenia dwukierunkowego kontraktu, który umożliwia klientom i serwerom komunikowanie się ze sobą niezależnie, tak aby można było inicjować wywołania do drugiego. Może to umożliwić, w szczególności serwerowi wykonywanie wywołań jednokierunkowych do klienta, które klient może traktować jako zdarzenia. Aby uzyskać szczegółowe informacje na temat określania metod jednokierunkowych, zobacz <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> Właściwość i <xref:System.ServiceModel.OperationContractAttribute> klasę.  
  
 Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej dla kontraktu dupleksowego, zobacz [jak: dostęp do usług za pomocą kontraktów jednokierunkowych i odpowiedzi na żądanie](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md). Aby zapoznać się z przykładem roboczym, zobacz przykład [jednokierunkowe](../samples/one-way.md) .  
  
### <a name="to-create-a-one-way-contract"></a>Aby utworzyć kontrakt jednokierunkowy  
  
1. Utwórz kontrakt usługi przez zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> klasy do interfejsu, który definiuje metody do wdrożenia przez usługę.  
  
2. Wskaż, które metody interfejsu klient może wywołać, stosując <xref:System.ServiceModel.OperationContractAttribute> do nich klasę.  
  
3. Wyznaczanie operacji, które nie mogą zawierać danych wyjściowych (brak wartości zwracanej ani parametrów out lub ref) jako jednokierunkowe przez ustawienie <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości na `true` . Należy zauważyć, że operacje, które przenoszą <xref:System.ServiceModel.OperationContractAttribute> klasę, domyślnie spełniają kontrakt żądanie-odpowiedź, ponieważ <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> Właściwość jest `false` domyślnie. Dlatego musisz jawnie określić wartość właściwości Attribute, `true` Jeśli chcesz, aby kontrakt jednokierunkowy dla metody został określony.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje kontrakt dla usługi, która zawiera kilka jednokierunkowych metod. Wszystkie metody mają jednokierunkowe kontrakty, z wyjątkiem `Equals` , które są domyślne do żądania-odpowiedzi i zwracają wynik.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Projektowanie i implementowanie usług](../designing-and-implementing-services.md)
- [Instrukcje: definiowanie kontraktu usługi](../how-to-define-a-wcf-service-contract.md)
- [Sesja](../samples/session.md)
- [Instrukcje: tworzenie kontraktu dwukierunkowego](how-to-create-a-duplex-contract.md)
