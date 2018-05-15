---
title: Personifikowanie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 4c5d911bfbfcd33248e15b9fc822abdc9cf4046c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="impersonating-the-client"></a><span data-ttu-id="a78ff-102">Personifikowanie klienta</span><span class="sxs-lookup"><span data-stu-id="a78ff-102">Impersonating the Client</span></span>
<span data-ttu-id="a78ff-103">Personifikacja — przykład pokazuje, jak dokonać personifikacji aplikacji obiektu wywołującego w usłudze, aby usługa może uzyskiwać dostęp do zasobów systemu imieniu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a78ff-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="a78ff-104">Ten przykład jest oparty na [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="a78ff-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="a78ff-105">Pliki konfiguracji usługi i klienta są takie same, jak te [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="a78ff-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a78ff-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a78ff-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a78ff-107">Zmodyfikowano kodu usługi tak, aby `Add` metody w usłudze personifikuje wywołującemu, korzystając z <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="a78ff-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="a78ff-108">W związku z tym przełączania kontekstu zabezpieczeń wykonywania wątku do personifikują wywołującego przed wprowadzeniem `Add` — metoda i przywrócone na kończenie metody.</span><span class="sxs-lookup"><span data-stu-id="a78ff-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="a78ff-109">`DisplayIdentityInformation` Metod przedstawionych w następujący przykładowy kod to funkcja narzędzia, która wyświetla tożsamość obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a78ff-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```  
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
  
 <span data-ttu-id="a78ff-110">`Subtract` Wywołującego przy użyciu wywołania konieczne, jak pokazano w poniższym kodzie próbki personifikuje metody dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a78ff-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="a78ff-111">Należy pamiętać, że w takim przypadku obiekt wywołujący nie jest traktowane całego wywołanie, ale Personifikowany jest tylko część wywołania.</span><span class="sxs-lookup"><span data-stu-id="a78ff-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="a78ff-112">Ogólnie rzecz biorąc personifikacja zakresie najmniejszą preferowane jest personifikacji dla całej operacji.</span><span class="sxs-lookup"><span data-stu-id="a78ff-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="a78ff-113">Inne metody nie personifikują wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a78ff-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="a78ff-114">Kod klienta została zmodyfikowana, aby ustawić poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span><span class="sxs-lookup"><span data-stu-id="a78ff-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="a78ff-115">Klient określa poziom personifikacji używanego przez usługę, używając <xref:System.Security.Principal.TokenImpersonationLevel> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a78ff-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="a78ff-116">Wyliczenie obsługuje następujące wartości: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> i <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span><span class="sxs-lookup"><span data-stu-id="a78ff-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="a78ff-117">Aby przeprowadzić sprawdzanie dostępu podczas uzyskiwania dostępu do zasobu systemu na komputerze lokalnym, który jest chroniony za pomocą listy ACL systemu Windows, poziom personifikacji musi mieć ustawioną <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="a78ff-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="a78ff-118">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="a78ff-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="a78ff-119">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="a78ff-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a78ff-120">Usługę należy uruchomić przy użyciu konta administratora lub konta, zostanie uruchomiony w musi otrzymać uprawnienia do rejestrowania http://localhost:8000/ServiceModelSamples identyfikatora URI z warstwą HTTP.</span><span class="sxs-lookup"><span data-stu-id="a78ff-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the http://localhost:8000/ServiceModelSamples URI with the HTTP layer.</span></span> <span data-ttu-id="a78ff-121">Te prawa można udzielić, konfigurując [rezerwacji Namespace](http://go.microsoft.com/fwlink/?LinkId=95012) przy użyciu [narzędzia Httpcfg.exe](http://go.microsoft.com/fwlink/?LinkId=95010).</span><span class="sxs-lookup"><span data-stu-id="a78ff-121">Such rights can be granted by setting up a [Namespace Reservation](http://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](http://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a78ff-122">Na komputerach z systemem [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], personifikacja jest obsługiwana tylko wtedy, gdy aplikacja Host.exe ma uprawnienie do personifikacji.</span><span class="sxs-lookup"><span data-stu-id="a78ff-122">On computers running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="a78ff-123">(Domyślnie tylko Administratorzy ma tych uprawnień). Aby dodać to uprawnienie do usługa jest uruchomiona jako konto, przejdź do **narzędzia administracyjne**, otwórz **zasady zabezpieczeń lokalnych**, otwórz **zasady lokalne**, kliknij przycisk **Przypisywanie praw użytkownika**i wybierz **Personifikuj klienta po uwierzytelnieniu** i kliknij dwukrotnie **właściwości** można dodać użytkownika lub grupę.</span><span class="sxs-lookup"><span data-stu-id="a78ff-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a78ff-124">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="a78ff-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a78ff-125">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a78ff-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a78ff-126">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a78ff-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a78ff-127">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a78ff-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="a78ff-128">Aby zademonstrować, że usługa personifikuje wywołującego, uruchom klienta przy użyciu innego konta niż ten, który jest uruchomiona w obszarze.</span><span class="sxs-lookup"><span data-stu-id="a78ff-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="a78ff-129">Aby to zrobić, w wierszu polecenia wpisz:</span><span class="sxs-lookup"><span data-stu-id="a78ff-129">To do so, at the command prompt, type:</span></span>  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="a78ff-130">Następnie zostanie wyświetlony monit o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="a78ff-130">You are then prompted for a password.</span></span> <span data-ttu-id="a78ff-131">Wprowadź hasło dla konta, które wcześniej określona.</span><span class="sxs-lookup"><span data-stu-id="a78ff-131">Enter the password for the account you previously specified.</span></span>  
  
5.  <span data-ttu-id="a78ff-132">Po uruchomieniu klienta, należy pamiętać tożsamości przed i po uruchomieniu go z innymi poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="a78ff-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78ff-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a78ff-133">See Also</span></span>
