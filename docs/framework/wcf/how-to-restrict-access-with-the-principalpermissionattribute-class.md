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
ms.openlocfilehash: ae2aa4c5629096ee7d888e7c4e334c3b6696db3f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323320"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute
Kontrolowanie dostępu do zasobów na komputerze domeny Windows jest zadaniem podstawowych zabezpieczeń. Na przykład tylko w przypadku niektórych użytkowników powinny mieć możliwość wyświetlania poufnych danych, np. informacji o płacach. W tym temacie wyjaśniono, jak ograniczyć dostęp do metody przez wymaganie, który użytkownik należy do wstępnie zdefiniowanej grupie. Przykładowy pracy [Autoryzowanie dostępu do operacji usługi](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 Zadanie składa się z dwóch osobnych procedur. Pierwszy tworzy grupy i wypełnia ją użytkownikom. Druga stosuje <xref:System.Security.Permissions.PrincipalPermissionAttribute> klasy, aby określić grupę.  
  
### <a name="to-create-a-windows-group"></a>Aby utworzyć grupę Windows  
  
1. Otwórz **Zarządzanie komputerem** konsoli.  
  
2. W okienku po lewej stronie kliknij **lokalnych użytkowników i grup**.  
  
3. Kliknij prawym przyciskiem myszy **grup**i kliknij przycisk **Nowa grupa**.  
  
4. W **Nazwa grupy** wpisz nazwę dla nowej grupy.  
  
5. W **opis** wpisz opis nowej grupy.  
  
6. Kliknij przycisk **Dodaj** przycisk, aby dodawać nowych członków do grupy.  
  
7. Jeśli dodano użytkownika do grupy i chcesz przetestować następujący kod, musisz się wylogować komputer i zalogować ponownie, aby zostać uwzględniona w grupie.  
  
### <a name="to-demand-user-membership"></a>Żądanie użytkownika członkostwa  
  
1. Otwórz plik kodu usług Windows Communication Foundation (WCF), który zawiera kodu kontraktu usługi zaimplementowane. Aby uzyskać więcej informacji na temat implementowania kontraktu zobacz [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2. Zastosuj <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybut do każdej metody, które muszą być ograniczone do określonej grupy. Ustaw <xref:System.Security.Permissions.SecurityAttribute.Action%2A> właściwości <xref:System.Security.Permissions.SecurityAction.Demand> i <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> właściwość na nazwę grupy. Na przykład:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  Jeśli zastosujesz <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybutu kontrakt <xref:System.Security.SecurityException> zostanie zgłoszony. Można zastosować tylko atrybut na poziomie metody.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Za pomocą certyfikatu w celu kontroli dostępu do metody  
 Można również użyć `PrincipalPermissionAttribute` klasy do kontrolowania dostępu do metody, jeśli typ poświadczeń klienta jest certyfikatem. Aby to zrobić, konieczne jest posiadanie podmiotu i odcisk palca certyfikatu.  
  
 Aby zbadać certyfikat dla jego właściwości, zobacz [jak: Wyświetlanie certyfikatów za pomocą przystawki programu MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Aby znaleźć wartość odcisku palca, zobacz [jak: Pobieranie odcisku palca certyfikatu](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Aby kontrolować dostęp przy użyciu certyfikatu  
  
1. Zastosuj <xref:System.Security.Permissions.PrincipalPermissionAttribute> klasy, aby ograniczyć dostęp do metody.  
  
2. Ustaw akcję atrybutu <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3. Ustaw `Name` właściwości na ciąg, który składa się z nazwy podmiotu i odcisk palca certyfikatu. Za pomocą średnika i spację, należy oddzielić dwie wartości, jak pokazano w poniższym przykładzie:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. Ustaw <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwość <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> jak pokazano w poniższym przykładzie konfiguracji:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Ustawienie tej wartości na `UseAspNetRoles` wskazuje, że `Name` właściwość `PrincipalPermissionAttribute` posłuży do przeprowadzenia porównania ciągu. Gdy certyfikat jest używany jako poświadczeń klienta, domyślnie WCF łączy nazwa pospolita certyfikatu i odcisk palca średnikiem, aby utworzyć unikatową wartość dla tożsamości podstawowej klienta. Za pomocą `UseAspNetRoles` ustawiony jako `PrincipalPermissionMode` w usłudze tej wartości tożsamości podstawowej jest porównywana z `Name` wartości właściwości w celu ustalenia praw dostępu użytkownika.  
  
     Także ustawić podczas tworzenia usługi samodzielnie hostowanej, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwości w kodzie, jak pokazano w poniższym kodzie:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [Autoryzowanie dostępu do operacji usługi](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
