---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614658"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a><span data-ttu-id="f2e96-101">Deszyfrowanie AesCryptoServiceProvider zapewnia przekształcenie wielokrotnego użytku</span><span class="sxs-lookup"><span data-stu-id="f2e96-101">AesCryptoServiceProvider decryptor provides a reusable transform</span></span>

#### <a name="details"></a><span data-ttu-id="f2e96-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f2e96-102">Details</span></span>

<span data-ttu-id="f2e96-103">Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.2, <xref:System.Security.Cryptography.AesCryptoServiceProvider> deszyfrowanie zapewnia przekształcenie wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="f2e96-103">Starting with apps that target the .NET Framework 4.6.2, the <xref:System.Security.Cryptography.AesCryptoServiceProvider> decryptor provides a reusable transform.</span></span> <span data-ttu-id="f2e96-104">Po wywołaniu <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> , transformacja zostanie zainicjowana i może być ponownie użyta.</span><span class="sxs-lookup"><span data-stu-id="f2e96-104">After a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, the transform is reinitialized and can be reused.</span></span> <span data-ttu-id="f2e96-105">W przypadku aplikacji, które są przeznaczone dla wcześniejszych wersji .NET Framework, próba ponownego użycia deszyfrującego przez wywołanie metody wyrzucania <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> <xref:System.Security.Cryptography.CryptographicException> lub powoduje uszkodzenie danych.</span><span class="sxs-lookup"><span data-stu-id="f2e96-105">For apps that target earlier versions of the .NET Framework, attempting to reuse the decryptor by calling <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> after a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> throws a <xref:System.Security.Cryptography.CryptographicException> or produces corrupted data.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f2e96-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f2e96-106">Suggestion</span></span>

<span data-ttu-id="f2e96-107">Wpływ tej zmiany powinien być minimalny, ponieważ jest to oczekiwane zachowanie. Aplikacje, które są zależne od poprzedniego zachowania, mogą zrezygnować z korzystania z niego, dodając następujące ustawienia konfiguracji do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="f2e96-107">The impact of this change should be minimal, since this is the expected behavior.Applications that depend on the previous behavior can opt out of it using it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

<span data-ttu-id="f2e96-108">Ponadto aplikacje przeznaczone dla wcześniejszej wersji .NET Framework ale działają w ramach wersji .NET Framework, zaczynając od .NET Framework 4.6.2, dodając następujące ustawienia konfiguracji do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="f2e96-108">In addition, applications that target a previous version of the .NET Framework but are running under a version of the .NET Framework starting with .NET Framework 4.6.2 can opt in to it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| <span data-ttu-id="f2e96-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f2e96-109">Name</span></span>    | <span data-ttu-id="f2e96-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="f2e96-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f2e96-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="f2e96-111">Scope</span></span>   | <span data-ttu-id="f2e96-112">Mały</span><span class="sxs-lookup"><span data-stu-id="f2e96-112">Minor</span></span>       |
| <span data-ttu-id="f2e96-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="f2e96-113">Version</span></span> | <span data-ttu-id="f2e96-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f2e96-114">4.6.2</span></span>       |
| <span data-ttu-id="f2e96-115">Typ</span><span class="sxs-lookup"><span data-stu-id="f2e96-115">Type</span></span>    | <span data-ttu-id="f2e96-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f2e96-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f2e96-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f2e96-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
