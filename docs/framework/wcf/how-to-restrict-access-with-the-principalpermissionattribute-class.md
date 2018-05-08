---
title: 'Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: a93726598b31ee57d583aca16012d615e90441f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute
Kontrolowanie dostępu do zasobów na komputerze domeny systemu Windows jest zadaniem podstawowych zabezpieczeń. Na przykład tylko określonym użytkownikom powinien móc wyświetlić poufnych danych, takich jak lista płac informacji. W tym temacie wyjaśniono, jak ograniczyć dostęp do metody przez wymaganie, który użytkownik należy do grupy wstępnie zdefiniowanych. Dla przykładu pracy, zobacz [Autoryzowanie dostępu do operacji usługi](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 Zadanie składa się z dwóch oddzielnych procedur. Pierwszy tworzy grupy i wypełnia je użytkownikom. Druga stosuje <xref:System.Security.Permissions.PrincipalPermissionAttribute> klasę, aby określić grupę.  
  
### <a name="to-create-a-windows-group"></a>Aby utworzyć grupy systemu Windows  
  
1.  Otwórz **Zarządzanie komputerem** konsoli.  
  
2.  W lewym panelu kliknij **lokalnych użytkowników i grup**.  
  
3.  Kliknij prawym przyciskiem myszy **grup**i kliknij przycisk **Nowa grupa**.  
  
4.  W **Nazwa grupy** wpisz nazwę nowej grupy.  
  
5.  W **opis** wpisz opis nowej grupy.  
  
6.  Kliknij przycisk **Dodaj** przycisk, aby dodać nowe elementy członkowskie do grupy.  
  
7.  Jeśli dodano użytkownika do grupy i chcesz przetestować następujący kod, musisz wylogować się komputer i zalogować ponownie, aby zostać zawarte w grupie.  
  
### <a name="to-demand-user-membership"></a>Żądanie użytkownika członkostwa  
  
1.  Otwórz plik kodu Windows Communication Foundation (WCF), który zawiera kodu kontraktu usługi zaimplementowany. Aby uzyskać więcej informacji o implementacji kontraktu, zobacz [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2.  Zastosuj <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybutu do każdej metody, która musi być ograniczony do określonej grupy. Ustaw <xref:System.Security.Permissions.SecurityAttribute.Action%2A> właściwości <xref:System.Security.Permissions.SecurityAction.Demand> i <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> właściwość na nazwę grupy. Na przykład:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  W przypadku zastosowania <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybutu kontrakt <xref:System.Security.SecurityException> zostanie wygenerowany. Można stosować tylko atrybut na poziomie metody.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Używa certyfikatu, aby kontrolować dostęp do metody  
 Można również użyć `PrincipalPermissionAttribute` klasy do kontrolowania dostępu do metody, jeśli certyfikat jest typu poświadczeń klienta. Aby to zrobić, musi mieć podmiotu i odcisk palca certyfikatu.  
  
 Aby zbadać jego właściwości certyfikatu, zobacz [porady: wyświetlanie certyfikatów w przystawce MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Aby znaleźć wartość odcisku palca, zobacz [porady: Pobieranie odcisku palca certyfikatu](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Aby kontrolować dostęp przy użyciu certyfikatu  
  
1.  Zastosuj <xref:System.Security.Permissions.PrincipalPermissionAttribute> klasy, do których chcesz ograniczyć dostęp do metody.  
  
2.  Ustawianie akcji atrybutu z <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3.  Ustaw `Name` właściwości na ciąg, który składa się z nazwy podmiotu i odcisk palca certyfikatu. Oddziel dwóch wartości średnikiem i spacji, jak pokazano w poniższym przykładzie:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  Ustaw <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwości <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> jak pokazano w poniższym przykładzie konfiguracji:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Ustawienie tej wartości na `UseAspNetRoles` oznacza to, że `Name` właściwość `PrincipalPermissionAttribute` posłuży do przeprowadzenia porównania ciągów. Gdy certyfikat jest używany jako poświadczeń klienta, domyślnie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] łączy nazwa pospolita certyfikatu i odcisk palca średnikiem, aby utworzyć unikatową wartość dla podstawowej tożsamości klienta. Z `UseAspNetRoles` Ustaw jako `PrincipalPermissionMode` w usłudze tej wartości podstawowej tożsamości jest porównywana z `Name` wartości właściwości, aby określić uprawnienia dostępu użytkownika.  
  
     Możesz również ustawić podczas tworzenia samodzielnie hostowana usługa, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwości w kodzie, jak pokazano w poniższym kodzie:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.SecurityAction.Demand>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>  
 [Autoryzowanie dostępu do operacji usługi](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
