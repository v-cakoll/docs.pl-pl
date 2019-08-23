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
ms.openlocfilehash: 3b109e3e6817c300af1e79258d555562dcba067a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951013"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute
Kontrolowanie dostępu do zasobów na komputerze z domeną systemu Windows to podstawowe zadanie zabezpieczeń. Na przykład tylko niektórzy użytkownicy powinni mieć możliwość wyświetlania poufnych danych, takich jak informacje o płacach. W tym temacie wyjaśniono, jak ograniczyć dostęp do metody przez wymaganie, aby użytkownik należał do wstępnie zdefiniowanej grupy. Aby uzyskać przykład roboczy, zobacz [autoryzowanie dostępu do operacji usługi](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 Zadanie składa się z dwóch oddzielnych procedur. Najpierw tworzy grupę i wypełnia ją użytkownikami. Drugi stosuje klasę, <xref:System.Security.Permissions.PrincipalPermissionAttribute> aby określić grupę.  
  
### <a name="to-create-a-windows-group"></a>Aby utworzyć grupę systemu Windows  
  
1. Otwórz konsolę **Zarządzanie komputerem** .  
  
2. Na panelu po lewej stronie kliknij pozycję **lokalni użytkownicy i grupy**.  
  
3. Kliknij prawym przyciskiem myszy pozycję **grupy**, a następnie kliknij pozycję **Nowa grupa**.  
  
4. W polu **Nazwa grupy** wpisz nazwę nowej grupy.  
  
5. W polu **Opis** wpisz opis nowej grupy.  
  
6. Kliknij przycisk **Dodaj** , aby dodać nowych członków do grupy.  
  
7. Jeśli dodano Cię do grupy i chcesz przetestować Poniższy kod, musisz wylogować się z komputera i ponownie zalogować się do grupy.  
  
### <a name="to-demand-user-membership"></a>Na żądanie członkostwa użytkowników  
  
1. Otwórz plik kodu Windows Communication Foundation (WCF), który zawiera zaimplementowany kod kontraktu usługi. Aby uzyskać więcej informacji na temat implementowania kontraktu, zobacz [implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Zastosuj atrybut do każdej metody, która musi być ograniczona do konkretnej grupy. Ustaw właściwość na <xref:System.Security.Permissions.SecurityAction.Demand> i<xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> właściwość na nazwę grupy. <xref:System.Security.Permissions.SecurityAttribute.Action%2A> Przykład:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > W przypadku zastosowania <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybutu do kontraktu a <xref:System.Security.SecurityException> zostanie zgłoszony. Atrybut można zastosować tylko na poziomie metody.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Używanie certyfikatu w celu kontrolowania dostępu do metody  
 Można również użyć `PrincipalPermissionAttribute` klasy do kontroli dostępu do metody, jeśli typ poświadczeń klienta jest certyfikatem. Aby to zrobić, musisz mieć podmiot certyfikatu i odcisk palca.  
  
 Aby sprawdzić certyfikat dla jego właściwości, zobacz [How to: Wyświetlanie certyfikatów z przystawką](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)programu MMC. Aby znaleźć wartość odcisku palca [, zobacz How to: Pobieranie odcisku palca certyfikatu](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Aby kontrolować dostęp przy użyciu certyfikatu  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Zastosuj klasę do metody, do której chcesz ograniczyć dostęp.  
  
2. Ustaw akcję atrybutu na <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3. `Name` Ustaw właściwość na ciąg, który składa się z nazwy podmiotu i odcisku palca certyfikatu. Rozdziel dwie wartości średnikami i spacjami, jak pokazano w następującym przykładzie:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. Ustaw właściwość na <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> tak, jak pokazano w następującym przykładzie konfiguracji: <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Ustawienie tej wartości `UseAspNetRoles` wskazuje `Name` , że właściwość `PrincipalPermissionAttribute` zostanie użyta do przeprowadzenia porównania ciągów. Jeśli certyfikat jest używany jako poświadczenie klienta, domyślnie program WCF łączy nazwę pospolitą certyfikatu i odcisk palca z średnikiem, aby utworzyć unikatową wartość dla podstawowej tożsamości klienta. W `UseAspNetRoles` przypadku ustawienia `PrincipalPermissionMode` jako dla usługi ta podstawowa `Name` wartość tożsamości jest porównywana z wartością właściwości w celu określenia praw dostępu użytkownika.  
  
     Alternatywnie, podczas tworzenia usługi samodzielnej, należy ustawić <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwość w kodzie, jak pokazano w poniższym kodzie:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [Autoryzowanie dostępu do operacji usługi](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
