---
title: 'Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 1a8d99e5d2bd21a74318718f43b5d1c091ed073e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047545"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="445c4-102">Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="445c4-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="445c4-103">Czas ma istotne znaczenie funkcje można derailed, jeśli różnią się ustawienia zegara na dwóch komputerach.</span><span class="sxs-lookup"><span data-stu-id="445c4-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="445c4-104">Aby uniknąć tej możliwości, możesz ustawić `MaxClockSkew` właściwość <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="445c4-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="445c4-105">Ta właściwość jest dostępna w dwóch klas:</span><span class="sxs-lookup"><span data-stu-id="445c4-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  <span data-ttu-id="445c4-106">Ważne dla bezpiecznej konwersacji zmieni się na `MaxClockSkew` właściwości muszą być wykonane, gdy jest załadować usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="445c4-106">Important   For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="445c4-107">Aby to zrobić, należy ustawić właściwość na <xref:System.ServiceModel.Channels.SecurityBindingElement> zwrócone przez <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="445c4-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.</span></span>  
  
 <span data-ttu-id="445c4-108">Aby zmienić właściwość na jednym z powiązań dostarczanych przez system, możesz znaleźć elementu powiązania zabezpieczeń w kolekcji powiązania i ustawić `MaxClockSkew` właściwości na nową wartość.</span><span class="sxs-lookup"><span data-stu-id="445c4-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="445c4-109">Dwoma klasami pochodnymi <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="445c4-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="445c4-110">Podczas pobierania powiązanie zabezpieczeń z kolekcji, należy rzutować do jednego z następujących typów Aby poprawnie ustawić `MaxClockSkew` właściwości.</span><span class="sxs-lookup"><span data-stu-id="445c4-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="445c4-111">W poniższym przykładzie użyto <xref:System.ServiceModel.WSHttpBinding>, który używa <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="445c4-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="445c4-112">Aby uzyskać listę, która określa typ zabezpieczeń powiązania do użycia w każdym powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="445c4-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="445c4-113">Aby utworzyć niestandardowego powiązania za pomocą nowego zegara pochylanie wartości w kodzie</span><span class="sxs-lookup"><span data-stu-id="445c4-113">To create a custom binding with a new clock skew value in code</span></span>  
  
1. > [!WARNING]
    >  <span data-ttu-id="445c4-114">Należy pamiętać, dodaj odwołania do następujących przestrzeni nazw w kodzie: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, i <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="445c4-114">Note   Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
     <span data-ttu-id="445c4-115">Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="445c4-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
2. <span data-ttu-id="445c4-116">Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.Channels.BindingElementCollection> klasy przez wywołanie metody <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="445c4-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="445c4-117">Użyj <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody <xref:System.ServiceModel.Channels.BindingElementCollection> klasy można znaleźć elementu powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="445c4-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="445c4-118">Korzystając z <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> metody rzutowany na typ rzeczywistego.</span><span class="sxs-lookup"><span data-stu-id="445c4-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="445c4-119">W poniższym rzutowania na przykładzie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> typu.</span><span class="sxs-lookup"><span data-stu-id="445c4-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="445c4-120">Ustaw <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> właściwość elementu powiązania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="445c4-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="445c4-121">Utwórz <xref:System.ServiceModel.ServiceHost> przy użyciu adresu typu i base odpowiednią usługę.</span><span class="sxs-lookup"><span data-stu-id="445c4-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="445c4-122">Użyj <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metodę, aby dodać punkt końcowy i zawierać <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="445c4-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="445c4-123">Aby ustawić konfigurację MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="445c4-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="445c4-124">Tworzenie [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) w [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="445c4-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="445c4-125">Tworzenie [ \<powiązania >](../../../../docs/framework/misc/binding.md) element i ustaw `name` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="445c4-125">Create a [\<binding>](../../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="445c4-126">Poniższy przykład ustawia ją na `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="445c4-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="445c4-127">Dodawanie elementu kodowania.</span><span class="sxs-lookup"><span data-stu-id="445c4-127">Add an encoding element.</span></span> <span data-ttu-id="445c4-128">Poniższy przykład dodaje [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="445c4-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="445c4-129">Dodaj [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element i ustaw `authenticationMode` atrybutu do odpowiedniego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="445c4-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="445c4-130">Poniższy przykład atrybut jest ustawiony na `Kerberos` do określenia, że usługa używa uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="445c4-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="445c4-131">Dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybutu wartości w postaci `"##:##:##"`.</span><span class="sxs-lookup"><span data-stu-id="445c4-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="445c4-132">Poniższy przykład ustawia ją na 7 minut.</span><span class="sxs-lookup"><span data-stu-id="445c4-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="445c4-133">Opcjonalnie dodaj [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) i ustaw `maxClockSkew` atrybutu do odpowiedniego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="445c4-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="445c4-134">Dodaj element transportu.</span><span class="sxs-lookup"><span data-stu-id="445c4-134">Add a transport element.</span></span> <span data-ttu-id="445c4-135">W poniższym przykładzie użyto [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="445c4-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="445c4-136">Do bezpiecznej konwersacji, ustawienia zabezpieczeń musi wystąpić na bootstrap w [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="445c4-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="445c4-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="445c4-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="445c4-138">Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="445c4-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
