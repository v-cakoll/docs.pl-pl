---
title: Modele hostingu aplikacji Blazor
description: Poznaj różne sposoby hostowania aplikacji Blazor, w tym w przeglądarce w zestawie webassembly lub na serwerze.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 3196c9ff284a23e61bdfec98e56da3f66180a18e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183827"
---
# <a name="blazor-app-hosting-models"></a><span data-ttu-id="18c97-103">Modele hostingu aplikacji Blazor</span><span class="sxs-lookup"><span data-stu-id="18c97-103">Blazor app hosting models</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="18c97-104">Aplikacje Blazor mogą być hostowane w usługach IIS, podobnie jak aplikacje ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="18c97-104">Blazor apps can be hosted in IIS just like ASP.NET Web Forms apps.</span></span> <span data-ttu-id="18c97-105">Aplikacje Blazor mogą być również hostowane w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="18c97-105">Blazor apps can also be hosted in one of the following ways:</span></span>

* <span data-ttu-id="18c97-106">Po stronie klienta w przeglądarce w programie webassembly.</span><span class="sxs-lookup"><span data-stu-id="18c97-106">Client-side in the browser on WebAssembly.</span></span>
* <span data-ttu-id="18c97-107">Po stronie serwera w aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="18c97-107">Server-side in an ASP.NET Core app.</span></span> 

## <a name="blazor-webassembly-apps"></a><span data-ttu-id="18c97-108">Blazor aplikacje webassembly</span><span class="sxs-lookup"><span data-stu-id="18c97-108">Blazor WebAssembly apps</span></span>

<span data-ttu-id="18c97-109">Blazor aplikacje webassembly są wykonywane bezpośrednio w przeglądarce w środowisku uruchomieniowym .NET opartym na zestawie.</span><span class="sxs-lookup"><span data-stu-id="18c97-109">Blazor WebAssembly apps execute directly in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="18c97-110">Blazor aplikacje webassembly działają w podobny sposób do platform języka JavaScript frontonu, takich jak kątowy lub reagowanie.</span><span class="sxs-lookup"><span data-stu-id="18c97-110">Blazor WebAssembly apps function in a similar way to front-end JavaScript frameworks like Angular or React.</span></span> <span data-ttu-id="18c97-111">Jednak zamiast pisania kodu JavaScript, należy napisać C#.</span><span class="sxs-lookup"><span data-stu-id="18c97-111">However, instead of writing JavaScript you write C#.</span></span> <span data-ttu-id="18c97-112">Środowisko uruchomieniowe platformy .NET jest pobierane wraz z aplikacją wraz z zestawem aplikacji i wszystkimi wymaganymi zależnościami.</span><span class="sxs-lookup"><span data-stu-id="18c97-112">The .NET runtime is downloaded with the app along with the app assembly and any required dependencies.</span></span> <span data-ttu-id="18c97-113">Nie są wymagane żadne wtyczki ani rozszerzenia przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="18c97-113">No browser plugins or extensions are required.</span></span> 

<span data-ttu-id="18c97-114">Pobrane zestawy są normalnymi zestawami .NET, tak jak w przypadku innych aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="18c97-114">The downloaded assemblies are normal .NET assemblies, like you would use in any other .NET app.</span></span> <span data-ttu-id="18c97-115">Ponieważ środowisko uruchomieniowe obsługuje .NET Standard, można użyć istniejących bibliotek .NET Standard z aplikacją Blazor webassembly.</span><span class="sxs-lookup"><span data-stu-id="18c97-115">Because the runtime supports .NET Standard, you can use existing .NET Standard libraries with your Blazor WebAssembly app.</span></span> <span data-ttu-id="18c97-116">Jednak te zestawy będą nadal wykonywane w piaskownicy zabezpieczeń przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="18c97-116">However, these assemblies will still execute in the browser security sandbox.</span></span> <span data-ttu-id="18c97-117">Niektóre funkcje mogą zgłosić <xref:System.PlatformNotSupportedException>, takie jak próba uzyskania dostępu do systemu plików lub otwarcie dowolnych połączeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="18c97-117">Some functionality may throw a <xref:System.PlatformNotSupportedException>, like trying to access the file system or opening arbitrary network connections.</span></span> 

