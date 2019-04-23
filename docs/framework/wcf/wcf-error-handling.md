---
title: Obsługa błędów programu WCF
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: d70edacd2447fbe0b0b6db42b93f699ce7c17003
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306290"
---
# <a name="wcf-error-handling"></a>Obsługa błędów programu WCF
Błędy napotykane przez aplikację WCF należeć do jednej z trzech grup:  
  
1. Błędy komunikacji  
  
2. Błędy serwera proxy/kanału  
  
3. Błędy aplikacji  
  
 Błędy komunikacji występują, gdy sieć jest niedostępny, klient używa niepoprawny adres lub host usługi nie nasłuchuje przychodzących wiadomości. Błędy tego typu są zwracane do klienta jako <xref:System.ServiceModel.CommunicationException> lub <xref:System.ServiceModel.CommunicationException>-klas pochodnych.  
  
 Błędy serwera proxy/kanału błędów występujących w ramach kanału lub serwera proxy. Błędy tego typu obejmują: Podjęto próbę użycia serwera proxy lub kanału, który został zamknięty, niezgodnością kontraktu istnieje między klientem a usługą lub poświadczenia klienta są odrzucane przez usługę. Istnieje wiele różnych typów błędów w tej kategorii zbyt wiele elementów do wyświetlenia w tym miejscu. Błędy tego typu są zwracane do klienta jako — jest (nie przekształcania odbywa się w obiektach wyjątków).  
  
 Występują błędy aplikacji podczas wykonywania operacji usługi. Błędy tego rodzaju są wysyłane do klienta jako <xref:System.ServiceModel.FaultException> lub <xref:System.ServiceModel.FaultException%601>.  
  
 Obsługa błędów w WCF odbywa się co najmniej jeden z następujących czynności:  
  
-   Bezpośrednio obsługi wyjątku. Jest to wykonywane tylko dla komunikacji i błędy kanału/serwera proxy.  
  
-   Używanie kontraktów błędów  
  
-   Implementowanie <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu  
  
-   Obsługa <xref:System.ServiceModel.ServiceHost> zdarzenia  
  
## <a name="fault-contracts"></a>Kontrakty błędów  
 Kontrakty błędów umożliwiają definiowanie błędów, które mogą wystąpić podczas operacji usługi na platformie sposób niezależny. Domyślnie wszystkie wyjątki zgłaszane z w ramach operacji usługi zostanie zwrócony do klienta jako <xref:System.ServiceModel.FaultException> obiektu. <xref:System.ServiceModel.FaultException> Obiektu będzie zawierać informacje bardzo mała. Informacje wysyłane do klienta, definiując kontrakt błędu i zwraca błąd, ponieważ możesz kontrolować <xref:System.ServiceModel.FaultException%601>. Aby uzyskać więcej informacji, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> Interfejs umożliwia większą kontrolę nad jak aplikację WCF reaguje na błędy.  Daje pełną kontrolę nad komunikat o błędzie, jest zwracana do klienta, która umożliwia wykonywanie przetwarzania, takich jak rejestrowanie błędów niestandardowych.  Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Dispatcher.IErrorHandler> i [rozszerzanie kontroli nad obsługę błędów i raportowanie](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>ServiceHost Events  
 <xref:System.ServiceModel.ServiceHost> Klasy usług hostów i definiuje kilka zdarzeń, które mogą być potrzebne do obsługi błędów. Na przykład:  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 Aby uzyskać więcej informacji zobacz <xref:System.ServiceModel.ServiceHost>
