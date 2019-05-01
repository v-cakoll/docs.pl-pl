---
title: 'Instrukcje: tworzenie poświadczeń pomocniczych'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 7c6c4ea777f62541f8ca8fa79fdd024e5f5cf2ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787611"
---
# <a name="how-to-create-a-supporting-credential"></a>Instrukcje: tworzenie poświadczeń pomocniczych
Istnieje możliwość schematu niestandardowego zabezpieczeń, która wymaga więcej niż jedno poświadczenie. Na przykład usługa może wymagać od klienta nie tylko nazwę użytkownika i hasło, ale również poświadczeń, który okazał się klienta znajduje się nad niż 18 lat. Drugie poświadczenie jest *obsługi poświadczeń*. W tym temacie wyjaśniono, jak wdrożyć tych poświadczeń w kliencie programu Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Specyfikacja do obsługi poświadczeń jest częścią specyfikacji WS-SecurityPolicy. Aby uzyskać więcej informacji, zobacz [specyfikacji zabezpieczenia usługi sieci Web](https://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Obsługa tokenów  
 Krótko mówiąc, gdy używasz zabezpieczeń komunikatów *podstawowej credential* zawsze służy do zabezpieczania komunikatu (na przykład certyfikat X.509 lub biletu protokołu Kerberos).  
  
 Zgodnie z definicją w specyfikacji, powiązanie zabezpieczeń używa *tokenów* zabezpieczyć wymianę komunikatów. A *tokenu* jest reprezentacją poświadczeń zabezpieczeń.  
  
 Powiązanie zabezpieczeń używa token podstawowy określone w zasadach zabezpieczeń powiązania do tworzenia podpisu. Podpis ten jest nazywany *podpisu wiadomości*.  
  
 Można określić dodatkowe tokeny rozszerzyć oświadczenia dostarczane przez tokenu skojarzone z podpisu wiadomości.  
  
## <a name="endorsing-signing-and-encrypting"></a>Potwierdzających, podpisywanie i szyfrowanie  
 Pomocnicze poświadczenia skutkuje *token pomocniczy* przekazywane wewnątrz komunikatu. Specyfikacja WS-SecurityPolicy definiuje cztery sposoby dołączenia tokenu pomocniczego do wiadomości, zgodnie z opisem w poniższej tabeli.  
  
|Cel|Opis|  
|-------------|-----------------|  
|Podpisany|Token pomocniczy znajduje się w nagłówku zabezpieczeń i jest podpisany przez podpisu wiadomości.|  
|Wprowadzająca|*Zatwierdzania token* podpisuje podpisu wiadomości.|  
|Ze znakiem i zatwierdzania|Podpisana, potwierdzających tokenów logowania całą `ds:Signature` element wyprodukowanych z podpisu wiadomości i są same podpisane przez ten podpis wiadomości; oznacza to, że oba tokeny (tokenu użytego do podpisania komunikatu i podpisany token zatwierdzania) Zaloguj się wzajemnie.|  
|Ze znakiem i szyfrowania|Podpisany, zaszyfrowanych tokenów pomocniczych są podpisane, Obsługa tokenów, które również są szyfrowane, gdy są one wyświetlane w `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Obsługa poświadczeń programowania  
 Aby utworzyć usługę, który używa tokenów pomocniczych, należy utworzyć [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md). (Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 Pierwszym krokiem podczas tworzenia niestandardowego powiązania jest utworzyć elementu powiązania zabezpieczeń, który może być jednym z trzech typów:  
  
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
  
- *Punkt końcowy tokenów pomocniczych* obsługuje wszystkie operacje dla punktu końcowego. Oznacza to, że poświadczenie, które reprezentuje token pomocniczy można zawsze wtedy, gdy dowolne operacje punktu końcowego są wywoływane.  
  
- *Obsługa tokenów operacji* obsługuje tylko operacji do określonego punktu końcowego.  
  
 Obsługa poświadczeń może być wskazane przez nazwy właściwości, wymaganego lub opcjonalnego. Oznacza to jeśli pomocnicze poświadczenie jest używane, jeśli jest obecny, chociaż nie jest konieczne, ale uwierzytelnianie zakończy się niepowodzeniem, jeśli nie jest obecny.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Tworzenie niestandardowego powiązania, które obejmuje pomocnicze poświadczenia  
  
1. Tworzenie elementu powiązania zabezpieczeń. Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> z `UserNameForCertificate` tryb uwierzytelniania. Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metody.  
  
2. Dodaj parametr pomocniczych do kolekcji typów zwracany przez właściwość odpowiednie (`Endorsing`, `Signed`, `SignedEncrypted`, lub `SignedEndorsed`). Typy w <xref:System.ServiceModel.Security.Tokens> przestrzeni nazw obejmują często używanych typów, takie jak <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i dodaje instancję <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> klasy do kolekcji właściwości Endorsing zwróconej.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
