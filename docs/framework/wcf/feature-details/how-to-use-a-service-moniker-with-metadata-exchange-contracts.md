---
title: 'Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 6265860c2e1efb2f74a0243157a223a33889629a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491253"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych
Po rozwinięciu niektóre nowe usługi WCF, mogą zdecydować, chcesz mieć możliwość wywołania tych usług z skryptu lub aplikacji Visual Basic 6.0. Jedna z metod byłoby wygenerować zestawu klienta WCF, zarejestrować zestawu w modelu COM, Instalowanie zestawu w pamięci podręcznej GAC i odwoływanie do typów COM w kodzie języka Visual Basic. Podczas dystrybucji aplikacji należy rozesłać także zestaw klienta WCF. Użytkownik będzie miał do rejestrowania zestawów klienta WCF COM i umieszczenie go w pamięci GAC. Współdziałanie z COM WCF umożliwia również wywoływać tej samej usługi bez polegania na zestawie klienta WCF. Monikera programu WCF pozwala wywoływać żadnej usługi WCF z dowolnego języka zgodny z modelu COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) i tak dalej), określając punkt końcowy programu exchange (Mex) metadanych identyfikator URI, który moniker usługi używany do wyodrębniania typu informacje o usłudze. W tym temacie opisano sposób wywołania próbki pobierania programu WCF za pomocą usługi WCF krótkiej nazwy, która określa punkt końcowy Mex.  
  
> [!NOTE]
>  Typy zdefiniowane przez zestaw klienta WCF nigdy są tworzone. Zestaw jest używany tylko dla metadanych.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Przy użyciu moniker usługi za pomocą adresu MEX.  
  
1.  Tworzenie przykładowej wprowadzenie i przejdź do adresu URL za pomocą programu Internet Explorer (http://localhost/ServiceModelSamples/Service.svc) aby upewnić się, że usługa jest uruchomiona.  
  
2.  Utwórz skrypt Visual Basic lub Visual Basic aplikacji, która zawiera następujący kod:  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  Uruchamianie aplikacji Visual Basic lub skryptu.  
  
    > [!NOTE]
    >  Usługa wywoływanego musi ujawniać punkt końcowy Mex dla krótkiej nazwy móc odczytać metadane z usługi. Aby uzyskać więcej informacji, zobacz [porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwróci błąd informujący o tym "Nieprawidłową składnię."  Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: używanie monikera programu Windows Communication Foundation bez rejestracji](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [Instrukcje: używanie krótkiej nazwy z kontraktami WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
