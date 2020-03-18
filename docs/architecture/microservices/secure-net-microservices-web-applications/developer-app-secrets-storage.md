---
title: Bezpieczne przechowywanie kluczy tajnych aplikacji podczas jej tworzenia
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — nie przechowuj kluczy tajnych aplikacji, takich jak hasła, parametry połączenia lub klucze interfejsu API w kontroli źródła, należy zrozumieć opcje, których można użyć w ASP.NET Core, w szczególności musisz zrozumieć, jak obsługiwać "użytkownika" tajemnice".
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 1ef2246746b9165f1564fa7be64ff7eb28eb1d32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501799"
---
# <a name="store-application-secrets-safely-during-development"></a>Bezpiecznie przechowuj wpisy tajne aplikacji podczas opracowywania

Aby połączyć się z chronionymi zasobami i innymi usługami, ASP.NET aplikacje podstawowe zazwyczaj muszą używać ciągów połączeń, haseł lub innych poświadczeń zawierających poufne informacje. Te wrażliwe informacje są nazywane *tajemnicami*. Jest najlepszym rozwiązaniem, aby nie zawierać wpisy tajne w kodzie źródłowym i upewniając się, aby nie przechowywać klucze tajne w kontroli źródła. Zamiast tego należy użyć ASP.NET modelu konfiguracji Core, aby odczytać klucze tajne z bezpieczniejszych lokalizacji.

Należy oddzielić klucze tajne dostępu do zasobów deweloperskich i przejściowych od tych używanych do uzyskiwania dostępu do zasobów produkcyjnych, ponieważ różne osoby będą potrzebować dostępu do tych różnych zestawów kluczy tajnych. Aby przechowywać wpisy tajne używane podczas tworzenia aplikacji, typowe podejścia mają na celu przechowywanie kluczy tajnych w zmiennych środowiskowych lub przy użyciu narzędzia ASP.NET Core Secret Manager. Aby zapewnić bezpieczniejsze przechowywanie w środowiskach produkcyjnych, mikrousługi mogą przechowywać klucze tajne w usłudze Azure Key Vault.

## <a name="store-secrets-in-environment-variables"></a>Przechowywanie kluczy tajnych w zmiennych środowiskowych

Jednym ze sposobów zachowania wpisów tajnych z kodu źródłowego jest dla deweloperów, aby ustawić wtajemnic opartych na [ciągach](/aspnet/core/security/app-secrets#environment-variables) jako zmienne środowiskowe na swoich komputerach deweloperskich. W przypadku używania zmiennych środowiskowych do przechowywania wpisów tajnych z nazwami hierarchicznymi, takimi jak te zagnieżdżone w sekcjach konfiguracji, należy nadać im nazwę, aby uwzględnić pełną hierarchię jej sekcji, rozdzieloną dwukropkami (:).

Na przykład ustawienie `Logging:LogLevel:Default` zmiennej `Debug` środowiskowej na wartość byłoby równoważne wartości konfiguracji z następującego pliku JSON:

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

Aby uzyskać dostęp do tych wartości ze zmiennych środowiskowych, aplikacja po prostu musi wywołać AddEnvironmentVariables na jego ConfigurationBuilder podczas konstruowania IConfigurationRoot obiektu.

Należy zauważyć, że zmienne środowiskowe są często przechowywane jako zwykły tekst, więc jeśli komputer lub proces ze zmiennymi środowiskowymi jest zagrożona, wartości zmiennej środowiskowej będą widoczne.

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a>Przechowuj sekrety za pomocą ASP.NET Core Secret Manager

Narzędzie ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) udostępnia inną metodę utrzymywania tajemnic poza kodem źródłowym podczas **tworzenia .** Aby użyć narzędzia Secret Manager, zainstaluj pakiet **Microsoft.Extensions.Configuration.SecretManager** w pliku projektu. Gdy ta zależność jest obecna i została `dotnet user-secrets` przywrócona, polecenie może służyć do ustawiania wartości kluczy tajnych z wiersza polecenia. Te wpisy tajne będą przechowywane w pliku JSON w katalogu profilu użytkownika (szczegóły różnią się w zależności od systemu operacyjnego), z dala od kodu źródłowego.

Wtajemnice ustawione przez narzędzie Secret `UserSecretsId` Manager są zorganizowane przez właściwość projektu, który używa kluczy tajnych. W związku z tym należy ustawić UserSecretsId właściwość w pliku projektu, jak pokazano w urywku poniżej. Wartością domyślną jest identyfikator GUID przypisany przez program Visual Studio, ale rzeczywisty ciąg nie jest ważny, o ile jest unikatowy na komputerze.

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

Za pomocą wpisów tajnych przechowywanych w `AddUserSecrets<T>` Secret Manager w aplikacji jest realizowane przez wywołanie wystąpienia ConfigurationBuilder do uwzględnienia wpisów tajnych dla aplikacji w jego konfiguracji. Parametr ogólny T powinien być typem z zestawu, do którego zastosowano identyfikator UserSecretId. Zwykle `AddUserSecrets<Startup>` używanie jest w porządku.

Jest `AddUserSecrets<Startup>()` ona uwzględniona w domyślnych `CreateDefaultBuilder` opcjach środowiska programistycznego podczas korzystania z metody w *Program.cs*.

>[!div class="step-by-step"]
>[Poprzedni](authorization-net-microservices-web-applications.md)
>[następny](azure-key-vault-protects-secrets.md)
