---
title: Personifikowanie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 40bde7d9bd2735dfd6f1a18f9359533db0e11724
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989823"
---
# <a name="impersonating-the-client"></a>Personifikowanie klienta
Przykład personifikacji demonstruje sposób personifikacji aplikacji wywołującej w usłudze, aby usługa mogła uzyskać dostęp do zasobów systemowych w imieniu obiektu wywołującego.  
  
 Ten przykład jest oparty [na przykładu samoobsługowego](../../../../docs/framework/wcf/samples/self-host.md) . Pliki konfiguracji usługi i klienta są takie same jak w przypadku przykładu samoobsługowego [hosta](../../../../docs/framework/wcf/samples/self-host.md) .  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kod usługi został zmodyfikowany w taki sposób, że `Add` Metoda w usłudze personifikuje obiekt wywołujący <xref:System.ServiceModel.OperationBehaviorAttribute> przy użyciu metody, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 `DisplayIdentityInformation` Metoda pokazana w poniższym przykładowym kodzie to funkcja narzędziowa, która wyświetla tożsamość obiektu wywołującego.  
  
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
  
 `Subtract` Metoda w usłudze personifikuje wywołującego za pomocą bezwzględnych wywołań, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Kod klienta został zmodyfikowany w celu ustawienia poziomu personifikacji na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>. Klient określa poziom personifikacji, który ma być używany przez usługę, przy użyciu <xref:System.Security.Principal.TokenImpersonationLevel> wyliczenia. Wyliczenie obsługuje następujące wartości: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> i. <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> Aby przeprowadzić sprawdzanie dostępu podczas uzyskiwania dostępu do zasobu systemowego na komputerze lokalnym, który jest chroniony przy użyciu list ACL systemu Windows, poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>musi być ustawiony na, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
> [!NOTE]
> Usługa musi być uruchomiona na koncie administracyjnym lub konto, w którym jest uruchamiane, musi mieć przyznane prawa do rejestracji `http://localhost:8000/ServiceModelSamples` identyfikatora URI za pomocą warstwy http. Takie prawa można udzielić przez skonfigurowanie [rezerwacji przestrzeni nazw](https://go.microsoft.com/fwlink/?LinkId=95012) za pomocą [narzędzia HttpCfg. exe](https://go.microsoft.com/fwlink/?LinkId=95010).  
  
> [!NOTE]
> Na komputerach z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]systemem Personifikacja jest obsługiwana tylko wtedy, gdy aplikacja host. exe ma uprawnienie personifikacji. (Domyślnie tylko Administratorzy mają to uprawnienie). Aby dodać to uprawnienie do konta, na którym działa usługa, przejdź do pozycji **Narzędzia administracyjne**, Otwórz pozycję **zasady zabezpieczeń lokalnych**, Otwórz **Zasady lokalne**, kliknij pozycję **Przypisywanie praw użytkownika**, a następnie wybierz opcję **Personifikuj klienta po Uwierzytelnianie** i kliknij dwukrotnie przycisk **Właściwości** , aby dodać użytkownika lub grupę.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Aby zademonstrować, że usługa personifikuje wywołującego, uruchom klienta przy użyciu innego konta niż to, w którym działa usługa. Aby to zrobić, w wierszu polecenia wpisz:  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Zostanie wyświetlony monit o podanie hasła. Wprowadź hasło do konta, które zostało wcześniej określone.  
  
5. Po uruchomieniu klienta należy zanotować jego tożsamość przed i po jej uruchomieniu z innymi poświadczeniami.  
