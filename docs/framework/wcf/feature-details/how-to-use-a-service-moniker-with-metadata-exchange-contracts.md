---
title: 'Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 8894fdc4fd085b9d55a8fc25043e5258c306024c
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143481"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych
Po rozpoczęciu tworzenia nowych usług WCF możesz zdecydować, że chcesz mieć możliwość wywoływania tych usług ze skryptu lub aplikacji Visual Basic 6,0. Jedną z metod jest generowanie zestawu klienta WCF, rejestrowanie zestawu przy użyciu modelu COM, Instalowanie zestawu w GAC, a następnie odwoływanie się do typów COM z kodu Visual Basic. Podczas dystrybucji aplikacji konieczne będzie również dystrybuowanie zestawu klienta WCF. Użytkownik będzie musiał następnie zarejestrować zestaw klienta programu WCF przy użyciu modelu COM i umieścić go w pamięci podręcznej GAC. Współdziałanie modelu COM WCF umożliwia również wykonywanie tych samych wywołań usługi bez polegania na zestawie klienta WCF. Moniker programu WCF umożliwia wywoływanie dowolnej usługi WCF z dowolnego języka zgodnego z modelem COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) itd.) przez określenie identyfikatora URI punktu końcowego wymiany metadanych (Mex), którego moniker usługi używa do wyodrębniania informacji o typie usługi. W tym temacie opisano sposób wywoływania przykładu Wprowadzenie WCF przy użyciu monikera programu WCF określającego punkt końcowy MEX.  
  
> [!NOTE]
> Typy zdefiniowane przez zestaw klienta WCF nigdy nie są tworzone w rzeczywistości. Zestaw jest używany tylko dla metadanych.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Używanie monikera usługi z adresem Mex  
  
1. Utwórz przykład Wprowadzenie i użyj programu Internet Explorer, aby przejść do jego adresu URL ( `http://localhost/ServiceModelSamples/Service.svc` ), aby upewnić się, że usługa działa.  
  
2. Utwórz skrypt Visual Basic lub aplikację Visual Basic, która zawiera następujący kod:  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. Uruchom aplikację Visual Basic lub skrypt.  
  
    > [!NOTE]
    > Wywoływana usługa musi uwidocznić punkt końcowy MEX, aby moniker mógł odczytać metadane z usługi. Aby uzyskać więcej informacji, zobacz [jak: Publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    > Jeśli moniker jest źle sformułowany lub usługa jest niedostępna, wywołanie `GetObject` zwróci komunikat o błędzie informujący o nieprawidłowej składni.  Jeśli wystąpi ten błąd, upewnij się, że moniker, którego używasz, jest poprawna i że usługa jest dostępna.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: używanie monikera programu Windows Communication Foundation bez rejestracji](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [Instrukcje: używanie krótkiej nazwy z kontraktami WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
