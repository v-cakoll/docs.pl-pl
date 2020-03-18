---
title: Funkcje platformy Azure — aplikacje bezserwerowe
description: Funkcje platformy Azure zapewniają funkcje bezserwerowe w wielu językach (C#, JavaScript, Java) i platformach, aby zapewnić kod błyskawicznej skali sterowanej zdarzeniami.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401614"
---
# <a name="azure-functions"></a><span data-ttu-id="f4b0c-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="f4b0c-103">Azure Functions</span></span>

<span data-ttu-id="f4b0c-104">Funkcje platformy Azure zapewniają środowisko obliczeniowe bezużycia serwera.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="f4b0c-105">Funkcja jest wywoływana przez *wyzwalacz* (na przykład dostęp do punktu końcowego HTTP lub czasowcy) i wykonuje blok kodu lub logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="f4b0c-106">Funkcje obsługują również *wyspecjalizowane powiązania,* które łączą się z zasobami, takimi jak magazyn i kolejki.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logo funkcji platformy Azure](./media/azure-functions-logo.png)

<span data-ttu-id="f4b0c-108">Istnieją dwie wersje platformy Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="f4b0c-109">Starsza wersja obsługuje pełną platformę .NET Framework, a nowa wersja uruchomieniowa obsługuje aplikacje .NET Core między platformami.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="f4b0c-110">Obsługiwane są dodatkowe języki oprócz języka C#, takie jak JavaScript, F#i Java.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="f4b0c-111">Funkcje utworzone w portalu zapewniają sformatowane składni skryptów.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="f4b0c-112">Funkcje utworzone jako projekty autonomiczne można wdrożyć z pełną obsługą platformy i możliwościami.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="f4b0c-113">Aby uzyskać więcej informacji, zobacz [dokumentację usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="f4b0c-114">Funkcje v1 vs. v2</span><span class="sxs-lookup"><span data-stu-id="f4b0c-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="f4b0c-115">Istnieją dwie wersje programu Windows Functions: 1.x i 2.x.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="f4b0c-116">Wersja 1.x jest ogólnie dostępna (GA).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="f4b0c-117">Obsługuje program .NET z portalu lub komputerów z systemem Windows i używa .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="f4b0c-118">1.x obsługuje C#, JavaScript i F#, z eksperymentalną obsługą pythona, PHP, TypeScript, Batch, Bash i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="f4b0c-119">[Wersja 2.x jest również ogólnie dostępna teraz](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="f4b0c-120">Wykorzystuje program .NET Core i obsługuje tworzenie wielu platform na komputerach z systemem Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="f4b0c-121">2.x dodaje pierwszorzędną obsługę języka Java, ale nie obsługuje jeszcze bezpośrednio żadnego z języków eksperymentalnych.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="f4b0c-122">Wersja 2.x używa nowego modelu rozszerzalności powiązania, który umożliwia rozszerzenia innych firm na platformie, niezależne przechowywanie wersji powiązań i usprawnione środowisko wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="f4b0c-123">**Znany jest problem w 1.x z [obsługą przekierowania powiązania](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="f4b0c-124">Problem jest specyficzny dla rozwoju .NET.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="f4b0c-125">Mają wpływ na projekty z zależnościami od bibliotek, które są inną wersją niż biblioteki zawarte w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="f4b0c-126">Zespół funkcji zobowiązał się do dokonania konkretnych postępów w tej sprawie.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="f4b0c-127">Zespół zajmie się powiązanie przekierowania w 2.x, zanim przejdzie do ogólnej dostępności.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="f4b0c-128">Oficjalne oświadczenie zespołu z sugerowanymi poprawkami i obejściami jest dostępne tutaj: [Rozpoznawanie zestawu w usłudze Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="f4b0c-129">Aby uzyskać więcej informacji, zobacz [Porównanie 1.x i 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="f4b0c-130">Obsługa języków programowania</span><span class="sxs-lookup"><span data-stu-id="f4b0c-130">Programming language support</span></span>

