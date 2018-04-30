---
title: 'Instrukcje: Personifikowanie klienta w usłudze'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 096a3dd1ae5035f6b015ec88ccd8f1ada1dc55ea
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Instrukcje: Personifikowanie klienta w usłudze
Personifikowanie klienta na [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi włącza usługę w celu wykonania zadań w imieniu klienta. Dla akcji może ulec dostępu formantu listy (ACL) sprawdza, takich jak dostęp do katalogów i plików na komputerze lub dostępu do bazy danych programu SQL Server, sprawdź listę kontroli dostępu jest konta użytkownika klienta. W tym temacie przedstawiono podstawowe czynności wymagane do włączenia klienta w domenie systemu Windows ustawić poziom personifikacji klienta. Na przykład pracy tego, zobacz [Personifikowanie klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md). Aby uzyskać więcej informacji na temat personifikacja klienta, zobacz [delegowanie i personifikacja](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
>  Gdy klient i usługa są uruchomione na tym samym komputerze i na kliencie jest uruchomiony na koncie systemu (czyli `Local System` lub `Network Service`), nie można spersonifikować klienta podczas nawiązywania bezpiecznej sesji jest nawiązywane z stanowe tokenów kontekstów zabezpieczeń. Aplikacja WinForms lub konsoli zwykle jest uruchamiane na koncie aktualnie zalogowanego, dzięki czemu mogą być personifikowani konto domyślne. Jednakże, gdy klient jest [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] i tej strony znajduje się w [!INCLUDE[iis601](../../../includes/iis601-md.md)] lub usług IIS 7.0, a następnie klient jest uruchamiany w `Network Service` konto domyślne. Domyślnie wszystkie powiązania dostarczane przez system, które obsługują bezpiecznej sesji używają bezstanowych token kontekstu zabezpieczeń. Jednak jeśli klient jest [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony i bezpieczne sesje z stanowe tokenów kontekstów zabezpieczeń są używane, nie można spersonifikować klienta. Aby uzyskać więcej informacji o używaniu stanowe tokenów kontekstów zabezpieczeń w ramach bezpiecznej sesji, zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Aby włączyć personifikacji klienta z pamięci podręcznej tokenu systemu Windows w usłudze  
  
1.  Utwórz usługę. Samouczek podstawowe procedury, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2.  Użyj powiązania, które używa uwierzytelniania systemu Windows i tworzy sesji, takie jak <xref:System.ServiceModel.NetTcpBinding> lub <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Podczas tworzenia implementacji interfejsu usługi należy zastosować <xref:System.ServiceModel.OperationBehaviorAttribute> klas do metody, która wymaga personifikacji klienta. Ustaw <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwości <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>Aby ustawić poziom personifikacji dozwolone na kliencie  
  
1.  Tworzenie przy użyciu kodu klienta usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Aby uzyskać więcej informacji, zobacz [dostęp do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2.  Po utworzeniu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta, ustaw <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość <xref:System.ServiceModel.Security.WindowsClientCredential> klasy do jednego z <xref:System.Security.Principal.TokenImpersonationLevel> wartości wyliczenia.  
  
    > [!NOTE]
    >  Aby użyć <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negocjowane uwierzytelnianie Kerberos (czasami nazywane *wieloetapowego* lub *wieloetapowych* protokołu Kerberos) musi być używany. Aby uzyskać opis sposobu implementacji, zobacz [najlepsze rozwiązania dotyczące zabezpieczeń](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [Personifikowanie klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [Delegowanie i personifikacja](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
