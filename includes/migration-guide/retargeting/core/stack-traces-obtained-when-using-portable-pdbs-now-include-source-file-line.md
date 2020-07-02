---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614796"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a><span data-ttu-id="122ed-101">Ślady stosu uzyskane podczas korzystania z przenośnego plików PDB teraz obejmują plik źródłowy i informacje o wierszu, jeśli jest to wymagane</span><span class="sxs-lookup"><span data-stu-id="122ed-101">Stack traces obtained when using portable PDBs now include source file and line information if requested</span></span>

#### <a name="details"></a><span data-ttu-id="122ed-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="122ed-102">Details</span></span>

<span data-ttu-id="122ed-103">Począwszy od .NET Framework 4.7.2, ślady stosu uzyskany podczas korzystania z przenośnego plików PDB Dołącz plik źródłowy i informacje o wierszu, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="122ed-103">Starting with .NET Framework 4.7.2, stack traces obtained when using portable PDBs include source file and line information when requested.</span></span> <span data-ttu-id="122ed-104">W wersjach wcześniejszych niż .NET Framework 4.7.2, plik źródłowy i informacje o wierszu byłyby niedostępne w przypadku używania przenośnych plików PDB, nawet jeśli zostały jawnie zażądane.</span><span class="sxs-lookup"><span data-stu-id="122ed-104">In versions prior to .NET Framework 4.7.2, source file and line information would be unavailable when using portable PDBs even if explicitly requested.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="122ed-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="122ed-105">Suggestion</span></span>

<span data-ttu-id="122ed-106">W przypadku aplikacji przeznaczonych dla .NET Framework 4.7.2 można zrezygnować z pliku źródłowego i informacji o wierszu w przypadku używania przenośnego plików PDB, jeśli nie jest to pożądane, dodając następujący element do `<runtime>` sekcji `app.config` pliku:</span><span class="sxs-lookup"><span data-stu-id="122ed-106">For applications that target the .NET Framework 4.7.2, you can opt out of the source file and line information when using portable PDBs if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

<span data-ttu-id="122ed-107">W przypadku aplikacji, które są przeznaczone dla wcześniejszych wersji .NET Framework ale są uruchamiane na .NET Framework 4.7.2 lub nowszych, można zrezygnować z pliku źródłowego i informacje o wierszu w przypadku używania przenośnego plików PDB przez dodanie następujących `<runtime>` elementów do sekcji `app.config` pliku:</span><span class="sxs-lookup"><span data-stu-id="122ed-107">For applications that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.2 or later, you can opt in to the source file and line information when using portable PDBs by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| <span data-ttu-id="122ed-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="122ed-108">Name</span></span>    | <span data-ttu-id="122ed-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="122ed-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="122ed-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="122ed-110">Scope</span></span>   | <span data-ttu-id="122ed-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="122ed-111">Edge</span></span>        |
| <span data-ttu-id="122ed-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="122ed-112">Version</span></span> | <span data-ttu-id="122ed-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="122ed-113">4.7.2</span></span>       |
| <span data-ttu-id="122ed-114">Typ</span><span class="sxs-lookup"><span data-stu-id="122ed-114">Type</span></span>    | <span data-ttu-id="122ed-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="122ed-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="122ed-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="122ed-116">Affected APIs</span></span>

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
