---
title: Zmiany w przestrzeni nazw System.Uri w wersji 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 97decd9054dfcdfc41204bf7683aebb95096e9d2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194926"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="c72fa-102">Zmiany w przestrzeni nazw System.Uri w wersji 2.0</span><span class="sxs-lookup"><span data-stu-id="c72fa-102">Changes to the System.Uri namespace in version 2.0</span></span>

<span data-ttu-id="c72fa-103">Wprowadzono kilka zmian <xref:System.Uri?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="c72fa-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c72fa-104">Te zmiany stałej nieprawidłowe zachowanie, rozszerzone użyteczność i lepsze zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="c72fa-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>

## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="c72fa-105">Elementy członkowskie przestarzała i przestarzałe</span><span class="sxs-lookup"><span data-stu-id="c72fa-105">Obsolete and deprecated Members</span></span>

 <span data-ttu-id="c72fa-106">Konstruktory:</span><span class="sxs-lookup"><span data-stu-id="c72fa-106">Constructors:</span></span>

- <span data-ttu-id="c72fa-107">Wszystkie konstruktory, które mają `dontEscape` parametru.</span><span class="sxs-lookup"><span data-stu-id="c72fa-107">All constructors that have a `dontEscape` parameter.</span></span>

 <span data-ttu-id="c72fa-108">Metody:</span><span class="sxs-lookup"><span data-stu-id="c72fa-108">Methods:</span></span>

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a><span data-ttu-id="c72fa-109">Zmiany</span><span class="sxs-lookup"><span data-stu-id="c72fa-109">Changes</span></span>

- <span data-ttu-id="c72fa-110">Dla schematów identyfikator URI, które nie mają części kwerendy (plik, ftp i inne) "?" znak jest zawsze poprzedzone znakiem zmiany znaczenia i nie jest uważany za początku <xref:System.Uri.Query%2A> części.</span><span class="sxs-lookup"><span data-stu-id="c72fa-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>

- <span data-ttu-id="c72fa-111">Niejawne pliku identyfikatorów URI (w postaci `c:\directory\file@name.txt`), znaku fragmentu ("#") jest zawsze poprzedzone znakiem zmiany znaczenia, chyba że wymagane są pełne unescaping lub <xref:System.Uri.LocalPath%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="c72fa-111">For implicit file URIs (of the form `c:\directory\file@name.txt`), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>

- <span data-ttu-id="c72fa-112">Obsługa hostname UNC została usunięta; przyjęto Specyfikacja IDN, reprezentujący międzynarodowych nazw hostów.</span><span class="sxs-lookup"><span data-stu-id="c72fa-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>

- <span data-ttu-id="c72fa-113"><xref:System.Uri.LocalPath%2A> zawsze zwraca ciąg całkowicie o niezmienionym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="c72fa-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>

- <span data-ttu-id="c72fa-114"><xref:System.Uri.ToString%2A> nie unescape o zmienionym znaczeniu '%', '?', lub znaku "#".</span><span class="sxs-lookup"><span data-stu-id="c72fa-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>

- <span data-ttu-id="c72fa-115"><xref:System.Uri.Equals%2A> zawiera teraz <xref:System.Uri.Query%2A> wchodzi w skład w sprawdzanie równości.</span><span class="sxs-lookup"><span data-stu-id="c72fa-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>

- <span data-ttu-id="c72fa-116">Operatory "=="i"! =" zastąpione i połączony z <xref:System.Uri.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c72fa-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>

- <span data-ttu-id="c72fa-117"><xref:System.Uri.IsLoopback%2A> teraz tworzy spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="c72fa-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>

- <span data-ttu-id="c72fa-118">Identyfikator URI "`file:///path`" nie jest już przetłumaczyć `file://path`.</span><span class="sxs-lookup"><span data-stu-id="c72fa-118">The URI "`file:///path`" is no longer translated into `file://path`.</span></span>

- <span data-ttu-id="c72fa-119">"#" teraz jest rozpoznawana jako terminatora nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="c72fa-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="c72fa-120">Oznacza to, że `http://contoso.com#fragment` teraz jest konwertowany na `http://contoso.com/#fragment`.</span><span class="sxs-lookup"><span data-stu-id="c72fa-120">That is, `http://contoso.com#fragment` is now converted to `http://contoso.com/#fragment`.</span></span>

- <span data-ttu-id="c72fa-121">Błąd podczas łączenia podstawowy identyfikator URI z fragmentem został rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="c72fa-121">A bug when combining a base URI with a fragment has been fixed.</span></span>

- <span data-ttu-id="c72fa-122">Błąd w <xref:System.Uri.HostNameType%2A> został rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="c72fa-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>

- <span data-ttu-id="c72fa-123">Naprawiono usterkę podczas analizowania NNTP.</span><span class="sxs-lookup"><span data-stu-id="c72fa-123">A bug in NNTP parsing is fixed.</span></span>

- <span data-ttu-id="c72fa-124">Identyfikator URI w postaci HTTP:contoso.com teraz zgłasza wyjątek podczas analizowania.</span><span class="sxs-lookup"><span data-stu-id="c72fa-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>

- <span data-ttu-id="c72fa-125">Struktura poprawnie przetwarza informacje o użytkowniku w identyfikatorze URI.</span><span class="sxs-lookup"><span data-stu-id="c72fa-125">The Framework correctly handles userinfo in a URI.</span></span>

- <span data-ttu-id="c72fa-126">Kompresja ścieżki identyfikatora URI jest stała, tak, aby uszkodzone URI nie może przechodzić przez system plików powyżej katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="c72fa-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>

## <a name="see-also"></a><span data-ttu-id="c72fa-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c72fa-127">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
