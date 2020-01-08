---
title: Personifikowanie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 0c262d8b5460f236ef0429154ae337c7adf96714
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338711"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="80940-102">Personifikowanie klienta</span><span class="sxs-lookup"><span data-stu-id="80940-102">Impersonating the Client</span></span>
<span data-ttu-id="80940-103">Przykład personifikacji demonstruje sposób personifikacji aplikacji wywołującej w usłudze, aby usługa mogła uzyskać dostęp do zasobów systemowych w imieniu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="80940-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="80940-104">Ten przykład jest oparty [na przykładu samoobsługowego](../../../../docs/framework/wcf/samples/self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="80940-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="80940-105">Pliki konfiguracji usługi i klienta są takie same jak w przypadku przykładu samoobsługowego [hosta](../../../../docs/framework/wcf/samples/self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="80940-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80940-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="80940-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="80940-107">Kod usługi został zmodyfikowany w taki sposób, że metoda `Add` w usłudze personifikuje obiekt wywołujący przy użyciu <xref:System.ServiceModel.OperationBehaviorAttribute>, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="80940-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="80940-108">W związku z tym kontekst zabezpieczeń wykonywanego wątku jest przełączany w celu personifikacji obiektu wywołującego przed wprowadzeniem metody `Add` i przywróceniem wyjścia z metody.</span><span class="sxs-lookup"><span data-stu-id="80940-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="80940-109">Metoda `DisplayIdentityInformation` pokazana w poniższym przykładowym kodzie to funkcja narzędziowa, która wyświetla tożsamość obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="80940-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```csharp
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",   
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 <span data-ttu-id="80940-110">Metoda `Subtract` w usłudze personifikuje obiekt wywołujący przy użyciu bezwzględnych wywołań, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="80940-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```csharp
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    Console.WriteLine("Before impersonating");  
    DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs   
            // on the system resource are enforced in the caller's context.   
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
    Console.WriteLine("After reverting");  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="80940-111">Należy zauważyć, że w tym przypadku obiekt wywołujący nie jest personifikowany dla całego wywołania, ale jest personifikowany tylko dla części wywołania.</span><span class="sxs-lookup"><span data-stu-id="80940-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="80940-112">Ogólnie rzecz biorąc, personifikowanie dla najmniejszego zakresu jest preferowane personifikacja dla całej operacji.</span><span class="sxs-lookup"><span data-stu-id="80940-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="80940-113">Inne metody nie personifikują wywołującego.</span><span class="sxs-lookup"><span data-stu-id="80940-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="80940-114">Kod klienta został zmodyfikowany w celu ustawienia poziomu personifikacji na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span><span class="sxs-lookup"><span data-stu-id="80940-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="80940-115">Klient określa poziom personifikacji, który ma być używany przez usługę, przy użyciu wyliczenia <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="80940-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="80940-116">Wyliczenie obsługuje następujące wartości: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> i <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="80940-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="80940-117">Aby przeprowadzić sprawdzanie dostępu podczas uzyskiwania dostępu do zasobu systemowego na komputerze lokalnym, który jest chroniony przy użyciu list ACL systemu Windows, poziom personifikacji musi być ustawiony na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="80940-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="80940-118">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="80940-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="80940-119">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="80940-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80940-120">Usługa musi być uruchomiona w ramach konta administracyjnego lub konto, na którym jest uruchamiane, musi mieć przyznane prawa do rejestrowania identyfikatora URI `http://localhost:8000/ServiceModelSamples` za pomocą warstwy HTTP.</span><span class="sxs-lookup"><span data-stu-id="80940-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="80940-121">Takie prawa można udzielić przez skonfigurowanie [rezerwacji przestrzeni nazw](https://go.microsoft.com/fwlink/?LinkId=95012) za pomocą [narzędzia HttpCfg. exe](https://go.microsoft.com/fwlink/?LinkId=95010).</span><span class="sxs-lookup"><span data-stu-id="80940-121">Such rights can be granted by setting up a [Namespace Reservation](https://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](https://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80940-122">Na komputerach z systemem Windows Server 2003 Personifikacja jest obsługiwana tylko wtedy, gdy aplikacja host. exe ma uprawnienie personifikacji.</span><span class="sxs-lookup"><span data-stu-id="80940-122">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="80940-123">(Domyślnie tylko Administratorzy mają to uprawnienie). Aby dodać to uprawnienie do konta, na którym działa usługa, przejdź do pozycji **Narzędzia administracyjne**, Otwórz **pozycję Zasady zabezpieczeń lokalnych**, Otwórz **Zasady lokalne**, kliknij pozycję **Przypisywanie praw użytkownika**, a następnie wybierz opcję **Personifikuj klienta po uwierzytelnieniu** , a następnie kliknij dwukrotnie pozycję **Właściwości** , aby dodać użytkownika lub grupę.</span><span class="sxs-lookup"><span data-stu-id="80940-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="80940-124">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="80940-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="80940-125">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80940-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="80940-126">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80940-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="80940-127">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80940-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="80940-128">Aby zademonstrować, że usługa personifikuje wywołującego, uruchom klienta przy użyciu innego konta niż to, w którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="80940-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="80940-129">Aby to zrobić, w wierszu polecenia wpisz:</span><span class="sxs-lookup"><span data-stu-id="80940-129">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="80940-130">Zostanie wyświetlony monit o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="80940-130">You are then prompted for a password.</span></span> <span data-ttu-id="80940-131">Wprowadź hasło do konta, które zostało wcześniej określone.</span><span class="sxs-lookup"><span data-stu-id="80940-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="80940-132">Po uruchomieniu klienta należy zanotować jego tożsamość przed i po jej uruchomieniu z innymi poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="80940-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
