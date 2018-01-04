---
title: "Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute"
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
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da91e3456fdca863980c89f45e0cc28db19170be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="f925a-102">Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="f925a-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>
<span data-ttu-id="f925a-103">Kontrolowanie dostępu do zasobów na komputerze domeny systemu Windows jest zadaniem podstawowych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f925a-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="f925a-104">Na przykład tylko określonym użytkownikom powinien móc wyświetlić poufnych danych, takich jak lista płac informacji.</span><span class="sxs-lookup"><span data-stu-id="f925a-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="f925a-105">W tym temacie wyjaśniono, jak ograniczyć dostęp do metody przez wymaganie, który użytkownik należy do grupy wstępnie zdefiniowanych.</span><span class="sxs-lookup"><span data-stu-id="f925a-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="f925a-106">Dla przykładu pracy, zobacz [Autoryzowanie dostępu do operacji usługi](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f925a-106">For a working sample, see [Authorizing Access to Service Operations](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="f925a-107">Zadanie składa się z dwóch oddzielnych procedur.</span><span class="sxs-lookup"><span data-stu-id="f925a-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="f925a-108">Pierwszy tworzy grupy i wypełnia je użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="f925a-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="f925a-109">Druga stosuje <xref:System.Security.Permissions.PrincipalPermissionAttribute> klasę, aby określić grupę.</span><span class="sxs-lookup"><span data-stu-id="f925a-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="f925a-110">Aby utworzyć grupy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f925a-110">To create a Windows group</span></span>  
  
1.  <span data-ttu-id="f925a-111">Otwórz **Zarządzanie komputerem** konsoli.</span><span class="sxs-lookup"><span data-stu-id="f925a-111">Open the **Computer Management** console.</span></span>  
  
2.  <span data-ttu-id="f925a-112">W lewym panelu kliknij **lokalnych użytkowników i grup**.</span><span class="sxs-lookup"><span data-stu-id="f925a-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="f925a-113">Kliknij prawym przyciskiem myszy **grup**i kliknij przycisk **Nowa grupa**.</span><span class="sxs-lookup"><span data-stu-id="f925a-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4.  <span data-ttu-id="f925a-114">W **Nazwa grupy** wpisz nazwę nowej grupy.</span><span class="sxs-lookup"><span data-stu-id="f925a-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5.  <span data-ttu-id="f925a-115">W **opis** wpisz opis nowej grupy.</span><span class="sxs-lookup"><span data-stu-id="f925a-115">In the **Description** box, type a description of the new group.</span></span>  
  
6.  <span data-ttu-id="f925a-116">Kliknij przycisk **Dodaj** przycisk, aby dodać nowe elementy członkowskie do grupy.</span><span class="sxs-lookup"><span data-stu-id="f925a-116">Click the **Add** button to add new members to the group.</span></span>  
  
7.  <span data-ttu-id="f925a-117">Jeśli dodano użytkownika do grupy i chcesz przetestować następujący kod, musisz wylogować się komputer i zalogować ponownie, aby zostać zawarte w grupie.</span><span class="sxs-lookup"><span data-stu-id="f925a-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="f925a-118">Żądanie użytkownika członkostwa</span><span class="sxs-lookup"><span data-stu-id="f925a-118">To demand user membership</span></span>  
  
1.  <span data-ttu-id="f925a-119">Otwórz [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] pliku kodu zawierającego kodu kontraktu usługi zaimplementowany.</span><span class="sxs-lookup"><span data-stu-id="f925a-119">Open the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] code file that contains the implemented service contract code.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f925a-120">Implementowanie kontraktu, zobacz [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f925a-120"> implementing a contract, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="f925a-121">Zastosuj <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybutu do każdej metody, która musi być ograniczony do określonej grupy.</span><span class="sxs-lookup"><span data-stu-id="f925a-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="f925a-122">Ustaw <xref:System.Security.Permissions.SecurityAttribute.Action%2A> właściwości <xref:System.Security.Permissions.SecurityAction.Demand> i <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> właściwość na nazwę grupy.</span><span class="sxs-lookup"><span data-stu-id="f925a-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="f925a-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f925a-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="f925a-124">W przypadku zastosowania <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybutu kontrakt <xref:System.Security.SecurityException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="f925a-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="f925a-125">Można stosować tylko atrybut na poziomie metody.</span><span class="sxs-lookup"><span data-stu-id="f925a-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="f925a-126">Używa certyfikatu, aby kontrolować dostęp do metody</span><span class="sxs-lookup"><span data-stu-id="f925a-126">Using a Certificate to Control Access to a Method</span></span>  
 <span data-ttu-id="f925a-127">Można również użyć `PrincipalPermissionAttribute` klasy do kontrolowania dostępu do metody, jeśli certyfikat jest typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="f925a-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="f925a-128">Aby to zrobić, musi mieć podmiotu i odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f925a-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="f925a-129">Aby zbadać jego właściwości certyfikatu, zobacz [porady: wyświetlanie certyfikatów w przystawce MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="f925a-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="f925a-130">Aby znaleźć wartość odcisku palca, zobacz [porady: Pobieranie odcisku palca certyfikatu](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="f925a-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="f925a-131">Aby kontrolować dostęp przy użyciu certyfikatu</span><span class="sxs-lookup"><span data-stu-id="f925a-131">To control access using a certificate</span></span>  
  
1.  <span data-ttu-id="f925a-132">Zastosuj <xref:System.Security.Permissions.PrincipalPermissionAttribute> klasy, do których chcesz ograniczyć dostęp do metody.</span><span class="sxs-lookup"><span data-stu-id="f925a-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2.  <span data-ttu-id="f925a-133">Ustawianie akcji atrybutu z <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f925a-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3.  <span data-ttu-id="f925a-134">Ustaw `Name` właściwości na ciąg, który składa się z nazwy podmiotu i odcisk palca certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f925a-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="f925a-135">Oddziel dwóch wartości średnikiem i spacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f925a-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  <span data-ttu-id="f925a-136">Ustaw <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwości <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> jak pokazano w poniższym przykładzie konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="f925a-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="f925a-137">Ustawienie tej wartości na `UseAspNetRoles` oznacza to, że `Name` właściwość `PrincipalPermissionAttribute` posłuży do przeprowadzenia porównania ciągów.</span><span class="sxs-lookup"><span data-stu-id="f925a-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="f925a-138">Gdy certyfikat jest używany jako poświadczeń klienta, domyślnie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] łączy nazwa pospolita certyfikatu i odcisk palca średnikiem, aby utworzyć unikatową wartość dla podstawowej tożsamości klienta.</span><span class="sxs-lookup"><span data-stu-id="f925a-138">When a certificate is used as a client credential, by default [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="f925a-139">Z `UseAspNetRoles` Ustaw jako `PrincipalPermissionMode` w usłudze tej wartości podstawowej tożsamości jest porównywana z `Name` wartości właściwości, aby określić uprawnienia dostępu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f925a-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="f925a-140">Możesz również ustawić podczas tworzenia samodzielnie hostowana usługa, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwości w kodzie, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f925a-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f925a-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f925a-141">See Also</span></span>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.SecurityAction.Demand>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>  
 [<span data-ttu-id="f925a-142">Autoryzowanie dostępu do operacji usługi</span><span class="sxs-lookup"><span data-stu-id="f925a-142">Authorizing Access to Service Operations</span></span>](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="f925a-143">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f925a-143">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="f925a-144">Implementowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="f925a-144">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
