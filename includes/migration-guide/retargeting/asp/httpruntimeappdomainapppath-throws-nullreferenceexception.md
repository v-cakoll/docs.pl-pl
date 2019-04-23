---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981468"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="4024d-101">HttpRuntime.AppDomainAppPath zgłasza obiektu NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="4024d-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4024d-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4024d-102">Details</span></span>|<span data-ttu-id="4024d-103">W programie .NET Framework 4.6.2, środowisko wykonawcze zgłasza <code>T:System.NullReferenceException</code> podczas pobierania <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> wartość, która zawiera znaki null. W .NET Framework 4.6.1 i wcześniejszych wersjach, środowisko wykonawcze zgłasza <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="4024d-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="4024d-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="4024d-104">Suggestion</span></span>|<span data-ttu-id="4024d-105">Możesz wykonać jedną z działaniami, aby odpowiedzieć na tę zmianę:</span><span class="sxs-lookup"><span data-stu-id="4024d-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="4024d-106">Obsługa <code>T:System.NullReferenceException</code> Jeśli aplikacja jest uruchomiona w środowisku .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="4024d-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="4024d-107">Uaktualnianie do programu .NET Framework 4.7, który przywraca poprzednie zachowanie i zgłasza <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="4024d-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="4024d-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="4024d-108">Scope</span></span>|<span data-ttu-id="4024d-109">Krawędź</span><span class="sxs-lookup"><span data-stu-id="4024d-109">Edge</span></span>|
|<span data-ttu-id="4024d-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="4024d-110">Version</span></span>|<span data-ttu-id="4024d-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="4024d-111">4.6.2</span></span>|
|<span data-ttu-id="4024d-112">Typ</span><span class="sxs-lookup"><span data-stu-id="4024d-112">Type</span></span>|<span data-ttu-id="4024d-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="4024d-113">Retargeting</span></span>|
|<span data-ttu-id="4024d-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4024d-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
