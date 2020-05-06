---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902001"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="08583-101">Ochrona danych: usługa dataprotection. AzureStorage używa nowych interfejsów API usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="08583-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="08583-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>zależy od [bibliotek usługi Azure Storage](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="08583-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="08583-103">Te biblioteki zmieniły swoje zestawy, pakiety i przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="08583-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="08583-104">Począwszy od ASP.NET Core 3,0, `Microsoft.AspNetCore.DataProtection.AzureStorage` program używa nowych `Microsoft.Azure.Storage.`prefiksów interfejsów API i pakietów.</span><span class="sxs-lookup"><span data-stu-id="08583-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="08583-105">Pytania dotyczące interfejsów API usługi Azure Storage można używać <https://github.com/Azure/azure-storage-net>.</span><span class="sxs-lookup"><span data-stu-id="08583-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="08583-106">Aby zapoznać się z omówieniem tego problemu, zobacz [dotnet/aspnetcore # 8472](https://github.com/dotnet/aspnetcore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="08583-106">For discussion on this issue, see [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="08583-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="08583-107">Version introduced</span></span>

<span data-ttu-id="08583-108">3.0</span><span class="sxs-lookup"><span data-stu-id="08583-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="08583-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="08583-109">Old behavior</span></span>

<span data-ttu-id="08583-110">Pakiet przywoływany `WindowsAzure.Storage` do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="08583-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="08583-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="08583-111">New behavior</span></span>

<span data-ttu-id="08583-112">Pakiet odwołuje się `Microsoft.Azure.Storage.Blob` do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="08583-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="08583-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="08583-113">Reason for change</span></span>

<span data-ttu-id="08583-114">Ta zmiana umożliwia `Microsoft.AspNetCore.DataProtection.AzureStorage` Migrowanie do zalecanych pakietów usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="08583-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="08583-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="08583-115">Recommended action</span></span>

<span data-ttu-id="08583-116">Jeśli nadal potrzebujesz użyć starszych interfejsów API usługi Azure Storage z ASP.NET Core 3,0, Dodaj bezpośrednią zależność do pakietu [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) .</span><span class="sxs-lookup"><span data-stu-id="08583-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="08583-117">Ten pakiet można zainstalować obok nowych `Microsoft.Azure.Storage` interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="08583-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="08583-118">W wielu przypadkach uaktualnienie obejmuje jedynie zmianę `using` instrukcji w celu użycia nowych przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="08583-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="08583-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="08583-119">Category</span></span>

<span data-ttu-id="08583-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="08583-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="08583-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="08583-121">Affected APIs</span></span>

<span data-ttu-id="08583-122">Brak</span><span class="sxs-lookup"><span data-stu-id="08583-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
