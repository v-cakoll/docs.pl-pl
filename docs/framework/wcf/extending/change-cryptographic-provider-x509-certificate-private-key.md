---
title: 'Porady: zmienianie dostawcy kryptograficznego dla certyfikatu X.509&#39;s klucza prywatnego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: 633e87bca302adc0963e1bf52d2470c9dbae81a5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificate39s-private-key"></a>Porady: zmienianie dostawcy kryptograficznego dla certyfikatu X.509&#39;s klucza prywatnego
W tym temacie pokazano sposób zintegrować dostawcy przez strukturę zabezpieczeń systemu Windows Communication Foundation (WCF) oraz sposobu zmiany dostawcy usług kryptograficznych, umożliwiające uzyskanie klucza prywatnego certyfikatu X.509. Aby uzyskać więcej informacji o korzystaniu z certyfikatów, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Struktura zabezpieczeń WCF umożliwia wprowadzenie nowych typów tokenu zabezpieczeń, zgodnie z opisem w [porady: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md). Użytkownik może również używać niestandardowy token, aby zastąpić istniejące typy tokenów dostarczane przez system.  
  
 W tym temacie tokenu zabezpieczającego X.509 dostarczane przez system zastępuje niestandardowy token X.509, który zawiera inną implementację dla klucza prywatnego certyfikatu. Jest to przydatne w scenariuszach, w którym podano rzeczywistego klucza prywatnego przez dostawcę usług kryptograficznych innego niż domyślny dostawca usług kryptograficznych systemu Windows. Przykładem alternatywnego dostawcy usług kryptograficznych jest sprzętowego modułu zabezpieczeń, który wykonuje wszystkie prywatnego klucza pokrewne operacje kryptograficzne, a nie przechowywania kluczy prywatnych w pamięci, co poprawia zabezpieczeń systemu.  
  
 Poniższy przykład jest tylko w celach demonstracyjnych. Nie zastępuje domyślny dostawca usług kryptograficznych systemu Windows, ale zawiera, gdzie można zintegrować takiego dostawcy.  
  
## <a name="procedures"></a>Procedury  
 Każdy token zabezpieczający, który ma skojarzony klucz lub klucze musi implementować <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> właściwość, która zwraca kolekcję kluczy z wystąpienia tokenu zabezpieczeń. Jeśli token jest tokenem zabezpieczającym X.509, Kolekcja zawiera pojedyncze wystąpienie <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> klasa, która reprezentuje klucze publiczny i prywatny skojarzony z certyfikatem. Aby zastąpić domyślny dostawca usług kryptograficznych używane w celu dostarczania kluczy do certyfikatu, Utwórz nową implementacją tej klasy.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Aby utworzyć niestandardowe klucza asymetrycznego X.509  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> klasy.  
  
2.  Zastąpienie <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> właściwości tylko do odczytu. Ta właściwość zwraca rzeczywisty rozmiar klucza certyfikatu pary kluczy publiczny/prywatny.  
  
3.  Zastąpienie <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> metody. Ta metoda jest wywoływana przez strukturę zabezpieczeń WCF do odszyfrowania klucza symetrycznego klucza prywatnego certyfikatu. (Klucz został wcześniej zaszyfrowany z użyciem klucza publicznego certyfikatu).  
  
4.  Zastąpienie <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> metody. Ta metoda jest wywoływana przez strukturę zabezpieczeń WCF można uzyskać wystąpienia <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasa, która reprezentuje dostawcy usług kryptograficznych dla jego certyfikat prywatny lub publiczny klucz, w zależności od parametrów przekazane do metody.  
  
5.  Opcjonalna. Zastąpienie <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> metody. Przesłonić tę metodę, jeśli różne implementacje <xref:System.Security.Cryptography.HashAlgorithm> klasa jest wymagana.  
  
6.  Zastąpienie <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> metody. Ta metoda zwraca wystąpienie klasy <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> klasy, która jest skojarzona z klucza prywatnego certyfikatu.  
  
7.  Zastąpienie <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> metody. Ta metoda jest używana w celu wskazania, czy konkretnego algorytmu kryptograficznego jest obsługiwana przez implementację klucza zabezpieczeń.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 Poniższa procedura przedstawia sposób integrowanie niestandardowych X.509 asymetrycznego klucza implementacji zabezpieczeń utworzony w poprzedniej procedurze z architekturą WCF zabezpieczeń, aby zastąpić zabezpieczeń X.509 dostarczane przez system tokenu.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Aby zastąpić niestandardowy token klucza asymetrycznego zabezpieczeń X.509 tokenu zabezpieczającego X.509 dostarczane przez system  
  
1.  Tworzenie niestandardowych token zabezpieczający X.509, który zwraca niestandardowe klucza asymetrycznego zabezpieczeń X.509 zamiast klucza dostarczane przez system zabezpieczeń, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat tokeny zabezpieczające niestandardowych, zobacz [porady: Tworzenie niestandardowego tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2.  Utwórz zabezpieczeń niestandardowego dostawcę tokenów, który zwraca token zabezpieczający X.509 niestandardowych, jak pokazano w przykładzie. Aby uzyskać więcej informacji na temat dostawcy tokenów zabezpieczeń niestandardowych, zobacz [porady: Tworzenie niestandardowego dostawcy tokenów zabezpieczających](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3.  Jeśli klucz niestandardowy zabezpieczeń musi być używane po stronie inicjatora, Utwórz niestandardowe klienta, Menedżer tokenów zabezpieczających i klasy poświadczenia niestandardowego klienta, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji o poświadczenia niestandardowego klienta i menedżerów tokenu zabezpieczeń klienta, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4.  Jeśli klucz niestandardowy zabezpieczeń musi być używane po stronie odbiorcy, Utwórz niestandardowe usługi Menedżer tokenów zabezpieczających i poświadczeń usługi niestandardowych, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat niestandardowe poświadczenia i menedżerów tokenu zabezpieczeń usługi, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>  
 <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.Security.Cryptography.AsymmetricAlgorithm>  
 <xref:System.Security.Cryptography.HashAlgorithm>  
 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>  
 [Przewodnik: tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Instrukcje: tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Instrukcje: tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Instrukcje: tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)  
 [Architektura zabezpieczeń](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
