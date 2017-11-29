---
title: "Instrukcje: Ustawianie właściwości ProtectionLevel"
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
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3a5c1104ca38f625d5869b4c34e6c48dbb145fed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-protectionlevel-property"></a>Instrukcje: Ustawianie właściwości ProtectionLevel
Stosowanie odpowiedniego atrybutu i ustawiając właściwości można ustawić poziom ochrony. Można ustawić ochrony na poziomie usługi wpływ na wszystkie części każdej wiadomości lub coraz bardziej szczegółowym poziomie, można ustawić ochrony z metody części wiadomości. [!INCLUDE[crabout](../../../includes/crabout-md.md)]`ProtectionLevel` właściwości, zobacz [poziom ochrony opis](../../../docs/framework/wcf/understanding-protection-level.md).  
  
> [!NOTE]
>  Poziomy ochrony można ustawić tylko w kodzie, a nie w konfiguracji.  
  
### <a name="to-sign-all-messages-for-a-service"></a>Aby podpisać wszystkie komunikaty dla usługi  
  
1.  Utwórz interfejs dla usługi.  
  
2.  Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> atrybutu z usługą i ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie (jest to domyślny poziom <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>Wszystkie części komunikatu dla operacji logowania  
  
1.  Interfejs dla usługi tworzenia i stosowania <xref:System.ServiceModel.ServiceContractAttribute> do interfejsu.  
  
2.  Dodawanie deklaracji metody interfejsu.  
  
3.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybut do metody i ustaw <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.Sign>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>Ochrona komunikatów "Fault"  
 Wyjątki, które są generowane w usłudze można wysłać do klienta jako błędach SOAP. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Tworzenie silnie typizowanej błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) i [porady: deklarowanie błędów w kontraktach usług](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).  
  
#### <a name="to-protect-a-fault-message"></a>Aby chronić komunikat o błędzie  
  
1.  Utwórz typ reprezentujący komunikat o błędzie. Poniższy przykład tworzy klasę o nazwie `MathFault` z dwoma polami.  
  
2.  Zastosuj <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do typu i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego pola, które powinny być serializowane, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  W interfejsie zwróci błąd, należy zastosować <xref:System.ServiceModel.FaultContractAttribute> atrybut do metody, która zwróci błąd i ustawić `detailType` parametru na typ klasy błędów.  
  
4.  Również w konstruktorze, należy ustawić <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>Ochrona części wiadomości  
 Użyj kontraktu komunikatu, aby chronić części wiadomości. [!INCLUDE[crabout](../../../includes/crabout-md.md)]kontrakty, zobacz [za pomocą kontraktów komunikatu](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
#### <a name="to-protect-a-message-body"></a>Aby chronić treści wiadomości  
  
1.  Utwórz typ, który reprezentuje wiadomość. Poniższy przykład tworzy `Company` klasy z polami dwóch `CompanyName` i `CompanyID`.  
  
2.  Zastosuj <xref:System.ServiceModel.MessageContractAttribute> do klasy atrybutu i ustaw <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
3.  Zastosuj <xref:System.ServiceModel.MessageHeaderAttribute> do pola, które będą wyrażone jako nagłówek wiadomości i ustawić atrybut `ProtectionLevel` właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
4.  Zastosuj <xref:System.ServiceModel.MessageBodyMemberAttribute> do dowolnego pola, które ma być wyrażone jako część treści wiadomości i ustaw `ProtectionLevel` właściwości <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `ProtectionLevel` właściwości kilka klas atrybutów w różnych miejscach w usłudze.  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższy kod przedstawia przestrzenie nazw wymaganego do skompilowania przykładowy kod.  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 [Omówienie poziomów ochrony](../../../docs/framework/wcf/understanding-protection-level.md)
