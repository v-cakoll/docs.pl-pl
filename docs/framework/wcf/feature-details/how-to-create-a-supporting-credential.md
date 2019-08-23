---
title: 'Instrukcje: tworzenie poświadczeń pomocniczych'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 1f95748235aa5238193b8869f8330f0a7fc650d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968896"
---
# <a name="how-to-create-a-supporting-credential"></a>Instrukcje: tworzenie poświadczeń pomocniczych
Istnieje możliwość, że niestandardowy schemat zabezpieczeń wymaga więcej niż jednego poświadczenia. Na przykład usługa może wymagać od klienta nie tylko nazwy użytkownika i hasła, ale również poświadczenia, które potwierdzają, że klient znajduje się w wieku 18 lat. Drugie poświadczenie jest *pomocniczą*poświadczeniem. W tym temacie wyjaśniono, jak zaimplementować takie poświadczenia w kliencie Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Specyfikacja dla obsługi poświadczeń jest częścią specyfikacji WS-SecurityPolicy. Aby uzyskać więcej informacji, zobacz [specyfikacje zabezpieczenia usług w sieci Web](https://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Obsługa tokenów  
 W przypadku korzystania z zabezpieczeń wiadomości *podstawowe poświadczenia* są zawsze używane do zabezpieczania wiadomości (na przykład certyfikatu X. 509 lub biletu Kerberos).  
  
 Zgodnie ze specyfikacją, powiązanie zabezpieczeń używa tokenów do zabezpieczenia wymiany komunikatów. *Token* jest reprezentacją poświadczenia zabezpieczeń.  
  
 Powiązanie zabezpieczeń używa tokenu podstawowego zidentyfikowanego w zasadzie powiązań zabezpieczeń w celu utworzenia podpisu. Ta sygnatura jest określana jako *sygnatura wiadomości*.  
  
 Dodatkowe tokeny można określić, aby rozszerzyć oświadczenia dostarczone przez token skojarzony z podpisem komunikatu.  
  
## <a name="endorsing-signing-and-encrypting"></a>Zatwierdzanie, podpisywanie i szyfrowanie  
 W wyniku obsługi poświadczenie pomocnicze przesyłane w komunikacie jest *obsługiwany token* . Specyfikacja WS-SecurityPolicy definiuje cztery sposoby dołączania tokenu pomocniczego do wiadomości, zgodnie z opisem w poniższej tabeli.  
  
|Cel|Opis|  
|-------------|-----------------|  
|Opatrzon|Token pomocniczy jest zawarty w nagłówku zabezpieczeń i jest podpisany przez sygnaturę wiadomości.|  
|Indosowania|*Token poświadczający* podpisuje sygnaturę wiadomości.|  
|Podpisywanie i zatwierdzanie|Podpisane, poświadczające tokeny podpisują `ds:Signature` cały element wystawiony na podstawie podpisu wiadomości i są podpisywane przez tę sygnaturę wiadomości; oznacza to, że oba tokeny (token używany dla podpisu wiadomości i podpisany token poświadczający) podpisują siebie nawzajem.|  
|Podpisywanie i szyfrowanie|Podpisane, zaszyfrowane tokeny pomocnicze są podpisywane tokeny pomocnicze, które są `wsse:SecurityHeader`również szyfrowane, gdy są wyświetlane w.|  
  
## <a name="programming-supporting-credentials"></a>Programowanie — poświadczenia pomocnicze  
 Aby utworzyć usługę korzystającą z tokenów pomocniczych, należy [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)utworzyć niestandardową >Binding. (Aby uzyskać więcej informacji, [zobacz How to: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 Pierwszym krokiem podczas tworzenia niestandardowego powiązania jest utworzenie elementu powiązania zabezpieczeń, który może być jednym z trzech typów:  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Wszystkie klasy dziedziczą z <xref:System.ServiceModel.Channels.SecurityBindingElement>, która obejmuje cztery odpowiednie właściwości:  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Zakresy  
 Istnieją dwa zakresy do obsługi poświadczeń:  
  
- *Tokeny obsługujące punkt końcowy* obsługują wszystkie operacje na punkcie końcowym. Oznacza to, że poświadczenie, którego token pomocniczy reprezentuje, może być używane za każdym razem, gdy zostaną wywołane wszystkie operacje punktów końcowych.  
  
- *Operacje* obsługujące tokeny obsługują tylko określoną operację punktu końcowego.  
  
 Jak wskazano nazwy właściwości, obsługa poświadczeń może być wymagana lub opcjonalna. Oznacza to, że jeśli jest używane poświadczenie pomocnicze, mimo że nie jest to konieczne, ale uwierzytelnianie nie powiedzie się, jeśli nie istnieje.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Tworzenie niestandardowego powiązania zawierającego poświadczenia pomocnicze  
  
1. Utwórz element powiązania zabezpieczeń. Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> `UserNameForCertificate` z trybem uwierzytelniania. <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> Użyj metody.  
  
2. Dodaj parametr pomocniczy do kolekcji typów zwracanych przez odpowiednią właściwość`Endorsing`(, `Signed`, `SignedEncrypted`lub `SignedEndorsed`). Typy w <xref:System.ServiceModel.Security.Tokens> przestrzeni nazw zawierają powszechnie używane typy, takie <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>jak.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i dodaje wystąpienie <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> klasy do kolekcji, która zwraca właściwość poświadczający.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
