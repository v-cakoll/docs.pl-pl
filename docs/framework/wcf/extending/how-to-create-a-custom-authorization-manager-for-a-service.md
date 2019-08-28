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
ms.openlocfilehash: ffdfe41db05eb5f2dd55a233f8ed646401777d0f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040298"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi

Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) obsługuje rozszerzalny model autoryzacji oparty na oświadczeniach. Oświadczenia są wyodrębniane z tokenów i opcjonalnie przetwarzane przez niestandardowe zasady autoryzacji, a następnie <xref:System.IdentityModel.Policy.AuthorizationContext>umieszczane w. Menedżer autoryzacji bada oświadczenia w <xref:System.IdentityModel.Policy.AuthorizationContext> usłudze w celu podejmowania decyzji dotyczących autoryzacji.

Domyślnie decyzje dotyczące autoryzacji są podejmowane przez <xref:System.ServiceModel.ServiceAuthorizationManager> klasę; jednak te decyzje mogą zostać zastąpione przez utworzenie niestandardowego Menedżera autoryzacji. Aby utworzyć niestandardowego Menedżera autoryzacji, należy utworzyć klasę, która pochodzi od <xref:System.ServiceModel.ServiceAuthorizationManager> i Implementuj <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodę. Decyzje dotyczące autoryzacji są podejmowane <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> w metodzie, `true` która zwraca w przypadku udzielenia `false` dostępu i w przypadku odmowy dostępu.

Jeśli decyzja dotycząca autoryzacji zależy od zawartości treści wiadomości, użyj <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metody.

Ze względu na problemy z wydajnością, jeśli to możliwe, należy ponownie zaprojektować aplikację, tak aby decyzja o autoryzacji nie wymagała dostępu do treści komunikatu.

Rejestrację niestandardowego Menedżera autoryzacji dla usługi można dokonać w kodzie lub konfiguracji.

### <a name="to-create-a-custom-authorization-manager"></a>Aby utworzyć niestandardowego Menedżera autoryzacji

1. Utwórz klasę z <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. Zastąp <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metody.

    Użyj, która jest przenoszona <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> do metody w celu podejmowania decyzji dotyczących autoryzacji. <xref:System.ServiceModel.OperationContext>

    Poniższy przykład kodu używa metody, <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> aby znaleźć `http://www.contoso.com/claims/allowedoperation` niestandardową autoryzację w celu podejmowania decyzji dotyczących autoryzacji.

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a>Aby zarejestrować niestandardowego Menedżera autoryzacji przy użyciu kodu

1. Utwórz wystąpienie niestandardowego Menedżera autoryzacji i przypisz je do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> właściwości.

    Dostęp <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> do niego można uzyskać <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> za pomocą właściwości.

    Poniższy przykład kodu rejestruje `MyServiceAuthorizationManager` niestandardowego Menedżera autoryzacji.

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Aby zarejestrować niestandardowego Menedżera autoryzacji przy użyciu konfiguracji

1. Otwórz plik konfiguracji dla usługi.

2. Dodaj > ServiceAuthorization do [> zachowań. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)

    Do > `serviceAuthorizationManagerType` ServiceAuthorization Dodaj atrybut i ustaw jego wartość na typ, który reprezentuje niestandardowego Menedżera autoryzacji. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)

3. Dodaj powiązanie, które zabezpiecza komunikację między klientem a usługą.

    Powiązanie wybrane dla tej komunikacji określa oświadczenia, które są dodawane do programu <xref:System.IdentityModel.Policy.AuthorizationContext>, który jest używany przez niestandardowego Menedżera autoryzacji do podejmowania decyzji dotyczących autoryzacji. Aby uzyskać więcej informacji na temat powiązań dostarczonych przez system, zobacz [powiązania dostarczone przez system](../../../../docs/framework/wcf/system-provided-bindings.md).

4. Skojarz zachowanie z punktem końcowym usługi przez dodanie `behaviorConfiguration` [ \<elementu > usługi](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) i ustaw wartość atrybutu na [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) wartość atrybutu Name dla elementu Behavior >.

    Aby uzyskać więcej informacji o konfigurowaniu punktu końcowego usługi [, zobacz How to: Utwórz punkt końcowy usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).

    Poniższy przykład kodu rejestruje niestandardowego menedżera `Samples.MyServiceAuthorizationManager`autoryzacji.

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
    > Należy pamiętać, że po określeniu serviceAuthorizationManagerType, ciąg musi zawierać w pełni kwalifikowaną nazwę typu. przecinek i nazwa zestawu, w którym jest zdefiniowany typ. Jeśli pozostawisz nazwę zestawu, funkcja WCF podejmie próbę załadowania typu z System. ServiceModel. dll.

## <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje podstawową implementację <xref:System.ServiceModel.ServiceAuthorizationManager> klasy, która obejmuje <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> zastąpienie metody. Przykładowy kod sprawdza, czy jest <xref:System.IdentityModel.Policy.AuthorizationContext> to niestandardowa, i `true` zwraca, gdy zasób tego żądania niestandardowego dopasowuje wartość akcji z <xref:System.ServiceModel.OperationContext>. Aby uzyskać bardziej kompletną implementację <xref:System.ServiceModel.ServiceAuthorizationManager> klasy, zobacz [zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md).

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md)
