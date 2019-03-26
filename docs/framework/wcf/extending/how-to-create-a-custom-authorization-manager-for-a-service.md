---
title: 'Instrukcje: Tworzenie menedżera autoryzacji niestandardowej dla usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: 571c1d66bcf1ea62972eb1be3fd694964581db38
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465142"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Instrukcje: Tworzenie menedżera autoryzacji niestandardowej dla usługi
Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) obsługuje model extensible autoryzacji opartej na oświadczeniach. Oświadczenia są wyodrębniane z tokenów i opcjonalnie przetwarzane przy użyciu zasad autoryzacji niestandardowej i następnie umieszczać w <xref:System.IdentityModel.Policy.AuthorizationContext>. Menedżer autoryzacji sprawdza, czy oświadczenia w <xref:System.IdentityModel.Policy.AuthorizationContext> do podejmowania decyzji dotyczących autoryzacji.  
  
 Domyślnie decyzji dotyczących autoryzacji są wykonywane przez <xref:System.ServiceModel.ServiceAuthorizationManager> klasy; jednak te decyzje może być zastąpiona przez tworzenie Menedżera autoryzacji niestandardowej. Tworzenie niestandardowej autoryzacji manager, należy utworzyć klasę, która pochodzi od klasy <xref:System.ServiceModel.ServiceAuthorizationManager> i zaimplementować <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody. Decyzji dotyczących autoryzacji są dokonywane w <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody, która zwraca `true` gdy dostęp jest udzielany i `false` kiedy odmowa dostępu.  
  
 Jeśli decyzja zależy od zawartości treści wiadomości, użyj <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metody.  
  
 Ze względu na problemy z wydajnością Jeśli jest to możliwe należy ponownie zaprojektować aplikację tak, aby decyzję dotyczącą autoryzacji nie wymaga dostępu do treści wiadomości.  
  
 Rejestracja Menedżera autoryzacji niestandardowej dla usługi może odbywać się w kodzie lub konfiguracji.  
  
### <a name="to-create-a-custom-authorization-manager"></a>Aby utworzyć Menedżera autoryzacji niestandardowej  
  
1.  Wyprowadzić klasę z <xref:System.ServiceModel.ServiceAuthorizationManager> klasy.  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  Zastąp <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metody.  
  
     Użyj <xref:System.ServiceModel.OperationContext> przekazana do <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metodę do podejmowania decyzji dotyczących autoryzacji.  
  
     Poniższy przykład kodu wykorzystuje <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> metody do znalezienia oświadczenia niestandardowego `http://www.contoso.com/claims/allowedoperation` podejmowanie decyzji o autoryzacji.  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a>Aby zarejestrować Menedżera autoryzacji niestandardowej przy użyciu kodu  
  
1.  Utwórz wystąpienie obiektu autoryzacja niestandardowa manager i przypisz ją do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> właściwości.  
  
     <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Można uzyskać dostęp za pomocą <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> właściwości.  
  
     Poniższy kod przykładowy rejestrów `MyServiceAuthorizationManager` Menedżera autoryzacji niestandardowej.  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Aby zarejestrować Menedżera autoryzacji niestandardowej przy użyciu konfiguracji  
  
1.  Otwórz plik konfiguracji usługi.  
  
2.  Dodaj [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) do [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
     Aby [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), Dodaj `serviceAuthorizationManagerType` atrybut i ustawić jej wartość na typ, który reprezentuje Menedżera autoryzacji niestandardowej.  
  
3.  Dodaj powiązanie, które zabezpiecza komunikację między klientem a usługą.  
  
     Powiązania, który wybrano dla tej komunikacji określa oświadczenia, które są dodawane do <xref:System.IdentityModel.Policy.AuthorizationContext>, który używa Menedżera autoryzacji niestandardowej w celu podejmowania decyzji dotyczących autoryzacji. Aby uzyskać więcej szczegółów na temat powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
4.  Kojarzenie zachowania punktu końcowego usługi, dodając [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element i ustaw wartość `behaviorConfiguration` atrybutu z wartością atrybutu nazwy [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.  
  
     Aby uzyskać więcej informacji na temat konfigurowania punktu końcowego usługi, zobacz [jak: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
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
    >  Należy pamiętać, że podczas określania serviceAuthorizationManagerType ciąg może zawierać w pełni kwalifikowana nazwa typu. przecinek, a nazwa zestawu, w którym typ jest zdefiniowany. Jeśli pozostawisz nazwy zestawu WCF spróbuje załadować typu z System.ServiceModel.dll.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje podstawową implementację <xref:System.ServiceModel.ServiceAuthorizationManager> klasa, która zawiera zastępowanie <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody. Przykład kodu sprawdza, czy <xref:System.IdentityModel.Policy.AuthorizationContext> niestandardowych oświadczeń i zwraca `true` po zasobów dla tego oświadczenia niestandardowego dopasowuje wartość akcji z <xref:System.ServiceModel.OperationContext>. Bardziej kompletny wykonania <xref:System.ServiceModel.ServiceAuthorizationManager> klasy, zobacz [zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md)
