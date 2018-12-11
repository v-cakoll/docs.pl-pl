---
title: Bezpieczne przechowywanie wpisów tajnych aplikacji podczas programowania
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Bezpieczne przechowywanie wpisów tajnych aplikacji podczas programowania
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6f5dfbb53b99fec4d7cc66c528fe866c71c2172f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143873"
---
# <a name="storing-application-secrets-safely-during-development"></a>Bezpieczne przechowywanie wpisów tajnych aplikacji podczas programowania

Aby połączyć się z chronionych zasobów i inne usługi, aplikacje platformy ASP.NET Core zazwyczaj należy użyć parametrów połączenia, hasła lub inne poświadczenia, które zawierają poufne informacje. Te elementy poufnych informacji są nazywane *wpisów tajnych*. Jest najlepszym rozwiązaniem jest wykluczającą wpisów tajnych w kodzie źródłowym i na pewno nie do przechowywania wpisów tajnych w kontroli źródła. Zamiast tego należy użyć modelu konfiguracji platformy ASP.NET Core na odczyt kluczy tajnych z bardziej bezpiecznych lokalizacjach.

Należy oddzielić wpisów tajnych dla uzyskiwanie dostępu do programowania i przemieszczania zasobów używanych do uzyskiwania dostępu do zasobów w środowisku produkcyjnym, ponieważ inne osoby będą potrzebowali dostępu do tych różnych zestawów wpisów tajnych. Do przechowywania wpisów tajnych używanych podczas tworzenia, wspólnego podejścia są przechowywanie wpisów tajnych w zmiennych środowiskowych lub za pomocą narzędzia ASP.NET Core klucz tajny menedżera. Dla bardziej bezpieczne przechowywanie w środowiskach produkcyjnych mikrousługi można przechowywać wpisy tajne w usłudze Azure Key Vault.

## <a name="storing-secrets-in-environment-variables"></a>Przechowywanie kluczy tajnych w zmiennych środowiskowych

Jest jednym ze sposobów odróżnienia wpisy tajne z kodu źródłowego, deweloperzy mogą ustawić oparte na ciągach wpisów tajnych jako [zmienne środowiskowe](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) na swoich komputerach deweloperskich. Użycie zmiennych środowiskowych do przechowywania wpisów tajnych za pomocą nazwy hierarchiczne, (te zagnieżdżonego w sekcji konfiguracji), Utwórz nazwę zmiennych środowiskowych, która zawiera pełnej hierarchii o nazwie klucza tajnego, lista z dwukropkiem (:).

Na przykład ustawienie zmiennej środowiskowej rejestrowania: LogLevel:Default debugowania byłaby równoważna wartości konfiguracji z następującego pliku JSON:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Dostępu do tych wartości w zmiennych środowiskowych, aplikacja musi jedynie może wywołać jej ConfigurationBuilder AddEnvironmentVariables przy konstruowaniu obiektu IConfigurationRoot.

Należy pamiętać, że zmienne środowiskowe zazwyczaj są przechowywane jako zwykły tekst, więc w przypadku naruszenia zabezpieczeń komputera lub proces, za pomocą zmiennych środowiskowych, wartości zmiennych środowiskowych będą widoczne.

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>Przechowywanie wpisów tajnych przy użyciu Menedżera klucz tajny platformy ASP.NET Core

ASP.NET Core [Menedżera klucz tajny](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) narzędzie udostępnia inną metodą przechowywanie wpisów tajnych z kodu źródłowego. Aby użyć narzędzia menedżera klucz tajny, należy dołączyć odwołanie narzędzia (DotNetCliToolReference) do pakietu Microsoft.Extensions.SecretManager.Tools w pliku projektu. Po tej zależności i zostało przywrócone, polecenia dotnet wpisami tajnymi użytkowników może służyć do ustawiania wartości kluczy tajnych z wiersza polecenia. Tych kluczy tajnych będą przechowywane w pliku JSON w katalogu profilu użytkownika (Szczegóły różnią się zależnie od systemu operacyjnego), od kodu źródłowego.

Wpisy tajne ustawione przez narzędzie Menedżer klucz tajny są uporządkowane według właściwości UserSecretsId projektu, który jest używany wpisy tajne. W związku z tym należy ustawić właściwość UserSecretsId w pliku projektu (jak pokazano w poniższym fragmencie kodu). Rzeczywisty ciąg używany jako identyfikator nie jest ważna, tak długo, jak jest unikatowa w projekcie.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Przy użyciu kluczy tajnych przechowywanych przy użyciu Menedżera klucz tajny aplikacji odbywa się przez wywołanie metody AddUserSecrets&lt;T&gt; wystąpieniu ConfigurationBuilder obejmujący wpisów tajnych aplikacji w konfiguracji. Parametr ogólny T powinien być typem z zestawu, która UserSecretId została zastosowana do. Zazwyczaj przy użyciu AddUserSecrets&lt;uruchamiania&gt; jest w dobrym stanie.


>[!div class="step-by-step"]
>[Poprzednie](authorization-net-microservices-web-applications.md)
>[dalej](azure-key-vault-protects-secrets.md)