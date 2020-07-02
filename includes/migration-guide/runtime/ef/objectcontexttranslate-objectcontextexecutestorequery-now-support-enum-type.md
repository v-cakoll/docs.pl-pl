---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620328"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="13786-101">Obiekt ObjectContext. tłumaczenia i ObjectContext.ExecuteStoreQuery teraz obsługują typ wyliczeniowy</span><span class="sxs-lookup"><span data-stu-id="13786-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="13786-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="13786-102">Details</span></span>

<span data-ttu-id="13786-103">W .NET Framework 4,0 parametr generyczny <code>T</code> <code>ObjectContext.Translate</code> i metody nie <code>ObjectContext.ExecuteStoreQuery</code> mogą być wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="13786-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="13786-104">Ten scenariusz jest teraz obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="13786-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="13786-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="13786-105">Suggestion</span></span>

<span data-ttu-id="13786-106">Jeśli polecenie Przetłumacz lub ExecuteStoreQuery zostało wywołane w typie wyliczeniowym w .NET Framework 4,0, zwrócono wartość "0".</span><span class="sxs-lookup"><span data-stu-id="13786-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="13786-107">W przypadku pożądanego zachowania, wywołania powinny być zastępowane stałą 0 (lub równoważnej wyliczeniu).</span><span class="sxs-lookup"><span data-stu-id="13786-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="13786-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="13786-108">Name</span></span>    | <span data-ttu-id="13786-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="13786-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="13786-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="13786-110">Scope</span></span>   |<span data-ttu-id="13786-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="13786-111">Edge</span></span>|
|<span data-ttu-id="13786-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="13786-112">Version</span></span>|<span data-ttu-id="13786-113">4.5</span><span class="sxs-lookup"><span data-stu-id="13786-113">4.5</span></span>|
|<span data-ttu-id="13786-114">Typ</span><span class="sxs-lookup"><span data-stu-id="13786-114">Type</span></span>|<span data-ttu-id="13786-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="13786-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="13786-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="13786-116">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
