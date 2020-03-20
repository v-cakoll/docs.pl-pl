---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859152"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="12788-101">HttpRuntime.AppDomainAppPath zgłasza NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="12788-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="12788-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="12788-102">Details</span></span>|<span data-ttu-id="12788-103">W programie .NET Framework 4.6.2 środowisko <code>T:System.NullReferenceException</code> wykonawcze zgłasza <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> podczas pobierania wartości zawierającej znaki null. W .NET Framework 4.6.1 i wcześniejszych wersjach <code>T:System.ArgumentNullException</code>środowisko uruchomieniowe zgłasza .</span><span class="sxs-lookup"><span data-stu-id="12788-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="12788-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="12788-104">Suggestion</span></span>|<span data-ttu-id="12788-105">Możesz wykonać jedną z dalszych działań, aby odpowiedzieć na tę zmianę:</span><span class="sxs-lookup"><span data-stu-id="12788-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="12788-106"><code>T:System.NullReferenceException</code> Obsługa, jeśli aplikacja jest uruchomiona w programie .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="12788-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="12788-107">Uaktualnij do programu .NET Framework 4.7, który przywraca <code>T:System.ArgumentNullException</code>poprzednie zachowanie i rzuca plik .</span><span class="sxs-lookup"><span data-stu-id="12788-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="12788-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="12788-108">Scope</span></span>|<span data-ttu-id="12788-109">Brzeg</span><span class="sxs-lookup"><span data-stu-id="12788-109">Edge</span></span>|
|<span data-ttu-id="12788-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="12788-110">Version</span></span>|<span data-ttu-id="12788-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="12788-111">4.6.2</span></span>|
|<span data-ttu-id="12788-112">Typ</span><span class="sxs-lookup"><span data-stu-id="12788-112">Type</span></span>|<span data-ttu-id="12788-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="12788-113">Retargeting</span></span>|
|<span data-ttu-id="12788-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="12788-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
