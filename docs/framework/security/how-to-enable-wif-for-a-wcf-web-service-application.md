---
title: 'Instrukcje: Włączanie programu WIF dla aplikacji usługi internetowej WCF'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: b9fa1f815a962adc0b3c91177021788734b92bb6
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041457"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>Instrukcje: Włączanie programu WIF dla aplikacji usługi internetowej WCF
## <a name="applies-to"></a>Dotyczy:

- Microsoft® Windows® Identity Foundation (WIF)

- Microsoft® Windows® Communication Foundation (WCF)

## <a name="summary"></a>Podsumowanie

Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku służące do włączania środowiska WIF w usłudze internetowej WCF. Znajdują się tu również instrukcje testowania aplikacji pozwalające sprawdzić, czy usługa internetowa poprawnie przedstawia oświadczenia w trakcie działania aplikacji. Instruktaż nie zawiera szczegółowych instrukcji tworzenia usługi tokenów zabezpieczających (STS). Zamiast tego wykorzystuje deweloperską usługę STS wbudowaną w narzędziu Tożsamość i dostęp. Deweloperska usługa STS nie wykonuje faktycznego uwierzytelniania i jest przeznaczona tylko do celów testowych. Narzędzie Tożsamość i dostęp jest koniecznie do ukończenia całego instruktażu. Można go pobrać z następującej lokalizacji: [Narzędzie tożsamości i dostępu](https://go.microsoft.com/fwlink/?LinkID=245849)

## <a name="contents"></a>Spis treści

- Cele

- Omówienie

- Zestawienie czynności

- Krok 1 — Utworzenie prostej usługi WCF

- Krok 2 — Utworzenie aplikacji klienckiej dla usługi WCF

- Krok 3 — Przetestowanie rozwiązania

## <a name="objectives"></a>Cele

- Utworzenie usługi WCF wymagającej wystawionych tokenów

- Utworzenie klienta WCF, który wymaga tokenu od usługi STS, po czym przekazuje go do usługi WCF

## <a name="overview"></a>Omówienie

Ten instruktaż ma pokazać, jak programista może używać funkcji federacyjnego uwierzytelniania podczas tworzenia usług WCF. Oto kilka najważniejszych zalet stosowania mechanizmu federacji w usługach WCF:

1. Wyprowadzenie logiki uwierzytelniania poza kod usługi WCF

2. Wykorzystanie istniejących rozwiązań do zarządzania tożsamościami

3. Współpraca z innymi systemami zarządzania tożsamością

4. Elastyczność i odporność na przyszłe zmiany

Środowisko WIF wraz z towarzyszącym narzędziem Tożsamość i dostęp ułatwia tworzenie oraz testowanie usług WCF dzięki wykorzystaniu funkcjonalności federacyjnego uwierzytelniania. Pokazano to poniżej.

## <a name="summary-of-steps"></a>Zestawienie czynności

- Krok 1 — Utworzenie prostej usługi WCF

- Krok 2 — Utworzenie aplikacji klienckiej dla usługi WCF

- Krok 3 — Przetestowanie rozwiązania

## <a name="step-1--create-a-simple-wcf-service"></a>Krok 1 — Utworzenie prostej usługi WCF

W tym kroku utworzysz nową usługę WCF, która wykorzystuje deweloperską usługę STS dołączoną do narzędzia Tożsamość i dostęp.

#### <a name="to-create-a-simple-wcf-service"></a>Aby utworzyć prostą usługę WCF

1. Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.

2. W programie Visual Studio kliknij pozycję **plik**, kliknij pozycję **Nowy**, a następnie kliknij pozycję **projekt**.

3. W oknie **Nowy projekt** kliknij pozycję **aplikacja usługi WCF**.

4. W polu **Nazwa**wprowadź `TestService` i naciśnij przycisk **OK**.

5. Kliknij prawym przyciskiem myszy projekt **TestService** w obszarze **Eksplorator rozwiązań**, a następnie wybierz pozycję **tożsamość i dostęp**.

6. Zostanie wyświetlone okno **tożsamość i dostęp** . W obszarze **dostawcy**wybierz pozycję **Testuj aplikację przy użyciu lokalnej usługi STS**, a następnie kliknij przycisk **Zastosuj**. Narzędzie tożsamości i dostępu konfiguruje usługę do korzystania z usługi WIF oraz do uwierzytelniania za pomocą programu Local Development STS (**LocalSTS**) przez dodanie elementów konfiguracji do pliku *Web. config* .

7. W pliku *Service1.svc.cs* Dodaj `using` dyrektywę dla przestrzeni nazw **System. Security. Claims** i Zastąp istniejący kod następującym kodem, a następnie Zapisz plik:

    ```csharp
    public class Service1 : IService1
    {
        public string ComputeResponse(string input)
        {
            // Get the caller's identity from ClaimsPrincipal.Current
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;

            // Start generating the output
            StringBuilder builder = new StringBuilder();
            builder.AppendLine("Computed by ClaimsAwareWebService");
            builder.AppendLine("Input received from client:" + input);

            if (claimsPrincipal != null)
            {
                // Display the claims from the caller. Do not use this code in a production application.
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;
                builder.AppendLine("Client Name:" + identity.Name);
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);
                builder.AppendLine("The service received the following issued claims of the client:");

                // Iterate over the caller’s claims and append to the output
                foreach (Claim claim in claimsPrincipal.Claims)
                {
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);
                }
            }

            return builder.ToString();
        }
    }
    ```

    Metoda Wyświetla właściwości różnych oświadczeń wystawionych przez **LocalSTS.** `ComputeResponse`

8. W pliku *IService1.cs* Zastąp istniejący kod następującym kodem, a następnie Zapisz plik:

    ```csharp
    [ServiceContract]
    public interface IService1
    {
        [OperationContract]
        string ComputeResponse(string input);
    }
    ```

9. Skompiluj projekt.

10. Naciśnij **klawisze CTRL + F5** , aby uruchomić usługę bez uruchamiania debugera. Dla usługi powinna zostać otwarta strona sieci Web. możesz sprawdzić, czy **LocalSTS** działa, przeglądając obszar powiadomień (zasobnik systemowy).

    > [!IMPORTANT]
    > Podczas dodawania odwołania do usługi do aplikacji klienckiej w następnym kroku musi działać zarówno **TestService** , jak i **LocalSTS** .

## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>Krok 2 — Utworzenie aplikacji klienckiej dla usługi WCF

W tym kroku utworzysz aplikację konsoli, która za pomocą deweloperskiej usługi STS będzie się uwierzytelniać w usłudze WCF utworzonej w poprzednim kroku.

#### <a name="to-create-a-client-application"></a>Aby utworzyć aplikację kliencką

1. W programie Visual Studio kliknij prawym przyciskiem myszy rozwiązanie, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.

2. W oknie **Dodawanie nowego projektu** wybierz pozycję **Aplikacja konsolowa** z listy **Szablony C# wizualizacji** , `Client`a następnie naciśnij przycisk **OK**. Nowy projekt zostanie utworzony w folderze rozwiązania.

3. Kliknij prawym przyciskiem myszy pozycję **odwołania** w projekcie **klienta** , a następnie kliknij pozycję **Dodaj odwołanie do usługi**.

4. W oknie **Dodaj odwołanie do usługi** kliknij strzałkę listy rozwijanej na przycisku Odnajdź, a następnie kliknij pozycję **usługi w rozwiązaniu**. **Adres** zostanie automatycznie wypełniony usługą WCF utworzoną wcześniej, a **przestrzeń nazw** zostanie ustawiona na **ServiceReference1**. Kliknij przycisk **OK**.

    > [!IMPORTANT]
    > Podczas dodawania odwołania do usługi do klienta musi być uruchomiony zarówno **TestService** , jak i **LocalSTS** .

5. Program Visual Studio wygeneruje klasy serwera proxy dla usługi WCF i doda wszystkie niezbędne parametry odwołań. Spowoduje to również dodanie elementów do pliku *App. config* w celu skonfigurowania klienta programu w celu uzyskania tokenu z usługi STS w celu uwierzytelnienia w usłudze. Po zakończeniu tego procesu zostanie otwarty plik **program.cs** . Dodaj dyrektywę dla elementu **System. ServiceModel** i innego elementu **Client. ServiceReference1**, Zastąp metodę Main następującym kodem, a następnie Zapisz plik: `using`

    ```csharp
    static void Main(string[] args)
    {
        // Create the client for the service
        Service1Client client = new Service1Client();
        Console.WriteLine("-------------WCF Client Application--------------\n");

        while (!ShouldQuitApplication())
        {
            try
            {
                Console.WriteLine(client.ComputeResponse("Hello World"));
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
                Console.WriteLine(e.StackTrace);
                Exception ex = e.InnerException;
                while (ex != null)
                {
                    Console.WriteLine("===========================");
                    Console.WriteLine(ex.Message);
                    Console.WriteLine(ex.StackTrace);
                    ex = ex.InnerException;
                }
            }
            catch (TimeoutException)
            {
                Console.WriteLine("Timed out...");
            }
            catch (Exception e)
            {
                Console.WriteLine("An unexpected exception occurred.");
                Console.WriteLine(e.StackTrace);
            }
        }

        client.Close();

        if (client != null)
        {
            client.Abort();
        }
    }

    static bool ShouldQuitApplication()
    {
        Console.WriteLine("---------------------------------------------------------------------");
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");
        Console.WriteLine("----------------------------------------------------------------------");

        ConsoleKeyInfo keyInfo = Console.ReadKey();
        if (keyInfo.Key == ConsoleKey.Enter)
            return false;
        return true;
    }
    ```

6. Otwórz plik *App. config* i Dodaj następujący kod XML jako pierwszy element podrzędny w obszarze `<system.serviceModel>` elementu, a następnie Zapisz plik:

    ```xml
    <behaviors>
       <endpointBehaviors>
         <behavior>
           <clientCredentials>
             <serviceCertificate>
               <authentication certificateValidationMode="None"/>
             </serviceCertificate>
           </clientCredentials>
         </behavior>
       </endpointBehaviors>
     </behaviors>
    ```

    Spowoduje to wyłączenie mechanizmu sprawdzania poprawności certyfikatów.

7. Kliknij prawym przyciskiem myszy rozwiązanie **TestService** , a następnie kliknij pozycję **Ustaw projekty startowe**. Zostanie otwarta strona właściwości **projekt startowy** . Na stronie właściwości **projekt startowy** wybierz opcję **wiele projektów startowych** , a następnie kliknij w polu **Akcja** dla każdego projektu i wybierz pozycję **Rozpocznij** z menu rozwijanego. Kliknij przycisk **OK** , aby zapisać ustawienia.

8. Skompiluj rozwiązanie.

## <a name="step-3--test-your-solution"></a>Krok 3 — Przetestowanie rozwiązania

W tym kroku przetestujesz aplikację WCF korzystającą ze środowiska WIF i sprawdzisz, czy są prezentowane oświadczenia.

#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>Aby przetestować aplikację WCF używającą środowiska WIF pod kątem oświadczeń

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację. Powinno zostać wyświetlone okno konsoli programu i następujący tekst: **Naciśnij klawisz ENTER, aby wywołać usługę, a następnie inny klawisz, aby zamknąć aplikację:**

2. Naciśnij klawisz **Enter**, a w konsoli powinny pojawić się następujące informacje dotyczące oświadczeń:

    ```
    Computed by Service1
    Input received from client: Hello World
    Client Name: Terry
    IsAuthenticated: True
    The service received the following issued claims of the client:
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com
    ```

    > [!IMPORTANT]
    > Przed naciśnięciem klawisza **Enter**musi być uruchomiona zarówno **TestService** , jak i **LocalSTS** . Dla usługi powinna zostać otwarta strona sieci Web. możesz sprawdzić, czy **LocalSTS** działa, przeglądając obszar powiadomień (zasobnik systemowy).

3. Jeśli te oświadczenia widać w konsoli, dokonano pomyślnego uwierzytelnienia w usłudze STS pozwalającego na wyświetlanie oświadczeń z usługi WCF.
