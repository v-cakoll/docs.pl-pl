---
title: 'Instrukcje: Personifikowanie klienta w usłudze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: d58f25f279bf2baa1caa7744cea94b909f48866f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310580"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Instrukcje: Personifikowanie klienta w usłudze
Personifikowanie klienta usługi Windows Communication Foundation (WCF) umożliwia usługi w celu wykonywania zadań w imieniu klienta. Dla akcji z zastrzeżeniem dostępu kontrolki listy (ACL) sprawdza, takich jak dostęp do katalogów i plików na maszynie lub dostęp do bazy danych programu SQL Server, sprawdź listy ACL jest względem konta użytkownika klienta. W tym temacie przedstawiono podstawowe kroki wymagane do włączenia klienta w domenie Windows ustawić poziom personifikacji klienta. Dla pracy na przykład, zobacz [Personifikowanie klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md). Aby uzyskać więcej informacji na temat personifikację klienta, zobacz [delegowanie i personifikacja](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
>  Gdy klienta i usługi są uruchomione na tym samym komputerze, a klient jest uruchomiony w ramach konta system (czyli `Local System` lub `Network Service`), nie można spersonifikować klienta, po nawiązaniu bezpiecznej sesji przy użyciu stanowych tokenów kontekstu zabezpieczeń. Aplikacja WinForms lub konsoli zwykle jest uruchamiany aktualnie zalogowanego konta, tak aby konta mogą personalizacji domyślnie. Jednakże, gdy klient jest [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony i na tej stronie znajduje się w [!INCLUDE[iis601](../../../includes/iis601-md.md)] lub usług IIS 7.0, a następnie klient jest uruchamiany w ramach `Network Service` konto domyślne. Domyślnie wszystkie powiązania dostarczane przez system, które obsługują bezpiecznej sesji używają bezstanowe tokenu kontekstu zabezpieczeń. Jednakże jeśli klient jest [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony i bezpiecznej sesji przy użyciu stanowych tokenów kontekstu zabezpieczeń są używane, nie można spersonifikować klienta. Aby uzyskać więcej informacji na temat tokeny stanowych kontekstu zabezpieczeń w ramach bezpiecznej sesji zobacz [jak: Utwórz kontekst zabezpieczeń tokenu dla bezpiecznej sesji](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Aby włączyć personifikację klienta z pamięci podręcznej tokenu Windows w usłudze  
  
1. Utwórz usługę. Samouczek, część tej procedury podstawowe, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2. Użyj powiązania, który korzysta z uwierzytelniania Windows i tworzy sesję, takich jak <xref:System.ServiceModel.NetTcpBinding> lub <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Podczas tworzenia implementacji interfejsu usługi należy zastosować <xref:System.ServiceModel.OperationBehaviorAttribute> klas do metody, która wymaga Personifikowanie klienta. Ustaw <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>Aby ustawić poziom personifikacji dozwolonych na komputerze klienckim  
  
1. Tworzenie kodu klienta usługi przy użyciu [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Aby uzyskać więcej informacji, zobacz [uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2. Po utworzeniu klienta WCF, należy ustawić <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość <xref:System.ServiceModel.Security.WindowsClientCredential> klasy do jednego z <xref:System.Security.Principal.TokenImpersonationLevel> wartości wyliczenia.  
  
    > [!NOTE]
    >  Do użycia <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, wynegocjowanym uwierzytelnianie Kerberos (nazywane czasem *wielu gałęzi* lub *wieloetapowego* protokołu Kerberos) musi być używana. Aby uzyskać opis sposobu implementacji, zobacz [najlepsze rozwiązania dotyczące zabezpieczeń](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [Personifikowanie klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [Delegowanie i personifikacja](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
