---
title: 'Instrukcje: Tworzenie poświadczeń pomocniczych'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 6ec7412d1de2bca349c7cfbf4a37c98ca60cc78d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-supporting-credential"></a>Instrukcje: Tworzenie poświadczeń pomocniczych
Istnieje możliwość schematu niestandardowego zabezpieczeń, która wymaga więcej niż jedno poświadczenie. Na przykład usługa może wymagać od klienta nie tylko nazwę użytkownika i hasło, ale również poświadczenia, który gwarantuje klienta znajduje się nad wiek 18. Drugi poświadczenie jest *Obsługa poświadczeń*. W tym temacie opisano sposób wdrożenia tych poświadczeń klienta Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Specyfikacja umożliwiającego poświadczeń jest częścią specyfikacji WS-SecurityPolicy. Aby uzyskać więcej informacji, zobacz [specyfikacji zabezpieczenia usługi sieci Web](http://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Obsługa tokenów  
 Krótko mówiąc, jeśli używasz zabezpieczenia komunikatów *poświadczenia podstawowego* zawsze jest używany do zabezpieczania komunikatów (na przykład certyfikat X.509 lub biletu protokołu Kerberos).  
  
 Zdefiniowane przez specyfikację elementu powiązania zabezpieczeń używa *tokenów* do zabezpieczania wymiany wiadomości. A *tokenu* reprezentacja poświadczeń zabezpieczeń.  
  
 Powiązanie zabezpieczeń używa token podstawowy określone w zasadach zabezpieczeń powiązania do tworzenia podpisu. Ta sygnatura jest określany jako *podpisu wiadomości*.  
  
 Aby rozszerzyć oświadczeń udostępniane przez token skojarzony z sygnaturą komunikat można określić dodatkowe tokeny.  
  
## <a name="endorsing-signing-and-encrypting"></a>Wprowadzająca podpisywania i szyfrowania  
 Wynikiem poświadczeń pomocniczych *tokenu pomocniczego* przesyłane w komunikacie. Specyfikacja WS-SecurityPolicy definiuje cztery sposoby dołączenia tokenu pomocniczego do wiadomości, zgodnie z opisem w poniższej tabeli.  
  
|Cel|Opis|  
|-------------|-----------------|  
|Podpisany|Token pomocniczy znajduje się w nagłówku zabezpieczeń i jest podpisany przez podpisu wiadomości.|  
|Wprowadzająca|*Indosowania token* podpisuje podpisu wiadomości.|  
|Podpisane i zatwierdzania|Podpisana, wprowadzająca tokeny logowania całą `ds:Signature` element wyprodukowane z podpisu wiadomości i są same podpisane przez tego podpisu wiadomości; oznacza to, że oba tokeny (tokenu użytego do podpisania wiadomości i podpisany token indosowania) Zarejestruj się wzajemnie.|  
|Podpisane i szyfrowania|Są podpisane podpisem, zaszyfrowanych tokenów pomocniczych, Obsługa tokenów, które również są szyfrowane, gdy są one wyświetlane w `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Programowanie Obsługa poświadczeń  
 Aby utworzyć usługę, która korzysta z tokenów pomocniczych, należy utworzyć [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md). (Aby uzyskać więcej informacji, zobacz [porady: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 Pierwszym krokiem podczas tworzenia niestandardowego powiązania jest można utworzyć elementu powiązania zabezpieczeń, które może być jedną z trzech typów:  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Wszystkie klasy dziedziczą <xref:System.ServiceModel.Channels.SecurityBindingElement>, która obejmuje cztery odpowiednie właściwości:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Zakresy  
 Istnieją dwa zakresy umożliwiającego poświadczeń:  
  
-   *Punkt końcowy tokenami pomocniczymi* obsługuje wszystkich operacji punktu końcowego. Oznacza to poświadczenia, który reprezentuje token pomocniczy można używać zawsze, gdy wszystkie operacje punktu końcowego są wywoływane.  
  
-   *Operacja tokenami pomocniczymi* obsługuje tylko operacji określonego punktu końcowego.  
  
 Wskazywany przez nazwy właściwości, obsługa poświadczeń może być wymagany lub opcjonalny. Oznacza to, że jeśli pomocniczy poświadczenie jest używane, jeśli jest obecny, chociaż nie jest konieczne, ale uwierzytelnianie zakończy się niepowodzeniem, jeśli nie jest zainstalowany.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Aby utworzyć niestandardowego powiązania, które zawiera Obsługa poświadczeń  
  
1.  Tworzenie elementu powiązania zabezpieczeń. Poniższy przykład tworzy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> z `UserNameForCertificate` tryb uwierzytelniania. Użyj <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metody.  
  
2.  Dodaj parametr pomocnicze do kolekcji typy zwracane przez odpowiednie właściwości (`Endorsing`, `Signed`, `SignedEncrypted`, lub `SignedEndorsed`). Typy w <xref:System.ServiceModel.Security.Tokens> przestrzeni nazw obejmują często używanych typów, takie jak <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i dodaje wystąpienie <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> klasy do kolekcji właściwości Endorsing zwróconej.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
