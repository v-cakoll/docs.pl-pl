---
title: "Porady: zestaw Max niedokładność zegara"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 16dc6c7dfc474a04e6f3b27db0efd8fb2ca78b82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="93841-102">Porady: zestaw Max niedokładność zegara</span><span class="sxs-lookup"><span data-stu-id="93841-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="93841-103">Funkcje o krytycznym znaczeniu czasu można derailed, jeśli są różne ustawienia zegara na dwóch komputerach.</span><span class="sxs-lookup"><span data-stu-id="93841-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="93841-104">Aby ograniczyć to ryzyko, można ustawić `MaxClockSkew` właściwości <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="93841-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="93841-105">Ta właściwość jest dostępna na dwie klasy:</span><span class="sxs-lookup"><span data-stu-id="93841-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93841-106">Ważne dla bezpiecznej konwersacji, zmienia się na `MaxClockSkew` muszą być wprowadzane właściwości, gdy jest zainicjowano usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="93841-106">Important   For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="93841-107">Aby to zrobić, należy ustawić właściwość na <xref:System.ServiceModel.Channels.SecurityBindingElement> zwrócony przez <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="93841-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span></span>  
  
 <span data-ttu-id="93841-108">Aby zmienić właściwości na jednym z powiązania dostarczane przez system, należy odnaleźć w kolekcji powiązania elementu powiązania zabezpieczeń i ustawić `MaxClockSkew` właściwości na nową wartość.</span><span class="sxs-lookup"><span data-stu-id="93841-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="93841-109">Dwie klasy pochodzi od <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="93841-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="93841-110">Podczas pobierania powiązania zabezpieczeń z kolekcji, należy rzutowanie do jednego z następujących typów, aby poprawnie ustawić `MaxClockSkew` właściwości.</span><span class="sxs-lookup"><span data-stu-id="93841-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="93841-111">W poniższym przykładzie użyto <xref:System.ServiceModel.WSHttpBinding>, który korzysta z <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="93841-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="93841-112">Aby uzyskać listę, która określa typ powiązania zabezpieczeń do użycia w każdego powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="93841-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="93841-113">Aby utworzyć niestandardowego powiązania z zegarem nowe pochylanie wartości w kodzie</span><span class="sxs-lookup"><span data-stu-id="93841-113">To create a custom binding with a new clock skew value in code</span></span>  
  
1.  > [!WARNING]
    >  <span data-ttu-id="93841-114">Należy pamiętać, dodaj odwołania do następujących przestrzeni nazw w kodzie: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, i <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="93841-114">Note   Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
     <span data-ttu-id="93841-115">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="93841-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
2.  <span data-ttu-id="93841-116">Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.Channels.BindingElementCollection> klasy przez wywołanie metody <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="93841-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="93841-117">Użyj <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody <xref:System.ServiceModel.Channels.BindingElementCollection> klasy można znaleźć elementu powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="93841-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4.  <span data-ttu-id="93841-118">Korzystając z <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody rzutowany na typ rzeczywistego.</span><span class="sxs-lookup"><span data-stu-id="93841-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="93841-119">Przykład poniżej rzutowania do <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typu.</span><span class="sxs-lookup"><span data-stu-id="93841-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5.  <span data-ttu-id="93841-120">Ustaw <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> właściwość elementu powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="93841-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6.  <span data-ttu-id="93841-121">Utwórz <xref:System.ServiceModel.ServiceHost> przy użyciu adresu typu i base odpowiednią usługę.</span><span class="sxs-lookup"><span data-stu-id="93841-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7.  <span data-ttu-id="93841-122">Użyj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metodę, aby dodać punkt końcowy i obejmują <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="93841-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="93841-123">Aby ustawić MaxClockSkew w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="93841-123">To set the MaxClockSkew in configuration</span></span>  
  
1.  <span data-ttu-id="93841-124">Utwórz [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) w [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="93841-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2.  <span data-ttu-id="93841-125">Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="93841-125">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="93841-126">Poniższy przykład ustawia ją na `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="93841-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3.  <span data-ttu-id="93841-127">Dodaj element kodowania.</span><span class="sxs-lookup"><span data-stu-id="93841-127">Add an encoding element.</span></span> <span data-ttu-id="93841-128">W poniższym przykładzie dodaje [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="93841-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4.  <span data-ttu-id="93841-129">Dodaj [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element i ustaw `authenticationMode` atrybutu odpowiednie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="93841-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="93841-130">Poniższy przykład ustaw dla atrybutu `Kerberos` do określenia, że usługa używa uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="93841-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5.  <span data-ttu-id="93841-131">Dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybut na wartość w formie `"##:##:##"`.</span><span class="sxs-lookup"><span data-stu-id="93841-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="93841-132">Poniższy przykład ustawia ją na 7 minut.</span><span class="sxs-lookup"><span data-stu-id="93841-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="93841-133">Opcjonalnie dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybutu odpowiednie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="93841-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6.  <span data-ttu-id="93841-134">Dodaj element transportu.</span><span class="sxs-lookup"><span data-stu-id="93841-134">Add a transport element.</span></span> <span data-ttu-id="93841-135">W poniższym przykładzie użyto [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="93841-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7.  <span data-ttu-id="93841-136">Dla bezpiecznej konwersacji, ustawienia zabezpieczeń musi być bootstrap w [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="93841-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="93841-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93841-137">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="93841-138">Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="93841-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
