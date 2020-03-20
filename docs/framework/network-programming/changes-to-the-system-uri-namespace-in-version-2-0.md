---
title: Zmiany w obszarze nazw System.Uri w wersji 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 987010b8367069e8089df3f809d23f258bb68f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642766"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="7b0bd-102">Zmiany w obszarze nazw System.Uri w wersji 2.0</span><span class="sxs-lookup"><span data-stu-id="7b0bd-102">Changes to the System.Uri namespace in version 2.0</span></span>

<span data-ttu-id="7b0bd-103">Wprowadzono kilka zmian <xref:System.Uri?displayProperty=nameWithType> w klasie.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7b0bd-104">Zmiany te naprawiły nieprawidłowe zachowanie, zwiększoną użyteczność i zwiększone zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>

## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="7b0bd-105">Przestarzali i przestarzali członkowie</span><span class="sxs-lookup"><span data-stu-id="7b0bd-105">Obsolete and deprecated Members</span></span>

 <span data-ttu-id="7b0bd-106">Konstruktorów:</span><span class="sxs-lookup"><span data-stu-id="7b0bd-106">Constructors:</span></span>

- <span data-ttu-id="7b0bd-107">Wszystkie konstruktory, które mają `dontEscape` parametr.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-107">All constructors that have a `dontEscape` parameter.</span></span>

 <span data-ttu-id="7b0bd-108">Metody:</span><span class="sxs-lookup"><span data-stu-id="7b0bd-108">Methods:</span></span>

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a><span data-ttu-id="7b0bd-109">Zmiany</span><span class="sxs-lookup"><span data-stu-id="7b0bd-109">Changes</span></span>

- <span data-ttu-id="7b0bd-110">W przypadku schematów URI, o których wiadomo, że nie mają części kwerendy (plik, ftp i inne), znak '?' jest zawsze zmieniany i nie jest uważany za początek <xref:System.Uri.Query%2A> części.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>

- <span data-ttu-id="7b0bd-111">W przypadku identyfikatorów URI `c:\directory\file@name.txt`pliku niejawnego (formularza) znak fragmentu ("#") jest <xref:System.Uri.LocalPath%2A> `true`zawsze zmieniany, chyba że wymagane jest pełne unescaping lub jest .</span><span class="sxs-lookup"><span data-stu-id="7b0bd-111">For implicit file URIs (of the form `c:\directory\file@name.txt`), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>

- <span data-ttu-id="7b0bd-112">Usunięto obsługę nazwy hosta UNC; przyjęto specyfikację IDN reprezentującą międzynarodowe nazwy hostów.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>

- <span data-ttu-id="7b0bd-113"><xref:System.Uri.LocalPath%2A>zawsze zwraca ciąg całkowicie nieograniczony.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>

- <span data-ttu-id="7b0bd-114"><xref:System.Uri.ToString%2A>nie unescape znak "%", "?", lub "#".</span><span class="sxs-lookup"><span data-stu-id="7b0bd-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>

- <span data-ttu-id="7b0bd-115"><xref:System.Uri.Equals%2A>teraz uwzględnia <xref:System.Uri.Query%2A> część kontroli równości.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>

- <span data-ttu-id="7b0bd-116">Operatory "==" i "!=" są zastępowane i połączone z <xref:System.Uri.Equals%2A> metodą.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>

- <span data-ttu-id="7b0bd-117"><xref:System.Uri.IsLoopback%2A>teraz daje spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>

- <span data-ttu-id="7b0bd-118">Identyfikator URI`file:///path`" " nie `file://path`jest już tłumaczony na .</span><span class="sxs-lookup"><span data-stu-id="7b0bd-118">The URI "`file:///path`" is no longer translated into `file://path`.</span></span>

- <span data-ttu-id="7b0bd-119">"#" jest teraz rozpoznawany jako terminator nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="7b0bd-120">Oznacza to, `http://contoso.com#fragment` że jest `http://contoso.com/#fragment`teraz konwertowany do .</span><span class="sxs-lookup"><span data-stu-id="7b0bd-120">That is, `http://contoso.com#fragment` is now converted to `http://contoso.com/#fragment`.</span></span>

- <span data-ttu-id="7b0bd-121">Naprawiono błąd podczas łączenia podstawowego identyfikatora URI z fragmentem.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-121">A bug when combining a base URI with a fragment has been fixed.</span></span>

- <span data-ttu-id="7b0bd-122">Naprawiono <xref:System.Uri.HostNameType%2A> błąd.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>

- <span data-ttu-id="7b0bd-123">Naprawiono błąd w analizowaniu NNTP.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-123">A bug in NNTP parsing is fixed.</span></span>

- <span data-ttu-id="7b0bd-124">Identyfikator URI formularza HTTP:contoso.com zgłasza teraz wyjątek analizy.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>

- <span data-ttu-id="7b0bd-125">Framework poprawnie obsługuje userinfo w identyfikatorze URI.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-125">The Framework correctly handles userinfo in a URI.</span></span>

- <span data-ttu-id="7b0bd-126">Kompresja ścieżki identyfikatora URI jest stała, dzięki czemu uszkodzony identyfikator URI nie może przechodzić przez system plików nad katalogiem głównym.</span><span class="sxs-lookup"><span data-stu-id="7b0bd-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b0bd-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b0bd-127">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
