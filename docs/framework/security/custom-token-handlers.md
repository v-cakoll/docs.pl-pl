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
# <a name="custom-token-handlers"></a><span data-ttu-id="a13e1-102">Niestandardowe programy obsługi tokenów</span><span class="sxs-lookup"><span data-stu-id="a13e1-102">Custom Token Handlers</span></span>
<span data-ttu-id="a13e1-103">W tym temacie omówiono programy obsługi tokenów w WIF oraz sposób ich używania do przetwarzania tokenów.</span><span class="sxs-lookup"><span data-stu-id="a13e1-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="a13e1-104">Temat zawiera również informacje o tym, co jest niezbędne do tworzenia niestandardowych obsługi tokenów dla typów tokenów, które nie są obsługiwane domyślnie w WIF.</span><span class="sxs-lookup"><span data-stu-id="a13e1-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="a13e1-105">Wprowadzenie do obsługi tokenów w WIF</span><span class="sxs-lookup"><span data-stu-id="a13e1-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="a13e1-106">WIF polega na obsłudze tokenów zabezpieczających do tworzenia, odczytywania, zapisywania i weryfikowania tokenów dla aplikacji jednostki uzależnionej (RP) lub usługi tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="a13e1-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="a13e1-107">Obsługa tokenów to punkty rozszerzalności umożliwiające dodanie niestandardowego programu obsługi tokenów w potoku WIF lub dostosowanie sposobu, w jaki istniejący program obsługi tokenów zarządza tokenami.</span><span class="sxs-lookup"><span data-stu-id="a13e1-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="a13e1-108">WIF zawiera dziewięć wbudowanych programów obsługi tokenów zabezpieczających, które mogą być modyfikowane lub całkowicie zastępowane w celu zmiany funkcjonalności w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="a13e1-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="a13e1-109">Wbudowane programy obsługi tokenów zabezpieczających w programie WIF</span><span class="sxs-lookup"><span data-stu-id="a13e1-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="a13e1-110">WIF 4,5 obejmuje dziewięć klas obsługi tokenów zabezpieczających, które pochodzą od abstrakcyjnej klasy bazowej <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="a13e1-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="a13e1-111">Dodawanie niestandardowego programu obsługi tokenów</span><span class="sxs-lookup"><span data-stu-id="a13e1-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="a13e1-112">Niektóre typy tokenów, takie jak proste tokeny sieci Web (SWT) i tokeny sieci Web JSON (JWT), nie mają wbudowanych programów obsługi tokenów udostępnianych przez WIF.</span><span class="sxs-lookup"><span data-stu-id="a13e1-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="a13e1-113">Dla tych typów tokenów i dla innych, które nie mają wbudowanej procedury obsługi, należy wykonać następujące kroki, aby utworzyć niestandardową procedurę obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="a13e1-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="a13e1-114">Dodawanie niestandardowego programu obsługi tokenów</span><span class="sxs-lookup"><span data-stu-id="a13e1-114">Adding a custom token handler</span></span>  
  
1. <span data-ttu-id="a13e1-115">Utwórz nową klasę pochodzącą z <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="a13e1-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2. <span data-ttu-id="a13e1-116">Zastąp następujące metody i podaj własną implementację:</span><span class="sxs-lookup"><span data-stu-id="a13e1-116">Override the following methods and provide your own implementation:</span></span>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. <span data-ttu-id="a13e1-117">Dodaj odwołanie do nowego niestandardowego programu obsługi tokenów w pliku *Web. config* lub *App. config* w sekcji **\<system. IdentityModel >** , która odnosi się do WIF.</span><span class="sxs-lookup"><span data-stu-id="a13e1-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="a13e1-118">Na przykład poniższy znacznik konfiguracji określa nowy program obsługi tokenów o nazwie **MyCustomTokenHandler** , który znajduje się w przestrzeni nazw **CustomToken** .</span><span class="sxs-lookup"><span data-stu-id="a13e1-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="a13e1-119">Należy pamiętać, że jeśli udostępniasz własny program obsługi tokenów do obsługi typu tokenu, który ma już wbudowaną procedurę obsługi tokenów, musisz dodać **\<Usuń element >** , aby usunąć domyślną procedurę obsługi i zamiast tego użyć niestandardowej procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="a13e1-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="a13e1-120">Na przykład następująca konfiguracja zastępuje domyślne <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> przy użyciu niestandardowego programu obsługi tokenów:</span><span class="sxs-lookup"><span data-stu-id="a13e1-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
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
