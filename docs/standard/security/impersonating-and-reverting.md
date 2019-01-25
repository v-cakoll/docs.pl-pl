---
title: Personifikacja i przywracanie
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bec065e2a78551b85fe766f1b81590b18f4679d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516827"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="c79a9-102">Personifikacja i przywracanie</span><span class="sxs-lookup"><span data-stu-id="c79a9-102">Impersonating and Reverting</span></span>
<span data-ttu-id="c79a9-103">Czasami może być konieczne do uzyskania tokenu konta Windows dokonać personifikacji konta Windows.</span><span class="sxs-lookup"><span data-stu-id="c79a9-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="c79a9-104">Na przykład aplikacji opartych na programie ASP.NET może być konieczne działanie w imieniu kilku użytkowników w różnym czasie.</span><span class="sxs-lookup"><span data-stu-id="c79a9-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="c79a9-105">Aplikację może akceptuje token, który reprezentuje administrator z Internet Information Services (IIS), personifikacji tego użytkownika, w trakcie operacji i powrócić do poprzedniej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="c79a9-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="c79a9-106">Następnie go może zaakceptować token za pomocą programu IIS, który reprezentuje użytkownika z prawami mniej, wykonać kilka operacji i przywrócić ponownie.</span><span class="sxs-lookup"><span data-stu-id="c79a9-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="c79a9-107">W sytuacjach, w której aplikacja musi dokonać personifikacji konta Windows, który nie został dołączony do bieżącego wątku przez usługi IIS należy pobrać tokenu dla konta i użyć go do aktywowania konta.</span><span class="sxs-lookup"><span data-stu-id="c79a9-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="c79a9-108">Można to zrobić, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c79a9-108">You can do this by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="c79a9-109">Pobieranie tokenu konta dla danego użytkownika przez wywołania do niezarządzanej **funkcji LogonUser** metody.</span><span class="sxs-lookup"><span data-stu-id="c79a9-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="c79a9-110">Ta metoda nie znajduje się w bibliotece klasy bazowej .NET Framework, ale znajduje się w niezarządzanej **advapi32.dll**.</span><span class="sxs-lookup"><span data-stu-id="c79a9-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="c79a9-111">Uzyskiwanie dostępu do metody w kodzie niezarządzanym jest zaawansowanym działaniem i wykracza poza zakres tej dyskusji.</span><span class="sxs-lookup"><span data-stu-id="c79a9-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="c79a9-112">Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="c79a9-112">For more information, see [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="c79a9-113">Aby uzyskać więcej informacji na temat **funkcji LogonUser** metody i **advapi32.dll**, znajdują się w dokumentacji zestawu SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="c79a9-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2.  <span data-ttu-id="c79a9-114">Utwórz nowe wystąpienie klasy **WindowsIdentity** klasy, przekazując tokenu.</span><span class="sxs-lookup"><span data-stu-id="c79a9-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="c79a9-115">Poniższy kod przedstawia to wywołanie, gdy `hToken` reprezentuje Windows token.</span><span class="sxs-lookup"><span data-stu-id="c79a9-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  <span data-ttu-id="c79a9-116">Rozpocznij personifikacji, tworząc nowe wystąpienie klasy <xref:System.Security.Principal.WindowsImpersonationContext> klasy i inicjując go przy użyciu <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> metody klasy zainicjowane, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c79a9-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  <span data-ttu-id="c79a9-117">Jeśli nie potrzebujesz już być Personifikowane przez aplikację, należy wywołać <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> metodę, aby przywrócić personifikacji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c79a9-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="c79a9-118">Jeśli zaufanego kodu jest już dołączony <xref:System.Security.Principal.WindowsPrincipal> obiekt wątku, można wywołać metodę wystąpienia **Personifikuj**, nie przyjmuje tokenu konta.</span><span class="sxs-lookup"><span data-stu-id="c79a9-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="c79a9-119">Należy pamiętać, że ta opcja jest przydatna podczas **WindowsPrincipal** obiektu w wątku reprezentuje użytkownik inny niż ten, w którym proces jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c79a9-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="c79a9-120">Na przykład można napotkać tę sytuację, za pomocą programu ASP.NET z uwierzytelnianiem Windows, włączone i wyłączone personifikacji.</span><span class="sxs-lookup"><span data-stu-id="c79a9-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="c79a9-121">W tym przypadku proces działa przy użyciu konta skonfigurowane w Internet Information Services (IIS), gdy bieżący podmiot zabezpieczeń reprezentuje użytkownika Windows, który uzyskuje dostęp do strony.</span><span class="sxs-lookup"><span data-stu-id="c79a9-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="c79a9-122">Należy pamiętać, że żadna z nich nie **Personifikuj** ani **Cofnij** zmiany **jednostki** obiektu (<xref:System.Security.Principal.IPrincipal>) skojarzony z bieżącym kontekstem wywołania.</span><span class="sxs-lookup"><span data-stu-id="c79a9-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="c79a9-123">Zamiast personifikacji i cofanie zmian tokenu skojarzone z bieżącym procesem systemu operacyjnego...</span><span class="sxs-lookup"><span data-stu-id="c79a9-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79a9-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c79a9-124">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="c79a9-125">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="c79a9-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
- [<span data-ttu-id="c79a9-126">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="c79a9-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