<span data-ttu-id="18c97-118">Po załadowaniu aplikacji środowisko uruchomieniowe platformy .NET jest uruchamiane i wskazywane w zestawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18c97-118">When the app loads, the .NET runtime is started and pointed at the app assembly.</span></span> <span data-ttu-id="18c97-119">Zostanie uruchomiona logika uruchamiania aplikacji i są renderowane składniki główne.</span><span class="sxs-lookup"><span data-stu-id="18c97-119">The app startup logic runs, and the root components are rendered.</span></span> <span data-ttu-id="18c97-120">Blazor oblicza aktualizacje interfejsu użytkownika w oparciu o renderowane dane wyjściowe ze składników.</span><span class="sxs-lookup"><span data-stu-id="18c97-120">Blazor calculates the UI updates based on the rendered output from the components.</span></span> <span data-ttu-id="18c97-121">Następnie są stosowane aktualizacje modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="18c97-121">The DOM updates are then applied.</span></span>

![Zestaw WebAssembly Blazor](media/hosting-models/blazor-webassembly.png)

<span data-ttu-id="18c97-123">Blazor aplikacje webassembly działają czysto po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="18c97-123">Blazor WebAssembly apps run purely client-side.</span></span> <span data-ttu-id="18c97-124">Takie aplikacje można wdrażać w ramach rozwiązań do hostingu witryn statycznych, takich jak strony usługi GitHub lub hostowanie statycznej witryny sieci Web platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="18c97-124">Such apps can be deployed to static site hosting solutions like GitHub Pages or Azure Static Website Hosting.</span></span> <span data-ttu-id="18c97-125">Platforma .NET nie jest wymagana na serwerze.</span><span class="sxs-lookup"><span data-stu-id="18c97-125">.NET isn't required on the server at all.</span></span> <span data-ttu-id="18c97-126">Głębokie łączenie z częściami aplikacji zwykle wymaga rozwiązania routingu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="18c97-126">Deep linking to parts of the app typically requires a routing solution on the server.</span></span> <span data-ttu-id="18c97-127">Rozwiązanie do routingu przekierowuje żądania do katalogu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18c97-127">The routing solution redirects requests to the root of the app.</span></span> <span data-ttu-id="18c97-128">Na przykład to przekierowanie może być obsługiwane przy użyciu reguł ponownego zapisywania adresów URL w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="18c97-128">For example, this redirection can be handled using URL rewrite rules in IIS.</span></span>

<span data-ttu-id="18c97-129">Aby uzyskać wszystkie korzyści wynikające z Blazor i opracowywania aplikacji sieci Web w pełnym stosie, należy hostować aplikację webassembly Blazor przy użyciu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="18c97-129">To get all the benefits of Blazor and full-stack .NET web development, host your Blazor WebAssembly app with ASP.NET Core.</span></span> <span data-ttu-id="18c97-130">Korzystając z platformy .NET zarówno na kliencie, jak i na serwerze, można łatwo udostępniać kod i kompilować swoją aplikację przy użyciu jednego spójnego zestawu języków, struktur i narzędzi.</span><span class="sxs-lookup"><span data-stu-id="18c97-130">By using .NET on both the client and server, you can easily share code and build your app using one consistent set of languages, frameworks, and tools.</span></span> <span data-ttu-id="18c97-131">Blazor udostępnia wygodne szablony służące do konfigurowania rozwiązania, które zawiera aplikację webassembly Blazor i projekt hosta ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="18c97-131">Blazor provides convenient templates for setting up a solution that contains both a Blazor WebAssembly app and an ASP.NET Core host project.</span></span> <span data-ttu-id="18c97-132">Po skompilowaniu rozwiązania skompilowane pliki statyczne z aplikacji Blazor są hostowane przez aplikację ASP.NET Core przy użyciu już skonfigurowanego routingu rezerwowego.</span><span class="sxs-lookup"><span data-stu-id="18c97-132">When the solution is built, the built static files from the Blazor app are hosted by the ASP.NET Core app with fallback routing already setup.</span></span>

## <a name="blazor-server-apps"></a><span data-ttu-id="18c97-133">Aplikacje serwera Blazor</span><span class="sxs-lookup"><span data-stu-id="18c97-133">Blazor Server apps</span></span>

