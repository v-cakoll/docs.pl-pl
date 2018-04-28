---
title: 'Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy'
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
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e1a66dd00592e24fd505cb1956b04d2856bf96a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy
Preferowany sposób tworzenia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Umowa jest przy użyciu interfejsu. Aby uzyskać więcej informacji, zobacz [porady: definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Tutaj alternatywne, obramowane ma utworzyć klasę, a następnie zastosować <xref:System.ServiceModel.ServiceContractAttribute> bezpośrednio do klasy atrybutu i <xref:System.ServiceModel.OperationContractAttribute> atrybutu do każdej z metod w klasie, które są częścią kontraktu.  
  
> [!WARNING]
>  `[ServiceContract]` i `[ServiceContractAttribute]` tak samo postąpić. To samo wartość true, aby uzyskać `[OperationContract]` i `[OperationContractAttribute]`. W każdym przypadku jest skrócona dla niego.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Umowy o świadczenie usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Tworzenie kontraktu programu Windows Communication Foundation z klasą  
  
1.  Utwórz nową klasę za pomocą Visual Basic, C# lub dowolnego innego wspólnego języka środowiska uruchomieniowego języka.  
  
2.  Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy do klasy.  
  
3.  Utwórz metody w klasie.  
  
4.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, która musi być udostępniany jako część publicznego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje klasa, która definiuje kontrakt usługi.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasa stosowana domyślnie używają komunikatów żądanie odpowiedź. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Ten wzorzec komunikatów, zobacz [porady: tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Można również utworzyć i używać innych wzorcach wiadomości przez ustawienie właściwości atrybutu. Więcej przykładów można znaleźć [porady: tworzenie kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
