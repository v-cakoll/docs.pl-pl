---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620134"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="5d1e1-101">Właściwość HttpRequest. ContentEncoding zabrania UTF7</span><span class="sxs-lookup"><span data-stu-id="5d1e1-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

#### <a name="details"></a><span data-ttu-id="5d1e1-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="5d1e1-102">Details</span></span>

<span data-ttu-id="5d1e1-103">Począwszy od .NET Framework 4,5, kodowanie UTF-7 jest zabronione w <xref:System.Web.HttpRequest?displayProperty=fullName> treści "s".</span><span class="sxs-lookup"><span data-stu-id="5d1e1-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=fullName>s' bodies.</span></span> <span data-ttu-id="5d1e1-104">Dane dla aplikacji, które zależą od danych przychodzących w formacie UTF-7, nie będą poprawnie dekodowane w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5d1e1-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="5d1e1-105">Suggestion</span></span>

<span data-ttu-id="5d1e1-106">W idealnym przypadku aplikacje należy zaktualizować tak, aby nie korzystały z kodowania UTF-7 w <xref:System.Web.HttpRequest?displayProperty=fullName> s.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=fullName>s.</span></span> <span data-ttu-id="5d1e1-107">Alternatywnie można przywrócić starsze zachowanie przy użyciu <code>aspnet:AllowUtf7RequestContentEncoding</code> atrybutu [AppSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>

| <span data-ttu-id="5d1e1-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5d1e1-108">Name</span></span>    | <span data-ttu-id="5d1e1-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="5d1e1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5d1e1-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="5d1e1-110">Scope</span></span>   |<span data-ttu-id="5d1e1-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="5d1e1-111">Edge</span></span>|
|<span data-ttu-id="5d1e1-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="5d1e1-112">Version</span></span>|<span data-ttu-id="5d1e1-113">4.5</span><span class="sxs-lookup"><span data-stu-id="5d1e1-113">4.5</span></span>|
|<span data-ttu-id="5d1e1-114">Typ</span><span class="sxs-lookup"><span data-stu-id="5d1e1-114">Type</span></span>|<span data-ttu-id="5d1e1-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5d1e1-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5d1e1-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5d1e1-116">Affected APIs</span></span>

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
