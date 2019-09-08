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
ms.openlocfilehash: 9c28cb81b78f80505cfcf5f7e4dfdba083bd0793
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797111"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="f01c9-102">Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi</span><span class="sxs-lookup"><span data-stu-id="f01c9-102">How to: Create a Custom Authorization Manager for a Service</span></span>

<span data-ttu-id="f01c9-103">Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) obsługuje rozszerzalny model autoryzacji oparty na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="f01c9-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="f01c9-104">Oświadczenia są wyodrębniane z tokenów i opcjonalnie przetwarzane przez niestandardowe zasady autoryzacji, a następnie <xref:System.IdentityModel.Policy.AuthorizationContext>umieszczane w.</span><span class="sxs-lookup"><span data-stu-id="f01c9-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="f01c9-105">Menedżer autoryzacji bada oświadczenia w <xref:System.IdentityModel.Policy.AuthorizationContext> usłudze w celu podejmowania decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f01c9-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>

<span data-ttu-id="f01c9-106">Domyślnie decyzje dotyczące autoryzacji są podejmowane przez <xref:System.ServiceModel.ServiceAuthorizationManager> klasę; jednak te decyzje mogą zostać zastąpione przez utworzenie niestandardowego Menedżera autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f01c9-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="f01c9-107">Aby utworzyć niestandardowego Menedżera autoryzacji, należy utworzyć klasę, która pochodzi od <xref:System.ServiceModel.ServiceAuthorizationManager> i Implementuj <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="f01c9-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="f01c9-108">Decyzje dotyczące autoryzacji są podejmowane <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> w metodzie, `true` która zwraca w przypadku udzielenia `false` dostępu i w przypadku odmowy dostępu.</span><span class="sxs-lookup"><span data-stu-id="f01c9-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>

<span data-ttu-id="f01c9-109">Jeśli decyzja dotycząca autoryzacji zależy od zawartości treści wiadomości, użyj <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f01c9-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>

<span data-ttu-id="f01c9-110">Ze względu na problemy z wydajnością, jeśli to możliwe, należy ponownie zaprojektować aplikację, tak aby decyzja o autoryzacji nie wymagała dostępu do treści komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f01c9-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>

<span data-ttu-id="f01c9-111">Rejestrację niestandardowego Menedżera autoryzacji dla usługi można dokonać w kodzie lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f01c9-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>

### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="f01c9-112">Aby utworzyć niestandardowego Menedżera autoryzacji</span><span class="sxs-lookup"><span data-stu-id="f01c9-112">To create a custom authorization manager</span></span>

1. <span data-ttu-id="f01c9-113">Utwórz klasę z <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="f01c9-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. <span data-ttu-id="f01c9-114">Zastąp <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metody.</span><span class="sxs-lookup"><span data-stu-id="f01c9-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>

    <span data-ttu-id="f01c9-115">Użyj, która jest przenoszona <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> do metody w celu podejmowania decyzji dotyczących autoryzacji. <xref:System.ServiceModel.OperationContext></span><span class="sxs-lookup"><span data-stu-id="f01c9-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>

    <span data-ttu-id="f01c9-116">Poniższy przykład kodu używa metody, <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> aby znaleźć `http://www.contoso.com/claims/allowedoperation` niestandardową autoryzację w celu podejmowania decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f01c9-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="f01c9-117">Aby zarejestrować niestandardowego Menedżera autoryzacji przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="f01c9-117">To register a custom authorization manager using code</span></span>

1. <span data-ttu-id="f01c9-118">Utwórz wystąpienie niestandardowego Menedżera autoryzacji i przypisz je do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f01c9-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>

    <span data-ttu-id="f01c9-119">Dostęp <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> do niego można uzyskać <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="f01c9-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>

    <span data-ttu-id="f01c9-120">Poniższy przykład kodu rejestruje `MyServiceAuthorizationManager` niestandardowego Menedżera autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f01c9-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="f01c9-121">Aby zarejestrować niestandardowego Menedżera autoryzacji przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f01c9-121">To register a custom authorization manager using configuration</span></span>

