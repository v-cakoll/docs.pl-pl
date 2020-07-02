---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614838"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a><span data-ttu-id="251b0-101">Sumy kontrolne przepływu pracy zmieniły się z MD5 na SHA1</span><span class="sxs-lookup"><span data-stu-id="251b0-101">Workflow checksums changed from MD5 to SHA1</span></span>

#### <a name="details"></a><span data-ttu-id="251b0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="251b0-102">Details</span></span>

<span data-ttu-id="251b0-103">Aby można było obsługiwać debugowanie za pomocą programu Visual Studio, środowisko uruchomieniowe przepływu pracy generuje sumę kontrolną wystąpienia przepływu pracy przy użyciu algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="251b0-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow instance using a hashing algorithm.</span></span> <span data-ttu-id="251b0-104">W .NET Framework 4.6.2 i starszych wersjach funkcja tworzenia skrótów sum kontrolnych przepływu pracy użyła algorytmu MD5, który spowodował problemy z systemami z obsługą FIPS.</span><span class="sxs-lookup"><span data-stu-id="251b0-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="251b0-105">Począwszy od .NET Framework 4,7, algorytm jest SHA1.</span><span class="sxs-lookup"><span data-stu-id="251b0-105">Starting with the .NET Framework 4.7, the algorithm is SHA1.</span></span> <span data-ttu-id="251b0-106">Jeśli kod spowodował utrwalenie tych sum kontrolnych, nie będą one zgodne.</span><span class="sxs-lookup"><span data-stu-id="251b0-106">If your code has persisted these checksums, they will be incompatible.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="251b0-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="251b0-107">Suggestion</span></span>

<span data-ttu-id="251b0-108">Jeśli kod nie może załadować wystąpień przepływu pracy z powodu błędu sumy kontrolnej, spróbuj ustawić `AppContext` przełącznik &quot;Switch.System. Activities. UseMD5ForWFDebugger &quot; na wartość true. W kodzie:</span><span class="sxs-lookup"><span data-stu-id="251b0-108">If your code is unable to load workflow instances due to a checksum failure, try setting the `AppContext` switch &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; to true.In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

<span data-ttu-id="251b0-109">Lub w konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="251b0-109">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="251b0-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="251b0-110">Name</span></span>    | <span data-ttu-id="251b0-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="251b0-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="251b0-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="251b0-112">Scope</span></span>   | <span data-ttu-id="251b0-113">Mały</span><span class="sxs-lookup"><span data-stu-id="251b0-113">Minor</span></span>       |
| <span data-ttu-id="251b0-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="251b0-114">Version</span></span> | <span data-ttu-id="251b0-115">4,7</span><span class="sxs-lookup"><span data-stu-id="251b0-115">4.7</span></span>         |
| <span data-ttu-id="251b0-116">Typ</span><span class="sxs-lookup"><span data-stu-id="251b0-116">Type</span></span>    | <span data-ttu-id="251b0-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="251b0-117">Retargeting</span></span> |
