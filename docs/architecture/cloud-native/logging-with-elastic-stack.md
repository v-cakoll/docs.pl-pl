---
title: Rejestrowanie przy użyciu elastycznego stosu
description: Rejestrowanie przy użyciu Elastic Stack, logstash i Kibana
ms.date: 02/05/2020
ms.openlocfilehash: 6863c66b63854fe3ecaabe2919beded2926ea64c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448926"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="5ed2d-103">Rejestrowanie przy użyciu elastycznego stosu</span><span class="sxs-lookup"><span data-stu-id="5ed2d-103">Logging with Elastic Stack</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5ed2d-104">Istnieje wiele dobrych narzędzi do rejestrowania, które różnią się kosztami od bezpłatnych, dostępnych narzędzi "open source" do bardziej kosztownych opcji.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="5ed2d-105">W wielu przypadkach bezpłatne narzędzia są tak dobre, jak w przypadku płatnych ofert.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="5ed2d-106">Jedno z tych narzędzi jest kombinacją trzech składników typu "open source": Elastic Search, logstash i Kibana.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span>

<span data-ttu-id="5ed2d-107">Zbiorowo te narzędzia są nazywane stosem elastycznym lub stosem ELK.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="5ed2d-108">Elastyczny stos</span><span class="sxs-lookup"><span data-stu-id="5ed2d-108">Elastic Stack</span></span>

<span data-ttu-id="5ed2d-109">Elastyczny stos to zaawansowana opcja zbierania informacji z klastra Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-109">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="5ed2d-110">Kubernetes obsługuje wysyłanie dzienników do punktu końcowego Elasticsearch, a w [większości](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), wszystko, co musisz zrobić, to ustawienie zmiennych środowiskowych, jak pokazano na rysunku 7-5:</span><span class="sxs-lookup"><span data-stu-id="5ed2d-110">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="5ed2d-111">**Rysunek 7-5**.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-111">**Figure 7-5**.</span></span> <span data-ttu-id="5ed2d-112">Zmienne konfiguracyjne dla Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5ed2d-112">Configuration variables for Kubernetes</span></span>

<span data-ttu-id="5ed2d-113">Spowoduje to zainstalowanie Elasticsearch w klastrze i skierowanie do niego wszystkich dzienników klastra.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-113">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="5ed2d-114">![przykładu pulpitu nawigacyjnego Kibana, pokazującego wyniki zapytania względem dzienników pozyskanych z Kubernetes](./media/kibana-dashboard.png)
**rysunek 7-6**.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-114">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="5ed2d-115">Przykład pulpitu nawigacyjnego Kibana, pokazujący wyniki zapytania względem dzienników, które są pozyskiwane z Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5ed2d-115">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="5ed2d-116">Jakie są zalety elastycznego stosu?</span><span class="sxs-lookup"><span data-stu-id="5ed2d-116">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="5ed2d-117">Elastyczny stos umożliwia scentralizowane rejestrowanie w niedrogim, skalowalnym, przyjaznym dla chmury.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-117">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="5ed2d-118">Interfejs użytkownika usprawnia analizę danych, dzięki czemu można poświęcać czas na zastosują wglądu w dane na podstawie danych, zamiast zwalczać interfejs clunky.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-118">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="5ed2d-119">Obsługuje szeroką gamę danych wejściowych, dlatego w przypadku, gdy aplikacja rozproszona obejmuje więcej i różne rodzaje usług, można oczekiwać, że dane dziennika i metryk są dostępne w systemie.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-119">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="5ed2d-120">Elastyczny stos obsługuje również szybkie wyszukiwania nawet w dużych zestawach danych, dzięki czemu można nawet w przypadku dużych aplikacji rejestrować szczegółowe dane i nadal mieć możliwość wglądu w nie w sposób w pełni.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-120">The Elastic Stack also supports fast searches even across large data sets, making it possible even for large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="5ed2d-121">Logstash</span><span class="sxs-lookup"><span data-stu-id="5ed2d-121">Logstash</span></span>