<span data-ttu-id="f4b0c-131">Następujące języki są obsługiwane w ogólnej dostępności (GA), podglądu lub eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="f4b0c-132">Język</span><span class="sxs-lookup"><span data-stu-id="f4b0c-132">Language</span></span>      |<span data-ttu-id="f4b0c-133">1.x</span><span class="sxs-lookup"><span data-stu-id="f4b0c-133">1.x</span></span>         |<span data-ttu-id="f4b0c-134">2.x</span><span class="sxs-lookup"><span data-stu-id="f4b0c-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="f4b0c-135">**C #**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-135">**C#**</span></span>        |<span data-ttu-id="f4b0c-136">Ogólna dostępność</span><span class="sxs-lookup"><span data-stu-id="f4b0c-136">GA</span></span>          |<span data-ttu-id="f4b0c-137">Wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="f4b0c-137">Preview</span></span>  |
|<span data-ttu-id="f4b0c-138">**Javascript**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-138">**JavaScript**</span></span>|<span data-ttu-id="f4b0c-139">Ogólna dostępność</span><span class="sxs-lookup"><span data-stu-id="f4b0c-139">GA</span></span>          |<span data-ttu-id="f4b0c-140">Wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="f4b0c-140">Preview</span></span>  |
|<span data-ttu-id="f4b0c-141">**F #**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-141">**F#**</span></span>        |<span data-ttu-id="f4b0c-142">Ogólna dostępność</span><span class="sxs-lookup"><span data-stu-id="f4b0c-142">GA</span></span>          |         |
|<span data-ttu-id="f4b0c-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-143">**Java**</span></span>      |            |<span data-ttu-id="f4b0c-144">Wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="f4b0c-144">Preview</span></span>  |
|<span data-ttu-id="f4b0c-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-145">**Python**</span></span>    |<span data-ttu-id="f4b0c-146">Eksperymentalne</span><span class="sxs-lookup"><span data-stu-id="f4b0c-146">Experimental</span></span>|         |
|<span data-ttu-id="f4b0c-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-147">**PHP**</span></span>       |<span data-ttu-id="f4b0c-148">Eksperymentalne</span><span class="sxs-lookup"><span data-stu-id="f4b0c-148">Experimental</span></span>|         |
|<span data-ttu-id="f4b0c-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-149">**TypeScript**</span></span>|<span data-ttu-id="f4b0c-150">Eksperymentalne</span><span class="sxs-lookup"><span data-stu-id="f4b0c-150">Experimental</span></span>|         |
|<span data-ttu-id="f4b0c-151">**Batch**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-151">**Batch**</span></span>     |<span data-ttu-id="f4b0c-152">Eksperymentalne</span><span class="sxs-lookup"><span data-stu-id="f4b0c-152">Experimental</span></span>|         |
|<span data-ttu-id="f4b0c-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-153">**Bash**</span></span>      |<span data-ttu-id="f4b0c-154">Eksperymentalne</span><span class="sxs-lookup"><span data-stu-id="f4b0c-154">Experimental</span></span>|         |
|<span data-ttu-id="f4b0c-155">**Powershell**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-155">**PowerShell**</span></span>|<span data-ttu-id="f4b0c-156">Eksperymentalne</span><span class="sxs-lookup"><span data-stu-id="f4b0c-156">Experimental</span></span>|         |

