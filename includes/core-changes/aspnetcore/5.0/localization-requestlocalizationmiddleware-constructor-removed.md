---
ms.openlocfilehash: b1d4b69b7a8ed68cd688dfd0249d5107b80e67c4
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281352"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="7e681-101">Lokalizacja: przestarzały Konstruktor został usunięty z oprogramowania pośredniczącego w lokalizacji żądania</span><span class="sxs-lookup"><span data-stu-id="7e681-101">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="7e681-102"><xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>Konstruktor, który <xref:Microsoft.Extensions.Logging.ILoggerFactory> nie ma parametru, został oznaczony jako przestarzały [w tym zatwierdzeniu](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span><span class="sxs-lookup"><span data-stu-id="7e681-102">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="7e681-103">W ASP.NET Core 5,0 przestarzały Konstruktor został usunięty.</span><span class="sxs-lookup"><span data-stu-id="7e681-103">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="7e681-104">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).</span><span class="sxs-lookup"><span data-stu-id="7e681-104">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7e681-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7e681-105">Version introduced</span></span>

<span data-ttu-id="7e681-106">5.0</span><span class="sxs-lookup"><span data-stu-id="7e681-106">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7e681-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="7e681-107">Old behavior</span></span>

<span data-ttu-id="7e681-108">Istnieje przestarzały `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="7e681-108">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7e681-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="7e681-109">New behavior</span></span>

<span data-ttu-id="7e681-110">Przestarzały `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Konstruktor nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7e681-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7e681-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="7e681-111">Reason for change</span></span>

<span data-ttu-id="7e681-112">Ta zmiana zapewnia, że oprogramowanie pośredniczące żądania ma zawsze dostęp do rejestratora.</span><span class="sxs-lookup"><span data-stu-id="7e681-112">This change ensures that the request localization middleware always has access to a logger.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7e681-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="7e681-113">Recommended action</span></span>

<span data-ttu-id="7e681-114">Podczas ręcznego konstruowania wystąpienia `RequestLocalizationMiddleware` , należy przekazać `ILoggerFactory` wystąpienie w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="7e681-114">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="7e681-115">Jeśli prawidłowe `ILoggerFactory` wystąpienie jest niedostępne w tym kontekście, rozważ przekazanie konstruktora oprogramowania pośredniczącego <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="7e681-115">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

#### <a name="category"></a><span data-ttu-id="7e681-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="7e681-116">Category</span></span>

<span data-ttu-id="7e681-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7e681-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7e681-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7e681-118">Affected APIs</span></span>

[<span data-ttu-id="7e681-119">RequestLocalizationMiddleware. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )</span><span class="sxs-lookup"><span data-stu-id="7e681-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
