---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291632"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="a65b6-101">Platforma Azure: usunięto pakiety integracji platformy Azure z prefiksem platformy Microsoft</span><span class="sxs-lookup"><span data-stu-id="a65b6-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="a65b6-102">Następujące `Microsoft.*` pakiety, które zapewniają integrację między ASP.NET Core i Azure SDK nie są zawarte w ASP.NET Core 5.0:</span><span class="sxs-lookup"><span data-stu-id="a65b6-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="a65b6-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), który integruje [usługę Azure Key Vault](/azure/key-vault/) z systemem [konfiguracji](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="a65b6-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="a65b6-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), który integruje usługę Azure Key Vault z [ASP.NET core data protection system](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="a65b6-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="a65b6-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), który integruje [usługę Azure Blob Storage](/azure/storage/blobs/) z ASP.NET podstawowym systemem ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="a65b6-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="a65b6-106">Aby do dyskusji na ten temat, zobacz [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="a65b6-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a65b6-107">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a65b6-107">Version introduced</span></span>

<span data-ttu-id="a65b6-108">5.0 Wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="a65b6-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a65b6-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="a65b6-109">Old behavior</span></span>

<span data-ttu-id="a65b6-110">Pakiety `Microsoft.*` zintegrowane usługi platformy Azure z interfejsów API konfiguracji i ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="a65b6-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a65b6-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="a65b6-111">New behavior</span></span>

<span data-ttu-id="a65b6-112">Nowe `Azure.*` pakiety integrują usługi platformy Azure z interfejsami API konfiguracji i ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="a65b6-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a65b6-113">Powód zmiany</span><span class="sxs-lookup"><span data-stu-id="a65b6-113">Reason for change</span></span>

<span data-ttu-id="a65b6-114">Zmiana została wniesiena, ponieważ pakiety `Microsoft.*` były:</span><span class="sxs-lookup"><span data-stu-id="a65b6-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="a65b6-115">Przy użyciu przestarzałych wersji narzędzia Azure SDK.</span><span class="sxs-lookup"><span data-stu-id="a65b6-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="a65b6-116">Proste aktualizacje nie były możliwe, ponieważ nowe wersje zestawu SDK platformy Azure zawierały zmiany wyłudania informacji.</span><span class="sxs-lookup"><span data-stu-id="a65b6-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="a65b6-117">Powiązany z harmonogramem wydania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a65b6-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="a65b6-118">Przeniesienie własności pakietów do zespołu zestawu Azure SDK umożliwia aktualizacje pakietów w miarę aktualizowannia zestawu Azure SDK.</span><span class="sxs-lookup"><span data-stu-id="a65b6-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a65b6-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="a65b6-119">Recommended action</span></span>

<span data-ttu-id="a65b6-120">W ASP.NET projektów Core 2.1 lub nowszych, zastąp stare `Microsoft.*` nowymi `Azure.*` pakietami.</span><span class="sxs-lookup"><span data-stu-id="a65b6-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="a65b6-121">Stary</span><span class="sxs-lookup"><span data-stu-id="a65b6-121">Old</span></span> | <span data-ttu-id="a65b6-122">Nowa</span><span class="sxs-lookup"><span data-stu-id="a65b6-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="a65b6-123">Usługa Azure.AspNetCore.DataProtection.Keys</span><span class="sxs-lookup"><span data-stu-id="a65b6-123">Azure.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="a65b6-124">Obiekty blob Azure.AspNetCore.DataProtection.Blob</span><span class="sxs-lookup"><span data-stu-id="a65b6-124">Azure.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="a65b6-125">Usługi Azure.Extensions.Configuration.Secrets</span><span class="sxs-lookup"><span data-stu-id="a65b6-125">Azure.Extensions.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

<span data-ttu-id="a65b6-126">Nowe pakiety używają nowej wersji zestawu SDK platformy Azure, która zawiera przełomowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="a65b6-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="a65b6-127">Ogólne wzorce użycia pozostają niezmienione.</span><span class="sxs-lookup"><span data-stu-id="a65b6-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="a65b6-128">Niektóre przeciążenia i opcje mogą się różnić, aby dostosować się do zmian w podstawowych interfejsach API zestawów SDK platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="a65b6-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="a65b6-129">Stare pakiety będą:</span><span class="sxs-lookup"><span data-stu-id="a65b6-129">The old packages will:</span></span>

* <span data-ttu-id="a65b6-130">Bądź obsługiwany przez zespół ASP.NET Core przez cały okres istnienia .NET Core 2.1 i 3.1.</span><span class="sxs-lookup"><span data-stu-id="a65b6-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="a65b6-131">Nie należy uwzględniać w .NET 5.</span><span class="sxs-lookup"><span data-stu-id="a65b6-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="a65b6-132">Podczas uaktualniania projektu do platformy .NET `Azure.*` 5, przejście do pakietów w celu utrzymania obsługi.</span><span class="sxs-lookup"><span data-stu-id="a65b6-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="a65b6-133">Kategoria</span><span class="sxs-lookup"><span data-stu-id="a65b6-133">Category</span></span>

<span data-ttu-id="a65b6-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a65b6-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a65b6-135">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a65b6-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