<span data-ttu-id="5ed2d-122">Pierwszy składnik to [logstash](https://www.elastic.co/products/logstash).</span><span class="sxs-lookup"><span data-stu-id="5ed2d-122">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="5ed2d-123">To narzędzie służy do zbierania informacji o dziennikach z wielu różnych źródeł.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-123">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="5ed2d-124">Na przykład logstash może odczytywać dzienniki z dysku, a także odbierać komunikaty z bibliotek rejestrowania, takich jak [Serilog](https://serilog.net/).</span><span class="sxs-lookup"><span data-stu-id="5ed2d-124">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="5ed2d-125">Logstash może wykonywać pewne podstawowe filtrowanie i rozszerzanie dzienników w miarę ich odbierania.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-125">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="5ed2d-126">Na przykład, Jeśli dzienniki zawierają adresy IP, logstash może być skonfigurowany do przeszukiwania geograficznego i uzyskania kraju lub nawet miejscowości pochodzenia dla tego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-126">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span>

<span data-ttu-id="5ed2d-127">Serilog to biblioteka rejestrowania dla języków .NET, która umożliwia rejestrowanie sparametryzowane.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-127">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="5ed2d-128">Zamiast generowania komunikatu dziennika tekstowego, który osadza pola, parametry są przechowywane oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-128">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="5ed2d-129">Pozwala to na bardziej inteligentne filtrowanie i wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-129">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="5ed2d-130">Przykładowa konfiguracja Serilog do zapisu do logstash pojawia się na rysunku 7-7.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-130">A sample Serilog configuration for writing to Logstash appears in Figure 7-7.</span></span>

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="5ed2d-131">**Rysunek 7-7**.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-131">**Figure 7-7**.</span></span> <span data-ttu-id="5ed2d-132">Serilog konfiguracja do zapisywania informacji dziennika bezpośrednio do logstash za pośrednictwem protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="5ed2d-132">Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="5ed2d-133">Logstash użyje konfiguracji podobnej do przedstawionej na rysunku 7-8.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-133">Logstash would use a configuration like the one shown in Figure 7-8.</span></span>

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

<span data-ttu-id="5ed2d-134">**Rysunek 7-8**.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-134">**Figure 7-8**.</span></span> <span data-ttu-id="5ed2d-135">Konfiguracja logstash do konsumowania dzienników z Serilog</span><span class="sxs-lookup"><span data-stu-id="5ed2d-135">A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="5ed2d-136">W przypadku scenariuszy, w których nie jest wymagana obszerne manipulowanie dziennikiem, istnieje alternatywa dla logstash znany jako [uderzeń](https://www.elastic.co/products/beats).</span><span class="sxs-lookup"><span data-stu-id="5ed2d-136">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="5ed2d-137">Uderzeń to rodzina narzędzi, która umożliwia gromadzenie różnorodnych danych z dzienników do danych sieciowych i informacji o przestoju.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-137">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="5ed2d-138">Wiele aplikacji będzie używać zarówno logstash, jak i uderzeń.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-138">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="5ed2d-139">Po zebraniu dzienników przez logstash należy je umieścić w miejscu.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-139">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="5ed2d-140">Choć logstash obsługuje wiele różnych danych wyjściowych, jedno z bardziej atrakcyjnych jest wyszukiwaniem elastycznym.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-140">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="5ed2d-141">Wyszukiwanie elastyczne</span><span class="sxs-lookup"><span data-stu-id="5ed2d-141">Elastic search</span></span>

<span data-ttu-id="5ed2d-142">Wyszukiwanie elastyczne to zaawansowany aparat wyszukiwania, który umożliwia indeksowanie dzienników w miarę ich odbierania.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-142">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="5ed2d-143">Umożliwia szybkie wykonywanie zapytań dotyczących dzienników.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-143">It makes running queries against the logs quick.</span></span> <span data-ttu-id="5ed2d-144">Wyszukiwanie elastyczne może obsługiwać duże ilości dzienników i w skrajnych przypadkach może być skalowane w wielu węzłach.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-144">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span>

<span data-ttu-id="5ed2d-145">Komunikaty dziennika, które zostały spreparowane w celu zawierają parametry lub które zostały poddane podzielenia między nimi za pośrednictwem przetwarzania logstash, można zbadać bezpośrednio, ponieważ Elasticsearch zachowuje te informacje.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-145">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="5ed2d-146">Zapytanie wyszukujące 10 najważniejszych stron odwiedzonych przez `jill@example.com`znajduje się na rysunku 7-9.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-146">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-9.</span></span>

```
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

<span data-ttu-id="5ed2d-147">**Rysunek 7-9**.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-147">**Figure 7-9**.</span></span> <span data-ttu-id="5ed2d-148">Zapytanie Elasticsearch do znajdowania 10 najważniejszych stron odwiedzonych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="5ed2d-148">An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="5ed2d-149">Wizualizacja informacji przy użyciu pulpitów nawigacyjnych sieci Web Kibana</span><span class="sxs-lookup"><span data-stu-id="5ed2d-149">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="5ed2d-150">Końcowym składnikiem stosu jest Kibana.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-150">The final component of the stack is Kibana.</span></span> <span data-ttu-id="5ed2d-151">To narzędzie służy do udostępniania interaktywnych wizualizacji na pulpicie nawigacyjnym sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-151">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="5ed2d-152">Pulpity nawigacyjne mogą być przygotowane nawet przez użytkowników, którzy nie są techniczne.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-152">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="5ed2d-153">Większość danych znajdujących się w indeksie Elasticsearch można dołączać do pulpitów nawigacyjnych Kibana.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-153">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="5ed2d-154">Indywidualni użytkownicy mogą korzystać z różnych pulpitów nawigacyjnych i Kibana umożliwia to dostosowanie przez umożliwienie pulpitów nawigacyjnych specyficznych dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-154">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span>

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="5ed2d-155">Instalowanie elastycznego stosu na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="5ed2d-155">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="5ed2d-156">Stos elastyczny można zainstalować na platformie Azure na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-156">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="5ed2d-157">Jak zawsze, możliwe jest [udostępnienie maszyn wirtualnych i bezpośrednie zainstalowanie na nich elastycznego stosu](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span><span class="sxs-lookup"><span data-stu-id="5ed2d-157">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="5ed2d-158">Ta opcja jest preferowana przez niektórych doświadczonych użytkowników, ponieważ oferuje ona najwyższy stopień szerszym.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-158">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="5ed2d-159">Wdrożenie w ramach infrastruktury jako usługi wprowadza znaczące narzuty związane z zarządzaniem wymuszające, że ta ścieżka przejęcie na własność wszystkich zadań związanych z infrastrukturą jako usługą, takich jak Zabezpieczanie maszyn i aktualizowanie ich przy użyciu poprawek.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-159">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span>

<span data-ttu-id="5ed2d-160">Opcja o mniejszej obciążeniu polega na użyciu jednego z wielu kontenerów platformy Docker, na którym został już skonfigurowany Stos elastyczny.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-160">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="5ed2d-161">Te kontenery można porzucić w istniejącym klastrze Kubernetes i uruchamiać wraz z kodem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-161">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="5ed2d-162">Kontener [sebp/Elk](https://elk-docker.readthedocs.io/) to dobrze udokumentowany i przetestowany kontener stosu elastycznego.</span><span class="sxs-lookup"><span data-stu-id="5ed2d-162">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="5ed2d-163">Kolejną opcją jest [niedawna ogłoszona oferta Elk jako usługa](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="5ed2d-163">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="5ed2d-164">Odwołania</span><span class="sxs-lookup"><span data-stu-id="5ed2d-164">References</span></span>

- [<span data-ttu-id="5ed2d-165">Instalowanie elastycznego stosu na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="5ed2d-165">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="5ed2d-166">[Poprzednie](observability-patterns.md)
>[dalej](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="5ed2d-166">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>
