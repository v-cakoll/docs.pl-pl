---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620257"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="c6404-101">Brak monikera platformy docelowej w wyniku 4,0</span><span class="sxs-lookup"><span data-stu-id="c6404-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="c6404-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c6404-102">Details</span></span>

<span data-ttu-id="c6404-103">Aplikacje bez <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> zastosowania na poziomie zestawu zostaną automatycznie uruchomione przy użyciu semantyki (osobliwości) .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="c6404-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="c6404-104">W celu zapewnienia wysokiej jakości zaleca się, aby wszystkie pliki binarne były jawnie przypisane do <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> wskazania wersji .NET Framework, z których zostały skompilowane.</span><span class="sxs-lookup"><span data-stu-id="c6404-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="c6404-105">Należy zauważyć, że użycie monikera platformy docelowej w pliku projektu spowoduje automatyczne zastosowanie przez program MSBuild <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="c6404-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c6404-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c6404-106">Suggestion</span></span>

<span data-ttu-id="c6404-107"><xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>Powinien być dostarczony przez dodanie atrybutu bezpośrednio do zestawu lub przez określenie platformy docelowej w [pliku projektu lub graficznego interfejsu użytkownika programu Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span><span class="sxs-lookup"><span data-stu-id="c6404-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="c6404-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c6404-108">Name</span></span>    | <span data-ttu-id="c6404-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="c6404-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c6404-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="c6404-110">Scope</span></span>   |<span data-ttu-id="c6404-111">Duży</span><span class="sxs-lookup"><span data-stu-id="c6404-111">Major</span></span>|
|<span data-ttu-id="c6404-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="c6404-112">Version</span></span>|<span data-ttu-id="c6404-113">4.5</span><span class="sxs-lookup"><span data-stu-id="c6404-113">4.5</span></span>|
|<span data-ttu-id="c6404-114">Typ</span><span class="sxs-lookup"><span data-stu-id="c6404-114">Type</span></span>|<span data-ttu-id="c6404-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c6404-115">Runtime</span></span>|
