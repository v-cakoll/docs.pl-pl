---
title: Personifikowanie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: b5272d8b4dbac60e14fe87accbb08a2073ed65ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594637"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="f6db0-102">Personifikowanie klienta</span><span class="sxs-lookup"><span data-stu-id="f6db0-102">Impersonating the Client</span></span>
<span data-ttu-id="f6db0-103">Przykład personifikacji demonstruje sposób personifikacji aplikacji wywołującej w usłudze, aby usługa mogła uzyskać dostęp do zasobów systemowych w imieniu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f6db0-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="f6db0-104">Ten przykład jest oparty [na przykładu samoobsługowego](self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="f6db0-104">This sample is based on the [Self-Host](self-host.md) sample.</span></span> <span data-ttu-id="f6db0-105">Pliki konfiguracji usługi i klienta są takie same jak w przypadku przykładu samoobsługowego [hosta](self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="f6db0-105">The service and client configuration files are the same as that of the [Self-Host](self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6db0-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f6db0-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f6db0-107">Kod usługi został zmodyfikowany w taki sposób, że `Add` Metoda w usłudze personifikuje obiekt wywołujący przy użyciu metody <xref:System.ServiceModel.OperationBehaviorAttribute> , jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f6db0-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="f6db0-108">W związku z tym kontekst zabezpieczeń wykonywanego wątku jest przełączany w celu personifikacji obiektu wywołującego przed wprowadzeniem `Add` metody i przywróceniem wyjścia z metody.</span><span class="sxs-lookup"><span data-stu-id="f6db0-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="f6db0-109">`DisplayIdentityInformation`Metoda pokazana w poniższym przykładowym kodzie to funkcja narzędziowa, która wyświetla tożsamość obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f6db0-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
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
  
 <span data-ttu-id="f6db0-110">`Subtract`Metoda w usłudze personifikuje wywołującego za pomocą bezwzględnych wywołań, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f6db0-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="f6db0-111">Należy zauważyć, że w tym przypadku obiekt wywołujący nie jest personifikowany dla całego wywołania, ale jest personifikowany tylko dla części wywołania.</span><span class="sxs-lookup"><span data-stu-id="f6db0-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="f6db0-112">Ogólnie rzecz biorąc, personifikowanie dla najmniejszego zakresu jest preferowane personifikacja dla całej operacji.</span><span class="sxs-lookup"><span data-stu-id="f6db0-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="f6db0-113">Inne metody nie personifikują wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f6db0-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="f6db0-114">Kod klienta został zmodyfikowany w celu ustawienia poziomu personifikacji na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> .</span><span class="sxs-lookup"><span data-stu-id="f6db0-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="f6db0-115">Klient określa poziom personifikacji, który ma być używany przez usługę, przy użyciu <xref:System.Security.Principal.TokenImpersonationLevel> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f6db0-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="f6db0-116">Wyliczenie obsługuje następujące wartości: <xref:System.Security.Principal.TokenImpersonationLevel.None> , <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> , <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> i <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> .</span><span class="sxs-lookup"><span data-stu-id="f6db0-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="f6db0-117">Aby przeprowadzić sprawdzanie dostępu podczas uzyskiwania dostępu do zasobu systemowego na komputerze lokalnym, który jest chroniony przy użyciu list ACL systemu Windows, poziom personifikacji musi być ustawiony na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> , jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f6db0-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="f6db0-118">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="f6db0-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f6db0-119">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="f6db0-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6db0-120">Usługa musi być uruchomiona na koncie administracyjnym lub konto, w którym jest uruchamiane, musi mieć przyznane prawa do rejestracji `http://localhost:8000/ServiceModelSamples` identyfikatora URI za pomocą warstwy http.</span><span class="sxs-lookup"><span data-stu-id="f6db0-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="f6db0-121">Takie prawa można udzielić przez skonfigurowanie [rezerwacji przestrzeni nazw](/windows/win32/http/namespace-reservations-registrations-and-routing) za pomocą [narzędzia HttpCfg. exe](/windows/win32/http/httpcfg-exe).</span><span class="sxs-lookup"><span data-stu-id="f6db0-121">Such rights can be granted by setting up a [Namespace Reservation](/windows/win32/http/namespace-reservations-registrations-and-routing) using the [Httpcfg.exe tool](/windows/win32/http/httpcfg-exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6db0-122">Na komputerach z systemem Windows Server 2003 Personifikacja jest obsługiwana tylko wtedy, gdy aplikacja host. exe ma uprawnienie personifikacji.</span><span class="sxs-lookup"><span data-stu-id="f6db0-122">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="f6db0-123">(Domyślnie tylko Administratorzy mają to uprawnienie). Aby dodać to uprawnienie do konta, na którym działa usługa, przejdź do pozycji **Narzędzia administracyjne**, Otwórz **pozycję Zasady zabezpieczeń lokalnych**, Otwórz **Zasady lokalne**, kliknij pozycję **Przypisywanie praw użytkownika**, a następnie wybierz opcję **Personifikuj klienta po uwierzytelnieniu** , a następnie kliknij dwukrotnie pozycję **Właściwości** , aby dodać użytkownika lub grupę.</span><span class="sxs-lookup"><span data-stu-id="f6db0-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f6db0-124">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="f6db0-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f6db0-125">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6db0-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f6db0-126">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6db0-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f6db0-127">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6db0-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="f6db0-128">Aby zademonstrować, że usługa personifikuje wywołującego, uruchom klienta przy użyciu innego konta niż to, w którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="f6db0-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="f6db0-129">Aby to zrobić, w wierszu polecenia wpisz:</span><span class="sxs-lookup"><span data-stu-id="f6db0-129">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="f6db0-130">Zostanie wyświetlony monit o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="f6db0-130">You are then prompted for a password.</span></span> <span data-ttu-id="f6db0-131">Wprowadź hasło do konta, które zostało wcześniej określone.</span><span class="sxs-lookup"><span data-stu-id="f6db0-131">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="f6db0-132">Po uruchomieniu klienta należy zanotować jego tożsamość przed i po jej uruchomieniu z innymi poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="f6db0-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