<span data-ttu-id="18c97-134">Odwołaj się z dyskusji [architektury Blazor](architecture-comparison.md#blazor) , że składniki Blazor renderują swoje dane wyjściowe do pośredniego `RenderTree`abstrakcji o nazwie a.</span><span class="sxs-lookup"><span data-stu-id="18c97-134">Recall from the [Blazor architecture](architecture-comparison.md#blazor) discussion that Blazor components render their output to an intermediate abstraction called a `RenderTree`.</span></span> <span data-ttu-id="18c97-135">Blazor Framework następnie porównuje elementy renderowane z wcześniej renderowanymi informacjami.</span><span class="sxs-lookup"><span data-stu-id="18c97-135">The Blazor framework then compares what was rendered with what was previously rendered.</span></span> <span data-ttu-id="18c97-136">Różnice są stosowane do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="18c97-136">The differences are applied to the DOM.</span></span> <span data-ttu-id="18c97-137">Składniki Blazor są oddzielone od sposobu zastosowania ich renderowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="18c97-137">Blazor components are decoupled from how their rendered output is applied.</span></span> <span data-ttu-id="18c97-138">W związku z tym same składniki nie muszą działać w tym samym procesie co proces aktualizowania interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="18c97-138">Consequently, the components themselves don't have to run in the same process as the process updating the UI.</span></span> <span data-ttu-id="18c97-139">W rzeczywistości nie trzeba nawet uruchamiać ich na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="18c97-139">In fact, they don't even have to run on the same machine.</span></span>

<span data-ttu-id="18c97-140">W aplikacjach serwera Blazor składniki są uruchamiane na serwerze, a nie po stronie klienta w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="18c97-140">In Blazor Server apps, the components run on the server instead of client-side in the browser.</span></span> <span data-ttu-id="18c97-141">Zdarzenia interfejsu użytkownika, które wystąpiły w przeglądarce, są wysyłane do serwera przez połączenie w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="18c97-141">UI events that occur in the browser are sent to the server over a real-time connection.</span></span> <span data-ttu-id="18c97-142">Zdarzenia są wysyłane do poprawnych wystąpień składników.</span><span class="sxs-lookup"><span data-stu-id="18c97-142">The events are dispatched to the correct component instances.</span></span> <span data-ttu-id="18c97-143">Składniki są renderowane i obliczeniowy różnic interfejsu użytkownika jest serializowany i wysyłany do przeglądarki, w której jest zastosowany do modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="18c97-143">The components render, and the calculated UI diff is serialized and sent to the browser where it's applied to the DOM.</span></span>

![Serwer Blazor](media/hosting-models/blazor-server.png)

<span data-ttu-id="18c97-145">Model hostingu serwera Blazor może dźwiękować, jeśli użyto ASP.NET AJAX i <xref:System.Web.UI.UpdatePanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="18c97-145">The Blazor Server hosting model may sound familiar if you've used ASP.NET AJAX and the <xref:System.Web.UI.UpdatePanel> control.</span></span> <span data-ttu-id="18c97-146">`UpdatePanel` Kontrolka obsługuje stosowanie aktualizacji stron częściowych w odpowiedzi na zdarzenia wyzwalające na stronie.</span><span class="sxs-lookup"><span data-stu-id="18c97-146">The `UpdatePanel` control handles applying partial page updates in response to trigger events on the page.</span></span> <span data-ttu-id="18c97-147">Gdy jest `UpdatePanel` wyzwalane, żąda aktualizacji częściowej, a następnie stosuje ją bez konieczności odświeżania strony.</span><span class="sxs-lookup"><span data-stu-id="18c97-147">When triggered, the `UpdatePanel` requests a partial update and then applies it without needing to refresh the page.</span></span> <span data-ttu-id="18c97-148">Stan interfejsu użytkownika jest zarządzany przy użyciu programu `ViewState`.</span><span class="sxs-lookup"><span data-stu-id="18c97-148">The state of the UI is managed using `ViewState`.</span></span> <span data-ttu-id="18c97-149">Aplikacje serwera Blazor są nieco inne w przypadku, gdy aplikacja wymaga aktywnego połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="18c97-149">Blazor Server apps are slightly different in that the app requires an active connection with the client.</span></span> <span data-ttu-id="18c97-150">Ponadto na serwerze jest zachowywany cały stan interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="18c97-150">Additionally, all UI state is maintained on the server.</span></span> <span data-ttu-id="18c97-151">Oprócz tych różnic te dwa modele są koncepcyjnie podobne.</span><span class="sxs-lookup"><span data-stu-id="18c97-151">Aside from those differences, the two models are conceptually similar.</span></span>

## <a name="how-to-choose-the-right-blazor-hosting-model"></a><span data-ttu-id="18c97-152">Jak wybrać odpowiedni model hostingu Blazor</span><span class="sxs-lookup"><span data-stu-id="18c97-152">How to choose the right Blazor hosting model</span></span>

<span data-ttu-id="18c97-153">Zgodnie z opisem w dokumentacji dotyczącej [modelu hostingu Blazor](https://docs.microsoft.com/aspnet/core/blazor/hosting-models#server-side)różne modele hostingu Blazor mają różne kompromisy.</span><span class="sxs-lookup"><span data-stu-id="18c97-153">As described in the [Blazor hosting model docs](https://docs.microsoft.com/aspnet/core/blazor/hosting-models#server-side), the different Blazor hosting models have different tradeoffs.</span></span>

<span data-ttu-id="18c97-154">Model hostingu zestawu webBlazor ma następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="18c97-154">The Blazor WebAssembly hosting model has the following benefits:</span></span>

* <span data-ttu-id="18c97-155">Nie istnieje zależność po stronie serwera .NET.</span><span class="sxs-lookup"><span data-stu-id="18c97-155">There's no .NET server-side dependency.</span></span> <span data-ttu-id="18c97-156">Aplikacja jest w pełni funkcjonalna po pobraniu do klienta programu.</span><span class="sxs-lookup"><span data-stu-id="18c97-156">The app is fully functioning after downloaded to the client.</span></span>
* <span data-ttu-id="18c97-157">Zasoby i możliwości klienta są w pełni wykorzystywane.</span><span class="sxs-lookup"><span data-stu-id="18c97-157">Client resources and capabilities are fully leveraged.</span></span>
* <span data-ttu-id="18c97-158">Zadania są Odciążone z serwera do klienta programu.</span><span class="sxs-lookup"><span data-stu-id="18c97-158">Work is offloaded from the server to the client.</span></span>
* <span data-ttu-id="18c97-159">Serwer sieci Web ASP.NET Core nie jest wymagany do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18c97-159">An ASP.NET Core web server isn't required to host the app.</span></span> <span data-ttu-id="18c97-160">Możliwe są scenariusze wdrażania bezserwerowego (na przykład obsługujące aplikację z sieci CDN).</span><span class="sxs-lookup"><span data-stu-id="18c97-160">Serverless deployment scenarios are possible (for example, serving the app from a CDN).</span></span>

<span data-ttu-id="18c97-161">Downsides modelu hostingu Blazor webassembly:</span><span class="sxs-lookup"><span data-stu-id="18c97-161">The downsides of the Blazor WebAssembly hosting model are:</span></span>

* <span data-ttu-id="18c97-162">Możliwości przeglądarki ograniczają aplikację.</span><span class="sxs-lookup"><span data-stu-id="18c97-162">Browser capabilities restrict the app.</span></span>
* <span data-ttu-id="18c97-163">Wymagany jest sprzęt i oprogramowanie klienta (na przykład obsługa zestawu webassembly).</span><span class="sxs-lookup"><span data-stu-id="18c97-163">Capable client hardware and software (for example, WebAssembly support) is required.</span></span>
* <span data-ttu-id="18c97-164">Rozmiar pobieranych plików jest większy i ładowanie aplikacji trwa dłużej.</span><span class="sxs-lookup"><span data-stu-id="18c97-164">Download size is larger, and apps take longer to load.</span></span>
* <span data-ttu-id="18c97-165">Środowisko uruchomieniowe platformy .NET i obsługa narzędzi są mniej dojrzałe.</span><span class="sxs-lookup"><span data-stu-id="18c97-165">.NET runtime and tooling support is less mature.</span></span> <span data-ttu-id="18c97-166">Na przykład istnieją ograniczenia dotyczące obsługi [.NET Standard](../../standard/net-standard.md) i debugowania.</span><span class="sxs-lookup"><span data-stu-id="18c97-166">For example, there are limitations in [.NET Standard](../../standard/net-standard.md) support and debugging.</span></span>

<span data-ttu-id="18c97-167">Z drugiej strony model hostingu serwera Blazor oferuje następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="18c97-167">Conversely, the Blazor Server hosting model offers the following benefits:</span></span>

* <span data-ttu-id="18c97-168">Rozmiar pobieranych plików jest znacznie mniejszy niż aplikacja po stronie klienta, a aplikacja jest znacznie szybsza.</span><span class="sxs-lookup"><span data-stu-id="18c97-168">Download size is much smaller than a client-side app, and the app loads much faster.</span></span>
* <span data-ttu-id="18c97-169">Aplikacja w pełni wykorzystuje możliwości serwera, w tym używanie dowolnego interfejsu API zgodnego z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="18c97-169">The app takes full advantage of server capabilities, including use of any .NET Core-compatible APIs.</span></span>
* <span data-ttu-id="18c97-170">Program .NET Core na serwerze jest używany do uruchamiania aplikacji, więc istniejące narzędzia platformy .NET, takie jak debugowanie, działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="18c97-170">.NET Core on the server is used to run the app, so existing .NET tooling, such as debugging, works as expected.</span></span>
* <span data-ttu-id="18c97-171">Klienci zubożoni są obsługiwani.</span><span class="sxs-lookup"><span data-stu-id="18c97-171">Thin clients are supported.</span></span> <span data-ttu-id="18c97-172">Na przykład aplikacje po stronie serwera współpracują z przeglądarkami, które nie obsługują zestawu webassembly i na urządzeniach z ograniczeniami zasobów.</span><span class="sxs-lookup"><span data-stu-id="18c97-172">For example, server-side apps work with browsers that don't support WebAssembly and on resource-constrained devices.</span></span>
* <span data-ttu-id="18c97-173">Baza danych platformy .NET/C# kodu aplikacji, w tym kod składnika aplikacji, nie jest obsługiwana dla klientów.</span><span class="sxs-lookup"><span data-stu-id="18c97-173">The app's .NET/C# code base, including the app's component code, isn't served to clients.</span></span>

<span data-ttu-id="18c97-174">Downsides do modelu hostingu serwera Blazor są następujące:</span><span class="sxs-lookup"><span data-stu-id="18c97-174">The downsides to the Blazor Server hosting model are:</span></span>

* <span data-ttu-id="18c97-175">Wyższe opóźnienia interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="18c97-175">Higher UI latency.</span></span> <span data-ttu-id="18c97-176">Każda interakcja użytkownika obejmuje przeskok sieci.</span><span class="sxs-lookup"><span data-stu-id="18c97-176">Every user interaction involves a network hop.</span></span>
* <span data-ttu-id="18c97-177">Brak obsługi offline.</span><span class="sxs-lookup"><span data-stu-id="18c97-177">There's no offline support.</span></span> <span data-ttu-id="18c97-178">Jeśli połączenie z klientem zakończy się niepowodzeniem, aplikacja przestanie działać.</span><span class="sxs-lookup"><span data-stu-id="18c97-178">If the client connection fails, the app stops working.</span></span>
* <span data-ttu-id="18c97-179">Skalowalność jest wyzwaniem dla aplikacji z wieloma użytkownikami.</span><span class="sxs-lookup"><span data-stu-id="18c97-179">Scalability is challenging for apps with many users.</span></span> <span data-ttu-id="18c97-180">Serwer musi zarządzać wieloma połączeniami klientów i obsługiwać stan klienta.</span><span class="sxs-lookup"><span data-stu-id="18c97-180">The server must manage multiple client connections and handle client state.</span></span>
* <span data-ttu-id="18c97-181">Do obsłużynia aplikacji wymagany jest serwer ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="18c97-181">An ASP.NET Core server is required to serve the app.</span></span> <span data-ttu-id="18c97-182">Scenariusze wdrażania bez użycia serwera nie są możliwe.</span><span class="sxs-lookup"><span data-stu-id="18c97-182">Serverless deployment scenarios aren't possible.</span></span> <span data-ttu-id="18c97-183">Nie można na przykład udostępniać aplikacji z sieci CDN.</span><span class="sxs-lookup"><span data-stu-id="18c97-183">For example, you can't serve the app from a CDN.</span></span>

<span data-ttu-id="18c97-184">Poprzednia lista zalet może być zastraszanie, ale model hostingu można później zmienić.</span><span class="sxs-lookup"><span data-stu-id="18c97-184">The preceding list of trade-offs may be intimidating, but your hosting model can be changed later.</span></span> <span data-ttu-id="18c97-185">Bez względu na wybrany model hostingu Blazor model składnika jest *taki sam*.</span><span class="sxs-lookup"><span data-stu-id="18c97-185">Regardless of the Blazor hosting model selected, the component model is *the same*.</span></span> <span data-ttu-id="18c97-186">W zasadzie te same składniki mogą być używane z modelem hostingu.</span><span class="sxs-lookup"><span data-stu-id="18c97-186">In principle, the same components can be used with either hosting model.</span></span> <span data-ttu-id="18c97-187">Kod aplikacji nie zmienia się; jednak dobrym sposobem jest wprowadzenie abstrakcji, tak aby składniki nadal miały model hostingu — niezależny od.</span><span class="sxs-lookup"><span data-stu-id="18c97-187">Your app code doesn't change; however, it's a good practice to introduce abstractions so that your components stay hosting model-agnostic.</span></span> <span data-ttu-id="18c97-188">Streszczenia umożliwiają aplikacji łatwiejsze wdrażanie innego modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="18c97-188">The abstractions allow your app to more easily adopt a different hosting model.</span></span>

## <a name="deploy-your-app"></a><span data-ttu-id="18c97-189">Wdrażanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="18c97-189">Deploy your app</span></span>

<span data-ttu-id="18c97-190">Aplikacje ASP.NET Web Forms są zwykle hostowane w usługach IIS na komputerze lub w klastrze z systemem Windows Server.</span><span class="sxs-lookup"><span data-stu-id="18c97-190">ASP.NET Web Forms apps are typically hosted on IIS on a Windows Server machine or cluster.</span></span> <span data-ttu-id="18c97-191">Aplikacje Blazor mogą również:</span><span class="sxs-lookup"><span data-stu-id="18c97-191">Blazor apps can also:</span></span>

* <span data-ttu-id="18c97-192">Być hostowane w usługach IIS, jako pliki statyczne lub jako aplikacja ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="18c97-192">Be hosted on IIS, either as static files or as an ASP.NET Core app.</span></span>
* <span data-ttu-id="18c97-193">Skorzystaj z elastyczności ASP.NET Core, która ma być hostowana na różnych platformach i infrastrukturach serwerów.</span><span class="sxs-lookup"><span data-stu-id="18c97-193">Leverage ASP.NET Core's flexibility to be hosted on various platforms and server infrastructures.</span></span> <span data-ttu-id="18c97-194">Na przykład możesz hostować aplikację Blazor przy użyciu usługi [Nginx](/aspnet/core/host-and-deploy/linux-nginx) lub [Apache](/aspnet/core/host-and-deploy/linux-apache) w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="18c97-194">For example, you can host a Blazor App using [Nginx](/aspnet/core/host-and-deploy/linux-nginx) or [Apache](/aspnet/core/host-and-deploy/linux-apache) on Linux.</span></span> <span data-ttu-id="18c97-195">Więcej informacji o sposobach publikowania i wdrażania aplikacji Blazor znajduje się w dokumentacji [hostingu i wdrażania](/aspnet/core/host-and-deploy/blazor/) Blazor.</span><span class="sxs-lookup"><span data-stu-id="18c97-195">For more information about how to publish and deploy Blazor apps, see the Blazor [Hosting and deployment](/aspnet/core/host-and-deploy/blazor/) documentation.</span></span>

<span data-ttu-id="18c97-196">W następnej sekcji dowiesz się, jak są skonfigurowane projekty dla aplikacji Blazor webassembly i Blazor Server.</span><span class="sxs-lookup"><span data-stu-id="18c97-196">In the next section, we'll look at how the projects for Blazor WebAssembly and Blazor Server apps are set up.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="18c97-197">[Poprzedni](architecture-comparison.md)
>[Następny](project-structure.md)</span><span class="sxs-lookup"><span data-stu-id="18c97-197">[Previous](architecture-comparison.md)
[Next](project-structure.md)</span></span>