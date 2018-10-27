---
title: Personifikowanie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 9e1c38abd1c9cacfd4db953d9fb875437b2f1093
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047673"
---
# <a name="impersonating-the-client"></a>Personifikowanie klienta
Personifikacja — przykład pokazuje, jak dokonać personifikacji aplikacji obiektu wywołującego na usługę tak, aby usługa może uzyskiwać dostęp do zasobów systemu imieniu obiekt wywołujący.  
  
 Ten przykład jest oparty na [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki. Pliki konfiguracji usługi i klienta są takie same jak w przypadku [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Kod usługi został zmodyfikowany tak, aby `Add` metody w usłudze personifikuje wywołującemu, korzystając z <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 W rezultacie, iż wątek wykonujący w kontekście zabezpieczeń zostanie przełączone na personifikują wywołującego przed wejściem `Add` metody i przywrócone na Kończenie wykonywania metody.  
  
 `DisplayIdentityInformation` Pokazaną w poniższym przykładowym kodzie metodą jest funkcja narzędziowa, który wyświetla tożsamości elementu wywołującego.  
  
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
  
 `Subtract` Metody w usłudze personifikuje wywołującemu, korzystając z wywołania imperatywnego, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Należy pamiętać, że w tym przypadku obiekt wywołujący nie jest Personifikowany dla całego wywołania, ale tylko jest Personifikowany przez pewną część wywołania. Ogólnie rzecz biorąc personifikacji dla zakresu najmniejszy preferowane jest personifikacji dla całej operacji.  
  
 Inne metody nie spersonifikować obiektu wywołującego.  
  
 Kod klienta została zmodyfikowana, aby ustawić poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>. Klient określa poziom personifikacji, który będzie używany przez usługę, za pomocą <xref:System.Security.Principal.TokenImpersonationLevel> wyliczenia. Wyliczanie obsługuje następujące wartości: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> i <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Aby przeprowadzić kontrolę dostępu podczas uzyskiwania dostępu do zasobu systemu na komputerze lokalnym, który jest chroniony za pomocą listy kontroli dostępu Windows, musi być równa poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Po uruchomieniu przykładu, operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.  
  
> [!NOTE]
>  Usługę należy uruchomić przy użyciu konta administracyjnego lub konto jest uruchamiana przy użyciu musi otrzymać uprawnienia do rejestrowania `http://localhost:8000/ServiceModelSamples` identyfikator URI przy użyciu warstwy protokołu HTTP. Te prawa mogą być przyznawane przez skonfigurowanie [rezerwacji Namespace](https://go.microsoft.com/fwlink/?LinkId=95012) przy użyciu [narzędzia Httpcfg.exe](https://go.microsoft.com/fwlink/?LinkId=95010).  
  
> [!NOTE]
>  Na komputerach z systemem [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], personifikacja jest obsługiwana tylko wtedy, gdy aplikacja Host.exe uprawnień personifikacji. (Domyślnie tylko administratorzy mają to uprawnienie). Aby dodać to uprawnienie jest uruchomiona jako konto, przejdź do **narzędzia administracyjne**, otwórz **zasady zabezpieczeń lokalnych**, otwórz **zasady lokalne**, kliknij przycisk **Przypisywanie praw użytkownika**i wybierz **Personifikowanie klienta po uwierzytelnieniu** i kliknij dwukrotnie **właściwości** można dodać użytkownika lub grupy.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Aby zademonstrować, że usługa personifikuje obiekt wywołujący, uruchom klienta przy użyciu innego konta niż ten, który jest uruchamiany przez usługę. Aby to zrobić, w wierszu polecenia wpisz polecenie:  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Następnie zostanie wyświetlony monit o podanie hasła. Wprowadź hasło dla konta, które wcześniej określono.  
  
5.  Po uruchomieniu klienta, Zapamiętaj tożsamość przed i po uruchomieniu przy użyciu różnych poświadczeń.  
  
## <a name="see-also"></a>Zobacz też
