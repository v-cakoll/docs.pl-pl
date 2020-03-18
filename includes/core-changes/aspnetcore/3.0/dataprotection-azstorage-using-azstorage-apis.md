---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902001"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="9f91e-101">Ochrona danych: DataProtection.AzureStorage korzysta z nowych interfejsów API usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="9f91e-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="9f91e-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>zależy od [bibliotek usługi Azure Storage](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="9f91e-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="9f91e-103">Te biblioteki zmienili nazwy swoich zestawów, pakietów i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9f91e-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="9f91e-104">Począwszy od ASP.NET Core `Microsoft.AspNetCore.DataProtection.AzureStorage` 3.0, używa nowych `Microsoft.Azure.Storage.`interfejsów API i pakietów z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="9f91e-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="9f91e-105">W przypadku pytań dotyczących interfejsów <https://github.com/Azure/azure-storage-net>API usługi Azure Storage użyj .</span><span class="sxs-lookup"><span data-stu-id="9f91e-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="9f91e-106">Aby uzyskać dyskusję na ten temat, zobacz [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="9f91e-106">For discussion on this issue, see [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9f91e-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9f91e-107">Version introduced</span></span>

<span data-ttu-id="9f91e-108">3.0</span><span class="sxs-lookup"><span data-stu-id="9f91e-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9f91e-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="9f91e-109">Old behavior</span></span>

<span data-ttu-id="9f91e-110">Pakiet odwołuje się `WindowsAzure.Storage` do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="9f91e-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9f91e-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="9f91e-111">New behavior</span></span>

<span data-ttu-id="9f91e-112">Pakiet odwołuje `Microsoft.Azure.Storage.Blob` się do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="9f91e-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9f91e-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="9f91e-113">Reason for change</span></span>

<span data-ttu-id="9f91e-114">Ta zmiana `Microsoft.AspNetCore.DataProtection.AzureStorage` umożliwia migrację do zalecanych pakietów usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="9f91e-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9f91e-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="9f91e-115">Recommended action</span></span>

<span data-ttu-id="9f91e-116">Jeśli nadal musisz używać starszych interfejsów API usługi Azure Storage z ASP.NET Core 3.0, dodaj bezpośrednią zależność do pakietu [WindowsAzure.Storage.](https://www.nuget.org/packages/WindowsAzure.Storage/)</span><span class="sxs-lookup"><span data-stu-id="9f91e-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="9f91e-117">Ten pakiet można zainstalować `Microsoft.Azure.Storage` obok nowych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="9f91e-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="9f91e-118">W wielu przypadkach uaktualnienie `using` polega tylko na zmianie instrukcji, aby użyć nowych obszarów nazw:</span><span class="sxs-lookup"><span data-stu-id="9f91e-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="9f91e-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9f91e-119">Category</span></span>

<span data-ttu-id="9f91e-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9f91e-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9f91e-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9f91e-121">Affected APIs</span></span>

<span data-ttu-id="9f91e-122">Brak</span><span class="sxs-lookup"><span data-stu-id="9f91e-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
