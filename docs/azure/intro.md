---
title: Wprowadzenie do platformy Azure i platformy .NET
description: Poznaj podstawy, które musisz znać na temat platformy Azure i platformy .NET.
ms.date: 03/15/2020
ms.openlocfilehash: 64defed4433647c2a0dcce91493d9ec77d21b541
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072145"
---
# <a name="introduction-to-azure-and-net"></a>Wprowadzenie do platform Azure i .NET

Ten dokument zawiera omówienie kluczowych pojęć i usług .NET deweloperzy powinni być zaznajomieni, aby rozpocząć tworzenie aplikacji przy użyciu usług platformy Azure.

## <a name="key-concepts"></a>Kluczowe pojęcia

**Konto platformy Azure:** Twoje konto platformy Azure to poświadczenia używane do logowania się do usług platformy Azure, takich jak [usługa Azure Portal](https://portal.azure.com) lub usługa Cloud [Shell.](https://shell.azure.com) Jeśli nie masz konta platformy Azure, możesz [je utworzyć bezpłatnie.](https://azure.microsoft.com/free/dotnet/)

**Subskrypcja platformy Azure:** subskrypcja to plan rozliczeniowy, w ramach którego tworzone są zasoby platformy Azure. Subskrypcje mogą być subskrypcjami indywidualnymi lub subskrypcjami korporacyjnymi zarządzanymi przez firmę. Twoje konto platformy Azure może być skojarzone z wieloma subskrypcjami. W takim przypadku upewnij się, że wybierasz poprawną subskrypcję podczas tworzenia zasobów. Aby uzyskać więcej informacji, zobacz [Opis kont, subskrypcji i rozliczeń](https://docs.microsoft.com/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing).

> [!TIP]
> Jeśli masz subskrypcję programu Visual Studio, [masz miesięczne środki platformy Azure oczekujące na aktywację.](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)

**Grupa zasobów:** Grupy zasobów to sposób organizowania zasobów platformy Azure w grupy do zarządzania. Zasoby utworzone na platformie Azure będą przechowywane w grupie zasobów, podobnie jak zapisywanie pliku w folderze na komputerze.

**Hosting:** Aby uruchomić kod na platformie Azure, musi być hostowany w usłudze, która obsługuje wykonywanie kodu dostarczonego przez użytkownika.

**Usługi zarządzane:** platforma Azure udostępnia niektóre usługi, w których udostępniasz dane lub informacje na platformie Azure, a implementacja platformy Azure podejmuje odpowiednie działania. Jednym z przykładów jest usługa Azure Blob Storage, gdzie można podać pliki i platformy Azure obsługuje odczytywanie, zapisywanie i utrwalanie ich.

## <a name="choosing-a-hosting-option"></a>Wybór opcji hostingu

Hosting na platformie Azure można podzielić na trzy kategorie.

* **Infrastruktura jako usługa (IaaS)**: Za pomocą usługi IaaS aprowizujesz maszyny wirtualne, których potrzebujesz wraz ze skojarzonymi składnikami sieci i magazynu. Następnie można wdrożyć wszelkie oprogramowanie i aplikacje, które chcesz na tych maszyn wirtualnych. Ten model jest najbliżej tradycyjnego środowiska lokalnego, z tą różnicą, że firma Microsoft zarządza infrastrukturą. Nadal zarządzasz poszczególnymi maszynami wirtualnymi, w tym systemem operacyjnym, oprogramowaniem niestandardowym i aktualizacjami zabezpieczeń.

* **Platforma jako usługa (PaaS)**: PaaS zapewnia zarządzane środowisko hostingowe, w którym wdrażasz aplikację bez konieczności zarządzania maszynami wirtualnymi lub zasobami sieciowymi. Na przykład zamiast tworzenia poszczególnych maszyn wirtualnych określasz liczbę wystąpień, a usługa aprowizuje i konfiguruje niezbędne zasoby oraz zarządza nimi. Usługa Azure App Service jest przykładem usługi PaaS.
  
* **Funkcje jako usługa (FaaS)**: Powszechnie określane jako komputerów bezserwerowych, FaaS idzie jeszcze dalej niż PaaS w abstrakcji obawy środowiska hostingowego. Zamiast tworzyć wystąpienia obliczeniowe, a następnie wdrażać kod w tych wystąpieniach, można wdrożyć kod i usługa automatycznie uruchamia go. Nie trzeba administrować zasobami obliczeniowymi. Platforma bezproblemowo skaluje kod w górę lub w dół do dowolnego poziomu niezbędnego do obsługi ruchu i płacisz tylko wtedy, gdy kod jest uruchomiony. Usługa Azure Functions to usługa FaaS.

Ogólnie rzecz biorąc, im bardziej aplikacja faworyzuje modele FaaS i PaaS, tym więcej korzyści zobaczysz z uruchamiania w chmurze. Poniżej znajduje się podsumowanie trzech typowych opcji hostingu na platformie Azure i kiedy je wybrać.

* [Usługa Azure App Service:](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is)Jeśli chcesz hostować aplikację lub usługę sieci web, najpierw zapoznaj się z usługą App Service. Aby rozpocząć korzystanie z usługi App Service i ASP.NET, WCF i aplikacji ASP.NET Core, zobacz [Tworzenie aplikacji sieci Web ASP.NET Core na platformie Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet).

* [Funkcje platformy Azure:](https://docs.microsoft.com/azure/azure-functions/functions-overview)Usługa Azure Functions doskonale sprawdza się w przepływach pracy opartych na zdarzeniach. Przykłady obejmują odpowiadanie na elementy webhook, przetwarzanie elementów w kolejkach lub magazynie obiektów blob i czasomierze. Aby rozpocząć korzystanie z usługi Azure Functions, zobacz [Tworzenie pierwszej funkcji przy użyciu programu Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

* [Maszyny wirtualne platformy Azure:](https://docs.microsoft.com/azure/virtual-machines/)Jeśli usługa app service nie spełnia twoich potrzeb dotyczących hostowania istniejącej aplikacji z powodu określonych zależności, maszyny wirtualne będą najłatwiejszym miejscem do uruchomienia. Aby rozpocząć pracę z maszynami wirtualnymi i ASP.NET lub WCF, zobacz [Wdrażanie aplikacji ASP.NET na maszynie wirtualnej platformy Azure.](https://tutorials.visualstudio.com/aspnet-vm/intro)

> [!TIP]
> Aby uzyskać więcej informacji na temat wybierania usługi, zobacz [Wybieranie usługi obliczeniowej platformy Azure dla aplikacji](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree).

## <a name="choose-a-data-storage-service"></a>Wybieranie usługi przechowywania danych

Platforma Azure oferuje kilka usług do przechowywania danych w zależności od potrzeb. Najczęstsze usługi danych dla deweloperów platformy .NET to:

* [Usługa Azure SQL Database:](https://docs.microsoft.com/azure/sql-database/)Jeśli chcesz przeprowadzić migrację aplikacji, która już używa programu SQL Server do chmury, usługa Azure SQL Database jest naturalnym miejscem do uruchomienia. Aby rozpocząć, zobacz [Samouczek: Tworzenie aplikacji ASP.NET na platformie Azure za pomocą bazy danych SQL](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase).

* [Usługa Azure Cosmos DB:](https://docs.microsoft.com/azure/cosmos-db/)Azure Cosmos DB to nowoczesna baza danych przeznaczona dla chmury. Podczas uruchamiania nowej aplikacji, która nie ma jeszcze określonej zależności bazy danych, należy spojrzeć na usługi Azure Cosmos DB. Cosmos DB to dobry wybór dla nowych aplikacji internetowych, mobilnych, gier i IoT, w których ważna jest automatyczna skala, przewidywalna wydajność, krótki czas reakcji i możliwość wykonywania zapytań o dane bez schematu. Aby rozpocząć, zobacz [Szybki start: Tworzenie aplikacji sieci web platformy .NET przy użyciu usługi Azure Cosmos DB przy użyciu interfejsu API SQL i portalu Azure.](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet)

* [Usługa Azure Blob Storage:](https://docs.microsoft.com/azure/storage/)Usługa Azure Blob Storage jest zoptymalizowana pod kątem przechowywania i pobierania dużych obiektów binarnych, takich jak obrazy, pliki i strumienie. Magazyny obiektów umożliwiają zarządzanie bardzo dużymi ilościami danych nieustrukturyzowanych. Aby rozpocząć, zobacz [Szybki start: Tworzenie obiektu blob w magazynie obiektów za pomocą platformy .NET.](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-dotnet)

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Wybieranie odpowiedniego magazynu danych](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview).

## <a name="connect-to-azure-services"></a>Łączenie z usługami platformy Azure

Jeśli używasz programu Visual Studio, można dodać obsługę niektórych usług platformy Azure do projektów. Okno dialogowe **Połączone usługi** w programie Visual Studio umożliwia łatwe dodawanie wszystkich wymaganych odwołań, kodu połączenia i ustawień konfiguracji do projektów. Niektóre powszechnie używane usługi platformy Azure są obsługiwane po wyjęciu z pudełka, takie jak [Magazyn,](/azure/vs-azure-tools-connected-services-storage)Uwierzytelnianie [usługi Azure Active Directory,](/azure/active-directory/develop/vs-active-directory-add-connected-service) [Usługa Azure Key Vault](/azure/key-vault/vs-key-vault-add-connected-service)i Usługi [Cognitive Services,](/azure/cognitive-services/) takie jak [Przetwarzanie komputerowe.](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service) Więcej usług, w tym usługi innych firm, są dostępne jako rozszerzenia w [programie Visual Studio Marketplace](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance).

## <a name="diagnosing-problems-in-the-cloud"></a>Diagnozowanie problemów w chmurze
Po wdrożeniu aplikacji na platformie Azure może wystąpić w przypadkach, w których działała w rozwoju, ale nie na platformie Azure. Poniżej znajdują się dwa dobre miejsca, aby rozpocząć podczas diagnozowania problemów:

* **Zdalne debugowanie z programu Visual Studio:** Większość usług obliczeniowych platformy Azure (w tym usługi omówione w tym dokumencie) obsługuje zdalne debugowanie za pomocą programu Visual Studio i dzienniki uzyskiwania. Aby eksplorować możliwości programu Visual Studio za pomocą aplikacji, otwórz okno narzędzia Cloud Explorer, wpisując "Cloud Explorer" na pasku narzędzi szybkiego uruchamiania programu Visual Studio (w prawym górnym rogu), a następnie znajdź aplikację w drzewie. Aby uzyskać szczegółowe informacje, zobacz [Rozwiązywanie problemów z aplikacją internetową w usłudze Azure App Service przy użyciu programu Visual Studio](https://docs.microsoft.com/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug).

* **Usługa Application Insights:** [Application Insights](https://docs.microsoft.com/azure/application-insights/) to kompletne rozwiązanie do monitorowania wydajności aplikacji (APM), które automatycznie przechwytuje dane diagnostyczne, dane telemetryczne i dane dotyczące wydajności z aplikacji. Aby rozpocząć zbieranie danych diagnostycznych dla aplikacji, zobacz [Rozpoczynanie monitorowania ASP.NET aplikacji sieci Web](https://docs.microsoft.com/azure/application-insights/quick-monitor-portal).

## <a name="next-steps"></a>Następne kroki

* [Wdrażanie pierwszej ASP.NET podstawowej aplikacji sieci Web na platformie Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)
* [Dowiedz się więcej o uwierzytelnianiu w usłudze Azure SDK dla platformy .NET](./sdk/authentication.md)
* [Diagnozowanie błędów w aplikacjach w chmurze](https://blogs.msdn.microsoft.com/webdev/2018/02/07/diagnosing-errors-on-your-cloud-apps)
* Pobierz bezpłatny przewodnik szybki [start platformy Azure dla programów .NET Dla deweloperów platformy Azure](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook)
