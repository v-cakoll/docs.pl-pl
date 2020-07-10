---
title: Wprowadzenie do platformy Azure i platformy .NET
description: Poznaj podstawowe informacje dotyczące platformy Azure i platformy .NET.
ms.date: 06/20/2020
ms.openlocfilehash: c64de800f47035b22cc62b6d08cb7b71246984a7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174325"
---
# <a name="introduction-to-azure-and-net"></a>Wprowadzenie do platform Azure i .NET

Ten dokument zawiera omówienie najważniejszych pojęć i usług, które deweloperzy muszą znać, aby rozpocząć opracowywanie aplikacji przy użyciu usług platformy Azure.

## <a name="key-concepts"></a>Kluczowe pojęcia

**Konto platformy Azure**: Twoje konto platformy Azure jest poświadczeniem używanym do logowania się do usług platformy Azure, takich jak [Witryna azure Portal](https://portal.azure.com) lub [Cloud Shell](https://shell.azure.com). Jeśli nie masz konta platformy Azure, możesz [utworzyć je bezpłatnie](https://azure.microsoft.com/free/dotnet/).

**Subskrypcja platformy Azure**: subskrypcja jest planem rozliczeniowym, w którym są tworzone zasoby platformy Azure. Subskrypcje mogą być indywidualnymi subskrypcjami lub subskrypcjami przedsiębiorstwa zarządzanymi przez firmę. Twoje konto platformy Azure może być skojarzone z wieloma subskrypcjami. W takim przypadku upewnij się, że wybierasz poprawną subskrypcję podczas tworzenia zasobów. Aby uzyskać więcej informacji, zobacz temat [Omówienie kont, subskrypcji i rozliczeń](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing).

> [!TIP]
> Jeśli masz subskrypcję programu Visual Studio, [masz miesięczne kredyty na korzystanie z platformy Azure, które oczekują na aktywowanie](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

**Grupa zasobów**: grupy zasobów to sposób organizowania zasobów platformy Azure w grupy do zarządzania. Zasoby utworzone na platformie Azure będą przechowywane w grupie zasobów podobnej do zapisywania pliku w folderze na komputerze.

**Hosting**: Aby uruchomić kod na platformie Azure, musi on być hostowany w usłudze obsługującej wykonywanie kodu dostarczonego przez użytkownika.

**Zarządzane usługi**: platforma Azure udostępnia niektóre usługi, które udostępniają dane lub informacje na platformie Azure, a implementacja platformy Azure podejmuje odpowiednie działania. Przykładem jest platforma Azure Blob Storage, w której udostępniamy pliki i platforma Azure obsługuje odczytywanie, zapisywanie i utrwalanie.

**Zestaw Azure SDK dla platformy .NET**: czasami określane jako **biblioteki platformy Azure dla platformy .NET**, zbiorczo odnoszą się do [pakietów NuGet](https://www.nuget.org/profiles/azure-sdk) instalowanych w projekcie, które udostępniają różne interakcje i funkcje z usługami platformy Azure. Te pakiety obejmują również biblioteki zarządzania używane do udostępniania zasobów i administrowania nimi.

## <a name="choosing-a-hosting-option"></a>Wybieranie opcji hostingu

Hosting na platformie Azure można podzielić na trzy kategorie.

* **Infrastruktura jako usługa (IaaS)**: w przypadku programu IaaS należy zainicjować obsługę potrzebnych maszyn wirtualnych wraz ze skojarzonymi składnikami sieci i magazynu. Następnie wdrażasz dowolne oprogramowanie i aplikacje, które chcesz umieścić na tych maszynach wirtualnych. Ten model jest najbliżej tradycyjnego środowiska lokalnego, z tą różnicą, że firma Microsoft zarządza infrastrukturą. Nadal zarządzasz indywidualnymi maszynami wirtualnymi, w tym systemem operacyjnym, oprogramowaniem niestandardowym i aktualizacjami zabezpieczeń.

* **Platforma jako usługa (PaaS)**: PaaS udostępnia zarządzane środowisko hostingu, w którym można wdrażać aplikację bez konieczności zarządzania maszynami wirtualnymi ani zasobami sieciowymi. Na przykład zamiast tworzenia poszczególnych maszyn wirtualnych określasz liczbę wystąpień, a usługa aprowizuje i konfiguruje niezbędne zasoby oraz zarządza nimi. Usługa Azure App Service jest przykładem usługi PaaS.
  
* **Funkcja as-a-Service (FaaS)**: często określana jako Obliczanie bezserwerowe, FaaS jest jeszcze większa niż PaaS w celu podzielenia problemów ze środowiskiem hostingu. Zamiast tworzyć wystąpienia obliczeniowe, a następnie wdrażać kod w tych wystąpieniach, należy wdrożyć kod i usługa automatycznie ją uruchamia. Nie musisz administrować zasobami obliczeniowymi. Platforma bezproblemowo skaluje swój kod w górę lub w dół do dowolnego poziomu, który jest niezbędny do obsługi ruchu, i płacisz tylko wtedy, gdy kod jest uruchomiony. Azure Functions to usługa FaaS.

Ogólnie rzecz biorąc, im bardziej preferuje modele FaaS i PaaS, tym większe korzyści będą wykonywane w chmurze. Poniżej znajduje się podsumowanie trzech typowych opcji hostingu na platformie Azure i ich wyboru.

* [Azure App Service](/azure/app-service/app-service-value-prop-what-is): Jeśli chcesz hostować aplikację sieci Web lub usługę, najpierw zapoznaj się z App Service. Aby rozpocząć pracę z aplikacjami App Service i ASP.NET, WCF i ASP.NET Core, zobacz [Tworzenie aplikacji internetowej ASP.NET Core na platformie Azure](/azure/app-service/app-service-web-get-started-dotnet).

* [Azure Functions](/azure/azure-functions/functions-overview): Azure Functions jest doskonałym rozwiązaniem dla przepływów pracy opartych na zdarzeniach. Przykłady obejmują odpowiadanie na elementy webhook, przetwarzanie elementów w kolejkach lub w magazynie obiektów blob oraz czasomierze. Aby rozpocząć pracę z usługą Azure Functions, zobacz [Tworzenie pierwszej funkcji przy użyciu programu Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio).

* [Virtual Machines platformy Azure](/azure/virtual-machines/): Jeśli App Service nie spełnia wymagań związanych z hostem istniejącej aplikacji z powodu określonych zależności, Virtual Machines będzie najłatwiej rozpocząć pracę. Aby rozpocząć pracę z usługami Virtual Machines i ASP.NET lub WCF, zobacz [wdrażanie aplikacji ASP.NET na maszynie wirtualnej platformy Azure](https://tutorials.visualstudio.com/aspnet-vm/intro).

> [!TIP]
> Aby uzyskać więcej informacji na temat wybierania usługi, zobacz [Wybieranie usługi obliczeniowej Azure dla swojej aplikacji](/azure/architecture/guide/technology-choices/compute-decision-tree).

## <a name="choose-a-data-storage-service"></a>Wybieranie usługi magazynu danych

Platforma Azure oferuje kilka usług służących do przechowywania danych w zależności od potrzeb. Najbardziej typowymi usługami danych dla deweloperów platformy .NET są:

* [Azure SQL Database](/azure/sql-database/): Jeśli zamierzasz przeprowadzić migrację aplikacji, która już używa SQL Server do chmury, Azure SQL Database jest naturalnym miejscem do rozpoczęcia. Aby rozpocząć, zobacz [Samouczek: Tworzenie aplikacji ASP.NET na platformie Azure przy użyciu SQL Database](/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase).

* [Azure Cosmos DB](/azure/cosmos-db/): Azure Cosmos DB jest nowoczesnej bazy danych zaprojektowanej dla chmury. Podczas uruchamiania nowej aplikacji, która nie ma jeszcze określonej zależności bazy danych, należy przyjrzeć się Azure Cosmos DB. Cosmos DB to dobry wybór w przypadku nowych aplikacji sieci Web, mobilnych, gier i IoT, w których automatyczne skalowanie, przewidywalna wydajność, szybkie czasy reakcji i możliwość wykonywania zapytań dotyczących danych bez schematu jest ważna. Aby rozpocząć, zobacz [Szybki Start: Tworzenie aplikacji sieci Web platformy .NET z Azure Cosmos dB przy użyciu interfejsu API SQL i Azure Portal](/azure/cosmos-db/create-sql-api-dotnet).

* [Azure BLOB Storage](/azure/storage/): usługa Azure Blob Storage jest zoptymalizowana pod kątem przechowywania i pobierania dużych obiektów binarnych, takich jak obrazy, pliki i strumienie. Magazyny obiektów umożliwiają zarządzanie bardzo dużymi ilościami danych bez struktury. Aby rozpocząć, zobacz [Szybki Start: korzystanie z platformy .NET do tworzenia obiektów BLOB w magazynie obiektów](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Wybieranie odpowiedniego magazynu danych](/azure/architecture/guide/technology-choices/data-store-overview).

## <a name="connect-to-azure-services"></a>Łączenie z usługami platformy Azure

Jeśli używasz programu Visual Studio, możesz dodać obsługę określonych usług platformy Azure do swoich projektów. Okno dialogowe **połączone usługi** w programie Visual Studio zapewnia łatwy sposób dodawania do projektów wszystkich wymaganych odwołań, kodu połączenia i ustawień konfiguracji. Niektóre często używane usługi platformy Azure są obsługiwane przez program, taki jak [Magazyn](/azure/vs-azure-tools-connected-services-storage), [Azure Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) uwierzytelnianie, [Azure Key Vault](/azure/key-vault/vs-key-vault-add-connected-service)i [Cognitive Services](/azure/cognitive-services/) na przykład [Przetwarzanie obrazów](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service). Więcej usług, w tym usług innych firm, jest dostępnych jako rozszerzenia w [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance).

## <a name="using-the-azure-sdk-for-net"></a>Korzystanie z zestawu Azure SDK dla platformy .NET

Jeśli używasz zestawu Azure SDK dla platformy .NET do uzyskiwania dostępu do zasobów platformy Azure lub zarządzania nimi, zwróć uwagę na następujące kwestie:

* **Uwierzytelnianie**: w wielu bibliotekach w zestawie SDK używana jest wspólna infrastruktura uwierzytelniania, podczas gdy niektóre biblioteki używają mechanizmów uwierzytelniania specyficznych dla usługi, do których są zużywane. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie przy użyciu zestawu Azure SDK dla platformy .NET](authentication.md).
* **Rejestrowanie**: Jeśli jest obsługiwana, biblioteki klienta obejmują możliwość rejestrowania operacji biblioteki klienta. Aby uzyskać więcej informacji, zobacz [Rejestrowanie przy użyciu zestawu Azure SDK dla platformy .NET](logging.md).
* **Interfejs API REST**: zestaw Azure SDK dla platformy .NET jest abstrakcją utworzoną w [interfejsie API REST platformy Azure](/rest/api/azure/). W razie potrzeby można użyć interfejsu API REST platformy Azure zamiast lub obok zestawu Azure SDK dla platformy .NET.

## <a name="diagnosing-problems-in-the-cloud"></a>Diagnozowanie problemów w chmurze
Po wdrożeniu aplikacji na platformie Azure można wypróbować przypadki, w których działały w programowaniu, ale nie na platformie Azure. Poniżej znajdują się dwa dobre miejsca do uruchomienia podczas diagnozowania problemów:

* **Zdalne debugowanie z programu Visual Studio**: większość usług obliczeniowych platformy Azure (łącznie z usługami opisanymi w tym dokumencie) obsługuje zdalne debugowanie przy użyciu programu Visual Studio i pobieranie dzienników. Aby poznać możliwości programu Visual Studio w aplikacji, Otwórz okno narzędzia Cloud Explorer, wpisując "Cloud Explorer" do paska narzędzi szybkiego uruchamiania programu Visual Studio (w prawym górnym rogu), a następnie zlokalizuj swoją aplikację w drzewie. Aby uzyskać szczegółowe informacje, zobacz [Rozwiązywanie problemów z aplikacją sieci Web w Azure App Service przy użyciu programu Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug).

* **Application Insights**: [Application Insights](/azure/application-insights/) to kompletne rozwiązanie do monitorowania wydajności aplikacji (APM), które automatycznie przechwytuje dane diagnostyczne oraz dane telemetryczne i wydajności z aplikacji. Aby rozpocząć zbieranie danych diagnostycznych dla aplikacji, zobacz [Rozpoczynanie monitorowania aplikacji sieci Web ASP.NET](/azure/application-insights/quick-monitor-portal).

## <a name="next-steps"></a>Następne kroki

* [Wdrażanie pierwszej aplikacji sieci Web ASP.NET Core na platformie Azure](/azure/app-service/app-service-web-get-started-dotnet)
* [Informacje o uwierzytelnianiu w zestawie Azure SDK dla platformy .NET](authentication.md)
* [Diagnozowanie błędów w aplikacjach w chmurze](https://devblogs.microsoft.com/aspnet/diagnosing-errors-on-your-cloud-apps/)
* Pobierz bezpłatną książkę elektroniczną [Przewodnik Szybki Start platformy Azure dla deweloperów platformy .NET](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook)
