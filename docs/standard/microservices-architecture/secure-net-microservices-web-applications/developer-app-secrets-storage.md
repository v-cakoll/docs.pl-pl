---
title: Bezpieczne przechowywanie kluczy tajnych aplikacji podczas jej tworzenia
description: Zabezpieczenia w Mikrousługach .NET i aplikacji sieci Web - odradzamy przechowywanie wpisów tajnych aplikacji, takie jak hasła, parametry połączenia lub klucze interfejsu API w kontroli źródła, informacje o opcjach, używane w programie ASP.NET Core, w szczególności należy zrozumieć, jak obsługiwać " wpisy tajne".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019428"
---
# <a name="store-application-secrets-safely-during-development"></a>Bezpiecznie Store wpisów tajnych aplikacji podczas programowania

Aby połączyć się z chronionych zasobów i inne usługi, aplikacje platformy ASP.NET Core zazwyczaj należy użyć parametrów połączenia, hasła lub inne poświadczenia, które zawierają poufne informacje. Te elementy poufnych informacji są nazywane *wpisów tajnych*. Jest najlepszym rozwiązaniem, aby nie zawierać wpisy tajne w kodzie źródłowym i upewniając się, nie będą przechowywane klucze tajne w kontroli źródła. Zamiast tego należy użyć modelu konfiguracji platformy ASP.NET Core na odczyt kluczy tajnych z bardziej bezpiecznych lokalizacjach.

Muszą być rozdzielone wpisów tajnych dla uzyskiwanie dostępu do programowania i przemieszczania zasobów z nich używane do uzyskiwania dostępu do zasobów w środowisku produkcyjnym, ponieważ inne osoby będą potrzebowali dostępu do tych różnych zestawów wpisów tajnych. Do przechowywania wpisów tajnych używanych podczas tworzenia, wspólnego podejścia są przechowywanie wpisów tajnych w zmiennych środowiskowych lub za pomocą narzędzia ASP.NET Core klucz tajny menedżera. Dla bardziej bezpieczne przechowywanie w środowiskach produkcyjnych mikrousługi można przechowywać wpisy tajne w usłudze Azure Key Vault.

## <a name="store-secrets-in-environment-variables"></a>Store wpisów tajnych w zmiennych środowiskowych

Jest jednym ze sposobów odróżnienia wpisy tajne z kodu źródłowego, deweloperzy mogą ustawić oparte na ciągach wpisów tajnych jako [zmienne środowiskowe](/aspnet/core/security/app-secrets#environment-variables) na swoich komputerach deweloperskich. Gdy zmienne środowiskowe są używane do przechowywania wpisów tajnych za pomocą nazw hierarchicznych, takich jak te zagnieżdżonego w sekcji konfiguracji nazwę zmienne, aby uwzględnić hierarchię pełną sekcjach rozdzielonych z dwukropkiem (:).

Na przykład ustawienie zmiennej środowiskowej `Logging:LogLevel:Default` do `Debug` wartość byłaby równoważna wartości konfiguracji z następującego pliku JSON:

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

Należy pamiętać, że zmienne środowiskowe są często przechowywane jako zwykły tekst, więc w przypadku naruszenia zabezpieczeń komputera lub proces, za pomocą zmiennych środowiskowych, wartości zmiennych środowiskowych będą widoczne.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>Wpisy tajne Store Menedżera wpisu tajnego za pomocą platformy ASP.NET Core

ASP.NET Core [Menedżera klucz tajny](/aspnet/core/security/app-secrets#secret-manager) narzędzie udostępnia inną metodą przechowywanie wpisów tajnych z kodu źródłowego. Aby użyć narzędzia Menedżer klucz tajny, należy zainstalować pakiet **Microsoft.Extensions.Configuration.SecretManager** w pliku projektu. Po tej zależności jest obecny i zostało przywrócone, `dotnet user-secrets` polecenia można ustawić wartości kluczy tajnych z wiersza polecenia. Tych kluczy tajnych będą przechowywane w pliku JSON w katalogu profilu użytkownika (Szczegóły różnią się zależnie od systemu operacyjnego), od kodu źródłowego.

Wpisy tajne ustawione przez narzędzie Menedżer klucz tajny są uporządkowane według `UserSecretsId` właściwości projektu, który jest używany wpisy tajne. W związku z tym należy ustawić właściwość UserSecretsId w pliku projektu, jak pokazano w poniższym fragmencie kodu. Wartość domyślna to identyfikator GUID przypisany przez program Visual Studio, ale rzeczywistego ciągu nie jest ważna, tak długo, jak jest unikatowa w komputerze.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Przy użyciu kluczy tajnych przechowywanych przy użyciu Menedżera klucz tajny aplikacji odbywa się przez wywołanie metody `AddUserSecrets<T>` wystąpieniu ConfigurationBuilder obejmujący wpisów tajnych aplikacji w konfiguracji. Parametr ogólny T powinien być typem z zestawu, która UserSecretId została zastosowana do. Zazwyczaj przy użyciu `AddUserSecrets<Startup>` jest w dobrym stanie.

`AddUserSecrets<Startup>()` Są objęte domyślne opcje dotyczące środowiska programistycznego, korzystając z `CreateDefaultBuilder` method in Class metoda *Program.cs*.

>[!div class="step-by-step"]
>[Poprzednie](authorization-net-microservices-web-applications.md)
>[dalej](azure-key-vault-protects-secrets.md)
