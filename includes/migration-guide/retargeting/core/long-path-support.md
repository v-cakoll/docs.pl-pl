---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614711"
---
### <a name="long-path-support"></a><span data-ttu-id="f0276-101">Obsługa długich ścieżek</span><span class="sxs-lookup"><span data-stu-id="f0276-101">Long path support</span></span>

#### <a name="details"></a><span data-ttu-id="f0276-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f0276-102">Details</span></span>

<span data-ttu-id="f0276-103">Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.2, obsługiwane są długie ścieżki (od do 32 znaków), a 260-znak (lub `MAX_PATH` ) ograniczenie długości ścieżki zostało usunięte. W przypadku aplikacji, które są ponownie kompilowane do .NET Framework 4.6.2, ścieżki kodu, które wcześniej wywołały, <xref:System.IO.PathTooLongException?displayProperty=fullName> ponieważ ścieżka przekroczyła 260 znaków, zostanie teraz zgłoszony <xref:System.IO.PathTooLongException?displayProperty=fullName> tylko w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="f0276-103">Starting with apps that target the .NET Framework 4.6.2, long paths (of up to 32K characters) are supported, and the 260-character (or `MAX_PATH`) limitation on path lengths has been removed.For apps that are recompiled to target the .NET Framework 4.6.2, code paths that previously threw a <xref:System.IO.PathTooLongException?displayProperty=fullName> because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException?displayProperty=fullName> only under the following conditions:</span></span>

- <span data-ttu-id="f0276-104">Długość ścieżki przekracza <xref:System.Int16.MaxValue> (32 767) znaków.</span><span class="sxs-lookup"><span data-stu-id="f0276-104">The length of the path is greater than <xref:System.Int16.MaxValue> (32,767) characters.</span></span>
- <span data-ttu-id="f0276-105">System operacyjny zwraca `COR_E_PATHTOOLONG` lub jego odpowiednik.</span><span class="sxs-lookup"><span data-stu-id="f0276-105">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>
<span data-ttu-id="f0276-106">W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.6.1 i wcześniejszych wersji, środowisko uruchomieniowe automatycznie zgłasza, <xref:System.IO.PathTooLongException?displayProperty=fullName> gdy ścieżka przekracza 260 znaków.</span><span class="sxs-lookup"><span data-stu-id="f0276-106">For apps that target the .NET Framework 4.6.1 and earlier versions, the runtime automatically throws a <xref:System.IO.PathTooLongException?displayProperty=fullName> whenever a path exceeds 260 characters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f0276-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f0276-107">Suggestion</span></span>

<span data-ttu-id="f0276-108">W przypadku aplikacji przeznaczonych dla .NET Framework 4.6.2 możesz zrezygnować z obsługi długiej ścieżki, jeśli nie jest to pożądane, dodając następujący element do `<runtime>` sekcji `app.config` pliku:</span><span class="sxs-lookup"><span data-stu-id="f0276-108">For apps that target the .NET Framework 4.6.2, you can opt out of long path support if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

<span data-ttu-id="f0276-109">W przypadku aplikacji, które są przeznaczone dla wcześniejszych wersji .NET Framework ale działają na .NET Framework 4.6.2 lub nowszych, możesz zrezygnować z obsługi ścieżek długich, dodając następujące elementy do `<runtime>` sekcji `app.config` pliku:</span><span class="sxs-lookup"><span data-stu-id="f0276-109">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.6.2 or later, you can opt in to long path support by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| <span data-ttu-id="f0276-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f0276-110">Name</span></span>    | <span data-ttu-id="f0276-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="f0276-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f0276-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="f0276-112">Scope</span></span>   | <span data-ttu-id="f0276-113">Mały</span><span class="sxs-lookup"><span data-stu-id="f0276-113">Minor</span></span>       |
| <span data-ttu-id="f0276-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="f0276-114">Version</span></span> | <span data-ttu-id="f0276-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f0276-115">4.6.2</span></span>       |
| <span data-ttu-id="f0276-116">Typ</span><span class="sxs-lookup"><span data-stu-id="f0276-116">Type</span></span>    | <span data-ttu-id="f0276-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f0276-117">Retargeting</span></span> |
