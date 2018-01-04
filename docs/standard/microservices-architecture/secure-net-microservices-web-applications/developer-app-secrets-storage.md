---
title: Bezpieczne przechowywanie kluczy tajnych aplikacji podczas tworzenia
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Bezpieczne przechowywanie kluczy tajnych aplikacji podczas tworzenia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f70f7c741da9653745e4f542125986c701b5d22d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="storing-application-secrets-safely-during-development"></a>Bezpieczne przechowywanie kluczy tajnych aplikacji podczas tworzenia

Aby połączyć się z chronionych zasobów i innych usług, aplikacji platformy ASP.NET Core zwykle muszą używać parametrów połączenia, hasła lub innych poświadczeń, które zawierają poufne informacje. Te elementy poufnych informacji są nazywane *kluczy tajnych*. Jest to najlepsze rozwiązanie, aby nie dołączać kluczy tajnych w kodzie źródłowym i na pewno nie do przechowywania kluczy tajnych w kontroli źródła. Zamiast tego należy używać model konfiguracji platformy ASP.NET Core odczytu kluczy tajnych z bardziej bezpiecznych lokalizacjach.

Rozdziel hasła podczas uzyskiwania dostępu do rozwoju i przemieszczania są używane na potrzeby uzyskiwania dostępu do zasobów w środowisku produkcyjnym, ponieważ inne osoby wymaga dostępu do tych kluczy tajnych różne zestawy zasobów. Do przechowywania kluczy tajnych używanych podczas tworzenia, wspólnego podejścia są przechowywanie kluczy tajnych w zmiennych środowiskowych lub za pomocą narzędzia platformy ASP.NET Core klucz tajny menedżera. Dla bardziej bezpieczny magazyn w środowiskach produkcyjnych mikrousług można przechowywać kluczy tajnych w usłudze Azure Key Vault.

## <a name="storing-secrets-in-environment-variables"></a>Przechowywanie kluczy tajnych w zmiennych środowiskowych

Jest jednym ze sposobów przechowywać klucze tajne poza kodu źródłowego dla deweloperów można ustawić na podstawie ciągu kluczy tajnych jako [zmiennych środowiskowych](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) na swoich komputerach programowanie. Użycie zmiennych środowiskowych do przechowywania kluczy tajnych nazwami hierarchicznych (te zagnieżdżona w sekcji konfiguracji), Utwórz nazwę zmiennych środowiskowych, która zawiera hierarchię Pełna nazwa klucza tajnego, rozdzielone dwukropkiem (:).

Na przykład ustawienie zmiennej środowiskowej rejestrowania: LogLevel:Default debugowania będzie odpowiednikiem wartości konfiguracji z następującego pliku JSON:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Aby uzyskać dostęp do tych wartości w zmiennych środowiskowych, aplikacja tylko musi wywołać jej ConfigurationBuilder AddEnvironmentVariables podczas konstruowania obiektu IConfigurationRoot.

Należy pamiętać, że zmienne środowiskowe zazwyczaj są przechowywane jako zwykły tekst, tak więc w przypadku naruszenia zabezpieczeń komputera lub proces o zmiennych środowiskowych, wartości zmiennych środowiskowych będzie widoczna.

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a>Przechowywanie kluczy tajnych za pomocą Menedżera platformy ASP.NET Core klucz tajny

Platformy ASP.NET Core [Manager klucz tajny](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) narzędzia zawiera inną metodą przechowywanie kluczy tajnych z kodu źródłowego. Aby użyć narzędzia menedżera klucz tajny, obejmują informacje dotyczące narzędzi (DotNetCliToolReference) do pakietu Microsoft.Extensions.SecretManager.Tools w pliku projektu. Po tym zależności i zostało przywrócone, polecenie kluczy tajnych użytkownika dotnet może służyć do wartości kluczy tajnych w wierszu polecenia. Te klucze tajne będą przechowywane w pliku JSON w katalogu profilu użytkownika (Szczegóły różnią się zależnie od systemu operacyjnego), od kodu źródłowego.

Klucze tajne ustawione przez narzędzie Menedżer klucz tajny są zorganizowane według właściwości UserSecretsId projektu, która używa kluczy tajnych. W związku z tym należy ustaw właściwość UserSecretsId w pliku projektu (jak pokazano w poniższy fragment). Rzeczywisty ciąg używany jako identyfikator nie jest ważne, ile jest unikatowa w projekcie.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Przy użyciu kluczy tajnych przechowywanych w aplikacji przy użyciu Menedżera klucz tajny odbywa się przez wywołanie metody AddUserSecrets&lt;T&gt; w wystąpieniu ConfigurationBuilder, aby uwzględnić klucze tajne dla aplikacji w swojej konfiguracji. Parametr generyczny T powinien być typem z zestawu, które zostało zastosowane UserSecretId. Zazwyczaj przy użyciu AddUserSecrets&lt;uruchamiania&gt; funkcjonuje prawidłowo.


>[!div class="step-by-step"]
[Poprzednie] (autoryzacji net mikrousług web-applications.md) [dalej] (azure-key magazynu chroni — secrets.md)
