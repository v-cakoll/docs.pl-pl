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
# <a name="impersonating-the-client"></a>Personifikowanie klienta
Przykład personifikacji demonstruje sposób personifikacji aplikacji wywołującej w usłudze, aby usługa mogła uzyskać dostęp do zasobów systemowych w imieniu obiektu wywołującego.  
  
 Ten przykład jest oparty [na przykładu samoobsługowego](self-host.md) . Pliki konfiguracji usługi i klienta są takie same jak w przypadku przykładu samoobsługowego [hosta](self-host.md) .  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kod usługi został zmodyfikowany w taki sposób, że `Add` Metoda w usłudze personifikuje obiekt wywołujący przy użyciu metody <xref:System.ServiceModel.OperationBehaviorAttribute> , jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 W związku z tym kontekst zabezpieczeń wykonywanego wątku jest przełączany w celu personifikacji obiektu wywołującego przed wprowadzeniem `Add` metody i przywróceniem wyjścia z metody.  
  
 `DisplayIdentityInformation`Metoda pokazana w poniższym przykładowym kodzie to funkcja narzędziowa, która wyświetla tożsamość obiektu wywołującego.  
  
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
  
 `Subtract`Metoda w usłudze personifikuje wywołującego za pomocą bezwzględnych wywołań, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Należy zauważyć, że w tym przypadku obiekt wywołujący nie jest personifikowany dla całego wywołania, ale jest personifikowany tylko dla części wywołania. Ogólnie rzecz biorąc, personifikowanie dla najmniejszego zakresu jest preferowane personifikacja dla całej operacji.  
  
 Inne metody nie personifikują wywołującego.  
  
 Kod klienta został zmodyfikowany w celu ustawienia poziomu personifikacji na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> . Klient określa poziom personifikacji, który ma być używany przez usługę, przy użyciu <xref:System.Security.Principal.TokenImpersonationLevel> wyliczenia. Wyliczenie obsługuje następujące wartości: <xref:System.Security.Principal.TokenImpersonationLevel.None> , <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> , <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> i <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> . Aby przeprowadzić sprawdzanie dostępu podczas uzyskiwania dostępu do zasobu systemowego na komputerze lokalnym, który jest chroniony przy użyciu list ACL systemu Windows, poziom personifikacji musi być ustawiony na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> , jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
> [!NOTE]
> Usługa musi być uruchomiona na koncie administracyjnym lub konto, w którym jest uruchamiane, musi mieć przyznane prawa do rejestracji `http://localhost:8000/ServiceModelSamples` identyfikatora URI za pomocą warstwy http. Takie prawa można udzielić przez skonfigurowanie [rezerwacji przestrzeni nazw](/windows/win32/http/namespace-reservations-registrations-and-routing) za pomocą [narzędzia HttpCfg. exe](/windows/win32/http/httpcfg-exe).  
  
> [!NOTE]
> Na komputerach z systemem Windows Server 2003 Personifikacja jest obsługiwana tylko wtedy, gdy aplikacja host. exe ma uprawnienie personifikacji. (Domyślnie tylko Administratorzy mają to uprawnienie). Aby dodać to uprawnienie do konta, na którym działa usługa, przejdź do pozycji **Narzędzia administracyjne**, Otwórz **pozycję Zasady zabezpieczeń lokalnych**, Otwórz **Zasady lokalne**, kliknij pozycję **Przypisywanie praw użytkownika**, a następnie wybierz opcję **Personifikuj klienta po uwierzytelnieniu** , a następnie kliknij dwukrotnie pozycję **Właściwości** , aby dodać użytkownika lub grupę.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
4. Aby zademonstrować, że usługa personifikuje wywołującego, uruchom klienta przy użyciu innego konta niż to, w którym działa usługa. Aby to zrobić, w wierszu polecenia wpisz:  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Zostanie wyświetlony monit o podanie hasła. Wprowadź hasło do konta, które zostało wcześniej określone.  
  
5. Po uruchomieniu klienta należy zanotować jego tożsamość przed i po jej uruchomieniu z innymi poświadczeniami.  
