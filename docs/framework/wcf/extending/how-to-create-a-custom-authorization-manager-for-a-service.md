---
title: "Instrukcje: Tworzenie menedżera autoryzacji niestandardowej dla usługi"
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
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cba64767aaac4092f3c6103f7417a9d707b9a380
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Instrukcje: Tworzenie menedżera autoryzacji niestandardowej dla usługi
Infrastruktura modelu tożsamości w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługuje model extensible autoryzacji opartej na oświadczeniach. Oświadczenia są wyodrębnione z tokenów i opcjonalnie przetwarzane przy użyciu zasad autoryzacji niestandardowej, a następnie są umieszczane w <xref:System.IdentityModel.Policy.AuthorizationContext>. Menedżer autoryzacji sprawdza oświadczeń z <xref:System.IdentityModel.Policy.AuthorizationContext> podejmowanie decyzji dotyczących autoryzacji.  
  
 Domyślnie decyzji dotyczących autoryzacji są wykonywane przez <xref:System.ServiceModel.ServiceAuthorizationManager> klasy; jednak tych decyzji może zostać przesłonięta przez tworzenie Menedżera autoryzacji niestandardowej. Można utworzyć Menedżera autoryzacji niestandardowej, Utwórz klasę, która pochodzi z <xref:System.ServiceModel.ServiceAuthorizationManager> i wdrożenie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody. Decyzje dotyczące autoryzacji zostały wprowadzone w <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody, która zwraca `true` po dostęp i `false` jeśli odmówiono dostępu.  
  
 Jeśli decyzję dotyczącą autoryzacji zależy od zawartości treści wiadomości, użyj <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metody.  
  
 Z powodu problemów z wydajnością Jeśli to możliwe powinien zmiany projektu aplikacji tak, aby decyzję dotyczącą autoryzacji nie wymagają dostępu do treści wiadomości.  
  
 Rejestracja Menedżera autoryzacji niestandardowej dla usługi można wykonać w konfiguracji lub kodu.  
  
### <a name="to-create-a-custom-authorization-manager"></a>Aby utworzyć Menedżera autoryzacji niestandardowej  
  
1.  Klasa wyprowadzona z <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  Zastąpienie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metody.  
  
     Użyj <xref:System.ServiceModel.OperationContext> przekazywany do <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metodę, aby podejmować decyzje dotyczące autoryzacji.  
  
     Poniższy przykład kodu wykorzystuje <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> metody do znalezienia oświadczenia niestandardowego `http://www.contoso.com/claims/allowedoperation` aby podjąć decyzję dotyczącą autoryzacji.  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a>Aby zarejestrować Menedżera autoryzacji niestandardowej przy użyciu kodu  
  
1.  Utwórz wystąpienie autoryzacji niestandardowej manager i przypisz je do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> właściwości.  
  
     <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Uzyskać dostęp za pomocą <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> właściwości.  
  
     Poniższy kod rejestruje przykład `MyServiceAuthorizationManager` Menedżera autoryzacji niestandardowej.  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Aby zarejestrować za pomocą konfiguracji Menedżera autoryzacji niestandardowej  
  
1.  Otwórz plik konfiguracji usługi.  
  
2.  Dodaj [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) do [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
     Aby [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), Dodaj `serviceAuthorizationManagerType` atrybutu i ustawić jej wartość na typ, który reprezentuje Menedżera autoryzacji niestandardowej.  
  
3.  Dodaj powiązanie, które zabezpiecza komunikację między klientem a usługą.  
  
     Wybrany dla tej komunikacji określa oświadczenia, które są dodawane do powiązania <xref:System.IdentityModel.Policy.AuthorizationContext>, który używa Menedżera autoryzacji niestandardowej podejmowanie decyzji dotyczących autoryzacji. Aby uzyskać więcej informacji na temat wiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
4.  Skojarz zachowania dla punktu końcowego, dodając [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element i ustaw wartość `behaviorConfiguration` atrybutu w wartości atrybutu nazwy dla [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.  
  
     Aby uzyskać więcej informacji na temat konfigurowania punktu końcowego usługi, zobacz [porady: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
     Poniższy przykład kodu rejestruje Menedżera autoryzacji niestandardowej `Samples.MyServiceAuthorizationManager`.  
  
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
    >  Należy pamiętać, że po określeniu serviceAuthorizationManagerType ciąg musi zawierać nazwę FQDN typu. przecinek, a nazwa zestawu, w którym jest zdefiniowany typ. Jeśli Opuść nazwę zestawu, WCF próbuje załadować typu z System.ServiceModel.dll.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje Podstawowa implementacja <xref:System.ServiceModel.ServiceAuthorizationManager> klasa, która zawiera zastępowanie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody. Przykład kodu sprawdza <xref:System.IdentityModel.Policy.AuthorizationContext> niestandardowych oświadczeń i zwraca `true` po zasobów dla tego oświadczenia niestandardowego pasuje do wartości akcji z <xref:System.ServiceModel.OperationContext>. Dla pełniejszego implementacji <xref:System.ServiceModel.ServiceAuthorizationManager> , zobacz [zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [Zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md)
