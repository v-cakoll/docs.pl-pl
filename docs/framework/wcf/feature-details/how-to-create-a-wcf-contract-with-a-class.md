---
title: 'Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: b32d4feb03daac33af8b7ca3b533a0b7013bb090
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658929"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy
Jest preferowany sposób tworzenia kontraktu usługi Windows Communication Foundation (WCF) przy użyciu interfejsu. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Tutaj alternatywne, schemat jest utworzyć klasę, a następnie zastosować <xref:System.ServiceModel.ServiceContractAttribute> bezpośrednio do klasy atrybutu i <xref:System.ServiceModel.OperationContractAttribute> atrybut do każdej metody w klasie, które są dostępne w ramach umowy.  
  
> [!WARNING]
>  `[ServiceContract]` i `[ServiceContractAttribute]` zrobić to samo. Dotyczy to samo `[OperationContract]` i `[OperationContractAttribute]`. W każdym przypadku jest skrócona, w przypadku drugiego nagłówka.  
  
 Aby uzyskać więcej informacji na temat kontraktów usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy  
  
1.  Utwórz nową klasę w języku Visual Basic C#, lub dowolnego innego języka środowiska uruchomieniowego języka wspólnego.  
  
2.  Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy do klasy.  
  
3.  Tworzenie metod w klasie.  
  
4.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, które muszą być widoczne jako część publicznego kontraktu usługi WCF.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje klasę, która definiuje kontrakt usługi.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasy stosowane domyślnie używają wzorzec komunikatów typu żądanie odpowiedź. Aby uzyskać więcej informacji na temat tego wzorca wiadomości zobacz [jak: Tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Można również tworzyć i używać innych wzorców komunikatu przez ustawienie właściwości atrybutu. Aby uzyskać więcej przykładów, zobacz [jak: Tworzenie kontraktu jednokierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [jak: Tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
