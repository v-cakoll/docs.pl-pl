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
ms.openlocfilehash: d471e860e74c9a01770c95671401bdbbc23643cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-token-handlers"></a><span data-ttu-id="9c459-102">Niestandardowe programy obsługi tokenu</span><span class="sxs-lookup"><span data-stu-id="9c459-102">Custom Token Handlers</span></span>
<span data-ttu-id="9c459-103">W tym temacie omówiono tokenu programy obsługi zdarzeń w wersji WIF i jak są one używane do przetwarzania tokenów.</span><span class="sxs-lookup"><span data-stu-id="9c459-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="9c459-104">Temat obejmuje również problemy, co jest niezbędne do utworzenia niestandardowych tokenu obsługi typów tokenu, które nie są obsługiwane w wersji WIF domyślnie.</span><span class="sxs-lookup"><span data-stu-id="9c459-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="9c459-105">Wprowadzenie do obsługi tokenu w WIF</span><span class="sxs-lookup"><span data-stu-id="9c459-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="9c459-106">WIF zależy od obsługi tokenu zabezpieczeń do tworzenia, odczytu, zapisu i sprawdzania poprawności tokenów dla jednostki uzależnionej aplikacji firmy (RP) lub usługę tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="9c459-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="9c459-107">Programy obsługi tokenu są punkty rozszerzeń dla możesz dodać niestandardowe programu obsługi tokenów w potoku WIF lub dostosować sposób zarządzania w programie istniejącego programu obsługi tokenów tokenów.</span><span class="sxs-lookup"><span data-stu-id="9c459-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="9c459-108">WIF udostępnia dziewięć obsługi tokenu zabezpieczeń, które mogą zostać zmodyfikowane lub całkowicie zastąpiona w celu zmiany funkcji w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="9c459-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="9c459-109">Token obsługi zabezpieczeń w WIF</span><span class="sxs-lookup"><span data-stu-id="9c459-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="9c459-110">Dziewięć klasy programu obsługi tokenów zabezpieczeń pochodzących od abstrakcyjna klasa podstawowa zawiera WIF 4.5 <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="9c459-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="9c459-111">Dodawanie niestandardowego programu obsługi tokenów</span><span class="sxs-lookup"><span data-stu-id="9c459-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="9c459-112">Niektóre typy tokenów, takie jak proste tokenów sieci Web (SWT) i tokenów sieci Web JSON (JWT) nie mają wbudowanej obsługi tokenu podał WIF.</span><span class="sxs-lookup"><span data-stu-id="9c459-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="9c459-113">Te typy tokenów i inne osoby, które nie mają wbudowanej obsługi należy wykonać następujące kroki, aby utworzyć niestandardowy program obsługi tokena.</span><span class="sxs-lookup"><span data-stu-id="9c459-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="9c459-114">Dodawanie niestandardowego programu obsługi tokenów</span><span class="sxs-lookup"><span data-stu-id="9c459-114">Adding a custom token handler</span></span>  
  
1.  <span data-ttu-id="9c459-115">Utwórz nową klasę, która jest pochodną <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="9c459-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2.  <span data-ttu-id="9c459-116">Zastąp następujące metody i własne implementacji:</span><span class="sxs-lookup"><span data-stu-id="9c459-116">Override the following methods and provide your own implementation:</span></span>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  <span data-ttu-id="9c459-117">Dodaj odwołanie do nowego niestandardowego programu obsługi tokenów w *Web.config* lub *App.config* pliku poziomu  **\<system.identityModel >** sekcja, która dotyczy WIF.</span><span class="sxs-lookup"><span data-stu-id="9c459-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="9c459-118">Na przykład następujący kod konfiguracji Określa nowy token program obsługi o nazwie **MyCustomTokenHandler** który znajduje się w **CustomToken** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9c459-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="9c459-119">Należy pamiętać, że jeśli udostępniasz własnego programu obsługi tokenów do obsługi typ tokenu, który ma już wbudowanego programu obsługi tokenów, należy dodać  **\<Usuń >** elementu, aby usunąć domyślny program obsługi i zamiast tego użyj programu obsługi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="9c459-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="9c459-120">Na przykład następująca konfiguracja zastępuje domyślny <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> z niestandardowego programu obsługi tokenów:</span><span class="sxs-lookup"><span data-stu-id="9c459-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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
