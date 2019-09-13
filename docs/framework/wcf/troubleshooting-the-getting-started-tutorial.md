---
title: Rozwiązywanie problemów z samouczkami wprowadzenie do Windows Communication Foundation
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 10a2f8f718d802a7aab067b882f0d5cf3dc28dca
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928580"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Rozwiązywanie problemów z samouczkami wprowadzenie do Windows Communication Foundation

Ten artykuł zawiera rozwiązania najczęstszych problemów i błędów, które mogą wystąpić podczas wykonywania kroków opisanych w [samouczku: Rozpocznij pracę z aplikacjami](getting-started-tutorial.md)Windows Communication Foundation. 
  
## <a name="common-problems"></a>Typowe problemy

**Nie mogę znaleźć plików projektu na moim dysku twardym.**

 Program Visual Studio zapisuje pliki projektu *w\\nazwie&gt;użytkownika C:\Users&lt;\source\repos*.  

**Nie mogę znaleźć pliku *App. config* wygenerowanego przez *Svcutil. exe*.**

 W programie Visual Studio okno **Dodaj istniejący element** domyślnie wyświetla tylko pliki z następującymi rozszerzeniami: 

- *.cs* 
- *. resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

Aby wyświetlić wszystkie typy plików, zaznacz **wszystkie pliki (\*.\*)** na liście rozwijanej w prawym dolnym rogu okna **Dodaj istniejący element** .  
  
## <a name="common-errors"></a>Typowe błędy

### <a name="compile-the-service-application"></a>Kompiluj aplikację usługi 

**Nie znaleziono błędu BC30420 "Sub Main" w elemencie "GettingStartedHost. Module1".**

Punkt wejścia jest nieprawidłowy dla aplikacji Visual Basic. Wprowadź następujące zmiany:

   1. W oknie **Eksplorator rozwiązań** wybierz folder **GettingStartedHost** , a następnie wybierz polecenie **Właściwości** z menu skrótów.
    a. W oknie **GettingStartedHost** w polu **obiekt uruchomieniowy**wybierz pozycję **Service. program** (lub punkt wejścia dla danej aplikacji) z listy. 
    b. Z menu głównego wybierz pozycję **plik** > **Zapisz wszystko**.

### <a name="run-the-service-application"></a>Uruchom aplikację usługi 

**Protokół HTTP nie może zarejestrować adresu URL "\/http:/+: 8000/GettingStarted/CalculatorService". Proces nie ma uprawnień dostępu do tej przestrzeni nazw.** 

 Aby uzyskać odpowiedni dostęp, uruchom proces hostujący usługę Windows Communication Foundation (WCF) z uprawnieniami administracyjnymi:

- Dla programu Visual Studio: Wybierz program Visual Studio w menu **Start** , a następnie wybierz polecenie **więcej** > **Uruchom jako administrator** z menu skrótów.
- W przypadku okna konsoli: Wybierz pozycję **wiersz polecenia** w menu **Start** , a następnie w menu skrótów wybierz polecenie **więcej** > **Uruchom jako administrator** .
- W Eksploratorze Windows: Wybierz plik wykonywalny, a następnie wybierz opcję **Uruchom jako administrator** z menu skrótów.

### <a name="compile-the-client-application"></a>Kompilowanie aplikacji klienckiej

**Element "CalculatorClient" nie zawiera definicji metody "\<Name >" i nie można znaleźć metody rozszerzającej "\<Name >" akceptującej pierwszy argument typu "CalculatorClient" (brak dyrektywy using lub odwołanie do zestawu?)**  

Tylko te metody, które można oznaczyć przy `ServiceOperationAttribute` użyciu atrybutu, są ujawniane publicznie. Jeśli pominięto `ServiceOperationAttribute` atrybut z metody `ICalculator` w interfejsie, podczas kompilacji pojawi się ten komunikat o błędzie.  

**Nie można znaleźć nazwy typu lub przestrzeni nazw "CalculatorClient" (czy nie brakuje dyrektywy using lub odwołania do zestawu?)**

 Ten błąd występuje, jeśli plik *generatedProxy.cs* (lub *generatedProxy. vb*) nie zostanie dodany do projektu klienta, gdy zostanie wygenerowany przy użyciu narzędzia *Svcutil. exe* .  

### <a name="run-the-client-application"></a>Uruchom aplikację kliencką

**Nieobsłużony wyjątek: System.ServiceModel.EndpointNotFoundException: Nie można nawiązać połączenia z serwerem\/"http:/localhost: 8000/GettingStarted/CalculatorService". Kod błędu TCP 10061: Nie można nawiązać połączenia, ponieważ maszyna docelowa aktywnie odrzuciła ją.**

Ten błąd występuje, gdy aplikacja kliencka jest uruchamiana bez wcześniejszego uruchomienia usługi. Najpierw uruchom aplikację hosta, aby uruchomić usługę, a następnie uruchom aplikację kliencką.

### <a name="use-the-svcutilexe-tool"></a>Korzystanie z narzędzia Svcutil. exe
   
**Element "svcutil" nie został rozpoznany jako polecenie wewnętrzne lub zewnętrzne, program interoperacyjny lub plik wsadowy.**

 *Svcutil. exe* musi znajdować się w ścieżce systemowej. Najprostszym rozwiązaniem jest użycie wiersza polecenia programu Visual Studio. Z menu **Start** wybierz katalog **> wersja programu Visual \<Studio** , a następnie wybierz pozycję **wiersz polecenia dla deweloperów dla programu \<vs version >** . Ten wiersz polecenia ustawia ścieżkę systemową do odpowiednich lokalizacji dla wszystkich narzędzi dostarczanych w ramach programu Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Uruchamianie usługi i aplikacji klienckich

**System.ServiceModel.Security.SecurityNegotiationException: Negocjowanie zabezpieczeń protokołu SOAP z opcją\/"http:/localhost: 8000/GettingStarted/CalculatorService" dla elementu\/docelowego "http:/localhost: 8000/GettingStarted/CalculatorService" nie powiodło się**  

Ten błąd występuje na komputerze przyłączonym do domeny, który nie ma łączności sieciowej. Połącz komputer z siecią lub Wyłącz zabezpieczenia zarówno dla usługi, jak i dla klienta. 

Aby wyłączyć zabezpieczenia:

- W przypadku usługi Zastąp kod, który tworzy `WSHttpBinding` następujący kod:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- W przypadku klienta w pliku konfiguracji zaktualizuj  **\<element > zabezpieczeń** w obszarze  **\<Powiązywanie >** w następujący sposób:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>Zobacz także  
 [Wprowadzenie do aplikacji WCF](getting-started-tutorial.md)  
 [Rozwiązywanie problemów z WCF — Szybki Start](wcf-troubleshooting-quickstart.md)  
 [Rozwiązywanie problemów z instalacją](troubleshooting-setup-issues.md)
