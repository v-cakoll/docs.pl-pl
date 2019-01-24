---
title: 'Instrukcje: Zmienianie dostawcy kryptograficznego dla certyfikatu X.509&#39;s klucza prywatnego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: 40c98d17a52643f451ec01bc8b97c60f2b011b36
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498976"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificate39s-private-key"></a>Instrukcje: Zmienianie dostawcy kryptograficznego dla certyfikatu X.509&#39;s klucza prywatnego
W tym temacie pokazano, jak zmienić dostawcy usług kryptograficznych, używane do zapewnienia klucza prywatnego certyfikatu X.509 oraz integrować dostawcę w ramach zabezpieczeń Windows Communication Foundation (WCF). Aby uzyskać więcej informacji o korzystaniu z certyfikatów, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Struktura zabezpieczeń programu WCF zapewnia sposób wprowadzenia nowych typów tokenu zabezpieczeń, zgodnie z opisem w [jak: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md). Użytkownik może również użyć niestandardowy token, aby zamienić istniejący dostarczane przez system typy tokenów.  
  
 W tym temacie tokenu zabezpieczającego X.509 dostarczane przez system zastępuje niestandardowy token X.509, który zawiera różne implementacje dla klucza prywatnego certyfikatu. Jest to przydatne w scenariuszach, gdzie rzeczywiste klucz prywatny jest udostępniany przez dostawcę usług kryptograficznych innej niż domyślny dostawca usług kryptograficznych Windows. Jednym z przykładów alternatywnego dostawcy usług kryptograficznych jest sprzętowego modułu zabezpieczeń, który wykonuje wszystkie prywatnych kluczy powiązanych operacji kryptograficznych, a nie przechowuje klucze prywatne w pamięci, co poprawia bezpieczeństwo systemu.  
  
 Poniższy przykład jest tylko w celach demonstracyjnych. Nie zastępuje domyślny dostawca usług kryptograficznych Windows, ale pokazuje, gdzie można zintegrować takiego dostawcy.  
  
## <a name="procedures"></a>Procedury  
 Każdy token zabezpieczający, który ma skojarzony klucz zabezpieczeń lub klucze muszą implementować <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> właściwość, która zwraca kolekcję kluczy z wystąpienia tokenu zabezpieczeń. Jeśli token jest tokenem zabezpieczeń X.509, Kolekcja zawiera jedno wystąpienie <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> klasa, która reprezentuje kluczy prywatnych i publicznych skojarzonego z certyfikatem. Aby zastąpić domyślny dostawca usług kryptograficznych używany w celu dostarczania kluczy certyfikatu, Utwórz nową metodę implementacji tej klasy.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Aby utworzyć niestandardowy klucz asymetryczny X.509  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> klasy.  
  
2.  Zastąp <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> właściwość tylko do odczytu. Ta właściwość zwraca rzeczywisty rozmiar klucza pary kluczy publiczny/prywatny certyfikatu.  
  
3.  Zastąp <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> metody. Ta metoda jest wywoływana przez strukturę zabezpieczeń programu WCF do odszyfrowania klucza symetrycznego przy użyciu klucza prywatnego certyfikatu. (Klucz wcześniej został zaszyfrowany za pomocą klucza publicznego certyfikatu).  
  
4.  Zastąp <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> metody. Ta metoda jest wywoływana przez platformę zabezpieczeń usługi WCF w celu uzyskania wystąpienie <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasa, która reprezentuje dostawcy usług kryptograficznych do certyfikatu prywatnej lub publicznej klucza, w zależności od parametrów przekazywany do metody.  
  
5.  Opcjonalna. Zastąp <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> metody. Przesłonić tę metodę, jeśli z inną implementacją <xref:System.Security.Cryptography.HashAlgorithm> klasy jest wymagana.  
  
6.  Zastąp <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> metody. Ta metoda zwraca wystąpienie <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> klasę, która jest skojarzona z klucza prywatnego certyfikatu.  
  
7.  Zastąp <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> metody. Ta metoda jest używana w celu wskazania, czy określonego algorytmu kryptograficznego jest obsługiwana przez implementację klucza zabezpieczeń.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 Poniższa procedura pokazuje, jak zintegrować X.509 asymetrycznego zabezpieczeń klucza implementację niestandardową utworzony w poprzedniej procedurze z architekturą WCF zabezpieczeń w celu zastąpienia zabezpieczeń X.509 dostarczane przez system tokenu.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Aby zastąpić token zabezpieczający X.509 dostarczane przez system niestandardowy token klucza asymetrycznego zabezpieczeń X.509  
  
1.  Utwórz niestandardowy token zabezpieczający X.509, który zwraca niestandardowy klucz asymetryczny zabezpieczeń X.509 zamiast klucz zabezpieczeń dostarczanych przez system, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat tokenów zabezpieczających niestandardowe zobacz [jak: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2.  Tworzenie niestandardowego dostawcy tokenów zabezpieczeń zwracające niestandardowy token zabezpieczający X.509, jak pokazano w przykładzie. Aby uzyskać więcej informacji na temat dostawcy tokenów zabezpieczeń niestandardowe zobacz [jak: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3.  Jeśli klucz niestandardowy zabezpieczeń wymaga do użycia na stronie inicjatora, tworzenie niestandardowego klienta Menedżer tokenów zabezpieczeń i klas poświadczenia niestandardowego klienta, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji o poświadczenia niestandardowego klienta i menedżerów tokenu zabezpieczeń klienta, zobacz [instruktażu: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4.  Jeśli klucz niestandardowy zabezpieczeń musi być używane po stronie odbiorcy, należy utworzyć niestandardowe usługi Menedżer tokenów zabezpieczeń i poświadczeń usługi niestandardowych, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat niestandardowe poświadczenia i menedżerów tokenu zabezpieczeń usługi, zobacz [instruktażu: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.Security.Cryptography.AsymmetricAlgorithm>
- <xref:System.Security.Cryptography.HashAlgorithm>
- <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>
- [Przewodnik: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [Instrukcje: Tworzenie wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Instrukcje: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [Instrukcje: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
- [Architektura zabezpieczeń](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
