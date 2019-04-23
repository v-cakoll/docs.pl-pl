---
title: 'Instrukcje: tworzenie usługi przy użyciu interfejsu kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 0aa5429d771aeda0b392b89ec4cc1a07de30973f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772898"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Instrukcje: tworzenie usługi przy użyciu interfejsu kontraktu
Jest to preferowany sposób tworzenie kontraktu programu Windows Communication Foundation (WCF) przy użyciu interfejsu. Ten kontrakt Określa, kolekcji i struktury komunikaty wymagane operacje dostępu do oferty usługi. Ten interfejs definiuje typy wejściowe i wyjściowe, stosując <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu i <xref:System.ServiceModel.OperationContractAttribute> klasy do metod, które chcesz udostępnić.  
  
 Aby uzyskać więcej informacji na temat kontraktów usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Tworzenie kontraktu usługi WCF za pomocą interfejsu  
  
1. Tworzenie nowego interfejsu w języku Visual Basic C#, lub dowolnego innego języka środowiska uruchomieniowego języka wspólnego.  
  
2. Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu.  
  
3. Określ metody w interfejsie.  
  
4. Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, które muszą być widoczne jako część publicznego kontraktu usługi WCF.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje interfejs, który definiuje kontrakt usługi.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasy stosowane domyślnie używają wzorzec komunikatów typu żądanie odpowiedź. Aby uzyskać więcej informacji na temat tego wzorca wiadomości zobacz [jak: Tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Można również tworzyć i używać innych wzorców komunikatu przez ustawienie właściwości atrybutu. Aby uzyskać więcej przykładów, zobacz [jak: Tworzenie kontraktu jednokierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [jak: Tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
