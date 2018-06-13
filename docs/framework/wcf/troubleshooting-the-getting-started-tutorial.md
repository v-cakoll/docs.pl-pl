---
title: Rozwiązywanie problemów z samouczkiem dotyczącym wprowadzenia
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 12812bd1ef88eab14a8defed0b71657b0d33c618
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807791"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>Rozwiązywanie problemów z samouczkiem dotyczącym wprowadzenia
W tym temacie wymieniono najczęściej występujących problemów podczas pracy za pośrednictwem Samouczek wprowadzający i sposobu ich rozwiązania.  
  
1.  [Nie można odnaleźć plików projektu na dysku twardego.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [Próba uruchomienia aplikacji usługi: HTTP nie może zarejestrować adresu URL http://+:8000/ServiceModelSamples/Service/. Proces nie ma praw dostępu do tej przestrzeni nazw.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [Podjęto próbę użycia narzędzia Svcutil.exe: "svcutil" nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [Nie można znaleźć pliku App.config, generowane przez Svcutil.exe.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [Kompilowanie aplikacji klienta: "CalculatorClient" nie zawiera definicji dla "&lt;nazwę metody&gt;"i nie — metoda rozszerzenia"&lt;nazwę metody&gt;" przyjmuje pierwszy argument typu "CalculatorClient" Odnaleziono (Brak using dyrektywa lub odwołania do zestawu?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [Kompilowanie aplikacji klienta: "CalculatorClient" nie można odnaleźć nazwy typu lub przestrzeni nazw (czy nie brakuje using dyrektywa lub odwołania do zestawu?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [Uruchamianie klienta: nieobsługiwany wyjątek: System.ServiceModel.EndpointNotFoundException: nie można połączyć z http://localhost:8000/ServiceModelSamples/Service/CalculatorService. Kod błędu TCP 10061: połączenie nie może ustanowione, ponieważ aktywnie odrzucił w komputerze docelowym.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## <a name="i-am-unable-to-find-the-project-files-on-my-hard-drive"></a>Nie można odnaleźć plików projektu na dysku twardego.  
 Visual Studio zapisuje pliki projektu w c:\users\\< name\Documents użytkownika\\< wersji programu Visual Studio\>\Projects w [!INCLUDE[wv](../../../includes/wv-md.md)] i [!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)]i c:\Documents and Settings\\< nazwa użytkownika \>\My dokumenty\\< wersji programu Visual Studio\>\Projects we wcześniejszych wersjach systemu Windows.  
  
<a name="BKMK_q2"></a>   
## <a name="attempting-to-run-the-service-application-http-could-not-register-url-http8000servicemodelsamplesservice-your-process-does-not-have-access-rights-to-this-namespace"></a>Próba uruchomienia aplikacji usługi: HTTP nie może zarejestrować adresu URL http://+:8000/ServiceModelSamples/Service/. Proces nie ma praw dostępu do tej przestrzeni nazw.  
 Proces, który jest hostem usługi WCF musi być uruchamiane z uprawnieniami administracyjnymi. Jeśli używasz usługi z wewnątrz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] należy uruchomić [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] jako Administrator. Kliknij tak zrobić **Start**, kliknij prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i wybierz **Uruchom jako Administrator**. Jeśli używasz usługi w wierszu polecenia należy uruchomić wpisz w wierszu polecenia z uprawnieniami administratora w podobny sposób. Kliknij przycisk **Start**, kliknij prawym przyciskiem myszy **wiersza polecenia** i wybierz **Uruchom jako Administrator**.  
  
