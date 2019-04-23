---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235751"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="98f69-101">Deserializacja obiektów MailMessage serializowane w .NET Framework 4.5 może zakończyć się niepowodzeniem</span><span class="sxs-lookup"><span data-stu-id="98f69-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="98f69-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="98f69-102">Details</span></span>|<span data-ttu-id="98f69-103">Począwszy od programu .NET Framework 4.5 <xref:System.Web.Mail.MailMessage> obiektów może zawierać znaki spoza zestawu ASCII.</span><span class="sxs-lookup"><span data-stu-id="98f69-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="98f69-104">W programie .NET Framework 4 obsługiwane są tylko znaki ASCII.</span><span class="sxs-lookup"><span data-stu-id="98f69-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="98f69-105"><xref:System.Web.Mail.MailMessage> obiekty, które zawierają znaki spoza zestawu ASCII i które są serializowane w ramach programu .NET Framework 4.5 lub nowszej nie mogą być deserializowane w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="98f69-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>|
|<span data-ttu-id="98f69-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="98f69-106">Suggestion</span></span>|<span data-ttu-id="98f69-107">Upewnij się, że kod zapewnia obsługę wyjątków podczas deserializacji <xref:System.Web.Mail.MailMessage> obiektu.</span><span class="sxs-lookup"><span data-stu-id="98f69-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>|
|<span data-ttu-id="98f69-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="98f69-108">Scope</span></span>|<span data-ttu-id="98f69-109">Mały</span><span class="sxs-lookup"><span data-stu-id="98f69-109">Minor</span></span>|
|<span data-ttu-id="98f69-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="98f69-110">Version</span></span>|<span data-ttu-id="98f69-111">4.5</span><span class="sxs-lookup"><span data-stu-id="98f69-111">4.5</span></span>|
|<span data-ttu-id="98f69-112">Typ</span><span class="sxs-lookup"><span data-stu-id="98f69-112">Type</span></span>|<span data-ttu-id="98f69-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="98f69-113">Runtime</span></span>|
|<span data-ttu-id="98f69-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="98f69-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
