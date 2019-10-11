---
ms.openlocfilehash: f9ae32c44e5648eb74d7eab9fa5aa6cc2f17b9a1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237434"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="f7377-101">Ustawienia regionalne "C" są mapowane na niezmienne ustawienia regionalne</span><span class="sxs-lookup"><span data-stu-id="f7377-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="f7377-102">Program .NET Core 2,2 i jego wcześniejsze wersje zależą od domyślnego zachowania ICU, które mapuje ustawienia regionalne "C" na ustawienia regionalne en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="f7377-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="f7377-103">Ustawienia regionalne en_US_POSIX mają niepożądane zachowanie sortowania, ponieważ nie obsługuje porównywania ciągów bez uwzględniania wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="f7377-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="f7377-104">Ponieważ niektóre dystrybucje systemu Linux ustawiają ustawienia regionalne "C" jako domyślne ustawienia regionalne, użytkownicy mieli nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f7377-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span> 

#### <a name="change-description"></a><span data-ttu-id="f7377-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="f7377-105">Change description</span></span>

<span data-ttu-id="f7377-106">Począwszy od platformy .NET Core 3,0, mapowanie ustawień regionalnych "C" zostało zmienione tak, aby korzystało z niezmiennej ustawień regionalnych zamiast en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="f7377-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="f7377-107">Ustawienia regionalne "C" do mapowania niezmiennej są również stosowane do systemu Windows w celu zapewnienia spójności.</span><span class="sxs-lookup"><span data-stu-id="f7377-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="f7377-108">Mapowanie "C" na kulturę en_US_POSIX spowodowało pomyłkę klienta, ponieważ en_US_POSIX nie obsługuje operacji wyszukiwania ciągów z uwzględnieniem wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="f7377-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="f7377-109">Ponieważ ustawienia regionalne "C" są używane jako domyślne ustawienia regionalne dla niektórych dystrybucje systemu Linux, klienci napotykali to niepożądane zachowanie w tych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="f7377-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="f7377-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="f7377-110">Version introduced</span></span>

<span data-ttu-id="f7377-111">3.0</span><span class="sxs-lookup"><span data-stu-id="f7377-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="f7377-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f7377-112">Recommended action</span></span>

<span data-ttu-id="f7377-113">Niczego nie ma więcej niż świadomość tej zmiany.</span><span class="sxs-lookup"><span data-stu-id="f7377-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="f7377-114">Ta zmiana dotyczy tylko aplikacji, które korzystają z mapowania ustawień regionalnych "C".</span><span class="sxs-lookup"><span data-stu-id="f7377-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="f7377-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f7377-115">Category</span></span>

<span data-ttu-id="f7377-116">Globalizacji</span><span class="sxs-lookup"><span data-stu-id="f7377-116">Globalization</span></span> 

### <a name="affected-apis"></a><span data-ttu-id="f7377-117">Narażone interfejsy API</span><span class="sxs-lookup"><span data-stu-id="f7377-117">Affected APIs</span></span>

<span data-ttu-id="f7377-118">Ta zmiana ma wpływ na wszystkie interfejsy API sortowania i kultury.</span><span class="sxs-lookup"><span data-stu-id="f7377-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
