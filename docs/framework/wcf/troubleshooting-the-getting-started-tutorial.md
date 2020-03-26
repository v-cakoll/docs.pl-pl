---
title: Rozwiązywanie problemów z samouczkami Wprowadzenie do programu Windows Communication Foundation
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 73aa0f5784784cb788a7532f8e22cbe925429c41
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249620"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Rozwiązywanie problemów z samouczkami Wprowadzenie do programu Windows Communication Foundation

Ten artykuł zawiera rozwiązania najczęstszych problemów i błędów, które mogą napotkać, gdy postępuj zgodnie z instrukcjami w [samouczku: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).
  
## <a name="common-problems"></a>Typowe problemy

**Nie mogę znaleźć plików projektu na dysku twardym.**

 Program Visual Studio zapisuje pliki projektu w *języku C:\Użytkownicy\\&lt;nazwa&gt;użytkownika \source\repos*.  

**Nie mogę znaleźć pliku *App.config* wygenerowanego przez *Svcutil.exe*.**

 W programie Visual Studio w oknie **Dodaj istniejący element** domyślnie są wyświetlane tylko pliki z następującymi rozszerzeniami:

- *.cs*
- *.resx*
- *.settings*
- *Xsd*
- *.wsdl*

Aby wyświetlić wszystkie typy plików, wybierz **pozycję Wszystkie pliki\*( .\*)** na liście rozwijanej w prawym dolnym rogu okna Dodaj **istniejący element.**  
  
## <a name="common-errors"></a>Typowe błędy

### <a name="compile-the-service-application"></a>Kompilowanie aplikacji usługi

**Nie znaleziono błędu BC30420 "Sub Main" w pliku "GettingStartedHost.Module1".**

Punkt wejścia jest niepoprawny dla aplikacji Visual Basic. Wprowadzać następujące zmiany:

   1. W oknie **Eksplorator rozwiązań** wybierz folder **GettingStartedHost,** a następnie z menu **skrótów** wybierz polecenie Właściwości.
    a. W oknie **GettingStartedHost** dla **obiektu Uruchamiani wybierz**z listy pozycję **Service.Program** (lub punkt wejścia dla danej aplikacji).
    b. Z menu głównego wybierz **polecenie Zapisz** > **wszystkie**pliki .

### <a name="run-the-service-application"></a>Uruchamianie aplikacji serwisowej

**HTTP nie może zarejestrować\/adresu URL "http: /+:8000/GettingStarted/CalculatorService". Proces nie ma praw dostępu do tej przestrzeni nazw.**

 Aby uzyskać odpowiedni dostęp, uruchom proces hostowania usługi Windows Communication Foundation (WCF) z uprawnieniami administracyjnymi:

- W programie Visual Studio: Wybierz program Visual Studio w menu **Start,** a następnie wybierz **polecenie Więcej** > **uruchom jako administrator** z menu skrótów.
- W przypadku okna konsoli: wybierz **polecenie Wiersz polecenia** w menu **Start,** a następnie z menu skrótów wybierz polecenie **Więcej** > **uruchom jako administrator.**
- W przypadku Eksploratora Windows: wybierz plik wykonywalny, a następnie wybierz z menu skrótów pozycję **Uruchom jako administrator.**

### <a name="compile-the-client-application"></a>Kompilowanie aplikacji klienckiej

**"CalculatorClient", nie zawiera definicji\<dla ' nazwa metody>" i\<nie metoda rozszerzenia "nazwa metody>" akceptując pierwszy argument typu "CalculatorClient" można znaleźć (czy brakuje using dyrektywy lub odwołania do zestawu?)**  

Tylko te metody, które `ServiceOperationAttribute` można oznaczyć za pomocą atrybutu są publicznie widoczne. Jeśli pominiesz `ServiceOperationAttribute` atrybut z metody `ICalculator` w interfejsie, ten komunikat o błędzie podczas kompilacji.  

**Nie można odnaleźć nazwy typu lub obszaru nazw "CalculatorClient" (czy brakuje dyrektywy lub odwołania do zestawu?)**

 Ten błąd jest wyświetlany, jeśli nie dodasz pliku *generatedProxy.cs* (lub *generatedProxy.vb)* do projektu klienta podczas generowania ich za pomocą narzędzia *Svcutil.exe.*  

### <a name="run-the-client-application"></a>Uruchamianie aplikacji klienckiej

**Nieobsługiwał wyjątek: System.ServiceModel.EndpointNotFoundException: Nie\/można połączyć się z 'http: /localhost:8000/GettingStarted/CalculatorService'. Kod błędu TCP 10061: Nie można nawiązać połączenia, ponieważ komputer docelowy aktywnie go odmówił.**

Ten błąd występuje, jeśli uruchomisz aplikację kliencką bez pierwszego uruchomienia usługi. Najpierw uruchom aplikację hosta, aby uruchomić usługę, a następnie uruchom aplikację kliencką.

### <a name="use-the-svcutilexe-tool"></a>Korzystanie z narzędzia Svcutil.exe

**"Svcutil" nie jest rozpoznawany jako polecenie wewnętrzne lub zewnętrzne, działający program lub plik wsadowy.**

 *Program Svcutil.exe* musi znajdować się w ścieżce systemowej. Najprostszym rozwiązaniem jest użycie wiersza polecenia programu Visual Studio. Z menu **Start** wybierz>katalogu **wersji programu Visual Studio, \<** a następnie wybierz pozycję Wiersz polecenia **dewelopera dla>wersji programu \<VS **. Ten wiersz polecenia ustawia ścieżkę systemową do odpowiednich lokalizacji dla wszystkich narzędzi dostarczanych w ramach programu Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Uruchamianie aplikacji usługowych i klienckich

**System.ServiceModel.Security.SecurityNegotiationException: NEGOCJACJA zabezpieczeń SOAP\/z "http: /localhost:8000/GettingStarted/CalculatorService" dla obiektu docelowego "http:\//localhost:8000/GettingStarted/CalculatorService" nie powiodło się**  

Ten błąd występuje na komputerze przyłączanym do domeny, który nie ma łączności sieciowej. Podłącz komputer do sieci lub wyłącz zabezpieczenia zarówno dla usługi, jak i klienta.

Aby wyłączyć zabezpieczenia:

- Dla usługi, zastąp `WSHttpBinding` kod, który tworzy z następującym kodem:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Dla klienta w pliku konfiguracyjnym zaktualizuj ** \<** element>zabezpieczeń w ramach elementu ** \<>powiązania** w następujący sposób:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator">
      <security mode="None" />
    </binding
    ```  

## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji WCF](getting-started-tutorial.md)  
 [Szybki start rozwiązywania problemów z WCF](wcf-troubleshooting-quickstart.md)  
 [Rozwiązywanie problemów z konfiguracją](troubleshooting-setup-issues.md)
