---
title: 'Instrukcje: zmienianie dostawcy kryptograficznego dla klucza prywatnego certyfikatu X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: 8101c0d1214eed2c6ea42a4faab774207aab3a79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797279"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificates-private-key"></a>Instrukcje: zmienianie dostawcy kryptograficznego dla klucza prywatnego certyfikatu X.509
W tym temacie pokazano, jak zmienić dostawcę usług kryptograficznych używany do udostępniania klucza prywatnego certyfikatu X. 509 oraz jak zintegrować dostawcę z platformą zabezpieczeń Windows Communication Foundation (WCF). Aby uzyskać więcej informacji o korzystaniu z certyfikatów, zobacz [Praca z certyfikatami](../feature-details/working-with-certificates.md).  
  
 Struktura zabezpieczeń WCF umożliwia wprowadzenie nowych typów tokenów zabezpieczających, zgodnie z opisem w [temacie How to: Utwórz token](how-to-create-a-custom-token.md)niestandardowy. Istnieje również możliwość użycia tokenu niestandardowego do zastępowania istniejących typów tokenów dostarczonych przez system.  
  
 W tym temacie, dostarczony przez system token zabezpieczający X. 509 jest zastępowany przez niestandardowy token X. 509, który zapewnia inną implementację klucza prywatnego certyfikatu. Jest to przydatne w scenariuszach, w których rzeczywisty klucz prywatny jest udostępniany przez innego dostawcę usług kryptograficznych niż domyślny dostawca usług kryptograficznych systemu Windows. Przykładem alternatywnego dostawcy usług kryptograficznych jest sprzętowy moduł zabezpieczeń, który wykonuje wszystkie operacje kryptograficzne związane z kluczem prywatnym i nie przechowuje kluczy prywatnych w pamięci, dzięki czemu można poprawić bezpieczeństwo systemu.  
  
 Poniższy przykład jest przeznaczony wyłącznie do celów demonstracyjnych. Nie zastępuje domyślnego dostawcy usług kryptograficznych systemu Windows, ale pokazuje, gdzie można zintegrować ten dostawca.  
  
## <a name="procedures"></a>Procedury  
 Każdy token zabezpieczający, który ma skojarzony klucz zabezpieczeń lub klucze, musi implementować <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> właściwość, która zwraca kolekcję kluczy z wystąpienia tokenu zabezpieczającego. Jeśli token jest tokenem zabezpieczającym X. 509, kolekcja zawiera pojedyncze wystąpienie <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> klasy, które reprezentuje klucze publiczne i prywatne skojarzone z certyfikatem. Aby zastąpić domyślnego dostawcę usług kryptograficznych używanego do dostarczania kluczy certyfikatu, Utwórz nową implementację tej klasy.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Aby utworzyć niestandardowy klucz asymetryczny X. 509  
  
1. Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> klasy.  
  
2. Zastąp <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> właściwość tylko do odczytu. Ta właściwość zwraca rzeczywisty rozmiar klucza pary kluczy publicznych/prywatnych certyfikatu.  
  
3. Zastąp <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> metody. Ta metoda jest wywoływana przez strukturę zabezpieczeń WCF w celu odszyfrowania klucza symetrycznego za pomocą klucza prywatnego certyfikatu. (Klucz został wcześniej zaszyfrowany przy użyciu klucza publicznego certyfikatu).  
  
4. Zastąp <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> metody. Ta metoda jest wywoływana przez strukturę zabezpieczeń WCF w celu uzyskania wystąpienia <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy, która reprezentuje dostawcę usług kryptograficznych dla klucza prywatnego lub publicznego certyfikatu, w zależności od parametrów przekazywania do metody.  
  
5. Opcjonalny. Zastąp <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> metody. Zastąp tę metodę, jeśli wymagana jest inna <xref:System.Security.Cryptography.HashAlgorithm> implementacja klasy.  
  
6. Zastąp <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> metody. Ta metoda zwraca wystąpienie <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> klasy skojarzonej z kluczem prywatnym certyfikatu.  
  
7. Zastąp <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> metody. Ta metoda służy do wskazywania, czy określony algorytm kryptograficzny jest obsługiwany przez implementację klucza zabezpieczeń.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 Poniższa procedura pokazuje, jak zintegrować niestandardową implementację klucza zabezpieczeń X. 509 utworzoną w poprzedniej procedurze z platformą zabezpieczeń WCF w celu zastąpienia dostarczonego przez system tokenu zabezpieczającego X. 509.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Aby zamienić określony przez system token zabezpieczający X. 509 z niestandardowym tokenem klucza zabezpieczeń X. 509  
  
1. Utwórz niestandardowy token zabezpieczający X. 509, który zwraca niestandardowy klucz zabezpieczeń X. 509, a nie klucz zabezpieczeń dostarczony przez system, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat niestandardowych tokenów [zabezpieczających, zobacz How to: Utwórz token](how-to-create-a-custom-token.md)niestandardowy.  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2. Utwórz niestandardowego dostawcę tokenów zabezpieczających, który zwraca niestandardowy token zabezpieczający X. 509, jak pokazano w przykładzie. Aby uzyskać więcej informacji o dostawcach niestandardowych tokenów [zabezpieczających, zobacz How to: Utwórz niestandardowego dostawcę](how-to-create-a-custom-security-token-provider.md)tokenów zabezpieczających.  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3. Jeśli na stronie inicjatora należy użyć niestandardowego klucza zabezpieczeń, należy utworzyć niestandardowe klasy Menedżer tokenów zabezpieczeń klienta i niestandardowe poświadczenia klienta, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat niestandardowych poświadczeń klienta i menedżerów tokenów [zabezpieczających klienta, zobacz Przewodnik: Tworzenie niestandardowych poświadczeń](walkthrough-creating-custom-client-and-service-credentials.md)klienta i usługi.  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4. Jeśli na stronie adresatów musi być używany niestandardowy klucz zabezpieczeń, Utwórz niestandardowy Menedżer tokenów zabezpieczeń usługi i poświadczenia usługi niestandardowej, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat poświadczeń usługi niestandardowych i menedżerów tokenów [zabezpieczeń usługi, zobacz Przewodnik: Tworzenie niestandardowych poświadczeń](walkthrough-creating-custom-client-and-service-credentials.md)klienta i usługi.  
  
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
- [Przewodnik: Tworzenie niestandardowych poświadczeń klienta i usługi](walkthrough-creating-custom-client-and-service-credentials.md)
- [Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](how-to-create-a-custom-security-token-authenticator.md)
- [Instrukcje: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](how-to-create-a-custom-security-token-provider.md)
- [Instrukcje: Tworzenie niestandardowego tokenu](how-to-create-a-custom-token.md)
