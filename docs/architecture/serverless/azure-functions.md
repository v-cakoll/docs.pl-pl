---
title: Azure Functions — aplikacje bezserwerowe
description: Usługa Azure Functions zapewnia bezserwerowe funkcje w wielu językach (C#, JavaScript, Java) i na platformach, aby zapewnić błyskawiczny kod skali oparty na zdarzeniach.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 2dee60e3635be94a55ee26a7f04942bc59cb8dec
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135727"
---
# <a name="azure-functions"></a><span data-ttu-id="ec2a2-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ec2a2-103">Azure Functions</span></span>

<span data-ttu-id="ec2a2-104">Usługa Azure Functions zapewnia środowisko obliczeniowe bezserwerowe.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="ec2a2-105">Funkcja jest wywoływana przez *wyzwalacz* (taki jak dostęp do punktu końcowego http lub Timer) i wykonuje blok kodu lub logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="ec2a2-106">Funkcje obsługują także wyspecjalizowane *powiązania* , które łączą się z zasobami, takimi jak magazyn i kolejki.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logo usługi Azure Functions](./media/azure-functions-logo.png)

<span data-ttu-id="ec2a2-108">Bieżąca wersja środowiska uruchomieniowego 3,0 obsługuje Międzyplatformowe aplikacje platformy .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-108">The current runtime version 3.0 supports cross-platform .NET Core 3.1 applications.</span></span> <span data-ttu-id="ec2a2-109">Obsługiwane są dodatkowe języki, takie jak JavaScript, F # i Java.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-109">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="ec2a2-110">Funkcje utworzone w portalu zawierają rozbudowaną składnię skryptów.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-110">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="ec2a2-111">Funkcje utworzone jako projekty autonomiczne mogą być wdrażane z pełną obsługą platformy i możliwościami.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-111">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="ec2a2-112">Aby uzyskać więcej informacji, zobacz [dokumentację Azure Functions](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-112">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="ec2a2-113">Obsługa języków programowania</span><span class="sxs-lookup"><span data-stu-id="ec2a2-113">Programming language support</span></span>

<span data-ttu-id="ec2a2-114">Poniższe języki są obsługiwane ogólnie dostępnym.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-114">The following languages are all supported in general availability (GA).</span></span>

|<span data-ttu-id="ec2a2-115">Język</span><span class="sxs-lookup"><span data-stu-id="ec2a2-115">Language</span></span>      |<span data-ttu-id="ec2a2-116">Obsługiwane środowiska uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ec2a2-116">Supported runtimes</span></span>|
|--------------|------------------|
|<span data-ttu-id="ec2a2-117">**S #**</span><span class="sxs-lookup"><span data-stu-id="ec2a2-117">**C#**</span></span>        |<span data-ttu-id="ec2a2-118">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ec2a2-118">.NET Core 3.1</span></span>     |
|<span data-ttu-id="ec2a2-119">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="ec2a2-119">**JavaScript**</span></span>|<span data-ttu-id="ec2a2-120">Node 10 & 12</span><span class="sxs-lookup"><span data-stu-id="ec2a2-120">Node 10 & 12</span></span>      |
|<span data-ttu-id="ec2a2-121">**F#**</span><span class="sxs-lookup"><span data-stu-id="ec2a2-121">**F#**</span></span>        |<span data-ttu-id="ec2a2-122">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ec2a2-122">.NET Core 3.1</span></span>     |
|<span data-ttu-id="ec2a2-123">**Java**</span><span class="sxs-lookup"><span data-stu-id="ec2a2-123">**Java**</span></span>      |<span data-ttu-id="ec2a2-124">Java 8</span><span class="sxs-lookup"><span data-stu-id="ec2a2-124">Java 8</span></span>            |
|<span data-ttu-id="ec2a2-125">**Python**</span><span class="sxs-lookup"><span data-stu-id="ec2a2-125">**Python**</span></span>    |<span data-ttu-id="ec2a2-126">Python 3,6, 3,7, & 3,8</span><span class="sxs-lookup"><span data-stu-id="ec2a2-126">Python 3.6, 3.7, & 3.8</span></span>|
|<span data-ttu-id="ec2a2-127">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="ec2a2-127">**TypeScript**</span></span>|<span data-ttu-id="ec2a2-128">Node 10 & 12 (za pośrednictwem języka JavaScript)</span><span class="sxs-lookup"><span data-stu-id="ec2a2-128">Node 10 & 12 (via JavaScript)</span></span>|
|<span data-ttu-id="ec2a2-129">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="ec2a2-129">**PowerShell**</span></span>|<span data-ttu-id="ec2a2-130">Program PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="ec2a2-130">PowerShell Core 6</span></span>|

<span data-ttu-id="ec2a2-131">Więcej informacji, zobacz [Obsługiwane języki](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-131">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="ec2a2-132">Plany usługi App Service</span><span class="sxs-lookup"><span data-stu-id="ec2a2-132">App service plans</span></span>

<span data-ttu-id="ec2a2-133">Funkcje są obsługiwane przez *plan usługi App Service*.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-133">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="ec2a2-134">Plan definiuje zasoby używane przez aplikację Functions.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-134">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="ec2a2-135">Można przypisać plany do regionu, określić rozmiar i liczbę maszyn wirtualnych, które będą używane, i wybrać warstwę cenową.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-135">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="ec2a2-136">W przypadku prawdziwej metody bezserwerowej aplikacje funkcji mogą korzystać z planu **zużycia** .</span><span class="sxs-lookup"><span data-stu-id="ec2a2-136">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="ec2a2-137">Plan zużycia spowoduje automatyczne skalowanie zaplecza na podstawie obciążenia.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-137">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="ec2a2-138">Inną opcją hostingu dla aplikacji funkcji jest [Plan Premium](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-138">Another hosting option for function apps is the [Premium plan](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan).</span></span> <span data-ttu-id="ec2a2-139">Ten plan zapewnia wystąpienie "Always On", aby uniknąć zimnego uruchamiania, obsługuje zaawansowane funkcje, takie jak łączność z siecią wirtualną i działa na sprzęcie Premium.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-139">This plan provides an "always on" instance to avoid cold start, supports advanced features like VNet connectivity, and runs on premium hardware.</span></span>

<span data-ttu-id="ec2a2-140">Aby uzyskać więcej informacji, zobacz [plany usługi App Service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-140">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="ec2a2-141">Tworzenie pierwszej funkcji</span><span class="sxs-lookup"><span data-stu-id="ec2a2-141">Create your first function</span></span>

<span data-ttu-id="ec2a2-142">Istnieją trzy typowe sposoby tworzenia aplikacji funkcji.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-142">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="ec2a2-143">Funkcje skryptów w portalu.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-143">Script functions in the portal.</span></span>
- <span data-ttu-id="ec2a2-144">Tworzenie niezbędnych zasobów przy użyciu interfejsu wiersza polecenia platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-144">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="ec2a2-145">Twórz funkcje lokalnie przy użyciu ulubionego środowiska IDE i publikuj je na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-145">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="ec2a2-146">Aby uzyskać więcej informacji na temat tworzenia funkcji skryptowej w portalu, zobacz [Tworzenie pierwszej funkcji w Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-146">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="ec2a2-147">Aby skompilować z poziomu interfejsu wiersza polecenia platformy Azure, zobacz [Tworzenie pierwszej funkcji przy użyciu interfejsu wiersza polecenia platformy Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-147">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="ec2a2-148">Aby utworzyć funkcję z programu Visual Studio, zobacz [Tworzenie pierwszej funkcji przy użyciu programu Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-148">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="ec2a2-149">Omówienie wyzwalaczy i powiązań</span><span class="sxs-lookup"><span data-stu-id="ec2a2-149">Understand triggers and bindings</span></span>

<span data-ttu-id="ec2a2-150">Funkcje są wywoływane przez *wyzwalacz* i mogą mieć dokładnie jeden.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-150">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="ec2a2-151">Oprócz wywoływania funkcji, niektóre wyzwalacze również pełnią rolę powiązań.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-151">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="ec2a2-152">Oprócz wyzwalacza można również zdefiniować wiele powiązań.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-152">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="ec2a2-153">*Powiązania* zapewniają deklaratywny sposób łączenia danych z kodem.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-153">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="ec2a2-154">Mogą być przekazywane (dane wejściowe) lub odbierać dane (dane wyjściowe).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-154">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="ec2a2-155">Wyzwalacze i powiązania ułatwiają korzystanie z funkcji.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-155">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="ec2a2-156">Powiązania usuwają koszty ręcznego tworzenia połączeń bazy danych lub systemu plików.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-156">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="ec2a2-157">Wszystkie informacje dotyczące powiązań są zawarte w specjalnym pliku *Functions. JSON* dla skryptów lub zadeklarowane z atrybutami w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-157">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="ec2a2-158">Niektóre typowe wyzwalacze obejmują:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-158">Some common triggers include:</span></span>

- <span data-ttu-id="ec2a2-159">Blob Storage: wywołaj funkcję, gdy plik lub folder zostanie przekazany lub zmieniony w magazynie.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-159">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="ec2a2-160">HTTP: wywoływanie funkcji, takiej jak interfejs API REST.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-160">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="ec2a2-161">Kolejka: wywoływanie funkcji, gdy istnieją elementy w kolejce.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-161">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="ec2a2-162">Czasomierz: wywołaj funkcję na zwykłych erze.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-162">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="ec2a2-163">Przykłady powiązań obejmują:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-163">Examples of bindings include:</span></span>

- <span data-ttu-id="ec2a2-164">CosmosDB: łatwo Nawiązuj połączenie z bazą danych w celu załadowania lub zapisania plików.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-164">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="ec2a2-165">Table Storage: Pracuj z magazynem kluczy/wartości z aplikacji funkcji.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-165">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="ec2a2-166">Queue Storage: łatwo Pobieraj elementy z kolejki lub umieszczaj nowe elementy w kolejce.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-166">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="ec2a2-167">Poniższy przykładowy plik *Functions. JSON* definiuje wyzwalacz i powiązanie:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-167">The following example *functions.json* file defines a trigger and a binding:</span></span>

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

<span data-ttu-id="ec2a2-168">W tym przykładzie funkcja jest wyzwalana przez zmianę w magazynie obiektów BLOB w `images` kontenerze.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-168">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="ec2a2-169">Informacje dotyczące pliku są przesyłane, więc wyzwalacz działa również jako powiązanie.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-169">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="ec2a2-170">Istnieje inne powiązanie, aby umieścić informacje w kolejce o `images`nazwie.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-170">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="ec2a2-171">Oto skrypt języka C# dla funkcji:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-171">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="ec2a2-172">Przykładem jest prosta funkcja, która przyjmuje nazwę pliku, który został zmodyfikowany lub przekazany do usługi BLOB Storage, i umieszcza go w kolejce do późniejszego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-172">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="ec2a2-173">Aby zapoznać się z pełną listą wyzwalaczy i powiązań, zobacz temat [Azure Functions wyzwalacze i koncepcje powiązań](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-173">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ec2a2-174">[Poprzedni](azure-serverless-platform.md)
>[Następny](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="ec2a2-174">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
