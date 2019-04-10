---
title: 'Instrukcje: używanie krótkiej nazwy usługi z kontraktami WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 2968641538bf0b4d0e136d5784bf69e5e7fcb3a0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298087"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>Instrukcje: używanie krótkiej nazwy usługi z kontraktami WSDL
Istnieją sytuacje, gdy chcesz całkowicie niezależna klient COM Interop. Usługi, którą chcesz wywołać nie może ujawniać punktu końcowego MEX i klienta WCF, które biblioteki DLL nie jest zarejestrowany dla współdziałania z modelem COM. W takich przypadkach można utworzyć pliku WSDL, który zawiera opis usługi i przekaż go do monikera programu WCF. W tym temacie opisano sposób wywoływania przykładu wprowadzenie usługi WCF, używanie monikera programu WCF WSDL.  
  
### <a name="using-the-wsdl-service-moniker"></a>Używanie monikera usługi WSDL  
  
1. Otworzyć i skompilować GettingStarted przykładowe rozwiązanie.  
  
2. Otwórz program Internet Explorer i przejdź do `http://localhost/ServiceModelSamples/Service.svc` aby upewnić się, że usługa działa.  
  
3. W pliku Service.cs Dodaj następujący atrybut w klasie CalculatorService:  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. Dodawanie przestrzeni nazw powiązania z usługą pliku App.config:  

5. Utwórz plik WSDL dla aplikacji na odczytywanie. Ponieważ przestrzenie nazw zostały dodane w kroku 3 i 4, można użyć programu Internet Explorer dla całego opis WSDL usługi kwerendy, przechodząc do `http://localhost/ServiceModelSamples/Service.svc?wsdl`. Można następnie zapisz plik w programie Internet Explorer jako serviceWSDL.xml. Jeśli nie określisz przestrzeni nazw w kroku 3 i 4, zwrócone w wyniku wykonywania zapytań na powyższy adres URL dokumentu WSDL nie będą pełne WSDL. Dokument WSDL, zwracana będzie zawierać kilka deklaracji importu, które importują inne dokumenty WSDL. Trzeba będzie przejść każda instrukcja importu i tworzyć pełny dokument WSDL, łącząc WSDL zwrócony przez usługę za pomocą języka WSDL, zaimportowane.  
  
6. Otwórz Visual Basic 6.0 i Utwórz nowy plik .exe standardowych. Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk aby dodać następujący kod programem obsługi kliknięcia:  
  
    ```  
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
    >  Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna wywołanie `GetObject` zwróci błąd informujący o "Nieprawidłowa składnia".  Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.  
  
7. Uruchom aplikację języka Visual Basic. Okno komunikatu pojawi się wraz z wynikami Subtract wywołującym (145, 76.54).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Przegląd integrowania z aplikacjami modelu COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
