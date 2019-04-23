---
title: Niestandardowe programy obsługi tokenów
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: b6b84271fc450a325270bad5f9e0355fe81a8a5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975679"
---
# <a name="custom-token-handlers"></a><span data-ttu-id="a1112-102">Niestandardowe programy obsługi tokenów</span><span class="sxs-lookup"><span data-stu-id="a1112-102">Custom Token Handlers</span></span>
<span data-ttu-id="a1112-103">W tym temacie omówiono programy obsługi tokenów programu WIF i jak są one używane do przetwarzania tokenów.</span><span class="sxs-lookup"><span data-stu-id="a1112-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="a1112-104">Temat obejmuje także, co jest potrzebne utworzyć niestandardowe programy obsługi tokenów dla tokenu typów, które nie są obsługiwane w WIF domyślnie.</span><span class="sxs-lookup"><span data-stu-id="a1112-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="a1112-105">Wprowadzenie do programy obsługi tokenów w programu WIF</span><span class="sxs-lookup"><span data-stu-id="a1112-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="a1112-106">Program WIF opiera się na programy obsługi tokenów zabezpieczających do tworzenia, odczytu, zapisu i sprawdzania poprawności tokenów dla aplikacji jednostki uzależnionej (RP) lub usługę tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="a1112-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="a1112-107">Programy obsługi tokenów są punkty rozszerzeń dla użytkownika do dodawania programu obsługi tokenów niestandardowych w potoku programu WIF lub dostosować sposób, że istniejącego programu obsługi tokenów zarządza tokenów.</span><span class="sxs-lookup"><span data-stu-id="a1112-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="a1112-108">Program WIF udostępnia dziewięć wbudowanych programy obsługi tokenów zabezpieczających, które mogą zostać zmodyfikowane lub całkowicie zastąpiona w celu zmiany funkcji zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="a1112-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="a1112-109">Programy obsługi tokenów zabezpieczeń wbudowanych w program WIF</span><span class="sxs-lookup"><span data-stu-id="a1112-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="a1112-110">Program WIF 4.5 zawiera dziewięć klasy programu obsługi tokenów zabezpieczeń, które wynikają z abstrakcyjna klasa bazowa <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="a1112-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="a1112-111">Dodawanie programu obsługi tokenów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a1112-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="a1112-112">Niektóre typy tokenów, takich jak proste tokenów sieci Web (SWT) i tokenów Web JSON (JWT) nie mają wbudowane programy obsługi tokenów, dostarczone przez programu WIF.</span><span class="sxs-lookup"><span data-stu-id="a1112-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="a1112-113">Te typy tokenów i inne osoby, które nie mają wbudowanej obsługi należy wykonać następujące kroki, aby utworzyć niestandardowy program obsługi tokena.</span><span class="sxs-lookup"><span data-stu-id="a1112-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="a1112-114">Dodawanie programu obsługi tokenów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a1112-114">Adding a custom token handler</span></span>  
  
1. <span data-ttu-id="a1112-115">Utwórz nową klasę, która pochodzi od klasy <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="a1112-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2. <span data-ttu-id="a1112-116">Zastąpić następujące metody i podaj Twojej własnej implementacji:</span><span class="sxs-lookup"><span data-stu-id="a1112-116">Override the following methods and provide your own implementation:</span></span>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. <span data-ttu-id="a1112-117">Dodaj odwołanie do nowego niestandardowego programu obsługi tokenów w *Web.config* lub *App.config* plików w ramach  **\<system.identityModel >** sekcji, która ma zastosowanie do programu WIF.</span><span class="sxs-lookup"><span data-stu-id="a1112-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="a1112-118">Na przykład, następujące znaczniki konfiguracji Określa nowy token programu obsługi o nazwie **MyCustomTokenHandler** które znajdują się na **CustomToken** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a1112-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="a1112-119">Należy pamiętać, że jeśli udostępniasz własnego programu obsługi tokenów, aby obsłużyć typ tokenu, który ma już wbudowanego programu obsługi tokenów, należy dodać  **\<Usuń >** element, aby usunąć domyślny program obsługi i zamiast tego użyj programu obsługi niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a1112-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="a1112-120">Na przykład następująca konfiguracja zastępuje domyślny <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> za pomocą programu obsługi tokenów niestandardowych:</span><span class="sxs-lookup"><span data-stu-id="a1112-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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
