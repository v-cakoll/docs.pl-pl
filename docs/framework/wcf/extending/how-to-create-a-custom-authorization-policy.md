---
title: 'Instrukcje: Tworzenie niestandardowych zasad autoryzacji'
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
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1af5e2cbf7c124e490fea04deadd1afffcde5cbb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Instrukcje: Tworzenie niestandardowych zasad autoryzacji
Infrastruktura modelu tożsamości w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługuje model autoryzacji na podstawie oświadczeń. Oświadczenia są wyodrębnione z tokenów, opcjonalnie przetworzone przez niestandardowych zasad autoryzacji i następnie są umieszczane w <xref:System.IdentityModel.Policy.AuthorizationContext> które następnie można zbadać podejmowanie decyzji dotyczących autoryzacji. Zasady niestandardowe mogą służyć do przekształcania oświadczeń z przychodzące tokeny oświadczeń oczekiwany przez aplikację. W ten sposób warstwy aplikacji mogą być wyłączone ze szczegółowe informacje o oświadczeniach różne obsługiwane przez token różne typy, które [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje. W tym temacie przedstawiono implementowania niestandardowych zasad autoryzacji oraz sposobu dodawania tej zasady do kolekcji zasad używanych przez usługę.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Aby zaimplementować niestandardowych zasad autoryzacji  
  
1.  Zdefiniuj nową klasę, która jest pochodną <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Implementuje tylko do odczytu <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> właściwości przez generowanie unikatowy ciąg w konstruktorze klasy i zwracanie tego ciągu przy każdym uzyskaniu dostępu do właściwości.  
  
3.  Implementuje tylko do odczytu <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> właściwości zwracając <xref:System.IdentityModel.Claims.ClaimSet> reprezentujący wystawcy zasad. Może to być `ClaimSet` reprezentujący aplikacji lub wbudowaną `ClaimSet` (na przykład `ClaimSet` zwrócony przez statycznych <xref:System.IdentityModel.Claims.ClaimSet.System%2A> właściwości.  
  
4.  Implementowanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-implement-the-evaluate-method"></a>Aby zaimplementować metodę oceny  
  
1.  Dwa parametry są przekazywane do tej metody: wystąpienie <xref:System.IdentityModel.Policy.EvaluationContext> klasy i odwołanie do obiektu.  
  
2.  Jeśli zasady autoryzacji niestandardowej dodaje <xref:System.IdentityModel.Claims.ClaimSet> wystąpień niezależnie bieżącą zawartość <xref:System.IdentityModel.Policy.EvaluationContext>, następnie dodać każdy `ClaimSet` przez wywołanie metody <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> — metoda i wróć `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> — metoda. Zwracanie `true` wskazuje infrastruktury autoryzacji, że zasady autoryzacji wykonał pracę i nie trzeba ponownie wywołany.  
  
3.  Jeśli zasady autoryzacji niestandardowej dodaje zestawów oświadczeń tylko wtedy, gdy niektóre oświadczenia jest już obecny w `EvaluationContext`, poszukaj te oświadczenia, sprawdzając `ClaimSet` wystąpień zwrócona przez <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> właściwości. Jeśli oświadczenia są obecne, Dodaj nowe oświadczenie ustawia wywołując <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> — metoda i, jeżeli nie ma więcej oświadczeń zestawy mają zostać dodane, zwróć `true`, wskazujące infrastruktury autoryzacji, że zasady autoryzacji ukończył pracę. Jeśli nie podano oświadczenia, zwróć `false`, wskazujący, że zasady autoryzacji powinna być wywoływana ponownie w przypadku innych zasad autoryzacji dodać więcej zestawów do oświadczeń `EvaluationContext`.  
  
4.  W bardziej złożonych scenariuszach przetwarzania, drugi parametr funkcji <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda jest używana do przechowywania stanu zmiennej, która przekazuje infrastruktury autoryzacji trakcie każde kolejne wywołanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metodę dla określonej wersji ewaluacyjnej.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Aby określić niestandardowych zasad autoryzacji przy użyciu konfiguracji  
  
1.  Określ typ zasad autoryzacji niestandardowej w `policyType` atrybutu w `add` element `authorizationPolicies` element `serviceAuthorization` elementu.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>         
            <add policyType="Samples.MyAuthorizationPolicy"  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Aby określić niestandardowych zasad autoryzacji przy użyciu kodu  
  
1.  Utwórz <xref:System.Collections.Generic.List%601> z <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Utwórz wystąpienie niestandardowych zasad autoryzacji.  
  
3.  Wystąpienie zasady autoryzacji można dodać do listy.  
  
4.  Powtórz kroki 2 i 3 dla każdej zasady autoryzacji niestandardowej.  
  
5.  Przypisz tylko do odczytu wersji na liście, aby <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> właściwości.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia kompletny <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementacji.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Instrukcje: porównywanie oświadczeń](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md)
