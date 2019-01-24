---
title: Rozwiązywanie problemów z samouczkiem dotyczącym wprowadzenia
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 5b8cd04ef4d98e522e255e1b7529e848351b2e0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695663"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>Rozwiązywanie problemów z samouczkiem dotyczącym wprowadzenia
W tym temacie wymieniono najbardziej typowe problemy występujące podczas pracy przy użyciu samouczka Wprowadzenie i ich rozwiązania.  
  
**Nie mogę znaleźć pliki projektu na dysku twardego.**

 Program Visual Studio zapisuje pliki projektu w c:\users\\<user name>\Documents\\< wersja programu Visual Studio\>\Projects.  
  
**Przy próbie uruchomienia aplikacji usługi: Protokół HTTP nie można zarejestrować adres URL `http://+:8000/ServiceModelSamples/Service/`.** 
 **Proces nie ma praw dostępu do tej przestrzeni nazw.** 

 Proces, który hostuje usługę WCF musi być uruchamiane z uprawnieniami administracyjnymi. Jeśli korzystasz z usługi z poziomu programu Visual Studio, należy uruchomić programu Visual Studio jako Administrator. Kliknij tak zrobić **Start**, kliknij prawym przyciskiem myszy **programu Visual Studio \< *wersji* >**  i wybierz **Uruchom jako Administrator**. Jeśli korzystasz z usługi, w wierszu polecenia w oknie konsoli, należy uruchomić w oknie konsoli jako Administrator, w podobny sposób. Kliknij przycisk **Start**, kliknij prawym przyciskiem myszy **polecenia** i wybierz **Uruchom jako Administrator**.  
  
**Podjęto próbę użycia narzędzia Svcutil.exe: "svcutil" nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, program wykonywalny lub plik wsadowy.**

 Svcutil.exe musi być w ścieżce systemowej. Najprostszym rozwiązaniu jest używać wiersza polecenia. Kliknij przycisk **Start**, wybierz opcję **wszystkie programy**, **programu Visual Studio \< *wersji*>**,  **Narzędzia programu Visual Studio**, i **wiersz polecenia programisty dla programu Visual Studio**. Ten wiersz polecenia ustawia ścieżkę systemu w poprawnych lokalizacjach, w przypadku wszystkich narzędzi dostarczana jako część programu Visual Studio.  

**Nie można odnaleźć pliku App.config, wygenerowanego przez Svcutil.exe.**

 **Dodaj istniejący element** domyślnie okno dialogowe tylko Wyświetla pliki z następującymi rozszerzeniami: .cs resx, .settings, XSD, .wsdl. Można określić, czy chcesz zobaczyć wszystkie typy plików, wybierając **wszystkie pliki (\*.\*)**  w polu listy rozwijanej w prawym dolnym rogu **Dodaj istniejący element** okno dialogowe.  


**Kompilowanie aplikacji klienta: "CalculatorClient" nie zawiera definicji dla "\<Nazwa metody >" i żadna metoda rozszerzenia "\<nazwę metody >" przyjmującej pierwszy argument typu "CalculatorClient" można odnaleźć (czy nie brakuje przy użyciu dyrektywy lub Odwołanie do zestawu?)**  

Tylko tych metod, które są oznaczone `ServiceOperationAttribute` są widoczne na zewnątrz. Jeżeli pominięto `ServiceOperationAttribute` atrybut z jednej z metod w `ICalculator` interfejsu, otrzymasz komunikat o błędzie podczas kompilowania aplikacji klienckiej, która sprawia, że wywołanie operacji Brak atrybutu.  

**Kompilowanie aplikacji klienta: Nazwa typu lub przestrzeni nazw, nie można odnaleźć "CalculatorClient" (Brak przy użyciu dyrektywy lub odwołania do zestawu?)**

 Ten błąd, jeśli plik Proxy.cs lub Proxy.vb nie należy dodawać do projektu klienta.  

**Uruchamianie klienta: Nieobsługiwany wyjątek: System.ServiceModel.EndpointNotFoundException: Nie można połączyć z `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. Kod błędu TCP 10061: Nie można ustanowić połączenia ponieważ aktywnie odrzucił w komputerze docelowym.**

Ten błąd występuje, jeśli aplikacja kliencka jest uruchomiona bez konieczności uruchamiania usługi.  
  
**Nieobsługiwany wyjątek: System.ServiceModel.Security.SecurityNegotiationException: Negocjowanie zabezpieczeń protokołu SOAP z `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` dla elementu docelowego `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` nie powiodło się**  

Ten błąd występuje na komputerze przyłączonym do domeny, który nie ma łączności sieciowej. Łączenie komputera z siecią lub wyłączyć funkcję zabezpieczeń dla klienta i usługi. Usługi należy zmodyfikować kod, który tworzy powiązanie WSHttpBinding do następujących.  
  
```csharp
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```

Dla klienta, należy zmienić  **\<zabezpieczeń >** pod  **\<powiązania >** element do następującego:  
  
```xml
<security mode="Node" />  
```  

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md)
- [Szybki start: rozwiązywanie problemów z architekturą WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)
- [Rozwiązywanie problemów dotyczących konfiguracji](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
