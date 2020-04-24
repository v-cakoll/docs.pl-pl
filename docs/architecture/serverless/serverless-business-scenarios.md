---
title: Przykładowe scenariusze biznesowe i przypadki użycia dla aplikacji bezserwerowych
description: Dowiedz się bezserwerowo, korzystając z praktycznego podejścia, uzyskując dostęp do próbek, które przedziały od przetwarzania obrazów do obsługi urządzeń przenośnych i potoków ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 5c2ee70b86fbc9a54d2a532eaa3d7509f23825df
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135662"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="78084-103">Scenariusze biznesowe i przypadki użycia bez korzystania z serwera</span><span class="sxs-lookup"><span data-stu-id="78084-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="78084-104">Istnieje wiele przypadków użycia i scenariuszy dotyczących aplikacji bezserwerowych.</span><span class="sxs-lookup"><span data-stu-id="78084-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="78084-105">Ten rozdział zawiera przykłady ilustrujące różne scenariusze.</span><span class="sxs-lookup"><span data-stu-id="78084-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="78084-106">Scenariusze obejmują linki do powiązanej dokumentacji i repozytoriów kodu publicznego.</span><span class="sxs-lookup"><span data-stu-id="78084-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="78084-107">Przykłady w tym rozdziale umożliwiają rozpoczęcie pracy nad tworzeniem i implementowaniem rozwiązań bezserwerowych.</span><span class="sxs-lookup"><span data-stu-id="78084-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="big-data-processing"></a><span data-ttu-id="78084-108">Przetwarzanie danych Big Data</span><span class="sxs-lookup"><span data-stu-id="78084-108">Big data processing</span></span>

