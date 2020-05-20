---
title: Konfiguracja scentralizowana
description: Scentralizowana konfiguracja aplikacji natywnych w chmurze przy użyciu usługi Azure App Configuration i magazynu AzureKey.
ms.date: 05/13/2020
ms.openlocfilehash: d389d29dcdb1db5162d95370d181ab5a85d72dc8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614230"
---
# <a name="centralized-configuration"></a>Konfiguracja scentralizowana

W przeciwieństwie do aplikacji monolitycznej, w której wszystko działa w ramach jednego wystąpienia, aplikacja natywna w chmurze składa się z niezależnych usług dystrybuowanych na maszynach wirtualnych, kontenerach i regionach geograficznych. Zarządzanie ustawieniami konfiguracji dla dziesiątek usług zależnych może być trudne. Duplikowanie kopii ustawień konfiguracji w różnych lokalizacjach jest podatne na błędy i trudne do zarządzania. Scentralizowana konfiguracja jest wymaganiem krytycznym dla rozproszonych aplikacji natywnych w chmurze.

Zgodnie z opisem w [rozdziale 1](introduction.md)rekomendacje dotyczące aplikacji 12-Factor wymagają ścisłego rozdzielenia kodu i konfiguracji. Konfiguracja musi być przechowywana zewnętrznie z aplikacji i w razie konieczności. Przechowywanie wartości konfiguracyjnych jako stałych lub wartości literałów w kodzie jest naruszeniem. Te same wartości konfiguracyjne są często używane przez wiele usług w tej samej aplikacji. Ponadto musimy obsługiwać te same wartości w wielu środowiskach, takich jak programowanie, testowanie i produkcja. Najlepszym rozwiązaniem jest przechowywanie ich w scentralizowanym magazynie konfiguracji.

W chmurze platformy Azure prezentowane są kilka doskonałych opcji.

## <a name="azure-app-configuration"></a>Azure App Configuration

[Konfiguracja aplikacji platformy Azure](https://docs.microsoft.com/azure/azure-app-configuration/overview) to w pełni zarządzana usługa platformy Azure, która przechowuje ustawienia konfiguracji inne niż tajne w bezpiecznej, scentralizowanej lokalizacji. Przechowywane wartości mogą być współużytkowane przez wiele usług i aplikacji.

Usługa jest prosta do użycia i oferuje kilka korzyści:

- Elastyczne reprezentacje klucza/wartości i mapowania
- Tagowanie przy użyciu etykiet platformy Azure
- Dedykowany interfejs użytkownika do zarządzania
- Szyfrowanie informacji poufnych
- Wykonywanie zapytań i pobieranie wsadowe

Konfiguracja aplikacji platformy Azure zachowuje zmiany wprowadzone w ustawieniach klucz-wartość przez siedem dni. Funkcja migawek do momentu umożliwia odtworzenie historii ustawienia, a nawet wycofanie dla niepowodzenia wdrożenia.

Konfiguracja aplikacji automatycznie buforuje każde ustawienie, aby uniknąć nadmiernych wywołań do magazynu konfiguracji. Operacja odświeżania czeka, aż wygaśnie wartość ustawienia w celu zaktualizowania tego ustawienia, nawet w przypadku zmiany jego wartości w magazynie konfiguracji. Domyślny czas wygaśnięcia pamięci podręcznej wynosi 30 sekund. Można przesłonić czas wygaśnięcia.

Konfiguracja aplikacji szyfruje wszystkie wartości konfiguracji podczas przesyłania i przechowywania. Nazwy kluczy i etykiety są używane jako indeksy do pobierania danych konfiguracji i nie są szyfrowane.

Mimo że konfiguracja aplikacji zapewnia zabezpieczenia z ograniczeniami, Azure Key Vault jest nadal najlepszym miejscem do przechowywania wpisów tajnych aplikacji. Key Vault zapewnia szyfrowanie na poziomie sprzętu, szczegółowe zasady dostępu oraz operacje zarządzania, takie jak rotacja certyfikatów. Można utworzyć wartości konfiguracji aplikacji, które odwołują się do wpisów tajnych przechowywanych w Key Vault.

## <a name="azure-key-vault"></a>W usłudze Azure Key Vault

Key Vault to usługa zarządzana w celu bezpiecznego przechowywania i uzyskiwania dostępu do wpisów tajnych. Wpis tajny to dowolny zasób, do którego dostęp powinien być ściśle kontrolowany. Przykładowe wpisy tajne to klucze interfejsu API, hasła i certyfikaty. Magazyn jest logiczną grupą kluczy tajnych.

Usługa Key Vault znacznie ogranicza prawdopodobieństwo przypadkowego ujawnienia wpisów tajnych. Korzystając z usługi Key Vault, deweloperzy aplikacji nie muszą już przechowywać informacji zabezpieczeń w aplikacji. To rozwiązanie eliminuje konieczność przechowywania tych informacji w kodzie. Na przykład aplikacja może potrzebować połączenia z bazą danych. Zamiast przechowywać parametry połączenia w kodzie aplikacji można je przechowywać bezpiecznie w usłudze Key Vault.

Twoje aplikacje mogą bezpiecznie uzyskiwać dostęp do potrzebnych informacji za pomocą identyfikatorów URI. Te identyfikatory URI umożliwiają aplikacjom pobranie określonych wersji wpisu tajnego. Nie ma potrzeby pisania niestandardowego kodu w celu ochrony informacji poufnych przechowywanych w Key Vault.

Dostęp do Key Vault wymaga właściwego uwierzytelniania i autoryzacji wywołującego. Zazwyczaj każda mikrousługa w chmurze używa kombinacji ClientId/ClientSecret. Ważne jest, aby zachować te poświadczenia poza kontrolą źródła. Najlepszym rozwiązaniem jest ustawienie ich w środowisku aplikacji. Bezpośredni dostęp do Key Vault z AKS można osiągnąć przy użyciu [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol).

## <a name="configuration-in-eshop"></a>Konfiguracja w eShop

Aplikacja eShopOnContainers obejmuje lokalne pliki ustawień aplikacji z każdą mikrousługą. Te pliki są sprawdzane w kontroli źródła, ale nie zawierają wpisów tajnych, takich jak parametry połączenia lub klucze interfejsu API. W środowisku produkcyjnym poszczególne ustawienia mogą zostać zastąpione zmiennymi środowiskowymi dla poszczególnych usług. Wprowadzanie wpisów tajnych w zmiennych środowiskowych jest powszechną metodą obsługi hostowanych aplikacji, ale nie zapewnia centralnego magazynu konfiguracji. Aby zapewnić obsługę scentralizowanego zarządzania ustawieniami konfiguracji, każda mikrousługa zawiera ustawienie umożliwiające przełączenie między użyciem ustawień lokalnych lub Azure Key Vault ustawień.

## <a name="references"></a>Dokumentacja

- [Architektura eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [Organizowanie aplikacji mikrousług i aplikacji z wieloma kontenerami w celu zapewnienia wysokiej skalowalności i dostępności](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications)
- [Azure API Management](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)
- [Przegląd Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
- [Azure Cache for Redis](https://azure.microsoft.com/services/cache/)
- [Interfejs API usługi Azure Cosmos DB dla bazy danych MongoDB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Omówienie usługi Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)
- [eShopOnContainers: Utwórz klaster Kubernetes w AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers: Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[Poprzedni](deploy-eshoponcontainers-azure.md) 
> [Dalej](scale-applications.md)
