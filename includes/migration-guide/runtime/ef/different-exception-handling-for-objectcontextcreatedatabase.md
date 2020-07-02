---
ms.openlocfilehash: 687118157020ede200f97a0125c4740a06bf4b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620307"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a><span data-ttu-id="7d736-101">Inna obsługa wyjątków dla metod ObjectContext. isdatabase i DbProviderServices. isdatabase</span><span class="sxs-lookup"><span data-stu-id="7d736-101">Different exception handling for ObjectContext.CreateDatabase and DbProviderServices.CreateDatabase methods</span></span>

#### <a name="details"></a><span data-ttu-id="7d736-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7d736-102">Details</span></span>

<span data-ttu-id="7d736-103">Począwszy od .NET Framework 4,5, jeśli Tworzenie bazy danych nie powiedzie się, <code>CreateDatabase</code> metody będą próbować usunąć pustą bazę danych.</span><span class="sxs-lookup"><span data-stu-id="7d736-103">Beginning in .NET Framework 4.5, if database creation fails, <code>CreateDatabase</code> methods will attempt to drop the empty database.</span></span> <span data-ttu-id="7d736-104">Jeśli ta operacja zakończy się pomyślnie, oryginalny <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> zostanie rozpropagowany (zamiast elementu <xref:System.InvalidOperationException?displayProperty=fullName> , który został zawsze wygenerowany w .NET Framework 4,0)</span><span class="sxs-lookup"><span data-stu-id="7d736-104">If that operation succeeds, the original <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> will be propagated (instead of the <xref:System.InvalidOperationException?displayProperty=fullName> that was always thrown in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7d736-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7d736-105">Suggestion</span></span>

<span data-ttu-id="7d736-106">Podczas przechwytywania <xref:System.InvalidOperationException?displayProperty=fullName> podczas wykonywania lub należy <xref:System.Data.Objects.ObjectContext.CreateDatabase> <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)> również przechwycić wyjątek SqlExceptions.</span><span class="sxs-lookup"><span data-stu-id="7d736-106">When catching an <xref:System.InvalidOperationException?displayProperty=fullName> while executing <xref:System.Data.Objects.ObjectContext.CreateDatabase> or <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions should now also be caught.</span></span>

| <span data-ttu-id="7d736-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7d736-107">Name</span></span>    | <span data-ttu-id="7d736-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="7d736-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7d736-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="7d736-109">Scope</span></span>   |<span data-ttu-id="7d736-110">Mały</span><span class="sxs-lookup"><span data-stu-id="7d736-110">Minor</span></span>|
|<span data-ttu-id="7d736-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="7d736-111">Version</span></span>|<span data-ttu-id="7d736-112">4.5</span><span class="sxs-lookup"><span data-stu-id="7d736-112">4.5</span></span>|
|<span data-ttu-id="7d736-113">Typ</span><span class="sxs-lookup"><span data-stu-id="7d736-113">Type</span></span>|<span data-ttu-id="7d736-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7d736-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7d736-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7d736-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