![Mapa/Zmniejsz diagram](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

<span data-ttu-id="78084-110">Ten przykład używa bezserwerowego, aby wykonać operację mapowania/zmniejszania dla zestawu danych Big Data.</span><span class="sxs-lookup"><span data-stu-id="78084-110">This example uses serverless to do a map/reduce operation on a big data set.</span></span> <span data-ttu-id="78084-111">Określa średnią prędkość w przypadku żółtej podróży w Nowym Jorku na dzień w 2017.</span><span class="sxs-lookup"><span data-stu-id="78084-111">It determines the average speed of New York Yellow taxi trips per day in 2017.</span></span>

[<span data-ttu-id="78084-112">Przetwarzanie danych Big Data: bezserwerowe MapReduce na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="78084-112">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a><span data-ttu-id="78084-113">Tworzenie aplikacji bezserwerowych: ćwiczenia praktyczne</span><span class="sxs-lookup"><span data-stu-id="78084-113">Create serverless applications: hands-on lab</span></span>

<span data-ttu-id="78084-114">Dowiedz się, jak używać funkcji do wykonywania logiki po stronie serwera i tworzenia architektur bezserwerowych.</span><span class="sxs-lookup"><span data-stu-id="78084-114">Learn how to use functions to execute server-side logic and build serverless architectures.</span></span>

- <span data-ttu-id="78084-115">Wybór najlepszej usługi platformy Azure dla Twojej firmy</span><span class="sxs-lookup"><span data-stu-id="78084-115">Choosing the best Azure service for your business</span></span>
- <span data-ttu-id="78084-116">Tworzenie Azure Functions</span><span class="sxs-lookup"><span data-stu-id="78084-116">Creating Azure Functions</span></span>
- <span data-ttu-id="78084-117">Korzystanie z wyzwalaczy</span><span class="sxs-lookup"><span data-stu-id="78084-117">Using triggers</span></span>
- <span data-ttu-id="78084-118">Funkcje łańcucha</span><span class="sxs-lookup"><span data-stu-id="78084-118">Chaining functions</span></span>
- <span data-ttu-id="78084-119">Długotrwałe przepływy pracy</span><span class="sxs-lookup"><span data-stu-id="78084-119">Long-running workflows</span></span>
- <span data-ttu-id="78084-120">Monitorowanie</span><span class="sxs-lookup"><span data-stu-id="78084-120">Monitoring</span></span>
- <span data-ttu-id="78084-121">Programowanie, testowanie i wdrażanie</span><span class="sxs-lookup"><span data-stu-id="78084-121">Development, testing, and deployment</span></span>

[<span data-ttu-id="78084-122">Tworzenie aplikacji bezserwerowych</span><span class="sxs-lookup"><span data-stu-id="78084-122">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a><span data-ttu-id="78084-123">Przeglądy klientów</span><span class="sxs-lookup"><span data-stu-id="78084-123">Customer reviews</span></span>

<span data-ttu-id="78084-124">Ten przykład przedstawia nowe narzędzia Azure Functions dla bibliotek klas C# w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78084-124">This sample showcases the new Azure Functions tooling for C# Class Libraries in Visual Studio.</span></span> <span data-ttu-id="78084-125">Utwórz witrynę sieci Web, w której klienci przesyłają przeglądy produktów, które są przechowywane w obiektach Blob usługi Azure Storage i CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="78084-125">Create a website where customers submit product reviews that are stored in Azure storage blobs and CosmosDB.</span></span> <span data-ttu-id="78084-126">Dodaj funkcję platformy Azure, aby przeprowadzać automatyczne moderowanie przeglądów klientów przy użyciu usługi Azure Cognitive Services.</span><span class="sxs-lookup"><span data-stu-id="78084-126">Add an Azure Function to perform automated moderation of the customer reviews using Azure Cognitive Services.</span></span> <span data-ttu-id="78084-127">Użyj kolejki usługi Azure Storage, aby oddzielić witrynę internetową od funkcji.</span><span class="sxs-lookup"><span data-stu-id="78084-127">Use an Azure storage queue to decouple the website from the function.</span></span>

[<span data-ttu-id="78084-128">Aplikacja przegląda klienta z Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="78084-128">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a><span data-ttu-id="78084-129">Obsługa obrazów platformy Docker Linux</span><span class="sxs-lookup"><span data-stu-id="78084-129">Docker Linux image support</span></span>

<span data-ttu-id="78084-130">Ten przykład pokazuje, jak utworzyć `Dockerfile` i uruchomić Azure Functions w kontenerze Docker systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="78084-130">This sample demonstrates how to create a `Dockerfile` to build and run Azure Functions on a Linux Docker container.</span></span>

[<span data-ttu-id="78084-131">Azure Functions w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="78084-131">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a><span data-ttu-id="78084-132">Przetwarzanie i sprawdzanie poprawności plików</span><span class="sxs-lookup"><span data-stu-id="78084-132">File processing and validation</span></span>

<span data-ttu-id="78084-133">Ten przykład analizuje zestaw plików CSV od hipotetycznych klientów.</span><span class="sxs-lookup"><span data-stu-id="78084-133">This example parses a set of CSV files from hypothetical customers.</span></span> <span data-ttu-id="78084-134">Gwarantuje to, że wszystkie pliki wymagane przez klienta "Batch" są gotowe, a następnie sprawdza poprawność struktury każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="78084-134">It ensures that all files required for a customer "batch" are ready, then validates the structure of each file.</span></span> <span data-ttu-id="78084-135">Różne rozwiązania są prezentowane przy użyciu Azure Functions, Logic Apps i Durable Functions.</span><span class="sxs-lookup"><span data-stu-id="78084-135">Different solutions are presented using Azure Functions, Logic Apps, and Durable Functions.</span></span>

[<span data-ttu-id="78084-136">Przetwarzanie i sprawdzanie poprawności plików przy użyciu Azure Functions, Logic Apps i Durable Functions</span><span class="sxs-lookup"><span data-stu-id="78084-136">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a><span data-ttu-id="78084-137">Wizualizacja danych gry</span><span class="sxs-lookup"><span data-stu-id="78084-137">Game data visualization</span></span>

![Telemetria gier](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

<span data-ttu-id="78084-139">Przykład sposobu, w jaki deweloper może zaimplementować rozwiązanie wizualizacji danych w edytorze dla swojej gry.</span><span class="sxs-lookup"><span data-stu-id="78084-139">An example of how a developer could implement an in-editor data visualization solution for their game.</span></span> <span data-ttu-id="78084-140">W rzeczywistości wtyczka aparatu Unreal 4 i wtyczka aparatu Unity zostały opracowane przy użyciu tego przykładu jako zaplecza.</span><span class="sxs-lookup"><span data-stu-id="78084-140">In fact, an Unreal Engine 4 Plugin and Unity Plugin were developed using this sample as its backend.</span></span> <span data-ttu-id="78084-141">Składnik usługi to niezależny od aparatu gry.</span><span class="sxs-lookup"><span data-stu-id="78084-141">The service component is game engine agnostic.</span></span>

[<span data-ttu-id="78084-142">Wizualizacja telemetrii gier w edytorze</span><span class="sxs-lookup"><span data-stu-id="78084-142">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a><span data-ttu-id="78084-143">GraphQL</span><span class="sxs-lookup"><span data-stu-id="78084-143">GraphQL</span></span>

<span data-ttu-id="78084-144">Utwórz bezserwerową funkcję, która uwidacznia interfejs API GraphQL.</span><span class="sxs-lookup"><span data-stu-id="78084-144">Create a serverless function that exposes a GraphQL API.</span></span>

[<span data-ttu-id="78084-145">Funkcje bezserwerowe dla GraphQL</span><span class="sxs-lookup"><span data-stu-id="78084-145">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a><span data-ttu-id="78084-146">Niezawodny przekaźnik graniczny Internet rzeczy (IoT)</span><span class="sxs-lookup"><span data-stu-id="78084-146">Internet of Things (IoT) reliable edge relay</span></span>

![Architektura IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

<span data-ttu-id="78084-148">Ten przykład implementuje nowy protokół komunikacyjny, aby umożliwić niezawodne komunikacji nadrzędnej z urządzeń IoT.</span><span class="sxs-lookup"><span data-stu-id="78084-148">This sample implements a new communication protocol to enable reliable upstream communication from IoT devices.</span></span> <span data-ttu-id="78084-149">Automatyzuje wykrywanie przerw w danych i wypełnianie.</span><span class="sxs-lookup"><span data-stu-id="78084-149">It automates data gap detection and backfill.</span></span>

[<span data-ttu-id="78084-150">Niezawodny przekaźnik IoT</span><span class="sxs-lookup"><span data-stu-id="78084-150">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a><span data-ttu-id="78084-151">Architektura referencyjna mikrousług</span><span class="sxs-lookup"><span data-stu-id="78084-151">Microservices reference architecture</span></span>

![Architektura referencyjna](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

<span data-ttu-id="78084-153">Architektura referencyjna, która przeprowadzi Cię przez proces podejmowania decyzji związanych z projektowaniem, tworzeniem i dostarczaniem RideShare przez aplikację Relecloud (fikcyjnej firmy).</span><span class="sxs-lookup"><span data-stu-id="78084-153">A reference architecture that walks you through the decision-making process involved in designing, developing, and delivering the Rideshare by Relecloud application (a fictitious company).</span></span> <span data-ttu-id="78084-154">Zawiera instrukcje praktyczne dotyczące konfigurowania i wdrażania wszystkich składników architektury.</span><span class="sxs-lookup"><span data-stu-id="78084-154">It includes hands-on instructions for configuring and deploying all of the architecture's components.</span></span>

[<span data-ttu-id="78084-155">Architektura referencyjna mikrousług bezserwerowych</span><span class="sxs-lookup"><span data-stu-id="78084-155">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a><span data-ttu-id="78084-156">Migrowanie aplikacji konsolowych do bezserwerowego</span><span class="sxs-lookup"><span data-stu-id="78084-156">Migrate console apps to serverless</span></span>

<span data-ttu-id="78084-157">Ten przykład to funkcja generyczna (`.csx` plik), która może służyć do konwersji dowolnej aplikacji konsolowej do usługi sieci Web HTTP w Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="78084-157">This sample is a generic function (`.csx` file) that can be used to convert any console application to an HTTP web service in Azure Functions.</span></span> <span data-ttu-id="78084-158">Wystarczy edytować plik konfiguracji i określić, jakie parametry wejściowe będą przekazane jako argumenty do `.exe`.</span><span class="sxs-lookup"><span data-stu-id="78084-158">All you have to do is edit a configuration file and specify what input parameters will be passed as arguments to the `.exe`.</span></span>

[<span data-ttu-id="78084-159">Uruchom aplikacje konsolowe na Azure Functions</span><span class="sxs-lookup"><span data-stu-id="78084-159">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a><span data-ttu-id="78084-160">Bezserwerowy dla urządzeń przenośnych</span><span class="sxs-lookup"><span data-stu-id="78084-160">Serverless for mobile</span></span>

<span data-ttu-id="78084-161">Azure Functions można łatwo zaimplementować i zachować i uzyskać dostęp za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="78084-161">Azure Functions are easy to implement and maintain, and accessible through HTTP.</span></span> <span data-ttu-id="78084-162">Są one doskonałym sposobem implementacji interfejsu API dla aplikacji mobilnej.</span><span class="sxs-lookup"><span data-stu-id="78084-162">They are a great way to implement an API for a mobile application.</span></span> <span data-ttu-id="78084-163">Firma Microsoft oferuje wspaniałe narzędzia dla wielu platform dla systemów iOS, Android i Windows za pomocą platformy Xamarin.</span><span class="sxs-lookup"><span data-stu-id="78084-163">Microsoft offers great cross-platform tools for iOS, Android, and Windows with Xamarin.</span></span> <span data-ttu-id="78084-164">W związku z tym platformy Xamarin i Azure Functions działają doskonale.</span><span class="sxs-lookup"><span data-stu-id="78084-164">As such, Xamarin and Azure Functions are working great together.</span></span> <span data-ttu-id="78084-165">W tym artykule pokazano, jak wdrożyć funkcję platformy Azure w portalu internetowym platformy Azure lub w programie Visual Studio w pierwszej kolejności oraz utworzyć klienta międzyplatformowego za pomocą interfejsu Xamarin. Forms działającego w systemach Android, iOS i Windows.</span><span class="sxs-lookup"><span data-stu-id="78084-165">This article shows how to implement an Azure Function in the Azure Web Portal or in Visual Studio at first, and build a cross-platform client with Xamarin.Forms, running on Android, iOS, and Windows.</span></span>

[<span data-ttu-id="78084-166">Implementowanie prostej funkcji platformy Azure przy użyciu klienta Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="78084-166">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a><span data-ttu-id="78084-167">Obsługa komunikatów bezserwerowych</span><span class="sxs-lookup"><span data-stu-id="78084-167">Serverless messaging</span></span>

<span data-ttu-id="78084-168">Ten przykład pokazuje, jak użyć wzorca wentylatorów Durable Functions "do załadowania dowolnej liczby komunikatów na dowolną liczbę sesji/partycji.</span><span class="sxs-lookup"><span data-stu-id="78084-168">This sample shows how to utilize Durable Functions' fan out pattern to load an arbitrary number of messages across any number of sessions/partitions.</span></span> <span data-ttu-id="78084-169">Jest ona przeznaczona dla kolejek Service Bus, Event Hubs lub magazynu.</span><span class="sxs-lookup"><span data-stu-id="78084-169">It targets Service Bus, Event Hubs, or Storage Queues.</span></span> <span data-ttu-id="78084-170">Przykład dodaje również możliwość korzystania z tych komunikatów z inną funkcją platformy Azure i ładowania powstających danych o chronometrażu w innym centrum zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="78084-170">The sample also adds the ability to consume those messages with another Azure Function and load the resulting timing data in to another Event Hub.</span></span> <span data-ttu-id="78084-171">Dane są następnie pozyskiwane na usługi analizy, takie jak Azure Eksplorator danych.</span><span class="sxs-lookup"><span data-stu-id="78084-171">The data is then ingested into analytics services like Azure Data Explorer.</span></span>

[<span data-ttu-id="78084-172">Tworzenie i używanie komunikatów za pomocą kolejek Service Bus, Event Hubs i magazynu przy użyciu Azure Functions</span><span class="sxs-lookup"><span data-stu-id="78084-172">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a><span data-ttu-id="78084-173">Zalecane zasoby</span><span class="sxs-lookup"><span data-stu-id="78084-173">Recommended resources</span></span>

- [<span data-ttu-id="78084-174">Azure Functions w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="78084-174">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [<span data-ttu-id="78084-175">Przetwarzanie danych Big Data: bezserwerowe MapReduce na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="78084-175">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [<span data-ttu-id="78084-176">Tworzenie aplikacji bezserwerowych</span><span class="sxs-lookup"><span data-stu-id="78084-176">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [<span data-ttu-id="78084-177">Aplikacja przegląda klienta z Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="78084-177">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [<span data-ttu-id="78084-178">Przetwarzanie i sprawdzanie poprawności plików przy użyciu Azure Functions, Logic Apps i Durable Functions</span><span class="sxs-lookup"><span data-stu-id="78084-178">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [<span data-ttu-id="78084-179">Implementowanie prostej funkcji platformy Azure przy użyciu klienta Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="78084-179">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [<span data-ttu-id="78084-180">Wizualizacja telemetrii gier w edytorze</span><span class="sxs-lookup"><span data-stu-id="78084-180">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [<span data-ttu-id="78084-181">Niezawodny przekaźnik IoT</span><span class="sxs-lookup"><span data-stu-id="78084-181">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [<span data-ttu-id="78084-182">Tworzenie i używanie komunikatów za pomocą kolejek Service Bus, Event Hubs i magazynu przy użyciu Azure Functions</span><span class="sxs-lookup"><span data-stu-id="78084-182">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [<span data-ttu-id="78084-183">Uruchom aplikacje konsolowe na Azure Functions</span><span class="sxs-lookup"><span data-stu-id="78084-183">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [<span data-ttu-id="78084-184">Funkcje bezserwerowe dla GraphQL</span><span class="sxs-lookup"><span data-stu-id="78084-184">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [<span data-ttu-id="78084-185">Architektura referencyjna mikrousług bezserwerowych</span><span class="sxs-lookup"><span data-stu-id="78084-185">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
><span data-ttu-id="78084-186">[Poprzedni](orchestration-patterns.md)
>[Następny](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="78084-186">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
