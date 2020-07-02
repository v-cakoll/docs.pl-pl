---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616294"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a><span data-ttu-id="05748-101">Sumy kontrolne XAML przepływu pracy dla symboli zmienionych z SHA1 na SHA256</span><span class="sxs-lookup"><span data-stu-id="05748-101">Workflow XAML checksums for symbols changed from SHA1 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="05748-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="05748-102">Details</span></span>

<span data-ttu-id="05748-103">Aby można było obsługiwać debugowanie za pomocą programu Visual Studio, środowisko uruchomieniowe przepływu pracy generuje sumę kontrolną dla pliku XAML przepływu pracy przy użyciu algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="05748-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow XAML file using a hashing algorithm.</span></span> <span data-ttu-id="05748-104">W .NET Framework 4.6.2 i starszych wersjach funkcja tworzenia skrótów sum kontrolnych przepływu pracy użyła algorytmu MD5, który spowodował problemy z systemami z obsługą FIPS.</span><span class="sxs-lookup"><span data-stu-id="05748-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="05748-105">Począwszy od .NET Framework 4,7, domyślny algorytm został zmieniony na SHA1.</span><span class="sxs-lookup"><span data-stu-id="05748-105">Starting with the .NET Framework 4.7, the default algorithm was changed to SHA1.</span></span> <span data-ttu-id="05748-106">Począwszy od .NET Framework 4,8, domyślny algorytm został zmieniony na SHA256.</span><span class="sxs-lookup"><span data-stu-id="05748-106">Starting with the .NET Framework 4.8, the default algorithm was changed to SHA256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="05748-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="05748-107">Suggestion</span></span>

<span data-ttu-id="05748-108">Jeśli kod nie może załadować wystąpień przepływu pracy lub znaleźć odpowiednich symboli ze względu na błąd sumy kontrolnej, spróbuj ustawić `AppContext` przełącznik "Switch.System. Activities. UseSHA1HashForDebuggerSymbols "do `true` .</span><span class="sxs-lookup"><span data-stu-id="05748-108">If your code is unable to load workflow instances or to find appropriate symbols due to a checksum failure, try setting the `AppContext` switch "Switch.System.Activities.UseSHA1HashForDebuggerSymbols" to `true`.</span></span> <span data-ttu-id="05748-109">W kodzie:</span><span class="sxs-lookup"><span data-stu-id="05748-109">In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

<span data-ttu-id="05748-110">Lub w konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="05748-110">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="05748-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="05748-111">Name</span></span>    | <span data-ttu-id="05748-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="05748-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="05748-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="05748-113">Scope</span></span>   | <span data-ttu-id="05748-114">Mały</span><span class="sxs-lookup"><span data-stu-id="05748-114">Minor</span></span>       |
| <span data-ttu-id="05748-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="05748-115">Version</span></span> | <span data-ttu-id="05748-116">4,8</span><span class="sxs-lookup"><span data-stu-id="05748-116">4.8</span></span>         |
| <span data-ttu-id="05748-117">Typ</span><span class="sxs-lookup"><span data-stu-id="05748-117">Type</span></span>    | <span data-ttu-id="05748-118">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="05748-118">Retargeting</span></span> |
