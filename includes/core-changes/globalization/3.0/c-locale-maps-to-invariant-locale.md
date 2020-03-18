---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567782"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="c843a-101">Mapy regionalne "C" do niezmiennych ustawień regionalnych</span><span class="sxs-lookup"><span data-stu-id="c843a-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="c843a-102">.NET Core 2.2 i wcześniejsze wersje zależą od domyślnego zachowania ICU, które mapuje ustawienia regionalne "C" na ustawienia regionalne en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="c843a-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="c843a-103">Ustawienia regionalne en_US_POSIX ma niepożądane zachowanie sortowania, ponieważ nie obsługuje porównania ciągów bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="c843a-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="c843a-104">Ponieważ niektóre dystrybucje systemu Linux ustawić ustawienia regionalne "C" jako domyślne ustawienia regionalne, użytkownicy doświadczali nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="c843a-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c843a-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="c843a-105">Change description</span></span>

<span data-ttu-id="c843a-106">Począwszy od .NET Core 3.0, mapowanie ustawień regionalnych "C" zostało zmienione, aby użyć ustawień regionalnych Niezmienne zamiast en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="c843a-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="c843a-107">Ustawienia regionalne "C" do mapowania niezmiennego jest również stosowany do systemu Windows dla spójności.</span><span class="sxs-lookup"><span data-stu-id="c843a-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="c843a-108">Mapowanie "C" na kulturę en_US_POSIX spowodowało zamieszanie klientów, ponieważ en_US_POSIX nie obsługuje operacji sortowania/wyszukiwania ciągów bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="c843a-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="c843a-109">Ponieważ ustawienia regionalne "C" są używane jako domyślne ustawienia regionalne w niektórych dystrybucjach systemu Linux, klienci doświadczyli tego niepożądanego zachowania w tych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="c843a-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c843a-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="c843a-110">Version introduced</span></span>

<span data-ttu-id="c843a-111">3.0</span><span class="sxs-lookup"><span data-stu-id="c843a-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="c843a-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="c843a-112">Recommended action</span></span>

<span data-ttu-id="c843a-113">Nic konkretnego więcej niż świadomość tej zmiany.</span><span class="sxs-lookup"><span data-stu-id="c843a-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="c843a-114">Ta zmiana dotyczy tylko aplikacji, które używają mapowania ustawień regionalnych "C".</span><span class="sxs-lookup"><span data-stu-id="c843a-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="c843a-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="c843a-115">Category</span></span>

<span data-ttu-id="c843a-116">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="c843a-116">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="c843a-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c843a-117">Affected APIs</span></span>

<span data-ttu-id="c843a-118">Ta zmiana dotyczy wszystkich interfejsów API sortowania i kultury.</span><span class="sxs-lookup"><span data-stu-id="c843a-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
