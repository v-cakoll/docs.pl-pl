---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235751"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="f39d3-101">Deserializacja obiektów MailMessage serializowane w .NET Framework 4.5 może zakończyć się niepowodzeniem</span><span class="sxs-lookup"><span data-stu-id="f39d3-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f39d3-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f39d3-102">Details</span></span>|<span data-ttu-id="f39d3-103">Począwszy od programu .NET Framework 4.5 <xref:System.Web.Mail.MailMessage> obiektów może zawierać znaki spoza zestawu ASCII.</span><span class="sxs-lookup"><span data-stu-id="f39d3-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="f39d3-104">W programie .NET Framework 4 obsługiwane są tylko znaki ASCII.</span><span class="sxs-lookup"><span data-stu-id="f39d3-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <xref:System.Web.Mail.MailMessage> <span data-ttu-id="f39d3-105">obiekty, które zawierają znaki spoza zestawu ASCII i które są serializowane w ramach programu .NET Framework 4.5 lub nowszej nie mogą być deserializowane w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f39d3-105">objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>|
|<span data-ttu-id="f39d3-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f39d3-106">Suggestion</span></span>|<span data-ttu-id="f39d3-107">Upewnij się, że kod zapewnia obsługę wyjątków podczas deserializacji <xref:System.Web.Mail.MailMessage> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f39d3-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>|
|<span data-ttu-id="f39d3-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="f39d3-108">Scope</span></span>|<span data-ttu-id="f39d3-109">Mały</span><span class="sxs-lookup"><span data-stu-id="f39d3-109">Minor</span></span>|
|<span data-ttu-id="f39d3-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="f39d3-110">Version</span></span>|<span data-ttu-id="f39d3-111">4.5</span><span class="sxs-lookup"><span data-stu-id="f39d3-111">4.5</span></span>|
|<span data-ttu-id="f39d3-112">Typ</span><span class="sxs-lookup"><span data-stu-id="f39d3-112">Type</span></span>|<span data-ttu-id="f39d3-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f39d3-113">Runtime</span></span>|
|<span data-ttu-id="f39d3-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f39d3-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
