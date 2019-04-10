---
title: 'Instrukcje: tworzenie niestandardowych zasad autoryzacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 05130e809356369ee2b43d9af86acf69fe527e9a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295422"
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Instrukcje: tworzenie niestandardowych zasad autoryzacji
Infrastruktura modelu tożsamości w Windows Communication Foundation (WCF) obsługuje model na podstawie oświadczeń autoryzacji. Wyodrębnione z tokenów, opcjonalnie przetwarzane przez niestandardowych zasad autoryzacji i następnie umieszczać w oświadczeń <xref:System.IdentityModel.Policy.AuthorizationContext> , następnie można zbadać do podejmowania decyzji dotyczących autoryzacji. Zasady niestandardowe może służyć do przekształcania oświadczeń przychodzących tokenów oświadczeń oczekiwane przez aplikację. W ten sposób warstwy aplikacji mogą być izolowane dane na różne oświadczenia, obsługiwane przez różne typy tokenów, które obsługuje usługi WCF. W tym temacie pokazano, jak zaimplementować niestandardowych zasad autoryzacji oraz sposób dodawania tej zasady do kolekcji zasad używanych przez usługę.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Aby zaimplementować niestandardowych zasad autoryzacji  
  
1. Zdefiniuj nową klasę, która pochodzi od klasy <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2. Implementowanie tylko do odczytu <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> właściwości przez wygenerowanie unikatowego ciągu w konstruktorze klasy i zwraca ciąg, w każdym przypadku, gdy uzyskano dostęp do właściwości.  
  
3. Implementowanie tylko do odczytu <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> właściwości, zwracając <xref:System.IdentityModel.Claims.ClaimSet> reprezentujący wystawcy zasad. Może to być `ClaimSet` reprezentujący aplikację lub wbudowanego `ClaimSet` (na przykład `ClaimSet` zwróconą przez statyczną <xref:System.IdentityModel.Claims.ClaimSet.System%2A> właściwości.  
  
4. Implementowanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-implement-the-evaluate-method"></a>Aby wdrożyć metodę Evaluate  
  
1. Dwa parametry są przekazywane do tej metody: wystąpienie <xref:System.IdentityModel.Policy.EvaluationContext> klasy i odwołanie do obiektu.  
  
2. Jeśli dodanie niestandardowych zasad autoryzacji <xref:System.IdentityModel.Claims.ClaimSet> wystąpienia, bez względu na bieżącą zawartość <xref:System.IdentityModel.Policy.EvaluationContext>, następnie dodać każdy `ClaimSet` przez wywołanie metody <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metody i wróć `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metody. Zwracanie `true` wskazuje infrastruktury autoryzacji, że zasady autoryzacji ma wykonać swoją pracę i nie trzeba ponownie wywołana.  
  
3. Jeśli niestandardowych zasad autoryzacji dodaje zestawów oświadczeń tylko wtedy, gdy niektóre oświadczenia jest już obecny w `EvaluationContext`, poszukaj te oświadczenia, sprawdzając `ClaimSet` wystąpień zwrócona przez <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> właściwości. Jeśli oświadczenia są obecne, Dodaj nowe oświadczenie ustawia przez wywołanie metody <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metoda i jeśli nie ma więcej oświadczeń zestawy mają być dodawane zwracany `true`oznaczający infrastruktury autoryzacji, że zasady autoryzacji zakończy pracę. Jeśli oświadczenia nie są obecne, zwracają `false`, wskazujący, że zasady autoryzacji powinna zostać wywołana, jeśli inne zasady autoryzacji, Dodaj więcej w zestawie oświadczeń do `EvaluationContext`.  
  
4. W bardziej złożonych scenariuszy przetwarzania, drugi parametr <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda jest używana do przechowywania zmiennej stanu, który infrastruktury autoryzacji będzie przekazywany w trakcie każde kolejne wywołanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metodę dla konkretnej wersji ewaluacyjnej.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Aby określić niestandardowych zasad autoryzacji za pomocą konfiguracji  
  
1. Określ typ niestandardowych zasad autoryzacji w `policyType` atrybutu w `add` element `authorizationPolicies` element `serviceAuthorization` elementu.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Aby określić niestandardowych zasad autoryzacji za pomocą kodu  
  
1. Tworzenie <xref:System.Collections.Generic.List%601> z <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2. Utwórz wystąpienie niestandardowych zasad autoryzacji.  
  
3. Dodaj wystąpienie zasad autoryzacji do listy.  
  
4. Powtórz kroki 2 i 3 dla każdego niestandardowych zasad autoryzacji.  
  
5. Przypisz wersji tylko do odczytu na liście, aby <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> właściwości.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kompletną <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementacji.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Instrukcje: porównywanie oświadczeń](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md)
