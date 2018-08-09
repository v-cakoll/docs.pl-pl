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
ms.locfileid: "33505013"
---
# <a name="impersonating-the-client"></a>Personifikowanie klienta
Personifikacja — przykład pokazuje, jak dokonać personifikacji aplikacji obiektu wywołującego w usłudze, aby usługa może uzyskiwać dostęp do zasobów systemu imieniu wywołującego.  
  
 Ten przykład jest oparty na [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki. Pliki konfiguracji usługi i klienta są takie same, jak te [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md) próbki.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Zmodyfikowano kodu usługi tak, aby `Add` metody w usłudze personifikuje wywołującemu, korzystając z <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym kodzie próbki.  
  
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
  
 W związku z tym przełączania kontekstu zabezpieczeń wykonywania wątku do personifikują wywołującego przed wprowadzeniem `Add` — metoda i przywrócone na kończenie metody.  
  
 `DisplayIdentityInformation` Metod przedstawionych w następujący przykładowy kod to funkcja narzędzia, która wyświetla tożsamość obiektu wywołującego.  
  
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
  
 `Subtract` Wywołującego przy użyciu wywołania konieczne, jak pokazano w poniższym kodzie próbki personifikuje metody dla usługi.  
  
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
  
 Należy pamiętać, że w takim przypadku obiekt wywołujący nie jest traktowane całego wywołanie, ale Personifikowany jest tylko część wywołania. Ogólnie rzecz biorąc personifikacja zakresie najmniejszą preferowane jest personifikacji dla całej operacji.  
  
 Inne metody nie personifikują wywołującego.  
  
 Kod klienta została zmodyfikowana, aby ustawić poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>. Klient określa poziom personifikacji używanego przez usługę, używając <xref:System.Security.Principal.TokenImpersonationLevel> wyliczenia. Wyliczenie obsługuje następujące wartości: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> i <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Aby przeprowadzić sprawdzanie dostępu podczas uzyskiwania dostępu do zasobu systemu na komputerze lokalnym, który jest chroniony za pomocą listy ACL systemu Windows, poziom personifikacji musi mieć ustawioną <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, jak pokazano w poniższym kodzie próbki.  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.  
  
> [!NOTE]
>  Usługę należy uruchomić przy użyciu konta administratora lub konta, zostanie uruchomiony w musi otrzymać uprawnienia do rejestrowania http://localhost:8000/ServiceModelSamples identyfikatora URI z warstwą HTTP. Te prawa można udzielić, konfigurując [rezerwacji Namespace](http://go.microsoft.com/fwlink/?LinkId=95012) przy użyciu [narzędzia Httpcfg.exe](http://go.microsoft.com/fwlink/?LinkId=95010).  
  
> [!NOTE]
>  Na komputerach z systemem [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], personifikacja jest obsługiwana tylko wtedy, gdy aplikacja Host.exe ma uprawnienie do personifikacji. (Domyślnie tylko Administratorzy ma tych uprawnień). Aby dodać to uprawnienie do usługa jest uruchomiona jako konto, przejdź do **narzędzia administracyjne**, otwórz **zasady zabezpieczeń lokalnych**, otwórz **zasady lokalne**, kliknij przycisk **Przypisywanie praw użytkownika**i wybierz **Personifikuj klienta po uwierzytelnieniu** i kliknij dwukrotnie **właściwości** można dodać użytkownika lub grupę.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Aby zademonstrować, że usługa personifikuje wywołującego, uruchom klienta przy użyciu innego konta niż ten, który jest uruchomiona w obszarze. Aby to zrobić, w wierszu polecenia wpisz:  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Następnie zostanie wyświetlony monit o podanie hasła. Wprowadź hasło dla konta, które wcześniej określona.  
  
5.  Po uruchomieniu klienta, należy pamiętać tożsamości przed i po uruchomieniu go z innymi poświadczeniami.  
  
## <a name="see-also"></a>Zobacz też
