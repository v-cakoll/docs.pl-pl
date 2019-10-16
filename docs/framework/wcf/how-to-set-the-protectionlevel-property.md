---
title: 'Instrukcje: Ustawianie właściwości ProtectionLevel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 4ff835f767852da586a3a35b7f4ce2edf99db283
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320913"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Instrukcje: Ustawianie właściwości ProtectionLevel
Poziom ochrony można ustawić, stosując odpowiedni atrybut i ustawiając właściwość. Można ustawić ochronę na poziomie usługi, aby mieć wpływ na wszystkie części każdego komunikatu, lub można ustawić ochronę na coraz większych poziomach, od metod do części komunikatów. Aby uzyskać więcej informacji na temat właściwości `ProtectionLevel`, zobacz [Opis poziomu ochrony](understanding-protection-level.md).  
  
> [!NOTE]
> Poziomy ochrony można ustawić tylko w kodzie, a nie w konfiguracji.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Aby podpisać wszystkie komunikaty dotyczące usługi  
  
1. Utwórz interfejs dla usługi.  
  
2. Zastosuj atrybut <xref:System.ServiceModel.ServiceContractAttribute> do usługi i ustaw właściwość <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie (poziom domyślny to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Aby podpisywać wszystkie części komunikatów dla operacji  
  
1. Utwórz interfejs dla usługi i zastosuj atrybut <xref:System.ServiceModel.ServiceContractAttribute> do interfejsu.  
  
2. Dodaj deklarację metody do interfejsu.  
  
3. Zastosuj atrybut <xref:System.ServiceModel.OperationContractAttribute> do metody i ustaw właściwość <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Ochrona komunikatów o błędach  
 Wyjątki zgłaszane w ramach usługi mogą być wysyłane do klienta jako błędy SOAP. Aby uzyskać więcej informacji na temat tworzenia jednoznacznie wpisanych błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md) oraz [instrukcje: deklarowanie błędów w kontraktach usługi](how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>Aby chronić komunikat o błędzie  
  
1. Utwórz typ, który reprezentuje komunikat o błędzie. Poniższy przykład tworzy klasę o nazwie `MathFault` z dwoma polami.  
  
2. Zastosuj atrybut <xref:System.Runtime.Serialization.DataContractAttribute> do typu i atrybutu <xref:System.Runtime.Serialization.DataMemberAttribute> do każdego pola, które powinny być serializowane, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. W interfejsie, który zwróci błąd, zastosuj atrybut <xref:System.ServiceModel.FaultContractAttribute> do metody, która zwróci błąd i ustawił parametr `detailType` na typ klasy Fault.  
  
4. Ponadto w konstruktorze ustaw właściwość <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Ochrona części komunikatów  
 Użyj kontraktu komunikatu, aby chronić części wiadomości. Aby uzyskać więcej informacji na temat umów dotyczących komunikatów, zobacz [Używanie kontraktów komunikatów](./feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>Aby chronić treść wiadomości  
  
1. Utwórz typ, który reprezentuje komunikat. Poniższy przykład tworzy klasę `Company` z dwoma polami, `CompanyName` i `CompanyID`.  
  
2. Zastosuj atrybut <xref:System.ServiceModel.MessageContractAttribute> do klasy i ustaw właściwość <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3. Zastosuj atrybut <xref:System.ServiceModel.MessageHeaderAttribute> do pola, które będzie wyrażone jako nagłówek komunikatu, i ustaw właściwość `ProtectionLevel` na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4. Zastosuj <xref:System.ServiceModel.MessageBodyMemberAttribute> do dowolnego pola, które będzie wyrażone jako część treści komunikatu, i ustaw właściwość `ProtectionLevel` na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ustawia właściwość `ProtectionLevel` kilku klas atrybutów w różnych miejscach w usłudze.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższy kod przedstawia przestrzenie nazw wymagane do skompilowania przykładowego kodu.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [Omówienie poziomów ochrony](understanding-protection-level.md)
