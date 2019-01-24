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
ms.openlocfilehash: 13e07d06ed795bc50822d95cdd1ab44c6c336d2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586859"
---
# <a name="how-to-set-the-protectionlevel-property"></a>Instrukcje: Ustawianie właściwości ProtectionLevel
Można ustawić poziom ochrony przez zastosowanie odpowiedniego atrybutu i ustawienie właściwości. Można ustawić ochrony na poziomie usługi, aby wpływają na wszystkie elementy w każdej wiadomości lub ochrony można ustawić na coraz bardziej szczegółowym poziomie, od metody części wiadomości. Aby uzyskać więcej informacji na temat `ProtectionLevel` właściwości, zobacz [zrozumieć poziom ochrony](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
>  Poziomy ochrony można ustawić tylko w przypadku kodu, a nie w konfiguracji.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Aby zarejestrować wszystkie komunikaty dla usługi  
  
1.  Utwórz interfejs dla usługi.  
  
2.  Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybutu w usłudze i ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie (jest to domyślny poziom <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Aby zarejestrować wszystkie części komunikatu dla operacji  
  
1.  Tworzenie interfejsu usługi i stosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu do interfejsu.  
  
2.  Dodaj deklarację metody interfejsu.  
  
3.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybutu do metody, a następnie ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Ochrona komunikaty o błędach  
 Wyjątki wyrzucane usługi mogą być wysyłane do klienta jako błędach SOAP. Aby uzyskać więcej informacji na temat tworzenia silnie typizowane błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) i [jak: Deklarowanie błędów w kontraktach usługi](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>Aby chronić komunikatu o błędzie  
  
1.  Utwórz typ, który reprezentuje komunikat o błędzie. Poniższy przykład tworzy klasę o nazwie `MathFault` przy użyciu dwóch pól.  
  
2.  Zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego pola, które powinny być Zserializowany, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  W interfejsie, który zwróci błąd, należy zastosować <xref:System.ServiceModel.FaultContractAttribute> atrybutu do metody, która zwróci błąd i ustawić `detailType` parametr typu klasy błędów.  
  
4.  Również w konstruktorze, należy ustawić <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Ochrona części wiadomości  
 Użyj kontraktu komunikatu, aby chronić części wiadomości. Aby uzyskać więcej informacji na temat kontraktów komunikatu zobacz [za pomocą kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>Aby chronić treść komunikatu  
  
1.  Utwórz typ, który reprezentuje komunikat. Poniższy przykład tworzy `Company` klasy przy użyciu dwóch pól `CompanyName` i `CompanyID`.  
  
2.  Zastosuj <xref:System.ServiceModel.MessageContractAttribute> do klasy atrybutu i ustaw <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> właściwość <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3.  Zastosuj <xref:System.ServiceModel.MessageHeaderAttribute> atrybutu do pola, które będą wyrażone jako nagłówek wiadomości oraz ustawić `ProtectionLevel` właściwość <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4.  Zastosuj <xref:System.ServiceModel.MessageBodyMemberAttribute> do dowolnego pola, które będą wyrażone jako część treści wiadomości oraz ustawić `ProtectionLevel` właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ustawia `ProtectionLevel` właściwość kilka klas atrybutów w różnych miejscach w usłudze.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższy kod przedstawia przestrzeni nazw, wymaganych do Kompilowanie przykładowego kodu.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [Omówienie poziomów ochrony](../../../docs/framework/wcf/understanding-protection-level.md)
