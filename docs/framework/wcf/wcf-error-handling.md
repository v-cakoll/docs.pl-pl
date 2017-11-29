---
title: "Obsługa błędów programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c5fa1aea718f3904eab38927d24a851043bbd896
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-error-handling"></a>Obsługa błędów programu WCF
Błędy napotykane przez aplikacja WCF należeć do jednej z trzech grup:  
  
1.  Błędy komunikacji  
  
2.  Błędy kanału/proxy  
  
3.  Błędy aplikacji  
  
 Jeśli sieć jest niedostępny, klient używa niepoprawny adres lub hosta usługi nie nasłuchuje przychodzących wiadomości występowania błędów komunikacji. Błędy tego typu są zwracane do klienta jako <xref:System.ServiceModel.CommunicationException> lub <xref:System.ServiceModel.CommunicationException>-klas pochodnych.  
  
 Błędy kanału/proxy są błędy występujące w kanału lub serwer proxy, samej siebie. Błędy tego typu obejmują: próba użycia serwera proxy lub kanału, który został zamknięty, niezgodnością kontraktu istnieje między klientem a usługą lub poświadczenia klienta są odrzucane przez usługę. Istnieje wiele różnych typów błędów w tej kategorii zbyt wiele elementów do wyświetlenia w tym miejscu. Błędy tego typu są zwracane do klienta jako — jest (przekształcenie nie jest wykonywana na obiekty wyjątków).  
  
 Występują błędy aplikacji podczas wykonywania operacji usługi. Błędy tego typu są wysyłane do klienta jako <xref:System.ServiceModel.FaultException> lub <xref:System.ServiceModel.FaultException%601>.  
  
 Obsługa błędów w WCF jest wykonywane przez jedną lub więcej z następujących czynności:  
  
-   Obsługa bezpośrednio zgłoszono wyjątek. Jest to wykonywane tylko dla komunikacji i błędy kanału/proxy.  
  
-   Używanie kontraktów błędów  
  
-   Implementowanie <xref:System.ServiceModel.Dispatcher.IErrorHandler> — interfejs  
  
-   Obsługa <xref:System.ServiceModel.ServiceHost> zdarzeń  
  
## <a name="fault-contracts"></a>Kontrakty błędów  
 Kontrakty usterek umożliwiają definiowanie błędów, które mogą wystąpić podczas operacji dotyczącej usługi na platformie sposób niezależny. Domyślnie wszystkie wyjątki zgłaszane z wewnątrz operacji usługi zostanie zwrócony do klienta jako <xref:System.ServiceModel.FaultException> obiektu. <xref:System.ServiceModel.FaultException> Obiektu będzie zawierać bardzo niewielka ilość informacji. Można kontrolować informacje wysyłane do klienta przez definiowanie kontraktu usterek i zwróci komunikat jako <xref:System.ServiceModel.FaultException%601>. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>Interfejsy IErrorHandler  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> Interfejs umożliwia większą kontrolę nad jak aplikacja WCF reaguje na błędy.  Udostępnia pełną kontrolę nad komunikat o błędzie, jest zwracana do klienta, który umożliwia wykonywanie przetwarzania, takich jak rejestrowanie błędów niestandardowych.  [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<xref:System.ServiceModel.Dispatcher.IErrorHandler> i [rozszerzanie kontroli obsługi i raportowania błędów](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>Zdarzenia ServiceHost  
 <xref:System.ServiceModel.ServiceHost> Klasa usług hostów i definiuje kilka zdarzeń, które mogą być potrzebne do obsługi błędów. Na przykład:  
  
1.  <!--zz <xref:System.ServiceModel.ServiceHost.Faulted>-->  `System.ServiceModel.ServiceHost.Faulted`
  
2. <!--zz  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  --> `System.ServiceModel.ServiceHost.UnknownMessageReceived`
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<xref:System.ServiceModel.ServiceHost>
