---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616289"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a><span data-ttu-id="e34e6-101">Zarządzane klasy kryptograficzne nie zgłaszają wyjątku kryptografii w trybie FIPS</span><span class="sxs-lookup"><span data-stu-id="e34e6-101">Managed cryptography classes do not throw a CryptographyException in FIPS mode</span></span>

#### <a name="details"></a><span data-ttu-id="e34e6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e34e6-102">Details</span></span>

<span data-ttu-id="e34e6-103">W .NET Framework 4.7.2 i starszych wersjach zarządzane klasy dostawcy usług kryptograficznych, takie jak <xref:System.Security.Cryptography.SHA256Managed> throw, <xref:System.Security.Cryptography.CryptographicException> gdy systemowe biblioteki kryptograficzne są skonfigurowane w trybie FIPS.</span><span class="sxs-lookup"><span data-stu-id="e34e6-103">In .NET Framework 4.7.2 and earlier versions, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in FIPS mode.</span></span> <span data-ttu-id="e34e6-104">Te wyjątki są zgłaszane, ponieważ zarządzane wersje nie zostały poddane FIPS (Federal Information Processing Standards) 140-2 certyfikacji, a także do blokowania algorytmów kryptograficznych, które nie zostały uznane za zatwierdzone na podstawie reguł FIPS.</span><span class="sxs-lookup"><span data-stu-id="e34e6-104">These exceptions are thrown because the managed versions have not undergone FIPS (Federal Information Processing Standards) 140-2 certification, as well as to block cryptographic algorithms that were not considered to be approved based on the FIPS rules.</span></span>  <span data-ttu-id="e34e6-105">Ponieważ kilku deweloperów ma swoje komputery deweloperskie w trybie FIPS, te wyjątki są często zgłaszane tylko w systemach produkcyjnych. Aplikacje przeznaczone dla .NET Framework 4,8 i nowszych wersji automatycznie przełączają się do nowszej, swobodnej zasady, tak aby <xref:System.Security.Cryptography.CryptographicException> nie było już zgłaszane domyślnie w takich przypadkach.</span><span class="sxs-lookup"><span data-stu-id="e34e6-105">Because few developers have their development machines in FIPS mode, these exceptions are frequently thrown only on production systems.Applications that target .NET Framework 4.8 and later versions automatically switch to the newer, relaxed policy, so that a <xref:System.Security.Cryptography.CryptographicException> is no longer thrown by default in such cases.</span></span> <span data-ttu-id="e34e6-106">Zamiast tego zarządzane klasy kryptograficzne przekierowują operacje kryptograficzne do biblioteki kryptografii systemu.</span><span class="sxs-lookup"><span data-stu-id="e34e6-106">Instead, the managed cryptography classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="e34e6-107">Ta zmiana zasad skutecznie usuwa potencjalne różnice między środowiskami deweloperskimi i środowiskami produkcyjnymi, dzięki czemu składniki macierzyste i zarządzane składniki działają w ramach tych samych zasad kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="e34e6-107">This policy change effectively removes a potentially confusing difference between developer environments and the production environments and makes native components and managed components operate under the same cryptographic policy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e34e6-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e34e6-108">Suggestion</span></span>

<span data-ttu-id="e34e6-109">Jeśli takie zachowanie jest niepożądane, można zrezygnować z niego i przywrócić poprzednie zachowanie, tak aby <xref:System.Security.Cryptography.CryptographicException> w trybie FIPS było zgłaszane, dodając następujące ustawienie konfiguracji [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="e34e6-109">If this behavior is undesirable, you can opt out of it and restore the previous behavior so that a <xref:System.Security.Cryptography.CryptographicException> is thrown in FIPS mode by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

<span data-ttu-id="e34e6-110">Jeśli aplikacja jest przeznaczona .NET Framework 4.7.2 lub wcześniejsza, możesz również przystąpić do tej zmiany, dodając następujące ustawienia konfiguracji [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="e34e6-110">If your application targets .NET Framework 4.7.2 or earlier, you can also opt in to this change by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| <span data-ttu-id="e34e6-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e34e6-111">Name</span></span>    | <span data-ttu-id="e34e6-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="e34e6-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e34e6-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="e34e6-113">Scope</span></span>   | <span data-ttu-id="e34e6-114">Brzeg</span><span class="sxs-lookup"><span data-stu-id="e34e6-114">Edge</span></span>        |
| <span data-ttu-id="e34e6-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="e34e6-115">Version</span></span> | <span data-ttu-id="e34e6-116">4,8</span><span class="sxs-lookup"><span data-stu-id="e34e6-116">4.8</span></span>         |
| <span data-ttu-id="e34e6-117">Typ</span><span class="sxs-lookup"><span data-stu-id="e34e6-117">Type</span></span>    | <span data-ttu-id="e34e6-118">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="e34e6-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e34e6-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e34e6-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>
