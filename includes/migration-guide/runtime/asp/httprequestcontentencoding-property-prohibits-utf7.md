---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235429"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="65270-101">HttpRequest.ContentEncoding property prohibits UTF7</span><span class="sxs-lookup"><span data-stu-id="65270-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

|   |   |
|---|---|
|<span data-ttu-id="65270-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="65270-102">Details</span></span>|<span data-ttu-id="65270-103">Począwszy od programu .NET Framework 4.5, kodowanie UTF-7 jest zabronione w <xref:System.Web.HttpRequest?displayProperty=name>s' treści.</span><span class="sxs-lookup"><span data-stu-id="65270-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=name>s' bodies.</span></span> <span data-ttu-id="65270-104">Dane dla aplikacji, które zależą od danych przychodzących w formacie UTF-7, nie będą poprawnie dekodowane w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="65270-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>|
|<span data-ttu-id="65270-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="65270-105">Suggestion</span></span>|<span data-ttu-id="65270-106">W idealnym przypadku aplikacji powinien zostać zaktualizowany w taki sposób, aby nie używać kodowania w UTF-7 <xref:System.Web.HttpRequest?displayProperty=name>s.</span><span class="sxs-lookup"><span data-stu-id="65270-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=name>s.</span></span> <span data-ttu-id="65270-107">Alternatywnie, można przywrócić starsze zachowanie za pomocą <code>aspnet:AllowUtf7RequestContentEncoding</code> atrybutu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="65270-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>|
|<span data-ttu-id="65270-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="65270-108">Scope</span></span>|<span data-ttu-id="65270-109">Krawędź</span><span class="sxs-lookup"><span data-stu-id="65270-109">Edge</span></span>|
|<span data-ttu-id="65270-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="65270-110">Version</span></span>|<span data-ttu-id="65270-111">4.5</span><span class="sxs-lookup"><span data-stu-id="65270-111">4.5</span></span>|
|<span data-ttu-id="65270-112">Typ</span><span class="sxs-lookup"><span data-stu-id="65270-112">Type</span></span>|<span data-ttu-id="65270-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="65270-113">Runtime</span></span>|
|<span data-ttu-id="65270-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="65270-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
