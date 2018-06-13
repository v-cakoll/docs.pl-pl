---
title: 'Instrukcje: Używanie krótkiej nazwy z kontraktami WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 838e7affcf47742c8f372879fcb33946d53ba43f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491046"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a>Instrukcje: Używanie krótkiej nazwy z kontraktami WSDL
Istnieją sytuacje, gdy chcesz całkowicie niezależna klient COM Interop. Usługi, którą chcesz wywołać nie może narazić punktu końcowego MEX i klienta WCF, które biblioteki DLL nie jest zarejestrowany dla modelu COM interop. W takich przypadkach możesz utworzyć plik WSDL, który zawiera opis usługi i przekaż go do krótkiej nazwy usługi WCF. W tym temacie opisano sposób wywołania próbki pobierania programu WCF za pomocą moniker WCF WSDL.  
  
### <a name="using-the-wsdl-service-moniker"></a>Przy użyciu moniker usługi WSDL  
  
1.  Otwórz i kompilacji GettingStarted przykładowe rozwiązanie.  
  
2.  Otwórz program Internet Explorer i przejdź do http://localhost/ServiceModelSamples/Service.svc aby upewnić się, że usługa jest uruchomiona.  
  
3.  W pliku Service.cs Dodaj następujący atrybut w klasie CalculatorService:  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4.  Dodawanie przestrzeni nazw powiązania z usługą App.config:  
  
  
  
5.  Utwórz plik WSDL dla aplikacji do odczytu. Ponieważ przestrzenie nazw zostały dodane w kroku 3 i 4, można użyć programu Internet Explorer dla całego opis WSDL usługi kwerendy, przechodząc do http://localhost/ServiceModelSamples/Service.svc?wsdl. Można następnie zapisz plik z programu Internet Explorer jako serviceWSDL.xml. Jeśli nie określisz przestrzenie nazw w kroku 3 i 4, dokument WSDL zwracane z zapytań powyższy adres URL nie będzie pełną WSDL. Zwrócony dokument WSDL zawiera kilka instrukcje importu, które importują innych dokumentów WSDL. Musisz przejść przez każdego instrukcję import i kompilacji cały dokument WSDL, łączenie WSDL zakończyła WSDL zaimportowane z usługi.  
  
6.  Otwórz program Visual Basic 6.0 i Utwórz nowy plik .exe standardowa. Dodawanie przycisku do formularza, a następnie kliknij dwukrotnie przycisk, aby dodać poniższego kodu do obsługi kliknięcia:  
  
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
    >  Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna wywołanie `GetObject` zwróci błąd informujący o tym "Nieprawidłowa składnia".  Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.  
  
7.  Uruchom aplikację języka Visual Basic. Wyniki wywołania Subtract (145, 76.54) pojawi się okno komunikatu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Przegląd integrowania z aplikacjami COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
