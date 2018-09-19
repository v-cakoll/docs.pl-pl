---
title: 'Instrukcje: Używanie wielu tokenów zabezpieczeń tego samego typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 25afbb268a0ef7772585a0f3829b56f135758b61
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002687"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Instrukcje: Używanie wielu tokenów zabezpieczeń tego samego typu
-   W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, token wiadomość tylko jeden zawartej klienta dla dowolnego typu. Teraz komunikatów klienta może zawierać wiele tokenów typu. W tym temacie pokazano jak dołączyć wielu tokenów tego samego typu w komunikacie klienta.  
  
-   Należy pamiętać, że nie można skonfigurować usługi w ten sposób: usługa może zawierać tylko jeden token pomocniczy.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Aby użyć wielu tokenów zabezpieczeń tego samego typu  
  
1.  Tworzenie powiązania pusta Kolekcja elementów do wypełnienia.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  Tworzenie <xref:System.ServiceModel.Channels.SecurityBindingElement> przez wywołanie metody <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  Utwórz <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> kolekcji.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  Dodaj tokeny SAML do kolekcji.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  Dodaj kolekcję do <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  Dodaj elementy powiązania do kolekcji element powiązania.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  Zwraca nowe powiązanie niestandardowych utworzone na podstawie kolekcji elementów powiązania.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono całą metodę opisane w poprzedniej procedurze.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura zabezpieczeń](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
