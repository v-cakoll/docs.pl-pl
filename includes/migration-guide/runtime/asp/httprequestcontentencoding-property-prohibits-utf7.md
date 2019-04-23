---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804722"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="52473-101">HttpRequest.ContentEncoding property prohibits UTF7</span><span class="sxs-lookup"><span data-stu-id="52473-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

|   |   |
|---|---|
|<span data-ttu-id="52473-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="52473-102">Details</span></span>|<span data-ttu-id="52473-103">Począwszy od programu .NET Framework 4.5, kodowanie UTF-7 jest zabronione w <xref:System.Web.HttpRequest?displayProperty=name>s' treści.</span><span class="sxs-lookup"><span data-stu-id="52473-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=name>s' bodies.</span></span> <span data-ttu-id="52473-104">Dane dla aplikacji, które zależą od danych przychodzących w formacie UTF-7, nie będą poprawnie dekodowane w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="52473-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>|
|<span data-ttu-id="52473-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="52473-105">Suggestion</span></span>|<span data-ttu-id="52473-106">W idealnym przypadku aplikacji powinien zostać zaktualizowany w taki sposób, aby nie używać kodowania w UTF-7 <xref:System.Web.HttpRequest?displayProperty=name>s.</span><span class="sxs-lookup"><span data-stu-id="52473-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=name>s.</span></span> <span data-ttu-id="52473-107">Alternatywnie, można przywrócić starsze zachowanie za pomocą <code>aspnet:AllowUtf7RequestContentEncoding</code> atrybutu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="52473-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>|
|<span data-ttu-id="52473-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="52473-108">Scope</span></span>|<span data-ttu-id="52473-109">Krawędź</span><span class="sxs-lookup"><span data-stu-id="52473-109">Edge</span></span>|
|<span data-ttu-id="52473-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="52473-110">Version</span></span>|<span data-ttu-id="52473-111">4.5</span><span class="sxs-lookup"><span data-stu-id="52473-111">4.5</span></span>|
|<span data-ttu-id="52473-112">Typ</span><span class="sxs-lookup"><span data-stu-id="52473-112">Type</span></span>|<span data-ttu-id="52473-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="52473-113">Runtime</span></span>|
|<span data-ttu-id="52473-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="52473-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
