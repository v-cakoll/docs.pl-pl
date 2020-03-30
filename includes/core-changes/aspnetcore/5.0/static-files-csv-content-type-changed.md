---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391185"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="1fca3-101">Pliki statyczne: typ zawartości CSV zmieniony na zgodny ze standardami</span><span class="sxs-lookup"><span data-stu-id="1fca3-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="1fca3-102">W ASP.NET Core 5.0 domyślna `Content-Type` wartość nagłówka odpowiedzi używana przez [oprogramowanie pośredniczące plików statycznych](/aspnet/core/fundamentals/static-files) dla `text/csv`plików *csv* została zmieniona na wartość ze standardami.</span><span class="sxs-lookup"><span data-stu-id="1fca3-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="1fca3-103">Aby do dyskusji na ten temat, zobacz [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="1fca3-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1fca3-104">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="1fca3-104">Version introduced</span></span>

<span data-ttu-id="1fca3-105">5.0 Wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="1fca3-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1fca3-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="1fca3-106">Old behavior</span></span>

<span data-ttu-id="1fca3-107">Użyto `Content-Type` `application/octet-stream` wartości nagłówka.</span><span class="sxs-lookup"><span data-stu-id="1fca3-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1fca3-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="1fca3-108">New behavior</span></span>

<span data-ttu-id="1fca3-109">Używana `Content-Type` jest `text/csv` wartość nagłówka.</span><span class="sxs-lookup"><span data-stu-id="1fca3-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1fca3-110">Powód zmiany</span><span class="sxs-lookup"><span data-stu-id="1fca3-110">Reason for change</span></span>

<span data-ttu-id="1fca3-111">Zgodność z normą [RFC 7111.](https://tools.ietf.org/html/rfc7111#section-5.1)</span><span class="sxs-lookup"><span data-stu-id="1fca3-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1fca3-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="1fca3-112">Recommended action</span></span>

<span data-ttu-id="1fca3-113">Jeśli ta zmiana ma wpływ na aplikację, można dostosować mapowanie typu rozszerzenia pliku do MIME.</span><span class="sxs-lookup"><span data-stu-id="1fca3-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="1fca3-114">Aby powrócić do `application/octet-stream` typu MIME, <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> zmodyfikuj wywołanie metody w `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="1fca3-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="1fca3-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1fca3-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="1fca3-116">Aby uzyskać więcej informacji na temat dostosowywania mapowania, zobacz [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="1fca3-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="1fca3-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="1fca3-117">Category</span></span>

<span data-ttu-id="1fca3-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1fca3-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1fca3-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1fca3-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
