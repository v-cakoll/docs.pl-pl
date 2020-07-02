---
ms.openlocfilehash: 06f4186e8f233f5c769dfc5e05d2de5eacd9b053
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622089"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="20563-101">Zmiana wysokiego kontrastu ComboBox svcTraceViewer</span><span class="sxs-lookup"><span data-stu-id="20563-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="20563-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="20563-102">Details</span></span>

<span data-ttu-id="20563-103">W [narzędziu Podgląd śledzenia usług firmy Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kontrolki ComboBox nie były wyświetlane w prawidłowym kolorze w niektórych motywach o dużym kontraście.</span><span class="sxs-lookup"><span data-stu-id="20563-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="20563-104">Problem został rozwiązany w .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="20563-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="20563-105">Jednak ze względu na wymagania zgodności z zestawem SDK .NET Framework, poprawka nie była domyślnie widoczna dla klientów.</span><span class="sxs-lookup"><span data-stu-id="20563-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="20563-106">Program .NET 4,8 wyświetla tę zmianę, dodając następujące [przełączniki konfiguracji AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do pliku svcTraceViewer.exe.config:</span><span class="sxs-lookup"><span data-stu-id="20563-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a><span data-ttu-id="20563-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="20563-107">Suggestion</span></span>

<ul><li><span data-ttu-id="20563-108">Jak zrezygnować z zmiany, jeśli nie chcesz mieć zmiany zachowania dużego kontrastu, możesz ją wyłączyć, usuwając następującą sekcję z pliku svcTraceViewer.exe.config:</span><span class="sxs-lookup"><span data-stu-id="20563-108">How to opt out of the change If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span></li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="20563-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="20563-109">Name</span></span>    | <span data-ttu-id="20563-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="20563-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="20563-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="20563-111">Scope</span></span>   |<span data-ttu-id="20563-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="20563-112">Edge</span></span>|
|<span data-ttu-id="20563-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="20563-113">Version</span></span>|<span data-ttu-id="20563-114">4,8</span><span class="sxs-lookup"><span data-stu-id="20563-114">4.8</span></span>|
|<span data-ttu-id="20563-115">Typ</span><span class="sxs-lookup"><span data-stu-id="20563-115">Type</span></span>|<span data-ttu-id="20563-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="20563-116">Runtime</span></span>|
