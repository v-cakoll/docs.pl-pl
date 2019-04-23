---
title: 'Instrukcje: używanie krótkiej nazwy usługi z kontraktami wymiany metadanych'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 367cbd4a2bfbde3d4ab0a74eeeaf5d5f5662ec27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319836"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Instrukcje: używanie krótkiej nazwy usługi z kontraktami wymiany metadanych
Po rozwinięciu niektórych nowych usług WCF, może zdecydować, chcesz można było wywołać te usługi z poziomu skryptu lub aplikacji w języku Visual Basic 6.0. Jedną z metod byłoby wygenerować zestaw klienta WCF, zarejestrować zestaw w modelu COM, zainstaluj zestaw w pamięci podręcznej GAC i następnie odwoływać się do typów modelu COM w kodzie języka Visual Basic. Podczas dystrybucji aplikacji, trzeba będzie dystrybuować także zestaw klienta platformy WCF. Użytkownik będzie miał zarejestrowania się zestaw klienta programu WCF za pomocą modelu COM i umieść go w pamięci podręcznej GAC. Usługa międzyoperacyjna modelu COM WCF umożliwia również wykonywanie tych samych wywołań usługi bez polegania na zestaw klienta programu WCF. Monikera programu WCF umożliwia wywoływanie żadnej usługi WCF z dowolnego języka zgodnego z COM. (Visual Basic, VBScript, Visual Basic for Applications (VBA) i tak dalej), określając punkt końcowy metadanych programu exchange (Mex) identyfikator URI, który monikera usługi używany do wyodrębniania typu informacje o usłudze. W tym temacie opisano sposób wywoływania przykładu wprowadzenie usługi WCF, używanie monikera programu WCF, która określa punkt końcowy wymiany metadanych.  
  
> [!NOTE]
>  Typy zdefiniowane przez zestaw klienta WCF faktycznie nigdy nie są tworzone. Zestaw jest używany tylko w przypadku metadanych.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Używanie monikera usługi przy użyciu adresu wymiany metadanych  
  
1. Wprowadzenie do przykładu kompilacji i użyj programu Internet Explorer, aby przejść do jej adresu URL (http://localhost/ServiceModelSamples/Service.svc) aby upewnić się, że usługa działa.  
  
2. Utwórz skrypt Visual Basic lub aplikacji Visual Basic, który zawiera następujący kod:  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. Uruchamianie aplikacji języka Visual Basic lub skryptu.  
  
    > [!NOTE]
    >  Usługi, którą wywołujesz musi ujawniać punkt końcowy wymiany metadanych dla monikera móc odczytać metadane z usługi. Aby uzyskać więcej informacji, zobacz [jak: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna, wywołanie `GetObject` zwróci błąd informujący o "Nieprawidłową składnię."  Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Użyj monikera usługi Windows Communication Foundation, bez rejestracji](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [Instrukcje: Używanie krótkiej nazwy z kontraktami WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
