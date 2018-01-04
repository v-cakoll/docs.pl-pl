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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 860f96ee92db6a11238942202d4e202ba912d748
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-error-handling"></a><span data-ttu-id="fe3a9-102">Obsługa błędów programu WCF</span><span class="sxs-lookup"><span data-stu-id="fe3a9-102">WCF Error Handling</span></span>
<span data-ttu-id="fe3a9-103">Błędy napotykane przez aplikacja WCF należeć do jednej z trzech grup:</span><span class="sxs-lookup"><span data-stu-id="fe3a9-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1.  <span data-ttu-id="fe3a9-104">Błędy komunikacji</span><span class="sxs-lookup"><span data-stu-id="fe3a9-104">Communication Errors</span></span>  
  
2.  <span data-ttu-id="fe3a9-105">Błędy kanału/proxy</span><span class="sxs-lookup"><span data-stu-id="fe3a9-105">Proxy/Channel Errors</span></span>  
  
3.  <span data-ttu-id="fe3a9-106">Błędy aplikacji</span><span class="sxs-lookup"><span data-stu-id="fe3a9-106">Application Errors</span></span>  
  
 <span data-ttu-id="fe3a9-107">Jeśli sieć jest niedostępny, klient używa niepoprawny adres lub hosta usługi nie nasłuchuje przychodzących wiadomości występowania błędów komunikacji.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="fe3a9-108">Błędy tego typu są zwracane do klienta jako <xref:System.ServiceModel.CommunicationException> lub <xref:System.ServiceModel.CommunicationException>-klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="fe3a9-109">Błędy kanału/proxy są błędy występujące w kanału lub serwer proxy, samej siebie.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="fe3a9-110">Błędy tego typu obejmują: próba użycia serwera proxy lub kanału, który został zamknięty, niezgodnością kontraktu istnieje między klientem a usługą lub poświadczenia klienta są odrzucane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="fe3a9-111">Istnieje wiele różnych typów błędów w tej kategorii zbyt wiele elementów do wyświetlenia w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="fe3a9-112">Błędy tego typu są zwracane do klienta jako — jest (przekształcenie nie jest wykonywana na obiekty wyjątków).</span><span class="sxs-lookup"><span data-stu-id="fe3a9-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="fe3a9-113">Występują błędy aplikacji podczas wykonywania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="fe3a9-114">Błędy tego typu są wysyłane do klienta jako <xref:System.ServiceModel.FaultException> lub <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="fe3a9-115">Obsługa błędów w WCF jest wykonywane przez jedną lub więcej z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="fe3a9-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
-   <span data-ttu-id="fe3a9-116">Obsługa bezpośrednio zgłoszono wyjątek.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="fe3a9-117">Jest to wykonywane tylko dla komunikacji i błędy kanału/proxy.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-117">This is only done for communication and proxy/channel errors.</span></span>  
  
-   <span data-ttu-id="fe3a9-118">Używanie kontraktów błędów</span><span class="sxs-lookup"><span data-stu-id="fe3a9-118">Using fault contracts</span></span>  
  
-   <span data-ttu-id="fe3a9-119">Implementowanie <xref:System.ServiceModel.Dispatcher.IErrorHandler> — interfejs</span><span class="sxs-lookup"><span data-stu-id="fe3a9-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
-   <span data-ttu-id="fe3a9-120">Obsługa <xref:System.ServiceModel.ServiceHost> zdarzeń</span><span class="sxs-lookup"><span data-stu-id="fe3a9-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="fe3a9-121">Kontrakty błędów</span><span class="sxs-lookup"><span data-stu-id="fe3a9-121">Fault Contracts</span></span>  
 <span data-ttu-id="fe3a9-122">Kontrakty usterek umożliwiają definiowanie błędów, które mogą wystąpić podczas operacji dotyczącej usługi na platformie sposób niezależny.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="fe3a9-123">Domyślnie wszystkie wyjątki zgłaszane z wewnątrz operacji usługi zostanie zwrócony do klienta jako <xref:System.ServiceModel.FaultException> obiektu.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="fe3a9-124"><xref:System.ServiceModel.FaultException> Obiektu będzie zawierać bardzo niewielka ilość informacji.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="fe3a9-125">Można kontrolować informacje wysyłane do klienta przez definiowanie kontraktu usterek i zwróci komunikat jako <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="fe3a9-126">[Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="fe3a9-126"> [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="fe3a9-127">Interfejsy IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="fe3a9-127">IErrorHandler</span></span>  
 <span data-ttu-id="fe3a9-128"><xref:System.ServiceModel.Dispatcher.IErrorHandler> Interfejs umożliwia większą kontrolę nad jak aplikacja WCF reaguje na błędy.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="fe3a9-129">Udostępnia pełną kontrolę nad komunikat o błędzie, jest zwracana do klienta, który umożliwia wykonywanie przetwarzania, takich jak rejestrowanie błędów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<span data-ttu-id="fe3a9-130"><xref:System.ServiceModel.Dispatcher.IErrorHandler> i [rozszerzanie kontroli obsługi i raportowania błędów](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="fe3a9-130"> <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="fe3a9-131">Zdarzenia ServiceHost</span><span class="sxs-lookup"><span data-stu-id="fe3a9-131">ServiceHost Events</span></span>  
 <span data-ttu-id="fe3a9-132"><xref:System.ServiceModel.ServiceHost> Klasa usług hostów i definiuje kilka zdarzeń, które mogą być potrzebne do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="fe3a9-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="fe3a9-133">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fe3a9-133">For example:</span></span>  
  
1.  <!--zz <xref:System.ServiceModel.ServiceHost.Faulted>-->  `System.ServiceModel.ServiceHost.Faulted`
  
2. <!--zz  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  --> `System.ServiceModel.ServiceHost.UnknownMessageReceived`
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="fe3a9-134"><xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="fe3a9-134"> <xref:System.ServiceModel.ServiceHost></span></span>
