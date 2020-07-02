---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617544"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="f6d68-101">HttpRuntime. AppDomainAppPath zgłasza NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="f6d68-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="f6d68-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f6d68-102">Details</span></span>

<span data-ttu-id="f6d68-103">W .NET Framework 4.6.2 środowisko uruchomieniowe zgłasza `T:System.NullReferenceException` wartość przy pobieraniu wartości zawierającej `P:System.Web.HttpRuntime.AppDomainAppPath` znaki null. W .NET Framework 4.6.1 i wcześniejszych wersji środowisko uruchomieniowe zgłasza `T:System.ArgumentNullException` .</span><span class="sxs-lookup"><span data-stu-id="f6d68-103">In the .NET Framework 4.6.2, the runtime throws a `T:System.NullReferenceException` when retrieving a `P:System.Web.HttpRuntime.AppDomainAppPath` value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an `T:System.ArgumentNullException`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f6d68-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f6d68-104">Suggestion</span></span>

<span data-ttu-id="f6d68-105">Aby odpowiedzieć na tę zmianę, możesz wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f6d68-105">You can do either of the follow to respond to this change:</span></span>

- <span data-ttu-id="f6d68-106">Obsługuj `T:System.NullReferenceException` aplikację, jeśli aplikacja jest uruchomiona na .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="f6d68-106">Handle the `T:System.NullReferenceException` if you application is running on the .NET Framework 4.6.2.</span></span>
- <span data-ttu-id="f6d68-107">Uaktualnij do .NET Framework 4,7, który przywraca poprzednie zachowanie i zgłasza `T:System.ArgumentNullException` .</span><span class="sxs-lookup"><span data-stu-id="f6d68-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an `T:System.ArgumentNullException`.</span></span>

| <span data-ttu-id="f6d68-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f6d68-108">Name</span></span>    | <span data-ttu-id="f6d68-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="f6d68-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f6d68-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="f6d68-110">Scope</span></span>   | <span data-ttu-id="f6d68-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="f6d68-111">Edge</span></span>        |
| <span data-ttu-id="f6d68-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="f6d68-112">Version</span></span> | <span data-ttu-id="f6d68-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f6d68-113">4.6.2</span></span>       |
| <span data-ttu-id="f6d68-114">Typ</span><span class="sxs-lookup"><span data-stu-id="f6d68-114">Type</span></span>    | <span data-ttu-id="f6d68-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f6d68-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f6d68-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f6d68-116">Affected APIs</span></span>

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
