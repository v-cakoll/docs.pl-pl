---
title: 'Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 2cd757107d9f62ce749d98db1d4968c02a09c5d2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988742"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy
Preferowanym sposobem tworzenia kontraktu Windows Communication Foundation (WCF) jest użycie interfejsu. Aby uzyskać więcej informacji, zobacz [jak: Zdefiniuj kontrakt](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)usługi. Alternatywną metodą jest utworzenie klasy, a następnie zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu do klasy bezpośrednio <xref:System.ServiceModel.OperationContractAttribute> i atrybutu do każdej metody w klasie, która jest częścią kontraktu.  
  
> [!WARNING]
> `[ServiceContract]`i `[ServiceContractAttribute]` wykonaj tę samą czynność. Ten sam element ma wartość true `[OperationContract]` dla `[OperationContractAttribute]`i. W każdym przypadku dawniej jest to skrót dla tej ostatniej.  
  
 Aby uzyskać więcej informacji na temat umów dotyczących usług, zobacz [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Tworzenie kontraktu Windows Communication Foundation z klasą  
  
1. Utwórz nową klasę przy użyciu Visual Basic, C#lub dowolnego innego języka środowiska uruchomieniowego języka wspólnego.  
  
2. <xref:System.ServiceModel.ServiceContractAttribute> Zastosuj klasę do klasy.  
  
3. Utwórz metody w klasie.  
  
4. <xref:System.ServiceModel.OperationContractAttribute> Zastosuj klasę do każdej metody, która musi być ujawniona w ramach publicznego kontraktu WCF.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia klasę, która definiuje kontrakt usługi.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Metody, do których <xref:System.ServiceModel.OperationContractAttribute> zastosowano klasę, domyślnie używają wzorca komunikatów żądanie-odpowiedź. Aby uzyskać więcej informacji na temat tego wzorca wiadomości [, zobacz How to: Utwórz kontrakt](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)żądanie-odpowiedź. Można również tworzyć i używać innych wzorców komunikatów przez ustawienie właściwości atrybutu. Aby uzyskać więcej przykładów, [zobacz How to: Utwórz jednokierunkową umowę](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) i [instrukcje: Utwórz kontrakt](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)dupleksowy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
