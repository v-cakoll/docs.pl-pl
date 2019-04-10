---
title: Personifikowanie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: d79ce0d189fc88310594f356f1901d93b3e1e06f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340922"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="4b833-102">Personifikowanie klienta</span><span class="sxs-lookup"><span data-stu-id="4b833-102">Impersonating the Client</span></span>
<span data-ttu-id="4b833-103">Personifikacja — przykład pokazuje, jak dokonać personifikacji aplikacji obiektu wywołującego na usługę tak, aby usługa może uzyskiwać dostęp do zasobów systemu imieniu obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="4b833-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="4b833-104">Ten przykład jest oparty na [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="4b833-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="4b833-105">Pliki konfiguracji usługi i klienta są takie same jak w przypadku [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="4b833-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b833-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4b833-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4b833-107">Kod usługi został zmodyfikowany tak, aby `Add` metody w usłudze personifikuje wywołującemu, korzystając z <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4b833-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="4b833-108">W rezultacie, iż wątek wykonujący w kontekście zabezpieczeń zostanie przełączone na personifikują wywołującego przed wejściem `Add` metody i przywrócone na Kończenie wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="4b833-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="4b833-109">`DisplayIdentityInformation` Pokazaną w poniższym przykładowym kodzie metodą jest funkcja narzędziowa, który wyświetla tożsamości elementu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4b833-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
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
  
 <span data-ttu-id="4b833-110">`Subtract` Metody w usłudze personifikuje wywołującemu, korzystając z wywołania imperatywnego, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4b833-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="4b833-111">Należy pamiętać, że w tym przypadku obiekt wywołujący nie jest Personifikowany dla całego wywołania, ale tylko jest Personifikowany przez pewną część wywołania.</span><span class="sxs-lookup"><span data-stu-id="4b833-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="4b833-112">Ogólnie rzecz biorąc personifikacji dla zakresu najmniejszy preferowane jest personifikacji dla całej operacji.</span><span class="sxs-lookup"><span data-stu-id="4b833-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="4b833-113">Inne metody nie spersonifikować obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4b833-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="4b833-114">Kod klienta została zmodyfikowana, aby ustawić poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span><span class="sxs-lookup"><span data-stu-id="4b833-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="4b833-115">Klient określa poziom personifikacji, który będzie używany przez usługę, za pomocą <xref:System.Security.Principal.TokenImpersonationLevel> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4b833-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="4b833-116">Wyliczanie obsługuje następujące wartości: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> i <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="4b833-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="4b833-117">Aby przeprowadzić kontrolę dostępu podczas uzyskiwania dostępu do zasobu systemu na komputerze lokalnym, który jest chroniony za pomocą listy kontroli dostępu Windows, musi być równa poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4b833-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="4b833-118">Po uruchomieniu przykładu, operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="4b833-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="4b833-119">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="4b833-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b833-120">Usługę należy uruchomić przy użyciu konta administracyjnego lub konto jest uruchamiana przy użyciu musi otrzymać uprawnienia do rejestrowania `http://localhost:8000/ServiceModelSamples` identyfikator URI przy użyciu warstwy protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4b833-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="4b833-121">Te prawa mogą być przyznawane przez skonfigurowanie [rezerwacji Namespace](https://go.microsoft.com/fwlink/?LinkId=95012) przy użyciu [narzędzia Httpcfg.exe](https://go.microsoft.com/fwlink/?LinkId=95010).</span><span class="sxs-lookup"><span data-stu-id="4b833-121">Such rights can be granted by setting up a [Namespace Reservation](https://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](https://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b833-122">Na komputerach z systemem [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], personifikacja jest obsługiwana tylko wtedy, gdy aplikacja Host.exe uprawnień personifikacji.</span><span class="sxs-lookup"><span data-stu-id="4b833-122">On computers running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="4b833-123">(Domyślnie tylko administratorzy mają to uprawnienie). Aby dodać to uprawnienie jest uruchomiona jako konto, przejdź do **narzędzia administracyjne**, otwórz **zasady zabezpieczeń lokalnych**, otwórz **zasady lokalne**, kliknij przycisk **Przypisywanie praw użytkownika**i wybierz **Personifikowanie klienta po uwierzytelnieniu** i kliknij dwukrotnie **właściwości** można dodać użytkownika lub grupy.</span><span class="sxs-lookup"><span data-stu-id="4b833-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4b833-124">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="4b833-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4b833-125">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b833-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4b833-126">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b833-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4b833-127">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b833-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="4b833-128">Aby zademonstrować, że usługa personifikuje obiekt wywołujący, uruchom klienta przy użyciu innego konta niż ten, który jest uruchamiany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="4b833-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="4b833-129">Aby to zrobić, w wierszu polecenia wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="4b833-129">To do so, at the command prompt, type:</span></span>  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="4b833-130">Następnie zostanie wyświetlony monit o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="4b833-130">You are then prompted for a password.</span></span> <span data-ttu-id="4b833-131">Wprowadź hasło dla konta, które wcześniej określono.</span><span class="sxs-lookup"><span data-stu-id="4b833-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="4b833-132">Po uruchomieniu klienta, Zapamiętaj tożsamość przed i po uruchomieniu przy użyciu różnych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="4b833-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
