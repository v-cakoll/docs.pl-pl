---
title: 'Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: e3d0143cd68bc94c6ff07e65ca5a3c8971b45f23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337841"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="f60a5-102">Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="f60a5-102">How to: Create a Custom Authorization Manager for a Service</span></span>
<span data-ttu-id="f60a5-103">Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) obsługuje model extensible autoryzacji opartej na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="f60a5-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="f60a5-104">Oświadczenia są wyodrębniane z tokenów i opcjonalnie przetwarzane przy użyciu zasad autoryzacji niestandardowej i następnie umieszczać w <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="f60a5-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="f60a5-105">Menedżer autoryzacji sprawdza, czy oświadczenia w <xref:System.IdentityModel.Policy.AuthorizationContext> do podejmowania decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f60a5-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>  
  
 <span data-ttu-id="f60a5-106">Domyślnie decyzji dotyczących autoryzacji są wykonywane przez <xref:System.ServiceModel.ServiceAuthorizationManager> klasy; jednak te decyzje może być zastąpiona przez tworzenie Menedżera autoryzacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f60a5-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="f60a5-107">Tworzenie niestandardowej autoryzacji manager, należy utworzyć klasę, która pochodzi od klasy <xref:System.ServiceModel.ServiceAuthorizationManager> i zaimplementować <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f60a5-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="f60a5-108">Decyzji dotyczących autoryzacji są dokonywane w <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody, która zwraca `true` gdy dostęp jest udzielany i `false` kiedy odmowa dostępu.</span><span class="sxs-lookup"><span data-stu-id="f60a5-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>  
  
 <span data-ttu-id="f60a5-109">Jeśli decyzja zależy od zawartości treści wiadomości, użyj <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f60a5-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>  
  
 <span data-ttu-id="f60a5-110">Ze względu na problemy z wydajnością Jeśli jest to możliwe należy ponownie zaprojektować aplikację tak, aby decyzję dotyczącą autoryzacji nie wymaga dostępu do treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f60a5-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>  
  
 <span data-ttu-id="f60a5-111">Rejestracja Menedżera autoryzacji niestandardowej dla usługi może odbywać się w kodzie lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f60a5-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>  
  
### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="f60a5-112">Aby utworzyć Menedżera autoryzacji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f60a5-112">To create a custom authorization manager</span></span>  
  
1. <span data-ttu-id="f60a5-113">Wyprowadzić klasę z <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="f60a5-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2. <span data-ttu-id="f60a5-114">Zastąp <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metody.</span><span class="sxs-lookup"><span data-stu-id="f60a5-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>  
  
     <span data-ttu-id="f60a5-115">Użyj <xref:System.ServiceModel.OperationContext> przekazana do <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metodę do podejmowania decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f60a5-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>  
  
     <span data-ttu-id="f60a5-116">Poniższy przykład kodu wykorzystuje <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> metody do znalezienia oświadczenia niestandardowego `http://www.contoso.com/claims/allowedoperation` podejmowanie decyzji o autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f60a5-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="f60a5-117">Aby zarejestrować Menedżera autoryzacji niestandardowej przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="f60a5-117">To register a custom authorization manager using code</span></span>  
  
1. <span data-ttu-id="f60a5-118">Utwórz wystąpienie obiektu autoryzacja niestandardowa manager i przypisz ją do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60a5-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>  
  
     <span data-ttu-id="f60a5-119"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Można uzyskać dostęp za pomocą <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60a5-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>  
  
     <span data-ttu-id="f60a5-120">Poniższy kod przykładowy rejestrów `MyServiceAuthorizationManager` Menedżera autoryzacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f60a5-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="f60a5-121">Aby zarejestrować Menedżera autoryzacji niestandardowej przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f60a5-121">To register a custom authorization manager using configuration</span></span>  
  
1. <span data-ttu-id="f60a5-122">Otwórz plik konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="f60a5-122">Open the configuration file for the service.</span></span>  
  
2. <span data-ttu-id="f60a5-123">Dodaj [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) do [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="f60a5-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span></span>  
  
     <span data-ttu-id="f60a5-124">Aby [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), Dodaj `serviceAuthorizationManagerType` atrybut i ustawić jej wartość na typ, który reprezentuje Menedżera autoryzacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f60a5-124">To the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>  
  
3. <span data-ttu-id="f60a5-125">Dodaj powiązanie, które zabezpiecza komunikację między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="f60a5-125">Add a binding that secures the communication between the client and service.</span></span>  
  
     <span data-ttu-id="f60a5-126">Powiązania, który wybrano dla tej komunikacji określa oświadczenia, które są dodawane do <xref:System.IdentityModel.Policy.AuthorizationContext>, który używa Menedżera autoryzacji niestandardowej w celu podejmowania decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f60a5-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="f60a5-127">Aby uzyskać więcej szczegółów na temat powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="f60a5-127">For more details about the system-provided bindings, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
4. <span data-ttu-id="f60a5-128">Kojarzenie zachowania punktu końcowego usługi, dodając [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element i ustaw wartość `behaviorConfiguration` atrybutu z wartością atrybutu nazwy [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f60a5-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
     <span data-ttu-id="f60a5-129">Aby uzyskać więcej informacji na temat konfigurowania punktu końcowego usługi, zobacz [jak: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f60a5-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
     <span data-ttu-id="f60a5-130">Poniższy przykład kodu rejestruje Menedżera autoryzacji niestandardowej `Samples.MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="f60a5-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.CalculatorService"  
              behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <endpoint address=""  
                      binding="wsHttpBinding_Calculator"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <WSHttpBinding>  
           <binding name = "wsHttpBinding_Calculator">  
             <security mode="Message">  
               <message clientCredentialType="Windows"/>  
             </security>  
            </binding>  
          </WSHttpBinding>  
    </bindings>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />  
             </behavior>  
         </serviceBehaviors>  
       </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
    > [!WARNING]
    >  <span data-ttu-id="f60a5-131">Należy pamiętać, że podczas określania serviceAuthorizationManagerType ciąg może zawierać w pełni kwalifikowana nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="f60a5-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="f60a5-132">przecinek, a nazwa zestawu, w którym typ jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="f60a5-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="f60a5-133">Jeśli pozostawisz nazwy zestawu WCF spróbuje załadować typu z System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="f60a5-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f60a5-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="f60a5-134">Example</span></span>  
 <span data-ttu-id="f60a5-135">Poniższy przykład kodu pokazuje podstawową implementację <xref:System.ServiceModel.ServiceAuthorizationManager> klasa, która zawiera zastępowanie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f60a5-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="f60a5-136">Przykład kodu sprawdza, czy <xref:System.IdentityModel.Policy.AuthorizationContext> niestandardowych oświadczeń i zwraca `true` po zasobów dla tego oświadczenia niestandardowego dopasowuje wartość akcji z <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="f60a5-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="f60a5-137">Bardziej kompletny wykonania <xref:System.ServiceModel.ServiceAuthorizationManager> klasy, zobacz [zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="f60a5-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f60a5-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f60a5-138">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="f60a5-139">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="f60a5-139">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
