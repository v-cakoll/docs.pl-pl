---
title: Niestandardowe programy obsługi tokenów
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: b6b84271fc450a325270bad5f9e0355fe81a8a5c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312114"
---
# <a name="custom-token-handlers"></a>Niestandardowe programy obsługi tokenów
W tym temacie omówiono programy obsługi tokenów programu WIF i jak są one używane do przetwarzania tokenów. Temat obejmuje także, co jest potrzebne utworzyć niestandardowe programy obsługi tokenów dla tokenu typów, które nie są obsługiwane w WIF domyślnie.  
  
## <a name="introduction-to-token-handlers-in-wif"></a>Wprowadzenie do programy obsługi tokenów w programu WIF  
 Program WIF opiera się na programy obsługi tokenów zabezpieczających do tworzenia, odczytu, zapisu i sprawdzania poprawności tokenów dla aplikacji jednostki uzależnionej (RP) lub usługę tokenu zabezpieczającego (STS). Programy obsługi tokenów są punkty rozszerzeń dla użytkownika do dodawania programu obsługi tokenów niestandardowych w potoku programu WIF lub dostosować sposób, że istniejącego programu obsługi tokenów zarządza tokenów. Program WIF udostępnia dziewięć wbudowanych programy obsługi tokenów zabezpieczających, które mogą zostać zmodyfikowane lub całkowicie zastąpiona w celu zmiany funkcji zgodnie z potrzebami.  
  
## <a name="built-in-security-token-handlers-in-wif"></a>Programy obsługi tokenów zabezpieczeń wbudowanych w program WIF  
 Program WIF 4.5 zawiera dziewięć klasy programu obsługi tokenów zabezpieczeń, które wynikają z abstrakcyjna klasa bazowa <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>Dodawanie programu obsługi tokenów niestandardowych  
 Niektóre typy tokenów, takich jak proste tokenów sieci Web (SWT) i tokenów Web JSON (JWT) nie mają wbudowane programy obsługi tokenów, dostarczone przez programu WIF. Te typy tokenów i inne osoby, które nie mają wbudowanej obsługi należy wykonać następujące kroki, aby utworzyć niestandardowy program obsługi tokena.  
  
#### <a name="adding-a-custom-token-handler"></a>Dodawanie programu obsługi tokenów niestandardowych  
  
1. Utwórz nową klasę, która pochodzi od klasy <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2. Zastąpić następujące metody i podaj Twojej własnej implementacji:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. Dodaj odwołanie do nowego niestandardowego programu obsługi tokenów w *Web.config* lub *App.config* plików w ramach  **\<system.identityModel >** sekcji, która ma zastosowanie do programu WIF. Na przykład, następujące znaczniki konfiguracji Określa nowy token programu obsługi o nazwie **MyCustomTokenHandler** które znajdują się na **CustomToken** przestrzeni nazw.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Należy pamiętać, że jeśli udostępniasz własnego programu obsługi tokenów, aby obsłużyć typ tokenu, który ma już wbudowanego programu obsługi tokenów, należy dodać  **\<Usuń >** element, aby usunąć domyślny program obsługi i zamiast tego użyj programu obsługi niestandardowych. Na przykład następująca konfiguracja zastępuje domyślny <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> za pomocą programu obsługi tokenów niestandardowych:  
  
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
