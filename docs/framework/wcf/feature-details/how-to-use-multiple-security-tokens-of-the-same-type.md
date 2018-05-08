---
title: 'Instrukcje: Używanie wielu tokenów zabezpieczeń tego samego typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 67a9fd51377294ab6afb5a3d7deaec19fb134b21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Instrukcje: Używanie wielu tokenów zabezpieczeń tego samego typu
-   W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, token wiadomości tylko jeden zawartych w niej klienta dla dowolnego typu. Teraz wiadomości klienta może zawierać wiele tokenów typu. W tym temacie przedstawiono sposób obejmują wiele tokenów tego samego typu w komunikacie klienta.  
  
-   Należy pamiętać, że nie można skonfigurować usługę w ten sposób: usługi może zawierać tylko jeden token pomocniczy.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Aby używanie wielu tokenów zabezpieczeń tego samego typu  
  
1.  Utwórz pusty powiązania elementu do wypełnienia.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  Utwórz <xref:System.ServiceModel.Channels.SecurityBindingElement> przez wywołanie metody <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  Utwórz <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> kolekcji.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  Dodawanie tokenów SAML do kolekcji.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  Dodawanie do kolekcji <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  Dodaj powiązania elementów do kolekcji elementu powiązania.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  Zwraca nowy niestandardowego powiązania utworzonych na podstawie kolekcji element powiązania.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono metodę całego opisanych w poprzedniej procedurze.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura zabezpieczeń](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
