---
title: Personifikowanie klienta
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 10a8d243b3f053879f183864e955d9260c07865b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183613"
---
# <a name="impersonating-the-client"></a>Personifikowanie klienta
Przykład personifikacji pokazuje, jak personifikować aplikację wywołującą w usłudze, dzięki czemu usługa może uzyskać dostęp do zasobów systemowych w imieniu obiektu wywołującego.  
  
 Ten przykład jest oparty na przykładzie [self-host.](../../../../docs/framework/wcf/samples/self-host.md) Pliki konfiguracji usługi i klienta są takie same jak w przykładzie [hosta samodzielnego.](../../../../docs/framework/wcf/samples/self-host.md)  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kod usługi został zmodyfikowany w `Add` taki sposób, że metoda w <xref:System.ServiceModel.OperationBehaviorAttribute> usłudze personifikuje wywołującego przy użyciu, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 W rezultacie kontekst zabezpieczeń wątku wykonywania jest przełączany do personifikacji `Add` wywołującego przed wprowadzeniem metody i przywrócona po zamknięciu metody.  
  
 Metoda `DisplayIdentityInformation` pokazana w poniższym przykładowym kodzie jest funkcją narzędzia, która wyświetla tożsamość wywołującego.  
  
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
  
 Metoda `Subtract` w usłudze personifikuje wywołującego przy użyciu wywołań imperatywów, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Należy zauważyć, że w tym przypadku obiekt wywołujący nie jest personifikowany dla całego wywołania, ale jest personifikowany tylko dla części wywołania. Ogólnie rzecz biorąc personifikacji dla najmniejszego zakresu jest lepsze niż personifikacji dla całej operacji.  
  
 Inne metody nie personifikują wywołującego.  
  
 Kod klienta został zmodyfikowany, aby ustawić <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>poziom personifikacji na . Klient określa poziom personifikacji, który ma być <xref:System.Security.Principal.TokenImpersonationLevel> używany przez usługę, przy użyciu wyliczenia. Wyliczenie obsługuje <xref:System.Security.Principal.TokenImpersonationLevel.None>następujące wartości: <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, i . Aby przeprowadzić sprawdzanie dostępu podczas uzyskiwania dostępu do zasobu systemowego na komputerze lokalnym, który <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>jest chroniony przy użyciu list ACL systemu Windows, poziom personifikacji musi być ustawiony na , jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
> [!NOTE]
> Usługa musi działać na podstawie konta administracyjnego lub konto, na którym `http://localhost:8000/ServiceModelSamples` działa, musi mieć przyznane prawa do rejestrowania identyfikatora URI w warstwie HTTP. Takie prawa można przyznać, konfigurując [rezerwację obszaru nazw](/windows/win32/http/namespace-reservations-registrations-and-routing) za pomocą [narzędzia Httpcfg.exe](/windows/win32/http/httpcfg-exe).  
  
> [!NOTE]
> Na komputerach z systemem Windows Server 2003 personifikacja jest obsługiwana tylko wtedy, gdy aplikacja Host.exe ma uprawnienie Personifikacja. (Domyślnie tylko administratorzy mają to uprawnienie). Aby dodać to uprawnienie do konta, na które działa usługa, przejdź do **pozycji Narzędzia administracyjne**, otwórz **pozycję Lokalne zasady zabezpieczeń**, otwórz pozycję Zasady **lokalne**, kliknij pozycję **Przypisanie praw użytkownika**i wybierz pozycję **Personifikuj klienta po uwierzytelnieniu** i kliknij dwukrotnie **pozycję Właściwości,** aby dodać użytkownika lub grupę.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Aby wykazać, że usługa personifikuje wywołującego, uruchom klienta na innym koncie niż to, pod które jest uruchomiona usługa. Aby to zrobić, w wierszu polecenia wpisz:  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     Następnie zostanie wyświetlony monit o podanie hasła. Wprowadź hasło dla wcześniej określonego konta.  
  
5. Po uruchomieniu klienta, należy zwrócić uwagę na tożsamość przed i po uruchomieniu go z różnych poświadczeń.  
