---
title: 'Instrukcje: Tworzenie kontraktu jednokierunkowego'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1a54b64826735d912bdf6507023da56118fb9a69
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-one-way-contract"></a>Instrukcje: Tworzenie kontraktu jednokierunkowego
W tym temacie przedstawiono podstawowe kroki, aby utworzyć metody, które używają kontraktu jednokierunkowego. Takie metody wywoływać operacje na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi od klienta, ale oczekiwano odpowiedzi. Ten typ umowy można na przykład do publikowania powiadomienia dla wielu subskrybentów. Umożliwia także kontraktów jednokierunkowych podczas tworzenia kontraktu dwukierunkowego (dwukierunkowej), dzięki czemu klienci i serwery komunikować się ze sobą niezależnie, aby albo mogą inicjować połączenia do drugiego. Może to umożliwić w szczególności serwera w celu wykonywania wywołań jednokierunkowe klientowi, który klient można traktować jako zdarzenia. Aby uzyskać szczegółowe informacje na temat określania metody jednokierunkowe, zobacz <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości i <xref:System.ServiceModel.OperationContractAttribute> klasy.  
  
 Aby uzyskać więcej informacji na temat tworzenia aplikacji klienckiej dla kontraktu dwukierunkowego, zobacz [porady: dostęp do usług pomocą kontraktów jednokierunkowych i kontraktów "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md). Dla przykładu pracy, zobacz [jednokierunkowe](../../../../docs/framework/wcf/samples/one-way.md) próbki.  
  
### <a name="to-create-a-one-way-contract"></a>Aby utworzyć kontraktu jednokierunkowego  
  
1.  Tworzenie kontraktu usługi, stosując <xref:System.ServiceModel.ServiceContractAttribute> interfejs, który definiuje metody usługi jest implementacja klasy.  
  
2.  Wskazuje, które metody w interfejsie klienta można wywoływane przez zastosowanie <xref:System.ServiceModel.OperationContractAttribute> klasy do nich.  
  
3.  Wyznaczyć operacje, które muszą mieć żadnych danych wyjściowych (Brak wartości zwracanej i poza nie lub parametrów ref) jako jednokierunkowe przez ustawienie <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `true`. Należy pamiętać, że operacje który przenoszenia <xref:System.ServiceModel.OperationContractAttribute> klasy spełnić kontraktu "żądanie-odpowiedź" Domyślnie, ponieważ <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> jest właściwość `false` domyślnie. Dlatego należy jawnie określić wartości właściwości atrybutów można `true` Jeśli chcesz kontraktu jednokierunkowego dla metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje kontrakt dla usługi, które są dostępne różne metody jednokierunkowe. Wszystkie metody mają jednokierunkowe umowy z wyjątkiem `Equals`, która domyślnie żądanie odpowiedź i zwraca wynik.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Projektowanie i implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Instrukcje: definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Sesja](../../../../docs/framework/wcf/samples/session.md)  
 [Instrukcje: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