<a name="BKMK_q3"></a>   
## <a name="attempting-to-use-the-svcutilexe-tool-svcutil-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Podjęto próbę użycia narzędzia Svcutil.exe: "svcutil" nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy.  
 Svcutil.exe musi być w ścieżce systemowej. Najlepszym rozwiązaniem jest, aby użyć wiersza polecenia. Kliknij przycisk **Start**, wybierz pozycję **wszystkie programy**, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], **programu Visual Studio Tools**, i [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] **wiersza polecenia**. Ten wiersz polecenia ustawia ścieżkę systemu w poprawnych lokalizacjach dla wszystkich narzędzi, które zostały wydane jako część [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
<a name="BKMK_q4"></a>   
## <a name="unable-to-find-the-appconfig-file-generated-by-svcutilexe"></a>Nie można znaleźć pliku App.config, generowane przez Svcutil.exe.  
 **Dodaj istniejący element** okno dialogowe wyświetlane są tylko pliki z następującymi rozszerzeniami domyślnie: CS resx, .settings, XSD, .wsdl. Można określić, czy chcesz wyświetlić wszystkie typy plików, wybierając **wszystkie pliki (\*.\*)**  w w prawym dolnym rogu listy rozwijanej **Dodaj istniejący element** okno dialogowe.  
  
<a name="BKMK_q5"></a>   
## <a name="compiling-the-client-application-calculatorclient-does-not-contain-a-definition-for-method-name-and-no-extension-method-method-name-accepting-a-first-argument-of-type-calculatorclient-could-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>Kompilowanie aplikacji klienta: "CalculatorClient" nie zawiera definicji dla "\<nazwę metody >" i nie — metoda rozszerzenia "\<nazwę metody >" przyjmuje pierwszy argument typu "CalculatorClient" można odnaleźć (czy Brak using dyrektywa lub odwołania do zestawu?)  
 Tylko metody, które są oznaczone ikoną z `ServiceOperationAttribute` są widoczne dla użytkowników zewnętrznych. Jeśli zostanie pominięta `ServiceOperationAttribute` atrybut z jednej z metod w `ICalculator` interfejsu otrzymasz ten komunikat o błędzie podczas kompilowania aplikacji klienckiej, która nawiązuje połączenie z operacją Brak atrybutu.  
  
<a name="BKMK_q6"></a>   
## <a name="compiling-the-client-application-the-type-or-namespace-name-calculatorclient-could-not-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>Kompilowanie aplikacji klienta: "CalculatorClient" nie można odnaleźć nazwy typu lub przestrzeni nazw (czy nie brakuje using dyrektywa lub odwołania do zestawu?)  
 Ten błąd wystąpi, jeśli nie dodasz Proxy.cs lub Proxy.vb plik do projektu klienta.  
  
<a name="BKMK_q7"></a>   
## <a name="running-the-client-unhandled-exception-systemservicemodelendpointnotfoundexception-could-not-connect-to-httplocalhost8000servicemodelsamplesservicecalculatorservice-tcp-error-code-10061-no-connection-could-be-made-because-the-target-machine-actively-refused-it"></a>Uruchamianie klienta: nieobsługiwany wyjątek: System.ServiceModel.EndpointNotFoundException: nie można połączyć z http://localhost:8000/ServiceModelSamples/Service/CalculatorService. Kod błędu TCP 10061: połączenie nie może ustanowione, ponieważ aktywnie odrzucił w komputerze docelowym.  
 Ten błąd występuje podczas uruchamiania aplikacji klienckiej bez konieczności uruchamiania usługi.  
  
<a name="BKMK_q8"></a>   
## <a name="unhandled-exception-systemservicemodelsecuritysecuritynegotiationexception-soap-security-negotiation-with-httplocalhost8000servicemodelsamplesservicecalculatorservice-for-target-httplocalhost8000servicemodelsamplesservicecalculatorservice-failed"></a>Nieobsługiwany wyjątek: System.ServiceModel.Security.SecurityNegotiationException: wynegocjować zabezpieczeń SOAP z "http://localhost:8000/ServiceModelSamples/Service/CalculatorService'dla obiektu docelowego"http://localhost:8000/ServiceModelSamples/Service/CalculatorService"nie powiodło się  
 Ten błąd występuje na komputerze przyłączonym do domeny, który nie ma łączności sieciowej. Połączenia komputera z siecią albo wyłącz zabezpieczeń zarówno klient, jak i usługi. Dla usługi należy zmodyfikować kod, który tworzy WSHttpBinding do następującego.  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```  
  
 Dla klienta, należy zmienić  **\<zabezpieczeń >** pod  **\<powiązania >** element ma być następujące:  
  
```xml  
<security mode="Node" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Szybki start: rozwiązywanie problemów z architekturą WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [Rozwiązywanie problemów dotyczących konfiguracji](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
