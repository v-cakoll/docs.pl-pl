---
title: <windows> z <clientCredentials> — Element
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: b5e92745b9e39534d2a0bc35504c2dbc8346d2ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769723"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="e5048-102">\<Windows > z \<clientCredentials > Element</span><span class="sxs-lookup"><span data-stu-id="e5048-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="e5048-103">Określa ustawienia dla poświadczenia Windows do użycia do reprezentacji klienta.</span><span class="sxs-lookup"><span data-stu-id="e5048-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="e5048-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e5048-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5048-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="e5048-105">\<behaviors></span></span>  
<span data-ttu-id="e5048-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e5048-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e5048-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e5048-107">\<behavior></span></span>  
<span data-ttu-id="e5048-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e5048-108">\<clientCredentials></span></span>  
<span data-ttu-id="e5048-109">\<windows></span><span class="sxs-lookup"><span data-stu-id="e5048-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5048-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5048-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5048-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e5048-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e5048-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e5048-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5048-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e5048-113">Attributes</span></span>  
  
|<span data-ttu-id="e5048-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e5048-114">Attribute</span></span>|<span data-ttu-id="e5048-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e5048-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="e5048-116">Ustawia preferencje personifikacji, który klient komunikuje się z serwerem.</span><span class="sxs-lookup"><span data-stu-id="e5048-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="e5048-117">Tryb personifikacji, który klient wybiera nie są wymuszane na serwerze.</span><span class="sxs-lookup"><span data-stu-id="e5048-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="e5048-118">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="e5048-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e5048-119">— Identyfikator: Serwer można uzyskać tożsamości i uprawnień klienta, ale nie można spersonifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="e5048-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="e5048-120">-Personifikacji: Serwer może personifikować klienta kontekstu zabezpieczeń w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e5048-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="e5048-121">-Delegowania: Serwer może personifikować klienta kontekstu zabezpieczeń w systemach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="e5048-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="e5048-122">-Anonimowe: Serwer nie może spersonifikować lub identyfikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="e5048-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="e5048-123">-Brak: Nie przypisano poziom personifikacji.</span><span class="sxs-lookup"><span data-stu-id="e5048-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="e5048-124">Wartość domyślna to identyfikator.</span><span class="sxs-lookup"><span data-stu-id="e5048-124">The default is Identification.</span></span> <span data-ttu-id="e5048-125">Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="e5048-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="e5048-126">Ustawienie tej właściwości na `true` umożliwia uwierzytelnianie do poziomu starszej wersji NTLM, jeżeli protokół Kerberos nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="e5048-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="e5048-127">Ustawienie tej właściwości na `false` powoduje, że Windows Communication Foundation (WCF) umożliwiają staranności do zgłoszenia wyjątku, jeśli używane jest uwierzytelnianie NTLM.</span><span class="sxs-lookup"><span data-stu-id="e5048-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="e5048-128">Należy pamiętać, że ustawienie tej właściwości na `false` może uniemożliwia poświadczeń NTLM są przesyłane przez sieć.</span><span class="sxs-lookup"><span data-stu-id="e5048-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5048-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e5048-129">Child Elements</span></span>  
 <span data-ttu-id="e5048-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="e5048-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5048-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e5048-131">Parent Elements</span></span>  
  
|<span data-ttu-id="e5048-132">Element</span><span class="sxs-lookup"><span data-stu-id="e5048-132">Element</span></span>|<span data-ttu-id="e5048-133">Opis</span><span class="sxs-lookup"><span data-stu-id="e5048-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5048-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e5048-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="e5048-135">Określa poświadczenia używane do uwierzytelniania klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="e5048-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5048-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5048-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="e5048-137">Zabezpieczanie klientów</span><span class="sxs-lookup"><span data-stu-id="e5048-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="e5048-138">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="e5048-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e5048-139">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e5048-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
