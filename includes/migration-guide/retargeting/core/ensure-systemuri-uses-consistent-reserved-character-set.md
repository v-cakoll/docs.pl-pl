---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614663"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a><span data-ttu-id="b9a86-101">Upewnij się, że system. URI używa spójnego zestawu znaków zarezerwowanych</span><span class="sxs-lookup"><span data-stu-id="b9a86-101">Ensure System.Uri uses a consistent reserved character set</span></span>

#### <a name="details"></a><span data-ttu-id="b9a86-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b9a86-102">Details</span></span>

<span data-ttu-id="b9a86-103">W programie <xref:System.Uri?displayProperty=fullName> niektóre znaki zakodowane w procentach, które były czasami zdekodowane, są teraz spójne z kodowaniem.</span><span class="sxs-lookup"><span data-stu-id="b9a86-103">In <xref:System.Uri?displayProperty=fullName>, certain percent-encoded characters that were sometimes decoded are now consistently left encoded.</span></span> <span data-ttu-id="b9a86-104">Dzieje się tak we właściwościach i metodach, które uzyskują dostęp do składników Path, Query, fragment lub UserInfo identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="b9a86-104">This occurs across the properties and methods that access the path, query, fragment, or userinfo components of the URI.</span></span> <span data-ttu-id="b9a86-105">Zachowanie zmieni się tylko wtedy, gdy oba poniższe warunki są spełnione:</span><span class="sxs-lookup"><span data-stu-id="b9a86-105">The behavior will change only when both of the following are true:</span></span>

- <span data-ttu-id="b9a86-106">Identyfikator URI zawiera zakodowaną postać dowolnego z następujących znaków zarezerwowanych: `:` , `'` ,, `(` `)` `!` lub `*` .</span><span class="sxs-lookup"><span data-stu-id="b9a86-106">The URI contains the encoded form of any of the following reserved characters: `:`, `'`, `(`, `)`, `!` or `*`.</span></span>
- <span data-ttu-id="b9a86-107">Identyfikator URI zawiera znak Unicode lub zakodowany zastrzeżony.</span><span class="sxs-lookup"><span data-stu-id="b9a86-107">The URI contains a Unicode or encoded non-reserved character.</span></span> <span data-ttu-id="b9a86-108">Jeśli obie powyższe wartości mają wartość true, zakodowane zarezerwowane znaki są zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="b9a86-108">If both of the above are true, the encoded reserved characters are left encoded.</span></span> <span data-ttu-id="b9a86-109">W poprzednich wersjach .NET Framework są one zdekodowane.</span><span class="sxs-lookup"><span data-stu-id="b9a86-109">In previous versions of the .NET Framework, they are decoded.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b9a86-110">Sugestia</span><span class="sxs-lookup"><span data-stu-id="b9a86-110">Suggestion</span></span>

<span data-ttu-id="b9a86-111">W przypadku aplikacji przeznaczonych dla wersji .NET Framework zaczynających się od 4.7.2 nowe zachowanie dekodowania jest domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b9a86-111">For applications that target versions of .NET Framework starting with 4.7.2, the new decoding behavior is enabled by default.</span></span> <span data-ttu-id="b9a86-112">Jeśli ta zmiana jest niepożądana, można ją wyłączyć, dodając następujący przełącznik [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b9a86-112">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

<span data-ttu-id="b9a86-113">W przypadku aplikacji przeznaczonych dla wcześniejszych wersji .NET Framework, które są uruchamiane w ramach wersji zaczynających się od .NET Framework 4.7.2, nowe zachowanie dekodowania jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="b9a86-113">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, the new decoding behavior is disabled by default.</span></span> <span data-ttu-id="b9a86-114">Można ją włączyć, dodając następujący przełącznik [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b9a86-114">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| <span data-ttu-id="b9a86-115">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b9a86-115">Name</span></span>    | <span data-ttu-id="b9a86-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="b9a86-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b9a86-117">Zakres</span><span class="sxs-lookup"><span data-stu-id="b9a86-117">Scope</span></span>   | <span data-ttu-id="b9a86-118">Mały</span><span class="sxs-lookup"><span data-stu-id="b9a86-118">Minor</span></span>       |
| <span data-ttu-id="b9a86-119">Wersja</span><span class="sxs-lookup"><span data-stu-id="b9a86-119">Version</span></span> | <span data-ttu-id="b9a86-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="b9a86-120">4.7.2</span></span>       |
| <span data-ttu-id="b9a86-121">Typ</span><span class="sxs-lookup"><span data-stu-id="b9a86-121">Type</span></span>    | <span data-ttu-id="b9a86-122">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="b9a86-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b9a86-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b9a86-123">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
