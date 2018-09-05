---
title: 'Porady: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 37827398ffd6041aa841e23381b6b072b297f089
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515453"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Porady: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń
W tym temacie pokazano, jak utworzyć nowe typy tokenów przy użyciu niestandardowego dostawcy tokenów zabezpieczeń i sposobu integracji dostawcę z Menedżer tokenów zabezpieczeń niestandardowych.  
  
> [!NOTE]
>  Tworzenie niestandardowego dostawcy tokenów, jeśli tokeny dostarczane przez system w <xref:System.IdentityModel.Tokens> przestrzeni nazw nie są zgodne z wymagań.  
  
 Dostawcy tokenów zabezpieczeń tworzy reprezentację tokenu zabezpieczeń, na podstawie informacji w poświadczeniach klienta lub usługę. Aby użyć niestandardowego dostawcy tokenów zabezpieczeń w usłudze security Windows Communication Foundation (WCF), należy utworzyć niestandardowe poświadczenia i implementacje Menedżer tokenów zabezpieczeń.  
  
 Aby uzyskać więcej informacji na temat niestandardowych poświadczeń i Menedżer tokenów zabezpieczeń zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Aby uzyskać więcej informacji na temat poświadczeń zabezpieczeń tokenu menedżera, dostawcy i wystawcy uwierzytelnienia klas, zobacz [architekturę zabezpieczeń](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
### <a name="to-create-a-custom-security-token-provider"></a>Aby utworzyć niestandardowego dostawcy tokenów zabezpieczeń  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy.  
  
2.  Implementowanie <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metody. Metoda jest odpowiedzialna za tworzenie i zwrócenia wystąpienia tokenu zabezpieczającego. Poniższy przykład tworzy klasę o nazwie `MySecurityTokenProvider`, przesłonięć i <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metodę, aby zwrócić wystąpienia <xref:System.IdentityModel.Tokens.X509SecurityToken> klasy. Konstruktor klasy wymaga wystąpienia <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Aby zintegrować niestandardowego dostawcy tokenów zabezpieczeń z usługą Menedżer tokenów zabezpieczeń niestandardowe  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy. (Poniższy przykład pochodzi z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy, która jest pochodną <xref:System.IdentityModel.Selectors.SecurityTokenManager> klasy.)  
  
2.  Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metody, jeśli nie jest już przesłonięty.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Metoda jest odpowiedzialna za zwrócenie wystąpienie <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy odpowiednie <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametr przekazywany do metody przez architekturę zabezpieczeń programu WCF. Zmodyfikować metodę, aby zwrócić implementację dostawcy tokenów zabezpieczeń niestandardowych (utworzonym w poprzedniej procedurze) kiedy metoda jest wywoływana z parametrem tokenu odpowiednie zabezpieczenia. Aby uzyskać więcej informacji na temat Menedżer tokenów zabezpieczeń, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
3.  Dodawanie logiki niestandardowej metody umożliwiającej mu do zwrócenia z niestandardowego dostawcy tokenów zabezpieczeń na podstawie <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametru. Poniższy przykład zwraca niestandardowego dostawcy tokenów zabezpieczeń, jeśli są spełnione wymagania tokenu. Wymagania obejmują token zabezpieczający X.509 i kierunek wiadomości (czy token jest używany przez dane wyjściowe komunikatu). W pozostałych przypadkach kod wywołuje klasę bazową, aby zapewnić odpowiednie zachowanie dostarczane przez system, pozostałe wymagania tokenu zabezpieczeń.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Przykład  
 Poniżej pokazano pełny <xref:System.IdentityModel.Selectors.SecurityTokenProvider> wdrożenia wraz z odpowiednią <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementacji.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [Przewodnik: tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Instrukcje: tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Architektura zabezpieczeń](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
