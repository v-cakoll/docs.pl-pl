---
title: "Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31720b0639f9be68a2124b4ff844a2837787ef81
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Instrukcje: Używanie krótkiej nazwy z kontraktami wymiany metadanych
Po rozwinięciu niektóre nowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług, użytkownik może zadecydować chcesz mieć możliwość wywołania tych usług z skryptu lub aplikacji Visual Basic 6.0. Jedna z metod byłoby Generowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zestawu klienta zarejestrować zestawu w modelu COM, zainstalowania zestawu w pamięci podręcznej GAC i odwoływanie do typów COM w kodzie języka Visual Basic. Podczas dystrybucji aplikacji, konieczne będzie dystrybuować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] również zestawu klienta. Użytkownik będzie miał do rejestrowania zestawów klienta WCF COM i umieszczenie go w pamięci GAC. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Współdziałanie z COM umożliwia także wywoływać tej samej usługi bez polegania na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zestawu klienta. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker pozwala wywoływać żadnego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług z dowolnego języka zgodny z modelu COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) i tak dalej), określając punkt końcowy programu exchange (Mex) metadanych identyfikator URI, który używa moniker usługi Aby wyodrębnić informacje o typie dotyczących usługi. W tym temacie opisano sposób wywołania wprowadzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbkowania przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] krótkiej nazwy, która określa punkt końcowy Mex.  
  
> [!NOTE]
>  Typy zdefiniowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wystąpienia zestawu klienta faktycznie nigdy nie są tworzone. Zestaw jest używany tylko dla metadanych.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Przy użyciu moniker usługi za pomocą adresu MEX.  
  
1.  Tworzenie przykładowych wprowadzenie i użyj programu Internet Explorer, aby przejść na adres URL (http://localhost/ServiceModelSamples/Service.svc), aby upewnić się, że usługa jest uruchomiona.  
  
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
 [Porady: Użyj Moniker usługi Windows Communication Foundation bez rejestracji](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [Porady: używanie krótkiej nazwy z kontraktami WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
