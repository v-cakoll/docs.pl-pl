---
title: "Element formatujący operacji i selektor operacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0e2dbd255a1fbadbd5dd4cd7e676b75e659fe2a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="477df-102">Element formatujący operacji i selektor operacji</span><span class="sxs-lookup"><span data-stu-id="477df-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="477df-103">W przykładzie pokazano, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] punkty rozszerzeń może służyć do Zezwalaj komunikat danych w innym formacie z co [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oczekuje.</span><span class="sxs-lookup"><span data-stu-id="477df-103">This sample demonstrates how [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] extensibility points can be used to allow message data in a different format from what [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects.</span></span> <span data-ttu-id="477df-104">Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] elementy formatujące oczekiwane parametry metody do uwzględnienia w obszarze `soap:body` elementu.</span><span class="sxs-lookup"><span data-stu-id="477df-104">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="477df-105">Przykład obejmuje implementowania niestandardowych operacji programu formatującego, zamiast tego analizuje dane parametru ciągu zapytania HTTP GET, który wywołuje metody przy użyciu tych danych.</span><span class="sxs-lookup"><span data-stu-id="477df-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="477df-106">Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="477df-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="477df-107">Go przedstawiono sposób dodawania, odejmowania wielokrotnie i dzielenia wiadomości, można zmienić użyć żądania HTTP GET dla żądań klienta do serwera i HTTP POST z POX wiadomości odpowiedzi serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="477df-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="477df-108">Aby to zrobić, próbki zapewnia następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="477df-108">To do so, the sample provides the following:</span></span>  
  
-   <span data-ttu-id="477df-109">`QueryStringFormatter`, które implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> i <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> dla klienta i serwera, odpowiednio i przetwarza dane w ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="477df-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
-   <span data-ttu-id="477df-110">`UriOperationSelector`, które implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serwerze do wykonywania operacji wysyłki na podstawie nazwy operacji w żądanie GET.</span><span class="sxs-lookup"><span data-stu-id="477df-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
-   <span data-ttu-id="477df-111">`EnableHttpGetRequestsBehavior`punkt końcowy zachowanie (i odpowiedniej konfiguracji), która dodaje selektor operacji niezbędne do środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="477df-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
-   <span data-ttu-id="477df-112">Pokazuje, jak można wstawić nowej programu formatującego operacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="477df-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
-   <span data-ttu-id="477df-113">W tym przykładzie zarówno klient, jak i usługi są aplikacje konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="477df-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="477df-114">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="477df-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="477df-115">Podstawowe pojęcia</span><span class="sxs-lookup"><span data-stu-id="477df-115">Key Concepts</span></span>  
 <span data-ttu-id="477df-116">`QueryStringFormatter`Programu formatującego operacji jest składnikiem w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odpowiada do konwertowania wiadomości na tablicę obiektów parametru i tablicę obiektów parametru do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="477df-116">`QueryStringFormatter` - The operation formatter is the component in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="477df-117">Ta próba polega na kliencie przy użyciu <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interfejsu i na serwerze z <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="477df-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="477df-118">Te interfejsy umożliwiają użytkownikom uzyskiwanie komunikatów żądań i odpowiedzi z `Serialize` i `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="477df-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="477df-119">W tym przykładzie `QueryStringFormatter` implementuje obu tych interfejsów i jest zaimplementowana na kliencie i serwerze.</span><span class="sxs-lookup"><span data-stu-id="477df-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="477df-120">Żądanie:</span><span class="sxs-lookup"><span data-stu-id="477df-120">Request:</span></span>  
  
-   <span data-ttu-id="477df-121">W przykładzie użyto <xref:System.ComponentModel.TypeConverter> klasy w celu przekonwertowania danych parametru w komunikacie żądania do i z ciągów.</span><span class="sxs-lookup"><span data-stu-id="477df-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="477df-122">Jeśli <xref:System.ComponentModel.TypeConverter> nie jest dostępny dla określonego typu, program formatujący próbki zwraca wyjątek.</span><span class="sxs-lookup"><span data-stu-id="477df-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
-   <span data-ttu-id="477df-123">W `IClientMessageFormatter.SerializeRequest` metoda na kliencie, program formatujący tworzy identyfikator URI odpowiedni adres i dołącza nazwy operacji sufiks.</span><span class="sxs-lookup"><span data-stu-id="477df-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="477df-124">Ta nazwa jest używana do wysłania do odpowiednich operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="477df-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="477df-125">Następnie pobiera tablicę obiektów parametru i serializuje dane parametru ciągu zapytania identyfikatora URI przy użyciu nazwy parametrów i wartości przekonwertowane przez <xref:System.ComponentModel.TypeConverter> klasy.</span><span class="sxs-lookup"><span data-stu-id="477df-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="477df-126"><xref:System.ServiceModel.Channels.MessageHeaders.To%2A> i <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> właściwości są następnie ustaw ten identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="477df-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="477df-127"><xref:System.ServiceModel.Channels.MessageProperties>jest dostępny za pośrednictwem <xref:System.ServiceModel.Channels.Message.Properties%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="477df-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
-   <span data-ttu-id="477df-128">W `IDispatchMessageFormatter.DeserializeRequest` metoda na serwerze, program formatujący pobiera `Via` URI we właściwościach komunikatu żądania przychodzące.</span><span class="sxs-lookup"><span data-stu-id="477df-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="477df-129">Analizuje pary nazwa wartość w ciągu zapytania identyfikatora URI do nazwy i wartości parametrów, a używa nazwy parametrów i wartości do wypełnienia Tablica parametrów przekazana do metody.</span><span class="sxs-lookup"><span data-stu-id="477df-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="477df-130">Należy pamiętać, że już przeprowadzono operacji wysyłania, więc sufiks nazwy operacji jest ignorowana w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="477df-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="477df-131">Odpowiedź:</span><span class="sxs-lookup"><span data-stu-id="477df-131">Response:</span></span>  
  
-   <span data-ttu-id="477df-132">W tym przykładzie HTTP GET jest używany tylko dla żądania.</span><span class="sxs-lookup"><span data-stu-id="477df-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="477df-133">Program formatujący deleguje wysyłanie odpowiedzi na oryginalny element formatujący, który będzie używany do generowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="477df-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="477df-134">Jest jednym z celów tego przykładu pokazanie implementowania delegujące formatującego.</span><span class="sxs-lookup"><span data-stu-id="477df-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="477df-135">Klasa UriPathSuffixOperationSelector</span><span class="sxs-lookup"><span data-stu-id="477df-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="477df-136"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Interfejs umożliwia użytkownikom wdrożenia własnej logiki dla operacji, które powinny wysłać danego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="477df-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="477df-137">W tym przykładzie `UriPathSuffixOperationSelector` musi zostać wdrożone na serwerze, aby wybrać odpowiednie działania, ponieważ nazwa operacji znajduje się identyfikator URI GET protokołu HTTP zamiast nagłówka action w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="477df-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="477df-138">Aby umożliwić działanie tylko bez uwzględniania wielkości liter nazwy skonfigurowano próbki.</span><span class="sxs-lookup"><span data-stu-id="477df-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="477df-139">`SelectOperation` Metoda pobiera komunikat przychodzący i wyszukuje `Via` identyfikatora URI w jego właściwościach komunikatu.</span><span class="sxs-lookup"><span data-stu-id="477df-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="477df-140">Go wyodrębnia sufiks nazwy operacji z identyfikatora URI, odwołuje się do wewnętrznej tabeli można uzyskać nazwy operacji, które wiadomości powinna być wysyłane do i zwraca nazwę tej operacji.</span><span class="sxs-lookup"><span data-stu-id="477df-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="477df-141">Klasa EnableHttpGetRequestsBehavior</span><span class="sxs-lookup"><span data-stu-id="477df-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="477df-142">`UriPathSuffixOperationSelector` Składnika można skonfigurować programowo lub za pośrednictwem zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="477df-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="477df-143">Implementuje próbki `EnableHttpGetRequestsBehavior` zachowanie, które jest określone w pliku konfiguracyjnym aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="477df-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="477df-144">Na serwerze:</span><span class="sxs-lookup"><span data-stu-id="477df-144">On the server:</span></span>  
  
 <span data-ttu-id="477df-145"><xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Ustawiono <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementacji.</span><span class="sxs-lookup"><span data-stu-id="477df-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="477df-146">Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa filtra dokładnie dopasowanego adresu.</span><span class="sxs-lookup"><span data-stu-id="477df-146">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses an exact-match address filter.</span></span> <span data-ttu-id="477df-147">Identyfikator URI w komunikacie przychodzącym zawiera sufiks nazwy operacji następuje zawierający dane parametru ciągu zapytania, dzięki zachowania punktu końcowego również zmiany filtr adresów jako prefiksu pasuje do filtru.</span><span class="sxs-lookup"><span data-stu-id="477df-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="477df-148">Używa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> w tym celu.</span><span class="sxs-lookup"><span data-stu-id="477df-148">It uses the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="477df-149">Instalowanie formatujących operacji</span><span class="sxs-lookup"><span data-stu-id="477df-149">Installing operation formatters</span></span>  
 <span data-ttu-id="477df-150">Operacja zachowania, określające elementy formatujące są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="477df-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="477df-151">Domyślnie dla każdej operacji tworzenia programu formatującego niezbędnych operacji zawsze zaimplementowano jednego takiego zachowania.</span><span class="sxs-lookup"><span data-stu-id="477df-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="477df-152">Jednak te zachowania wyglądać kolejna operacja zachowanie; nie są identyfikowane przez inny atrybut.</span><span class="sxs-lookup"><span data-stu-id="477df-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="477df-153">Aby zainstalować zachowanie zastąpienia, implementacja musi wyglądać dla określonego programu formatującego zachowania, które są instalowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modułu ładującego typu domyślnie i zastąp go lub dodać zachowanie zgodne do uruchomienia po zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="477df-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="477df-154">Te zachowania elementy formatujące operacji można skonfigurować programowo przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> lub określając zachowanie operacji, która jest wykonywana po domyślny.</span><span class="sxs-lookup"><span data-stu-id="477df-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="477df-155">Jednak go nie można łatwo można skonfigurować przy zachowanie punktu końcowego (i w związku z tym w konfiguracji) ponieważ modelu zachowanie nie zezwala na zachowanie zastąpić innych zachowań lub modyfikację drzewa opis.</span><span class="sxs-lookup"><span data-stu-id="477df-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="477df-156">Na komputerze klienckim:</span><span class="sxs-lookup"><span data-stu-id="477df-156">On the client:</span></span>  
  
 <span data-ttu-id="477df-157"><xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Wdrożenia musi być implementowana tak, aby można przekonwertować żądania na żądania HTTP GET i delegować do oryginalnego program formatujący dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="477df-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="477df-158">Jest to realizowane przez wywołanie `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika.</span><span class="sxs-lookup"><span data-stu-id="477df-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="477df-159">Należy to zrobić przed wywołaniem `CreateChannel`.</span><span class="sxs-lookup"><span data-stu-id="477df-159">This must be done before calling `CreateChannel`.</span></span>  
  
```  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 <span data-ttu-id="477df-160">Na serwerze:</span><span class="sxs-lookup"><span data-stu-id="477df-160">On the server:</span></span>  
  
-   <span data-ttu-id="477df-161"><xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Interfejs musi zostać wdrożone, dzięki czemu może odczytywać żądania HTTP GET i delegować do oryginalnego elementu formatującego do zapisywania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="477df-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="477df-162">Polega to na takie same wywoływania `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metody pomocnika jako klient (zobacz poprzedni przykład kodu).</span><span class="sxs-lookup"><span data-stu-id="477df-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
-   <span data-ttu-id="477df-163">Należy to zrobić przed <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="477df-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="477df-164">W tym przykładzie zostanie przedstawiony sposób program formatujący jest modyfikowany ręcznie przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="477df-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="477df-165">Innym sposobem uzyskania samo jest wyprowadzenia klasy z <xref:System.ServiceModel.ServiceHost> dzięki temu wywołań `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` przed otwarciem (Zobacz hosting dokumentacja i przykłady przykłady).</span><span class="sxs-lookup"><span data-stu-id="477df-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="477df-166">Środowisko użytkownika</span><span class="sxs-lookup"><span data-stu-id="477df-166">User experience</span></span>  
 <span data-ttu-id="477df-167">Na serwerze:</span><span class="sxs-lookup"><span data-stu-id="477df-167">On the server:</span></span>  
  
-   <span data-ttu-id="477df-168">Serwer `ICalculator` implementacji nie trzeba zmieniać.</span><span class="sxs-lookup"><span data-stu-id="477df-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="477df-169">App.config dla usługi, należy użyć niestandardowego powiązania POX, która ustawia `messageVersion` atrybutu `textMessageEncoding` elementu `None`.</span><span class="sxs-lookup"><span data-stu-id="477df-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   <span data-ttu-id="477df-170">App.config dla usługi również określić niestandardowe `EnableHttpGetRequestsBehavior` przez dodanie go do sekcji rozszerzenia zachowania i przy jego użyciu.</span><span class="sxs-lookup"><span data-stu-id="477df-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add   
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
-   <span data-ttu-id="477df-171">Dodaj elementy formatujące operacji przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="477df-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="477df-172">Na komputerze klienckim:</span><span class="sxs-lookup"><span data-stu-id="477df-172">On the client:</span></span>  
  
-   <span data-ttu-id="477df-173">Implementacja klienta nie trzeba zmieniać.</span><span class="sxs-lookup"><span data-stu-id="477df-173">The client implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="477df-174">App.config dla klienta, należy użyć niestandardowego powiązania POX, która ustawia `messageVersion` atrybutu `textMessageEncoding` elementu `None`.</span><span class="sxs-lookup"><span data-stu-id="477df-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="477df-175">Różnica jednego z usługi jest klienta należy włączyć, ręcznego adresowania, tak aby wychodzących na adres może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="477df-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
-   <span data-ttu-id="477df-176">App.config dla klienta należy określić niestandardowy tego samego `EnableHttpGetRequestsBehavior` jako serwer.</span><span class="sxs-lookup"><span data-stu-id="477df-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
-   <span data-ttu-id="477df-177">Dodaj elementy formatujące operacji przed wywołaniem <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span><span class="sxs-lookup"><span data-stu-id="477df-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="477df-178">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="477df-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="477df-179">Wszystkie cztery operacje (Dodawanie, odjąć mnożenia i dzielenia) musi się zakończyć powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="477df-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="477df-180">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="477df-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="477df-181">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="477df-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="477df-182">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="477df-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="477df-183">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="477df-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="477df-184">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="477df-184">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="477df-185">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="477df-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="477df-186">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="477df-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="477df-187">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="477df-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="477df-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="477df-188">See Also</span></span>
