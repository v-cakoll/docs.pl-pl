---
title: "Instrukcje: Tworzenie usługi przy użyciu interfejsu kontraktu"
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
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b00a7cbbab343eb209895affbbbba76ef2af2959
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Instrukcje: Tworzenie usługi przy użyciu interfejsu kontraktu
Preferowany sposób tworzenia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Umowa jest przy użyciu interfejsu. Tego kontraktu określono, kolekcji i struktura wiadomości wymagany dostęp do oferty usługi. Ten interfejs definiuje typów wejściowych i wyjściowych przez zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu i <xref:System.ServiceModel.OperationContractAttribute> klas do metody, które chcesz udostępnić.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Umowy o świadczenie usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Tworzenie przy użyciu interfejsu kontraktu usługi WCF  
  
1.  Tworzenie nowego przy użyciu interfejsu [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# lub dowolnego innego wspólnego języka środowiska uruchomieniowego języka.  
  
2.  Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu.  
  
3.  Zdefiniuj metody w interfejsie.  
  
4.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, która musi być udostępniany jako część publicznego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje interfejs, który definiuje kontrakt usługi.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasa stosowana domyślnie używają komunikatów żądanie odpowiedź. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Ten wzorzec komunikatów, zobacz [porady: tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Można również utworzyć i używać innych wzorcach wiadomości przez ustawienie właściwości atrybutu. Więcej przykładów można znaleźć [porady: tworzenie kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
