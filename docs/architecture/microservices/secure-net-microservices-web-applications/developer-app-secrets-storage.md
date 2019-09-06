---
title: Bezpieczne przechowywanie kluczy tajnych aplikacji podczas jej tworzenia
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — nie przechowuj wpisów tajnych aplikacji, takich jak hasła, parametry połączenia lub klucze interfejsu API w kontroli źródła, Poznaj opcje, których można użyć w ASP.NET Core, w szczególności musisz zrozumieć, jak obsługiwać "użytkownika wpisy tajne ".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296485"
---
# <a name="store-application-secrets-safely-during-development"></a>Bezpieczne przechowywanie wpisów tajnych aplikacji podczas opracowywania

Aby nawiązać połączenie z chronionymi zasobami i innymi usługami, ASP.NET Core aplikacje zwykle muszą używać parametrów połączenia, haseł lub innych poświadczeń, które zawierają informacje poufne. Te poufne informacje są nazywane *tajemnicami*. Najlepszym rozwiązaniem jest, aby nie uwzględnić wpisów tajnych w kodzie źródłowym i upewnić się, że wpisy tajne nie są przechowywane w kontroli źródła. Zamiast tego należy użyć modelu konfiguracji ASP.NET Core, aby odczytać wpisy tajne z bardziej bezpiecznych lokalizacji.

Należy oddzielić wpisy tajne, aby uzyskać dostęp do zasobów deweloperskich i przejściowych z tych, które są używane do uzyskiwania dostępu do zasobów produkcyjnych, ponieważ różne osoby będą potrzebować dostępu do tych różnych zestawów kluczy tajnych. Aby przechowywać wpisy tajne używane podczas opracowywania, typowe podejścia do przechowywania wpisów tajnych w zmiennych środowiskowych lub za pomocą narzędzia ASP.NET Core Secret Manager. Aby zapewnić większy bezpieczny magazyn w środowiskach produkcyjnych, mikrousługi mogą przechowywać wpisy tajne w Azure Key Vault.

## <a name="store-secrets-in-environment-variables"></a>Przechowuj wpisy tajne w zmiennych środowiskowych

Jednym ze sposobów utrzymywania tajemnicy kodu źródłowego jest to, aby deweloperzy mogli ustawiać klucze tajne na podstawie ciągów jako [zmienne środowiskowe](/aspnet/core/security/app-secrets#environment-variables) na swoich maszynach deweloperskich. W przypadku używania zmiennych środowiskowych do przechowywania wpisów tajnych z nazwami hierarchicznymi, takimi jak zagnieżdżone w sekcjach konfiguracji, należy nazwać zmienne, aby uwzględnić pełną hierarchię jej sekcji, rozdzielaną średnikami (:).

Na przykład ustawienie zmiennej `Logging:LogLevel:Default` środowiskowej na `Debug` wartość będzie równoważne wartości konfiguracji z następującego pliku JSON:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Aby uzyskać dostęp do tych wartości ze zmiennych środowiskowych, aplikacja po prostu musi wywołać AddEnvironmentVariables na ConfigurationBuilder podczas konstruowania obiektu IConfigurationRoot.

Należy pamiętać, że zmienne środowiskowe są zwykle przechowywane jako zwykły tekst, więc jeśli komputer lub proces ze zmiennymi środowiskowymi zostanie naruszony, wartości zmiennych środowiskowych będą widoczne.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>Przechowywanie wpisów tajnych za pomocą programu ASP.NET Core Secret Manager

Narzędzie ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) zapewnia kolejną metodę utrzymywania wpisów tajnych z kodu źródłowego. Aby użyć narzędzia Secret Manager, zainstaluj pakiet **Microsoft. Extensions. Configuration. SecretManager** w pliku projektu. Gdy ta zależność jest obecna i przywrócona, `dotnet user-secrets` polecenie może służyć do ustawiania wartości wpisów tajnych z wiersza polecenia. Te wpisy tajne będą przechowywane w pliku JSON w katalogu profilu użytkownika (szczegóły różnią się w zależności od systemu operacyjnego), a nie od kodu źródłowego.

Wpisy tajne ustawiane przez narzędzie tajnego Menedżera są `UserSecretsId` zorganizowane według właściwości projektu, który używa wpisów tajnych. W związku z tym należy ustawić właściwość UserSecretsId w pliku projektu, jak pokazano w poniższym fragmencie kodu. Wartość domyślna to identyfikator GUID przypisany przez program Visual Studio, ale rzeczywisty ciąg nie jest ważny, o ile jest unikatowy na komputerze.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Korzystanie z wpisów tajnych przechowywanych w ramach Menedżera wpisów tajnych w aplikacji `AddUserSecrets<T>` jest realizowane przez wywołanie wystąpienia ConfigurationBuilder w celu uwzględnienia wpisów tajnych aplikacji w konfiguracji. Parametr generyczny T powinien być typem z zestawu, do którego zastosowano UserSecretId. Zwykle korzystanie `AddUserSecrets<Startup>` z programu jest bardzo precyzyjne.

Program jest zawarty w domyślnych opcjach środowiska programistycznego, gdy jest `CreateDefaultBuilder` używana metoda w *program.cs*. `AddUserSecrets<Startup>()`

>[!div class="step-by-step"]
>[Poprzedni](authorization-net-microservices-web-applications.md)Następny
>[](azure-key-vault-protects-secrets.md)
