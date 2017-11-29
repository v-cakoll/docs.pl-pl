---
title: Personifikacja i przywracanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d1bd053cacc677ca66fc2e2a9e14620e1d3a8b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="db842-102">Personifikacja i przywracanie</span><span class="sxs-lookup"><span data-stu-id="db842-102">Impersonating and Reverting</span></span>
<span data-ttu-id="db842-103">Czasami może być konieczne uzyskanie tokenu konta systemu Windows do personifikacji konta systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="db842-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="db842-104">Na przykład aplikacja oparty na programie ASP.NET może być konieczne działają w imieniu kilku użytkowników w różnym czasie.</span><span class="sxs-lookup"><span data-stu-id="db842-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="db842-105">Aplikacja może akceptuje token, który reprezentuje administrator z Internet Information Services (IIS), personifikacji tego użytkownika w trakcie operacji i powrócić do poprzedniej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="db842-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="db842-106">Następnie go może zaakceptować tokenu z usług IIS, które reprezentuje użytkownika z prawami mniej, niektórych operacji i przywrócić ponownie.</span><span class="sxs-lookup"><span data-stu-id="db842-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="db842-107">W sytuacjach, w którym musi być Personifikowane przez aplikację konto systemu Windows, który nie został dołączony do bieżącego wątku przez usługi IIS należy pobrać token tego konta i użyj go, aby aktywować konto.</span><span class="sxs-lookup"><span data-stu-id="db842-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="db842-108">Można to zrobić, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="db842-108">You can do this by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="db842-109">Pobrać tokenu konta dla danego użytkownika poprzez wywołanie niezarządzanej **funkcji LogonUser** metody.</span><span class="sxs-lookup"><span data-stu-id="db842-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="db842-110">Ta metoda nie jest w bibliotece programu .NET Framework klasy podstawowej, ale znajduje się w niezarządzanej **advapi32.dll**.</span><span class="sxs-lookup"><span data-stu-id="db842-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="db842-111">Uzyskiwanie dostępu do metody za pomocą kodu niezarządzanego jest zaawansowanym działaniem i wykracza poza zakres tej dyskusji.</span><span class="sxs-lookup"><span data-stu-id="db842-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="db842-112">Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="db842-112">For more information, see [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="db842-113">Aby uzyskać więcej informacji na temat **funkcji LogonUser** — metoda i **advapi32.dll**, można znaleźć w dokumentacji zestawu SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="db842-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2.  <span data-ttu-id="db842-114">Utwórz nowe wystąpienie klasy **WindowsIdentity** klasy, przekazując tokenu.</span><span class="sxs-lookup"><span data-stu-id="db842-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="db842-115">Poniższy kod ilustruje to wywołanie, gdy `hToken` reprezentuje token systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="db842-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  <span data-ttu-id="db842-116">Rozpocznij personifikacji, tworząc nowe wystąpienie klasy <xref:System.Security.Principal.WindowsImpersonationContext> klasy i Inicjowanie za pomocą <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> metody klasy zainicjowane, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="db842-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  <span data-ttu-id="db842-117">Jeśli nie jest już potrzebne personifikacji, wywołaj <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> metodę, aby przywrócić personifikacji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="db842-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="db842-118">Jeśli zaufany kod został już dołączony <xref:System.Security.Principal.WindowsPrincipal> obiektów w wątku, należy wywołać metodę wystąpienia **Impersonate**, nie ma tokenu konta.</span><span class="sxs-lookup"><span data-stu-id="db842-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="db842-119">Należy pamiętać, że jest to przydatne tylko kiedy **WindowsPrincipal** obiektu w wątku reprezentuje użytkownika innego niż ten, w którym proces jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="db842-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="db842-120">Na przykład może wystąpić sytuacja przy użyciu platformy ASP.NET z uwierzytelniania systemu Windows, włączona i personifikacji wyłączone.</span><span class="sxs-lookup"><span data-stu-id="db842-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="db842-121">W takim przypadku proces działa w ramach konta skonfigurowane w Internet Information Services (IIS), podczas gdy bieżący podmiot zabezpieczeń reprezentuje użytkownika systemu Windows, który uzyskuje dostęp do strony.</span><span class="sxs-lookup"><span data-stu-id="db842-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="db842-122">Należy pamiętać, że ani **personifikacji** ani **Cofnij** zmiany **główna** obiektu (<xref:System.Security.Principal.IPrincipal>) skojarzone z bieżącego kontekstu wywołania.</span><span class="sxs-lookup"><span data-stu-id="db842-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="db842-123">Zamiast personifikacja i przywracanie zmiany token skojarzone z bieżącego procesu systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="db842-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db842-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db842-124">See Also</span></span>  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.Security.Principal.WindowsImpersonationContext>  
 [<span data-ttu-id="db842-125">Główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="db842-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)  
 [<span data-ttu-id="db842-126">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="db842-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
