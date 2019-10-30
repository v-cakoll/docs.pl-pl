---
title: Niestandardowe programy obsługi tokenów
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: ccf794b4c229bbc9b40ae7ec2fd649825122cecf
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040557"
---
# <a name="custom-token-handlers"></a>Niestandardowe programy obsługi tokenów
W tym temacie omówiono programy obsługi tokenów w WIF oraz sposób ich używania do przetwarzania tokenów. Temat zawiera również informacje o tym, co jest niezbędne do tworzenia niestandardowych obsługi tokenów dla typów tokenów, które nie są obsługiwane domyślnie w WIF.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>Wprowadzenie do obsługi tokenów w WIF  
 WIF polega na obsłudze tokenów zabezpieczających do tworzenia, odczytywania, zapisywania i weryfikowania tokenów dla aplikacji jednostki uzależnionej (RP) lub usługi tokenu zabezpieczającego (STS). Obsługa tokenów to punkty rozszerzalności umożliwiające dodanie niestandardowego programu obsługi tokenów w potoku WIF lub dostosowanie sposobu, w jaki istniejący program obsługi tokenów zarządza tokenami. WIF zawiera dziewięć wbudowanych programów obsługi tokenów zabezpieczających, które mogą być modyfikowane lub całkowicie zastępowane w celu zmiany funkcjonalności w razie potrzeby.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>Wbudowane programy obsługi tokenów zabezpieczających w programie WIF  
 WIF 4,5 obejmuje dziewięć klas obsługi tokenów zabezpieczających, które pochodzą od abstrakcyjnej klasy bazowej <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Dodawanie niestandardowego programu obsługi tokenów  
 Niektóre typy tokenów, takie jak proste tokeny sieci Web (SWT) i tokeny sieci Web JSON (JWT), nie mają wbudowanych programów obsługi tokenów udostępnianych przez WIF. Dla tych typów tokenów i dla innych, które nie mają wbudowanej procedury obsługi, należy wykonać następujące kroki, aby utworzyć niestandardową procedurę obsługi tokenów.  
  
#### <a name="adding-a-custom-token-handler"></a>Dodawanie niestandardowego programu obsługi tokenów  
  
1. Utwórz nową klasę pochodzącą z <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2. Zastąp następujące metody i podaj własną implementację:  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. Dodaj odwołanie do nowego niestandardowego programu obsługi tokenów w pliku *Web. config* lub *App. config* w sekcji **\<system. IdentityModel >** , która odnosi się do WIF. Na przykład poniższy znacznik konfiguracji określa nowy program obsługi tokenów o nazwie **MyCustomTokenHandler** , który znajduje się w przestrzeni nazw **CustomToken** .  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Należy pamiętać, że jeśli udostępniasz własny program obsługi tokenów do obsługi typu tokenu, który ma już wbudowaną procedurę obsługi tokenów, musisz dodać **\<Usuń element >** , aby usunąć domyślną procedurę obsługi i zamiast tego użyć niestandardowej procedury obsługi. Na przykład następująca konfiguracja zastępuje domyślne <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> przy użyciu niestandardowego programu obsługi tokenów:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789" />  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
