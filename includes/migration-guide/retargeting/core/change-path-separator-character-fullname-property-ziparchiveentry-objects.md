---
ms.openlocfilehash: 148312743dd274728b178951548889dc3a680528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614694"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a><span data-ttu-id="70af8-101">Zmień znak separatora ścieżki w właściwości FullName obiektów klasy ZipArchiveEntry</span><span class="sxs-lookup"><span data-stu-id="70af8-101">Change in path separator character in FullName property of ZipArchiveEntry objects</span></span>

#### <a name="details"></a><span data-ttu-id="70af8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="70af8-102">Details</span></span>

<span data-ttu-id="70af8-103">W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.6.1 i nowszych wersji, znak separatora ścieżki został zmieniony z ukośnika odwrotnego (" \" ) na ukośnik ("/") we <xref:System.IO.Compression.ZipArchiveEntry.FullName> właściwości <xref:System.IO.Compression.ZipArchiveEntry> obiektów utworzonych przez przeciążenia <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="70af8-103">For apps that target the .NET Framework 4.6.1 and later versions, the path separator character has changed from a backslash ("\") to a forward slash ("/") in the <xref:System.IO.Compression.ZipArchiveEntry.FullName> property of <xref:System.IO.Compression.ZipArchiveEntry>  objects created by overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> method.</span></span> <span data-ttu-id="70af8-104">Zmiana powoduje, że implementacja platformy .NET jest zgodna z sekcją 4.4.17.1 [. Specyfikacja formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i zezwala na to. Archiwa ZIP do skompresowania w systemach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="70af8-104">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span><br /><span data-ttu-id="70af8-105">Dekompresowanie pliku zip utworzonego przez aplikację, która jest przeznaczona dla starszej wersji .NET Framework w systemach operacyjnych innych niż Windows, takich jak Macintosh, nie można zachować struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="70af8-105">Decompressing a zip file created by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="70af8-106">Na przykład w systemie Macintosh tworzy zestaw plików, których nazwa pliku łączy ścieżkę katalogu, wraz z dowolnym znakiem ukośnika odwrotnego ("") i nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="70af8-106">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("") characters, and the filename.</span></span> <span data-ttu-id="70af8-107">W związku z tym struktura katalogów nieskompresowanych plików nie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="70af8-107">As a result, the directory structure of decompressed files is not preserved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="70af8-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="70af8-108">Suggestion</span></span>

<span data-ttu-id="70af8-109">Wpływ tej zmiany na. Pliki ZIP, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw .NET Framework powinny być minimalne, ponieważ te interfejsy API mogą bezproblemowo obsługiwać ukośnik ("/") lub ukośnik odwrotny (" \" ) jako znak separatora ścieżki.</span><span class="sxs-lookup"><span data-stu-id="70af8-109">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO?displayProperty=nameWithType> namespace should be minimal, since these APIs can seamlessly handle either a forward slash ("/") or a backslash ("\") as the path separator character.</span></span><br /><span data-ttu-id="70af8-110">Jeśli ta zmiana jest niepożądana, można zrezygnować z jej przez dodanie ustawienia konfiguracji do [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70af8-110">If this change is undesirable, you can opt out of it by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="70af8-111">Poniższy przykład pokazuje `<runtime>` sekcję i `Switch.System.IO.Compression.ZipFile.UseBackslash` przełącznik rezygnacji:</span><span class="sxs-lookup"><span data-stu-id="70af8-111">The following example shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-out switch:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

<span data-ttu-id="70af8-112">Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 i nowszych wersjach, mogą zrezygnować z tego zachowania przez dodanie ustawienia konfiguracji do [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70af8-112">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="70af8-113">Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i `Switch.System.IO.Compression.ZipFile.UseBackslash` przełącznik zgody.</span><span class="sxs-lookup"><span data-stu-id="70af8-113">The following shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-in switch.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| <span data-ttu-id="70af8-114">Nazwa</span><span class="sxs-lookup"><span data-stu-id="70af8-114">Name</span></span>    | <span data-ttu-id="70af8-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="70af8-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="70af8-116">Zakres</span><span class="sxs-lookup"><span data-stu-id="70af8-116">Scope</span></span>   | <span data-ttu-id="70af8-117">Brzeg</span><span class="sxs-lookup"><span data-stu-id="70af8-117">Edge</span></span>        |
| <span data-ttu-id="70af8-118">Wersja</span><span class="sxs-lookup"><span data-stu-id="70af8-118">Version</span></span> | <span data-ttu-id="70af8-119">4.6.1</span><span class="sxs-lookup"><span data-stu-id="70af8-119">4.6.1</span></span>       |
| <span data-ttu-id="70af8-120">Typ</span><span class="sxs-lookup"><span data-stu-id="70af8-120">Type</span></span>    | <span data-ttu-id="70af8-121">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="70af8-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="70af8-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="70af8-122">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
