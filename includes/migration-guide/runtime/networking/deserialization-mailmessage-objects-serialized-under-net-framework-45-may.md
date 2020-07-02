---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620347"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="206ab-101">Deserializacja serializowanych obiektów MailMessage w .NET Framework 4,5 może zakończyć się niepowodzeniem</span><span class="sxs-lookup"><span data-stu-id="206ab-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="206ab-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="206ab-102">Details</span></span>

<span data-ttu-id="206ab-103">Począwszy od .NET Framework 4,5, <xref:System.Web.Mail.MailMessage> obiekty mogą zawierać znaki inne niż ASCII.</span><span class="sxs-lookup"><span data-stu-id="206ab-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="206ab-104">W .NET Framework 4 obsługiwane są tylko znaki ASCII.</span><span class="sxs-lookup"><span data-stu-id="206ab-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="206ab-105"><xref:System.Web.Mail.MailMessage>obiekty, które zawierają znaki inne niż ASCII i które są serializowane w .NET Framework 4,5 lub nowszej, nie mogą być deserializowane w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="206ab-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="206ab-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="206ab-106">Suggestion</span></span>

<span data-ttu-id="206ab-107">Upewnij się, że kod zapewnia obsługę wyjątków podczas deserializacji <xref:System.Web.Mail.MailMessage> obiektu.</span><span class="sxs-lookup"><span data-stu-id="206ab-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="206ab-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="206ab-108">Name</span></span>    | <span data-ttu-id="206ab-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="206ab-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="206ab-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="206ab-110">Scope</span></span>   |<span data-ttu-id="206ab-111">Mały</span><span class="sxs-lookup"><span data-stu-id="206ab-111">Minor</span></span>|
|<span data-ttu-id="206ab-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="206ab-112">Version</span></span>|<span data-ttu-id="206ab-113">4.5</span><span class="sxs-lookup"><span data-stu-id="206ab-113">4.5</span></span>|
|<span data-ttu-id="206ab-114">Typ</span><span class="sxs-lookup"><span data-stu-id="206ab-114">Type</span></span>|<span data-ttu-id="206ab-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="206ab-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="206ab-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="206ab-116">Affected APIs</span></span>

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
