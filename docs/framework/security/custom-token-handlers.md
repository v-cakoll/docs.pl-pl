---
title: "Niestandardowe programy obsługi tokenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 56fb7fcb162025ec05bc1171cb137d445c4dfee5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="custom-token-handlers"></a>Niestandardowe programy obsługi tokenu
W tym temacie omówiono tokenu programy obsługi zdarzeń w wersji WIF i jak są one używane do przetwarzania tokenów. Temat obejmuje również problemy, co jest niezbędne do utworzenia niestandardowych tokenu obsługi typów tokenu, które nie są obsługiwane w wersji WIF domyślnie.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>Wprowadzenie do obsługi tokenu w WIF  
 WIF zależy od obsługi tokenu zabezpieczeń do tworzenia, odczytu, zapisu i sprawdzania poprawności tokenów dla jednostki uzależnionej aplikacji firmy (RP) lub usługę tokenu zabezpieczającego (STS). Programy obsługi tokenu są punkty rozszerzeń dla możesz dodać niestandardowe programu obsługi tokenów w potoku WIF lub dostosować sposób zarządzania w programie istniejącego programu obsługi tokenów tokenów. WIF udostępnia dziewięć obsługi tokenu zabezpieczeń, które mogą zostać zmodyfikowane lub całkowicie zastąpiona w celu zmiany funkcji w razie potrzeby.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>Token obsługi zabezpieczeń w WIF  
 Dziewięć klasy programu obsługi tokenów zabezpieczeń pochodzących od abstrakcyjna klasa podstawowa zawiera WIF 4.5 <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Dodawanie niestandardowego programu obsługi tokenów  
 Niektóre typy tokenów, takie jak proste tokenów sieci Web (SWT) i tokenów sieci Web JSON (JWT) nie mają wbudowanej obsługi tokenu podał WIF. Te typy tokenów i inne osoby, które nie mają wbudowanej obsługi należy wykonać następujące kroki, aby utworzyć niestandardowy program obsługi tokena.  
  
#### <a name="adding-a-custom-token-handler"></a>Dodawanie niestandardowego programu obsługi tokenów  
  
1.  Utwórz nową klasę, która jest pochodną <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2.  Zastąp następujące metody i własne implementacji:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  Dodaj odwołanie do nowego niestandardowego programu obsługi tokenów w *Web.config* lub *App.config* pliku poziomu  **\<system.identityModel >** sekcja, która dotyczy WIF. Na przykład następujący kod konfiguracji Określa nowy token program obsługi o nazwie **MyCustomTokenHandler** który znajduje się w **CustomToken** przestrzeni nazw.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Należy pamiętać, że jeśli udostępniasz własnego programu obsługi tokenów do obsługi typ tokenu, który ma już wbudowanego programu obsługi tokenów, należy dodać  **\<Usuń >** elementu, aby usunąć domyślny program obsługi i zamiast tego użyj programu obsługi niestandardowej. Na przykład następująca konfiguracja zastępuje domyślny <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> z niestandardowego programu obsługi tokenów:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789">  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
