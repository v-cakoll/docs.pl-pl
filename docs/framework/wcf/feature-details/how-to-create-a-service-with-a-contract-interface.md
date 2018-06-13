---
title: 'Instrukcje: Tworzenie usługi przy użyciu interfejsu kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 796870b80ed72db2353e79db3e4e3fc164c22875
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489797"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Instrukcje: Tworzenie usługi przy użyciu interfejsu kontraktu
Jest to preferowany sposób tworzenia kontraktu usługi Windows Communication Foundation (WCF) przy użyciu interfejsu. Tego kontraktu określono, kolekcji i struktura wiadomości wymagany dostęp do oferty usługi. Ten interfejs definiuje typów wejściowych i wyjściowych przez zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu i <xref:System.ServiceModel.OperationContractAttribute> klas do metody, które chcesz udostępnić.  
  
 Aby uzyskać więcej informacji na temat kontraktów usług, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Tworzenie przy użyciu interfejsu kontraktu usługi WCF  
  
1.  Utwórz nowy interfejs, za pomocą Visual Basic, C# lub dowolnego innego wspólnego języka środowiska uruchomieniowego języka.  
  
2.  Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasy interfejsu.  
  
3.  Zdefiniuj metody w interfejsie.  
  
4.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasy do każdej metody, która musi być udostępniany jako część publicznego kontraktu usługi WCF.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje interfejs, który definiuje kontrakt usługi.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Metody, które mają <xref:System.ServiceModel.OperationContractAttribute> klasa stosowana domyślnie używają komunikatów żądanie odpowiedź. Aby uzyskać więcej informacji o tym wzorcu komunikatów, zobacz [porady: tworzenie kontraktu "żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Można również utworzyć i używać innych wzorcach wiadomości przez ustawienie właściwości atrybutu. Więcej przykładów można znaleźć [porady: tworzenie kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [porady: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