1. <span data-ttu-id="f01c9-122">Otwórz plik konfiguracji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f01c9-122">Open the configuration file for the service.</span></span>

2. <span data-ttu-id="f01c9-123">Dodaj > ServiceAuthorization do [> zachowań. \<](../../configure-apps/file-schema/wcf/behaviors.md) [ \<](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="f01c9-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md).</span></span>

    <span data-ttu-id="f01c9-124">Do > `serviceAuthorizationManagerType` ServiceAuthorization Dodaj atrybut i ustaw jego wartość na typ, który reprezentuje niestandardowego Menedżera autoryzacji. [ \<](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="f01c9-124">To the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>

3. <span data-ttu-id="f01c9-125">Dodaj powiązanie, które zabezpiecza komunikację między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="f01c9-125">Add a binding that secures the communication between the client and service.</span></span>

    <span data-ttu-id="f01c9-126">Powiązanie wybrane dla tej komunikacji określa oświadczenia, które są dodawane do programu <xref:System.IdentityModel.Policy.AuthorizationContext>, który jest używany przez niestandardowego Menedżera autoryzacji do podejmowania decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f01c9-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="f01c9-127">Aby uzyskać więcej informacji na temat powiązań dostarczonych przez system, zobacz [powiązania dostarczone przez system](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="f01c9-127">For more details about the system-provided bindings, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

4. <span data-ttu-id="f01c9-128">Skojarz zachowanie z punktem końcowym usługi przez dodanie `behaviorConfiguration` [ \<elementu > usługi](../../configure-apps/file-schema/wcf/service.md) i ustaw wartość atrybutu na [ \<](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) wartość atrybutu Name dla elementu Behavior >.</span><span class="sxs-lookup"><span data-stu-id="f01c9-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    <span data-ttu-id="f01c9-129">Aby uzyskać więcej informacji o konfigurowaniu punktu końcowego usługi [, zobacz How to: Utwórz punkt końcowy usługi w konfiguracji](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f01c9-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>

    <span data-ttu-id="f01c9-130">Poniższy przykład kodu rejestruje niestandardowego menedżera `Samples.MyServiceAuthorizationManager`autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="f01c9-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>

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
    > <span data-ttu-id="f01c9-131">Należy pamiętać, że po określeniu serviceAuthorizationManagerType, ciąg musi zawierać w pełni kwalifikowaną nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="f01c9-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="f01c9-132">przecinek i nazwa zestawu, w którym jest zdefiniowany typ.</span><span class="sxs-lookup"><span data-stu-id="f01c9-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="f01c9-133">Jeśli pozostawisz nazwę zestawu, funkcja WCF podejmie próbę załadowania typu z System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="f01c9-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>

## <a name="example"></a><span data-ttu-id="f01c9-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="f01c9-134">Example</span></span>

<span data-ttu-id="f01c9-135">Poniższy przykład kodu demonstruje podstawową implementację <xref:System.ServiceModel.ServiceAuthorizationManager> klasy, która obejmuje <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> zastąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="f01c9-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="f01c9-136">Przykładowy kod sprawdza, czy jest <xref:System.IdentityModel.Policy.AuthorizationContext> to niestandardowa, i `true` zwraca, gdy zasób tego żądania niestandardowego dopasowuje wartość akcji z <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="f01c9-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="f01c9-137">Aby uzyskać bardziej kompletną implementację <xref:System.ServiceModel.ServiceAuthorizationManager> klasy, zobacz [zasady autoryzacji](../samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="f01c9-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../samples/authorization-policy.md).</span></span>

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a><span data-ttu-id="f01c9-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f01c9-138">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="f01c9-139">Zasady autoryzacji</span><span class="sxs-lookup"><span data-stu-id="f01c9-139">Authorization Policy</span></span>](../samples/authorization-policy.md)