<span data-ttu-id="f4b0c-157">Więcej informacji, zobacz [Obsługiwane języki](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="f4b0c-158">Plany usług aplikacji</span><span class="sxs-lookup"><span data-stu-id="f4b0c-158">App service plans</span></span>

<span data-ttu-id="f4b0c-159">Funkcje są obsługiwane przez *plan usługi aplikacji*.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="f4b0c-160">Plan definiuje zasoby używane przez aplikację funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="f4b0c-161">Można przypisać plany do regionu, określić rozmiar i liczbę maszyn wirtualnych, które będą używane, i wybrać warstwę cenową.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="f4b0c-162">W przypadku prawdziwego podejścia bezużycia serwera aplikacje funkcji mogą używać planu **zużycia.**</span><span class="sxs-lookup"><span data-stu-id="f4b0c-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="f4b0c-163">Plan zużycia automatycznie skaluje zaplecze na podstawie obciążenia.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="f4b0c-164">Aby uzyskać więcej informacji, zobacz [Plany usług aplikacji](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="f4b0c-165">Tworzenie pierwszej funkcji</span><span class="sxs-lookup"><span data-stu-id="f4b0c-165">Create your first function</span></span>

<span data-ttu-id="f4b0c-166">Istnieją trzy typowe sposoby tworzenia aplikacji funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="f4b0c-167">Funkcje skryptu w portalu.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-167">Script functions in the portal.</span></span>
- <span data-ttu-id="f4b0c-168">Utwórz niezbędne zasoby przy użyciu interfejsu cli platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-168">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="f4b0c-169">Twórz funkcje lokalnie przy użyciu ulubionego środowiska IDE i publikuj je na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="f4b0c-170">Aby uzyskać więcej informacji na temat tworzenia funkcji skryptów w portalu, zobacz [Tworzenie pierwszej funkcji w witrynie Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="f4b0c-171">Aby utworzyć kompilację z interfejsu cli platformy Azure, zobacz [Tworzenie pierwszej funkcji przy użyciu interfejsu cli platformy Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="f4b0c-172">Aby utworzyć funkcję z programu Visual Studio, zobacz [Tworzenie pierwszej funkcji przy użyciu programu Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="f4b0c-173">Opis wyzwalaczy i powiązań</span><span class="sxs-lookup"><span data-stu-id="f4b0c-173">Understand triggers and bindings</span></span>

<span data-ttu-id="f4b0c-174">Funkcje są wywoływane przez *wyzwalacz* i może mieć dokładnie jeden.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="f4b0c-175">Oprócz wywoływania funkcji, niektóre wyzwalacze również służyć jako powiązania.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="f4b0c-176">Oprócz wyzwalacza można również zdefiniować wiele powiązań.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="f4b0c-177">*Powiązania* zapewniają deklaratywny sposób łączenia danych z kodem.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="f4b0c-178">Mogą być przekazywane (wejściowe) lub odbierać dane (dane wyjściowe).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="f4b0c-179">Wyzwalacze i wiązania ułatwiają pracę z funkcjami.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="f4b0c-180">Powiązania usuwają obciążenie związane z ręcznym tworzeniem połączeń bazy danych lub systemu plików.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="f4b0c-181">Wszystkie informacje potrzebne dla powiązań jest zawarte w pliku special *functions.json* dla skryptów lub zadeklarowane z atrybutami w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="f4b0c-182">Niektóre typowe wyzwalacze obejmują:</span><span class="sxs-lookup"><span data-stu-id="f4b0c-182">Some common triggers include:</span></span>

- <span data-ttu-id="f4b0c-183">Magazyn obiektów Blob: wywołaj funkcję, gdy plik lub folder zostanie przekazany lub zmieniony w magazynie.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="f4b0c-184">HTTP: wywołać funkcję, takich jak interfejs API REST.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="f4b0c-185">Kolejka: wywołać funkcję, gdy elementy istnieją w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="f4b0c-186">Timer: wywołać funkcję na regularne rytm.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="f4b0c-187">Przykłady powiązań obejmują:</span><span class="sxs-lookup"><span data-stu-id="f4b0c-187">Examples of bindings include:</span></span>

- <span data-ttu-id="f4b0c-188">CosmosDB: łatwo połączyć się z bazą danych, aby załadować lub zapisać pliki.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="f4b0c-189">Przechowywanie tabel: praca z magazynem kluczy/wartości z aplikacji funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="f4b0c-190">Magazyn kolejek: łatwo pobierać elementy z kolejki lub umieszczać nowe elementy w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="f4b0c-191">Poniższy przykład owy plik *functions.json* definiuje wyzwalacz i powiązanie:</span><span class="sxs-lookup"><span data-stu-id="f4b0c-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="f4b0c-192">W tym przykładzie funkcja jest wyzwalana przez zmianę `images` magazynu obiektów blob w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="f4b0c-193">Informacje o pliku są przekazywane, więc wyzwalacz działa również jako powiązanie.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="f4b0c-194">Istnieje inne powiązanie, aby umieścić `images`informacje w kolejce o nazwie .</span><span class="sxs-lookup"><span data-stu-id="f4b0c-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="f4b0c-195">Oto skrypt C# dla funkcji:</span><span class="sxs-lookup"><span data-stu-id="f4b0c-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="f4b0c-196">Przykład jest prostą funkcją, która przyjmuje nazwę pliku, który został zmodyfikowany lub przekazany do magazynu obiektów blob i umieszcza go w kolejce do późniejszego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="f4b0c-197">Aby uzyskać pełną listę wyzwalaczy i powiązań, zobacz [Usługi Azure Functions wyzwala i powiązania pojęcia](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="f4b0c-198">Serwerów proxy</span><span class="sxs-lookup"><span data-stu-id="f4b0c-198">Proxies</span></span>

<span data-ttu-id="f4b0c-199">Serwery proxy zapewniają funkcje przekierowania dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="f4b0c-200">Serwery proxy udostępniają punkt końcowy i mapują ten punkt końcowy na inny zasób.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="f4b0c-201">Z serwerami proxy możesz:</span><span class="sxs-lookup"><span data-stu-id="f4b0c-201">With proxies, you can:</span></span>

- <span data-ttu-id="f4b0c-202">Przekierowanie żądania przychodzącego do innego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="f4b0c-203">Zmodyfikuj żądanie przychodzące, zanim zostanie przekazane.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="f4b0c-204">Zmodyfikuj lub udzielij odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-204">Modify or provide a response.</span></span>

<span data-ttu-id="f4b0c-205">Serwery proxy są używane w scenariuszach takich jak:</span><span class="sxs-lookup"><span data-stu-id="f4b0c-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="f4b0c-206">Upraszczanie, skracanie lub zmienianie adresu URL.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="f4b0c-207">Zapewnienie spójnego prefiksu interfejsu API do wielu usług zaplecza.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="f4b0c-208">Szyderczy odpowiedzi na punkt końcowy jest rozwijany.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="f4b0c-209">Zapewnienie statycznej odpowiedzi na dobrze znany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="f4b0c-210">Utrzymywanie punktu końcowego interfejsu API spójne, gdy zaplecze jest przenoszone lub migrowane.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="f4b0c-211">Serwery proxy są przechowywane jako definicje JSON.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="f4b0c-212">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="f4b0c-212">Here is an example:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

<span data-ttu-id="f4b0c-213">Serwer `Domain Redirect` proxy przyjmuje skróconą trasę i mapuje ją do dłuższego zasobu funkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="f4b0c-214">Transformacja wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="f4b0c-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="f4b0c-215">Serwer `Root` proxy pobiera wszystko, co`https://--shorturl--/`jest wysyłane do głównego adresu URL ( ) i przekierowuje go do witryny dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="f4b0c-216">Przykład korzystania z serwerów proxy jest wyświetlany w filmie [Azure: Przenieś aplikację do chmury za pomocą bezserwerowych funkcji platformy Azure](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="f4b0c-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="f4b0c-217">W czasie rzeczywistym ASP.NET podstawowa aplikacja uruchomiona w lokalnym programie SQL Server jest migrowana do usługi Azure Cloud.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="f4b0c-218">Serwery proxy są używane do refaktoryzacji tradycyjnego projektu interfejsu API sieci Web do korzystania z funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4b0c-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="f4b0c-219">Aby uzyskać więcej informacji na temat serwerów proxy, zobacz [Praca z serwerami proxy usługi Azure Functions .](https://docs.microsoft.com/azure/azure-functions/functions-proxies)</span><span class="sxs-lookup"><span data-stu-id="f4b0c-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f4b0c-220">[Poprzedni](azure-serverless-platform.md)
>[następny](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="f4b0c-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
