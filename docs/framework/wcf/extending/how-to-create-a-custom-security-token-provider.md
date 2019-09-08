---
title: 'Instrukcje: tworzenie niestandardowego dostawcy tokenów zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
ms.openlocfilehash: 1ca12274358ed6de475b0c2b8b47dd5cb52e941e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797035"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Instrukcje: tworzenie niestandardowego dostawcy tokenów zabezpieczeń
W tym temacie pokazano, jak utworzyć nowe typy tokenów za pomocą niestandardowego dostawcy tokenów zabezpieczających oraz jak zintegrować dostawcę z menedżerem niestandardowego tokenu zabezpieczeń.  
  
> [!NOTE]
> Utwórz niestandardowego dostawcę tokenów, jeśli tokeny dostarczone przez system w <xref:System.IdentityModel.Tokens> przestrzeni nazw nie pasują do Twoich wymagań.  
  
 Dostawca tokenów zabezpieczających tworzy reprezentację tokenu zabezpieczającego na podstawie informacji zawartych w poświadczeniach klienta lub usługi. Aby użyć niestandardowego dostawcy tokenów zabezpieczeń w ramach zabezpieczeń programu Windows Communication Foundation (WCF), należy utworzyć niestandardowe poświadczenia i implementacje Menedżera tokenów zabezpieczających.  
  
 Aby uzyskać więcej informacji na temat poświadczeń niestandardowych i Menedżera tokenów [zabezpieczających, zobacz Przewodnik: Tworzenie niestandardowych poświadczeń](walkthrough-creating-custom-client-and-service-credentials.md)klienta i usługi.  
  
### <a name="to-create-a-custom-security-token-provider"></a>Aby utworzyć niestandardowego dostawcę tokenów zabezpieczających  
  
1. Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy.  
  
2. Zaimplementuj <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metodę. Metoda jest odpowiedzialna za utworzenie i zwrócenie wystąpienia tokenu zabezpieczającego. Poniższy przykład tworzy klasę o nazwie `MySecurityTokenProvider`i <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> zastępuje metodę <xref:System.IdentityModel.Tokens.X509SecurityToken> zwracającą wystąpienie klasy. Konstruktor klasy wymaga wystąpienia <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Aby zintegrować niestandardowego dostawcę tokenów zabezpieczających z menedżerem niestandardowego tokenu zabezpieczeń  
  
1. Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy. (Poniższy przykład pochodzi od <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy, która pochodzi <xref:System.IdentityModel.Selectors.SecurityTokenManager> od klasy).  
  
2. Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metodę, jeśli nie została jeszcze przesłonięta.  
  
     Metoda jest odpowiedzialna za zwracanie wystąpienia <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy właściwej <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> dla parametru przesłanego do metody przez strukturę zabezpieczeń WCF. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Zmodyfikuj metodę w celu zwrócenia niestandardowej implementacji dostawcy tokenów zabezpieczeń (utworzonej w poprzedniej procedurze), gdy metoda jest wywoływana z odpowiednim parametrem tokenu zabezpieczającego. Aby uzyskać więcej informacji na temat Menedżera tokenów zabezpieczeń, [zobacz Przewodnik: Tworzenie niestandardowych poświadczeń](walkthrough-creating-custom-client-and-service-credentials.md)klienta i usługi.  
  
3. Dodaj logikę niestandardową do metody, aby umożliwić jej zwrócenie niestandardowego dostawcy tokenów zabezpieczających <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> na podstawie parametru. Poniższy przykład zwraca niestandardowego dostawcę tokenów zabezpieczających w przypadku spełnienia wymagań dotyczących tokenu. Wymagania obejmują token zabezpieczający X. 509 oraz kierunek komunikatów (używany token do wyprowadzania wiadomości). We wszystkich innych przypadkach kod wywołuje klasę bazową, aby zachować zachowanie dostarczone przez system dla innych wymagań dotyczących tokenów zabezpieczających.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono kompletną <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementację wraz z odpowiadającą <xref:System.IdentityModel.Selectors.SecurityTokenManager> jej implementacją.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.X509SecurityToken>
- [Przewodnik: Tworzenie niestandardowych poświadczeń klienta i usługi](walkthrough-creating-custom-client-and-service-credentials.md)
- [Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](how-to-create-a-custom-security-token-authenticator.md)
