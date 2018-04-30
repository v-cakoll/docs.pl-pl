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
# <a name="how-to-impersonate-a-client-on-a-service"></a><span data-ttu-id="50a7d-102">Instrukcje: Personifikowanie klienta w usłudze</span><span class="sxs-lookup"><span data-stu-id="50a7d-102">How to: Impersonate a Client on a Service</span></span>
<span data-ttu-id="50a7d-103">Personifikowanie klienta na [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi włącza usługę w celu wykonania zadań w imieniu klienta.</span><span class="sxs-lookup"><span data-stu-id="50a7d-103">Impersonating a client on a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service enables the service to perform actions on behalf of the client.</span></span> <span data-ttu-id="50a7d-104">Dla akcji może ulec dostępu formantu listy (ACL) sprawdza, takich jak dostęp do katalogów i plików na komputerze lub dostępu do bazy danych programu SQL Server, sprawdź listę kontroli dostępu jest konta użytkownika klienta.</span><span class="sxs-lookup"><span data-stu-id="50a7d-104">For actions subject to access control list (ACL) checks, such as access to directories and files on a machine or access to a SQL Server database, the ACL check is against the client user account.</span></span> <span data-ttu-id="50a7d-105">W tym temacie przedstawiono podstawowe czynności wymagane do włączenia klienta w domenie systemu Windows ustawić poziom personifikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="50a7d-105">This topic shows the basic steps required to enable a client in a Windows domain to set a client impersonation level.</span></span> <span data-ttu-id="50a7d-106">Na przykład pracy tego, zobacz [Personifikowanie klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span><span class="sxs-lookup"><span data-stu-id="50a7d-106">For a working example of this, see [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span></span> <span data-ttu-id="50a7d-107">Aby uzyskać więcej informacji na temat personifikacja klienta, zobacz [delegowanie i personifikacja](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="50a7d-107">For more information about client impersonation, see [Delegation and Impersonation](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50a7d-108">Gdy klient i usługa są uruchomione na tym samym komputerze i na kliencie jest uruchomiony na koncie systemu (czyli `Local System` lub `Network Service`), nie można spersonifikować klienta podczas nawiązywania bezpiecznej sesji jest nawiązywane z stanowe tokenów kontekstów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="50a7d-108">When the client and service are running on the same computer and the client is running under a system account (that is, `Local System` or `Network Service`), the client cannot be impersonated when a secure session is established with stateful Security Context tokens.</span></span> <span data-ttu-id="50a7d-109">Aplikacja WinForms lub konsoli zwykle jest uruchamiane na koncie aktualnie zalogowanego, dzięki czemu mogą być personifikowani konto domyślne.</span><span class="sxs-lookup"><span data-stu-id="50a7d-109">A WinForms or console application typically is run under the currently logged in account, so that account can be impersonated by default.</span></span> <span data-ttu-id="50a7d-110">Jednakże, gdy klient jest [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] i tej strony znajduje się w [!INCLUDE[iis601](../../../includes/iis601-md.md)] lub usług IIS 7.0, a następnie klient jest uruchamiany w `Network Service` konto domyślne.</span><span class="sxs-lookup"><span data-stu-id="50a7d-110">However, when the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and that page is hosted in [!INCLUDE[iis601](../../../includes/iis601-md.md)] or IIS 7.0, then the client does run under the `Network Service` account by default.</span></span> <span data-ttu-id="50a7d-111">Domyślnie wszystkie powiązania dostarczane przez system, które obsługują bezpiecznej sesji używają bezstanowych token kontekstu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="50a7d-111">All of the system-provided bindings that support secure sessions use a stateless Security Context token by default.</span></span> <span data-ttu-id="50a7d-112">Jednak jeśli klient jest [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] strony i bezpieczne sesje z stanowe tokenów kontekstów zabezpieczeń są używane, nie można spersonifikować klienta.</span><span class="sxs-lookup"><span data-stu-id="50a7d-112">However, if the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and secure sessions with stateful Security Context tokens are used, the client cannot be impersonated.</span></span> <span data-ttu-id="50a7d-113">Aby uzyskać więcej informacji o używaniu stanowe tokenów kontekstów zabezpieczeń w ramach bezpiecznej sesji, zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="50a7d-113">For more information about using stateful Security Context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a><span data-ttu-id="50a7d-114">Aby włączyć personifikacji klienta z pamięci podręcznej tokenu systemu Windows w usłudze</span><span class="sxs-lookup"><span data-stu-id="50a7d-114">To enable impersonation of a client from a cached Windows token on a service</span></span>  
  
1.  <span data-ttu-id="50a7d-115">Utwórz usługę.</span><span class="sxs-lookup"><span data-stu-id="50a7d-115">Create the service.</span></span> <span data-ttu-id="50a7d-116">Samouczek podstawowe procedury, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="50a7d-116">For a tutorial of this basic procedure, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
2.  <span data-ttu-id="50a7d-117">Użyj powiązania, które używa uwierzytelniania systemu Windows i tworzy sesji, takie jak <xref:System.ServiceModel.NetTcpBinding> lub <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="50a7d-117">Use a binding that uses Windows authentication and creates a session, such as <xref:System.ServiceModel.NetTcpBinding> or <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3.  <span data-ttu-id="50a7d-118">Podczas tworzenia implementacji interfejsu usługi należy zastosować <xref:System.ServiceModel.OperationBehaviorAttribute> klas do metody, która wymaga personifikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="50a7d-118">When creating the implementation of the service's interface, apply the <xref:System.ServiceModel.OperationBehaviorAttribute> class to the method that requires client impersonation.</span></span> <span data-ttu-id="50a7d-119">Ustaw <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwości <xref:System.ServiceModel.ImpersonationOption.Required>.</span><span class="sxs-lookup"><span data-stu-id="50a7d-119">Set the <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> property to <xref:System.ServiceModel.ImpersonationOption.Required>.</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a><span data-ttu-id="50a7d-120">Aby ustawić poziom personifikacji dozwolone na kliencie</span><span class="sxs-lookup"><span data-stu-id="50a7d-120">To set the allowed impersonation level on the client</span></span>  
  
1.  <span data-ttu-id="50a7d-121">Tworzenie przy użyciu kodu klienta usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="50a7d-121">Create service client code by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="50a7d-122">Aby uzyskać więcej informacji, zobacz [dostęp do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="50a7d-122">For more information, see [Accessing Services Using a WCF Client](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="50a7d-123">Po utworzeniu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta, ustaw <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość <xref:System.ServiceModel.Security.WindowsClientCredential> klasy do jednego z <xref:System.Security.Principal.TokenImpersonationLevel> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="50a7d-123">After creating the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client, set the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property of the <xref:System.ServiceModel.Security.WindowsClientCredential> class to one of the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration values.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50a7d-124">Aby użyć <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negocjowane uwierzytelnianie Kerberos (czasami nazywane *wieloetapowego* lub *wieloetapowych* protokołu Kerberos) musi być używany.</span><span class="sxs-lookup"><span data-stu-id="50a7d-124">To use <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negotiated Kerberos authentication (sometimes called *multi-leg* or *multi-step* Kerberos) must be used.</span></span> <span data-ttu-id="50a7d-125">Aby uzyskać opis sposobu implementacji, zobacz [najlepsze rozwiązania dotyczące zabezpieczeń](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="50a7d-125">For a description of how to implement this, see [Best Practices for Security](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="50a7d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50a7d-126">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [<span data-ttu-id="50a7d-127">Personifikowanie klienta</span><span class="sxs-lookup"><span data-stu-id="50a7d-127">Impersonating the Client</span></span>](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [<span data-ttu-id="50a7d-128">Delegowanie i personifikacja</span><span class="sxs-lookup"><span data-stu-id="50a7d-128">Delegation and Impersonation</span></span>](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
