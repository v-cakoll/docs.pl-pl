---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614634"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a><span data-ttu-id="00566-101">Zezwalaj na znaki kontrolne dwukierunkowej Unicode w identyfikatorach URI</span><span class="sxs-lookup"><span data-stu-id="00566-101">Allow Unicode Bidirectional Control Characters in URIs</span></span>

#### <a name="details"></a><span data-ttu-id="00566-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="00566-102">Details</span></span>

<span data-ttu-id="00566-103">Unicode określa kilka specjalnych znaków sterujących używanych do określania orientacji tekstu.</span><span class="sxs-lookup"><span data-stu-id="00566-103">Unicode specifies several special control characters used to specify the orientation of text.</span></span> <span data-ttu-id="00566-104">W poprzednich wersjach .NET Framework te znaki zostały nieprawidłowo usunięte ze wszystkich identyfikatorów URI, nawet jeśli były obecne w postaci kodowanej według wartości procentowej.</span><span class="sxs-lookup"><span data-stu-id="00566-104">In previous versions of the .NET Framework, these characters were incorrectly stripped from all URIs even if they were present in their percent-encoded form.</span></span> <span data-ttu-id="00566-105">W celu lepszego przestrzegania [specyfikacji RFC 3987](https://tools.ietf.org/html/rfc3987)zezwalamy teraz na te znaki w identyfikatorach URI.</span><span class="sxs-lookup"><span data-stu-id="00566-105">In order to better follow [RFC 3987](https://tools.ietf.org/html/rfc3987), we now allow these characters in URIs.</span></span> <span data-ttu-id="00566-106">W przypadku znalezienia niezaszyfrowanego identyfikatora URI są one kodowane według wartości procentowej.</span><span class="sxs-lookup"><span data-stu-id="00566-106">When found unencoded in a URI, they are percent-encoded.</span></span> <span data-ttu-id="00566-107">W przypadku znalezienia zakodowanej procentowo są one pozostawione jako-is.</span><span class="sxs-lookup"><span data-stu-id="00566-107">When found percent-encoded they are left as-is.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="00566-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="00566-108">Suggestion</span></span>

<span data-ttu-id="00566-109">W przypadku aplikacji przeznaczonych dla wersji .NET Framework począwszy od 4.7.2, obsługa znaków dwukierunkowych Unicode jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="00566-109">For applications that target versions of .NET Framework starting with 4.7.2, support for Unicode bidirectional characters is enabled by default.</span></span> <span data-ttu-id="00566-110">Jeśli ta zmiana jest niepożądana, można ją wyłączyć, dodając następujący przełącznik [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="00566-110">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

<span data-ttu-id="00566-111">W przypadku aplikacji przeznaczonych dla wcześniejszych wersji .NET Framework, które są uruchamiane w ramach wersji zaczynających się od .NET Framework 4.7.2, obsługa znaków dwukierunkowych Unicode jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="00566-111">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, support for Unicode bidirectional characters is disabled by default.</span></span> <span data-ttu-id="00566-112">Można ją włączyć, dodając następujący przełącznik [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="00566-112">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file::</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| <span data-ttu-id="00566-113">Nazwa</span><span class="sxs-lookup"><span data-stu-id="00566-113">Name</span></span>    | <span data-ttu-id="00566-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="00566-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="00566-115">Zakres</span><span class="sxs-lookup"><span data-stu-id="00566-115">Scope</span></span>   | <span data-ttu-id="00566-116">Mały</span><span class="sxs-lookup"><span data-stu-id="00566-116">Minor</span></span>       |
| <span data-ttu-id="00566-117">Wersja</span><span class="sxs-lookup"><span data-stu-id="00566-117">Version</span></span> | <span data-ttu-id="00566-118">4.7.2</span><span class="sxs-lookup"><span data-stu-id="00566-118">4.7.2</span></span>       |
| <span data-ttu-id="00566-119">Typ</span><span class="sxs-lookup"><span data-stu-id="00566-119">Type</span></span>    | <span data-ttu-id="00566-120">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="00566-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="00566-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="00566-121">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
