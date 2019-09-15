---
title: 'Instrukcje: używanie krótkiej nazwy usługi z kontraktami WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 7bc628952d4a7198f0b5545014ae931bbf73dab3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969000"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>Instrukcje: używanie krótkiej nazwy usługi z kontraktami WSDL
Istnieją sytuacje, w których można chcieć korzystać z całkowicie niezależnego klienta międzyoperacyjnego modelu COM. Usługa, która ma zostać wywołana, może nie ujawniać punktu końcowego MEX, a Biblioteka DLL klienta WCF nie może być zarejestrowana na potrzeby współdziałania z modelem COM. W takich przypadkach można utworzyć plik WSDL opisujący usługę i przekazać go do monikera usługi WCF. W tym temacie opisano sposób wywoływania przykładu Wprowadzenie WCF przy użyciu monikera WSDL programu WCF.  
  
### <a name="using-the-wsdl-service-moniker"></a>Używanie monikera usługi WSDL  
  
1. Otwórz i skompiluj przykładowe rozwiązanie GettingStarted.  
  
2. Otwórz program Internet Explorer i przejdź `http://localhost/ServiceModelSamples/Service.svc` do programu, aby upewnić się, że usługa działa.  
  
3. W pliku Service.cs Dodaj następujący atrybut klasy CalculatorService:  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. Dodawanie powiązania przestrzeni nazw do pliku App. config usługi:  

5. Utwórz plik WSDL, aby można było odczytać aplikację. Ponieważ przestrzenie nazw zostały dodane w krokach 3 i 4, można użyć programu IE do zapytania o cały opis WSDL usługi, przechodząc do `http://localhost/ServiceModelSamples/Service.svc?wsdl`tematu. Następnie można zapisać plik z programu Internet Explorer jako serviceWsdl. XML. Jeśli nie określisz przestrzeni nazw w krokach 3 i 4, dokument WSDL zwrócony z zapytania o powyższy adres URL nie będzie kompletny w języku WSDL. Zwrócony dokument WSDL będzie zawierać kilka instrukcji importu, które zaimportują inne dokumenty WSDL. Trzeba będzie przejść przez każdą instrukcję importu i utworzyć kompletny dokument WSDL, łącząc element WSDL zwrócony z usługi z zaimportowanym WSDL.  
  
6. Otwórz Visual Basic 6,0 i Utwórz nowy plik w standardowym pliku. exe. Dodaj przycisk do formularza i kliknij dwukrotnie przycisk, aby dodać następujący kod do procedury obsługi kliknięcia:  
  
    ```vb
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    > Jeśli moniker jest źle sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwróci błąd mówiąc "Nieprawidłowa składnia".  Jeśli wystąpi ten błąd, upewnij się, że moniker, którego używasz, jest poprawna i że usługa jest dostępna.  
  
7. Uruchom aplikację Visual Basic. Zostanie wyświetlone okno komunikatu z wynikami wywoływania odejmowania (145, 76,54).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Przegląd integrowania z aplikacjami COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
