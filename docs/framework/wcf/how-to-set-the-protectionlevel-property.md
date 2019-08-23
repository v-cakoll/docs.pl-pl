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
ms.openlocfilehash: 222fda180923cdc7b0d7b7ab413c151c69add259
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950976"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Instrukcje: Ustawianie właściwości ProtectionLevel
Poziom ochrony można ustawić, stosując odpowiedni atrybut i ustawiając właściwość. Można ustawić ochronę na poziomie usługi, aby mieć wpływ na wszystkie części każdego komunikatu, lub można ustawić ochronę na coraz większych poziomach, od metod do części komunikatów. Aby uzyskać więcej informacji na `ProtectionLevel` temat właściwości, zobacz [Opis poziomu ochrony](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
> Poziomy ochrony można ustawić tylko w kodzie, a nie w konfiguracji.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Aby podpisać wszystkie komunikaty dotyczące usługi  
  
1. Utwórz interfejs dla usługi.  
  
2. Zastosuj atrybut do usługi i <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> ustaw właściwość na <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie (poziom domyślny to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>). <xref:System.ServiceModel.ServiceContractAttribute>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Aby podpisywać wszystkie części komunikatów dla operacji  
  
1. Utwórz interfejs dla usługi i Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybut do interfejsu.  
  
2. Dodaj deklarację metody do interfejsu.  
  
3. Zastosuj atrybut do metody i <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> ustaw właściwość na <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie. <xref:System.ServiceModel.OperationContractAttribute>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Ochrona komunikatów o błędach  
 Wyjątki zgłaszane w ramach usługi mogą być wysyłane do klienta jako błędy SOAP. Aby uzyskać więcej informacji na temat tworzenia jednoznacznie wpisanych błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) oraz [jak: Zadeklaruj błędy w kontraktach](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)usługi.  
  
#### <a name="to-protect-a-fault-message"></a>Aby chronić komunikat o błędzie  
  
1. Utwórz typ, który reprezentuje komunikat o błędzie. Poniższy przykład tworzy klasę o nazwie `MathFault` z dwoma polami.  
  
2. Zastosuj atrybut do typu i atrybutu do każdego pola, które powinny być serializowane, jak pokazano w poniższym kodzie. <xref:System.Runtime.Serialization.DataMemberAttribute> <xref:System.Runtime.Serialization.DataContractAttribute>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. W interfejsie, który zwróci błąd, Zastosuj <xref:System.ServiceModel.FaultContractAttribute> atrybut do metody, która zwróci błąd, i `detailType` ustaw parametr na typ klasy Fault.  
  
4. Ponadto w konstruktorze Ustaw <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> właściwość na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Ochrona części komunikatów  
 Użyj kontraktu komunikatu, aby chronić części wiadomości. Aby uzyskać więcej informacji na temat umów dotyczących komunikatów, zobacz [Używanie kontraktów komunikatów](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>Aby chronić treść wiadomości  
  
1. Utwórz typ, który reprezentuje komunikat. Poniższy przykład tworzy `Company` klasę z dwoma `CompanyName` polami i `CompanyID`.  
  
2. Zastosuj atrybut do klasy i <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> ustaw właściwość na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>. <xref:System.ServiceModel.MessageContractAttribute>  
  
3. Zastosuj atrybut do pola, które będzie wyrażone jako nagłówek komunikatu, i `ProtectionLevel` ustaw właściwość na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>. <xref:System.ServiceModel.MessageHeaderAttribute>  
  
4. Zastosuj do każdego pola, które będzie wyrażone jako część treści komunikatu, i `ProtectionLevel` ustaw właściwość na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym przykładzie. <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ustawia `ProtectionLevel` Właściwość kilku klas atrybutów w różnych miejscach w usłudze.  
  
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
- [Omówienie poziomów ochrony](../../../docs/framework/wcf/understanding-protection-level.md)
