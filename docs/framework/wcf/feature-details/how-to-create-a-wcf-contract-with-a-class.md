---
title: 'Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 0be2400ef3da5f0bbc218032ecd69af23f82cabd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597140"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Instrukcje: Tworzenie kontraktu programu Windows Communication Foundation za pomocą klasy
Preferowanym sposobem tworzenia kontraktu Windows Communication Foundation (WCF) jest użycie interfejsu. Aby uzyskać więcej informacji, zobacz [How to: define a Service Contract](../how-to-define-a-wcf-service-contract.md). Alternatywną metodą jest utworzenie klasy, a następnie zastosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu do klasy bezpośrednio i <xref:System.ServiceModel.OperationContractAttribute> atrybutu do każdej metody w klasie, która jest częścią kontraktu.  
  
> [!WARNING]
> `[ServiceContract]`i `[ServiceContractAttribute]` Wykonaj tę samą czynność. Ten sam element ma wartość true dla `[OperationContract]` i `[OperationContractAttribute]` . W każdym przypadku dawniej jest to skrót dla tej ostatniej.  
  
 Aby uzyskać więcej informacji na temat umów dotyczących usług, zobacz [Projektowanie kontraktów usług](../designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Tworzenie kontraktu Windows Communication Foundation z klasą  
  
1. Utwórz nową klasę przy użyciu Visual Basic, C# lub dowolnego innego języka środowiska uruchomieniowego języka wspólnego.  
  
2. Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> klasę do klasy.  
  
3. Utwórz metody w klasie.  
  
4. Zastosuj <xref:System.ServiceModel.OperationContractAttribute> klasę do każdej metody, która musi być ujawniona w ramach publicznego kontraktu WCF.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia klasę, która definiuje kontrakt usługi.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Metody, do których <xref:System.ServiceModel.OperationContractAttribute> zastosowano klasę, domyślnie używają wzorca komunikatów żądanie-odpowiedź. Aby uzyskać więcej informacji na temat tego wzorca wiadomości, zobacz [How to: Create a Request-Reply kontraktu](how-to-create-a-request-reply-contract.md). Można również tworzyć i używać innych wzorców komunikatów przez ustawienie właściwości atrybutu. Aby uzyskać więcej przykładów, zobacz [How to: Create](how-to-create-a-one-way-contract.md) a jednokierunkowe kontraktu i [How to: Create a Duplex kontraktu](how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
