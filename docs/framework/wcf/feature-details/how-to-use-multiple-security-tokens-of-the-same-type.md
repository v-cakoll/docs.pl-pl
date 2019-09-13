---
title: 'Instrukcje: używanie wielu tokenów zabezpieczeń tego samego typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 84009eacca113fcd83a0e4908c7d6eb0c82db7d5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928761"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Instrukcje: używanie wielu tokenów zabezpieczeń tego samego typu

- W .NET Framework 3,0 komunikat klienta zawiera tylko jeden token danego typu. Teraz komunikaty klienta mogą zawierać wiele tokenów typu. W tym temacie pokazano, jak uwzględnić wiele tokenów tego samego typu w komunikacie klienta.  
  
- Należy pamiętać, że usługi nie można skonfigurować w ten sposób: usługa może zawierać tylko jeden token pomocniczy.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Aby użyć wielu tokenów zabezpieczających tego samego typu  
  
1. Utwórz pustą kolekcję elementów powiązania, która ma zostać wypełniona.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. Utwórz przez wywołanie <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>. <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> Utwórz kolekcję.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. Dodaj tokeny SAML do kolekcji.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. Dodaj kolekcję do <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. Dodaj elementy powiązania do kolekcji elementów powiązania.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. Zwróć nowe niestandardowe powiązanie utworzone na podstawie kolekcji elementów powiązania.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się cała Metoda opisana przez poprzednią procedurę.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
