---
title: Rozwiązywanie problemów z Get pracy z usługą Windows Communication Foundation samouczki
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 8089e0fee262d07be591069982b1aacfbeae2521
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791472"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Rozwiązywanie problemów z Get pracy z usługą Windows Communication Foundation samouczki

Ten artykuł zawiera rozwiązania najczęstszych problemów i błędów, może występować po wykonaniu kroków w [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md). 
  
## <a name="common-problems"></a>Typowe problemy

**Nie mogę znaleźć pliki projektu na dysku twardego.**

 Program Visual Studio zapisuje pliki projektu *C:\Users\\&lt;nazwa_użytkownika&gt;\source\repos*.  

**Nie można odnaleźć *App.config* pliku wygenerowanego przez *Svcutil.exe*.**

 W programie Visual Studio **Dodaj istniejący element** domyślnie okno tylko Wyświetla pliki z następującymi rozszerzeniami: 
- *.cs* 
- *.resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

Aby wyświetlić wszystkie typy plików, wybierz **wszystkie pliki (\*.\*)**  na liście rozwijanej w prawym dolnym rogu **Dodaj istniejący element** okna.  
  
## <a name="common-errors"></a>Typowe błędy

### <a name="compile-the-service-application"></a>Kompilowanie aplikacji usługi 

**Błąd BC30420 "Sub Main" nie został znaleziony w "GettingStartedHost.Module1".**

Punkt wejścia jest niepoprawny dla aplikacji Visual Basic. Wprowadź następujące zmiany:

   1. W **Eksploratora rozwiązań** wybierz **GettingStartedHost** folder, a następnie wybierz **właściwości** z menu skrótów.
    a. W **GettingStartedHost** okna, aby uzyskać **obiekt początkowy**, wybierz opcję **Service.Program** (lub punkt wejścia dla określonej aplikacji) z listy. 
    b. W menu głównym wybierz **pliku** > **Zapisz wszystko**.

### <a name="run-the-service-application"></a>Uruchamianie aplikacji usługi 

**Protokół HTTP nie można zarejestrować adres URL "http:\// +: 8000/GettingStarted/CalculatorService". Proces nie ma praw dostępu do tej przestrzeni nazw.** 

 Do niej dostęp należy uruchomić proces, obsługujący usługę Windows Communication Foundation (WCF) z uprawnieniami administracyjnymi:
- For Visual Studio: Wybierz program Visual Studio w **Start** menu, a następnie wybierz pozycję **więcej** > **Uruchom jako administrator** z menu skrótów.
- W oknie konsoli: Wybierz **polecenia** w **Start** menu, a następnie wybierz pozycję **więcej** > **Uruchom jako administrator** ze skrótu menu.
- W Eksploratorze Windows: Wybierz plik wykonywalny, a następnie wybierz **Uruchom jako administrator** z menu skrótów.

### <a name="compile-the-client-application"></a>Kompilowanie aplikacji klienta

**"CalculatorClient" nie zawiera definicji dla "\<Nazwa metody >" i żadna metoda rozszerzenia "\<nazwę metody >" przyjmującej pierwszy argument typu "CalculatorClient" można odnaleźć (czy nie brakuje przy użyciu dyrektywy lub Odwołanie do zestawu?)**  

Tylko oznaczonych przez użytkownika za pomocą metod `ServiceOperationAttribute` atrybutu są publicznie widoczne. Jeżeli pominięto `ServiceOperationAttribute` atrybut z metody w `ICalculator` interfejsu, pojawi się ten komunikat o błędzie podczas kompilacji.  

**Nazwa typu lub przestrzeni nazw, nie można odnaleźć "CalculatorClient" (Brak przy użyciu dyrektywy lub odwołania do zestawu?)**

 Ten błąd jest wyświetlany, jeśli nie dodasz *generatedProxy.cs* (lub *generatedProxy.vb*) plik, aby projekt klienta, gdy został wygenerowany za pomocą *Svcutil.exe* narzędzia .  

### <a name="run-the-client-application"></a>Uruchom aplikację klienta

**Nieobsługiwany wyjątek: System.ServiceModel.EndpointNotFoundException: Nie można połączyć z "http:\//localhost:8000/GettingStarted/CalculatorService". Kod błędu TCP 10061: Nie można ustanowić połączenia ponieważ aktywnie odrzucił w komputerze docelowym.**

Ten błąd występuje, jeśli aplikacja kliencka jest uruchomiona bez uruchamiania usługi. Najpierw uruchom aplikacji hosta, aby uruchomić usługę, a następnie uruchom aplikację klienta.

### <a name="use-the-svcutilexe-tool"></a>Użyj narzędzia Svcutil.exe
   
**"Svcutil" nie został rozpoznany jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy.**

 *Svcutil.exe* musi znajdować się w ścieżce systemowej. Najprostszym rozwiązaniu jest Użyj wiersza polecenia programu Visual Studio. Z **Start** menu, wybierz opcję **programu Visual Studio \<wersji >** katalogu, a następnie wybierz opcję **wiersz polecenia programisty dla programu VS \<wersji >**. Ten wiersz polecenia ustawia ścieżkę systemu w poprawnych lokalizacjach, w przypadku wszystkich narzędzi dostarczana jako część programu Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Uruchamianie aplikacji usługi i klienta

**System.ServiceModel.Security.SecurityNegotiationException: Negocjowanie zabezpieczeń protokołu SOAP z "http:\//localhost:8000/GettingStarted/CalculatorService" dla elementu docelowego "http:\//localhost:8000/GettingStarted/CalculatorService" nie powiodło się**  

Ten błąd występuje na komputerze przyłączonym do domeny, która nie ma łączności sieciowej. Łączenie komputera z siecią lub wyłączyć zabezpieczeń dla usługi i klienta. 

Aby wyłączyć zabezpieczeń:

- Usługi, Zastąp kod, który tworzy `WSHttpBinding` następującym kodem:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Aktualizacja klienta, w pliku konfiguracyjnym  **\<zabezpieczeń >** pod  **\<powiązania >** elementu w następujący sposób:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>Zobacz także  
 [Rozpoczynanie pracy z aplikacjami usługi WCF](getting-started-tutorial.md)  
 [Szybki Start rozwiązywania problemów z architekturą WCF](wcf-troubleshooting-quickstart.md)  
 [Rozwiązywanie problemów dotyczących konfiguracji](troubleshooting-setup-issues.md)
