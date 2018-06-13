---
title: Zmiany w przestrzeni nazw System.Uri w wersji 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 169454edd04bfdb55affcc2be12140f42dd2f7ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392451"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="0e84e-102">Zmiany w przestrzeni nazw System.Uri w wersji 2.0</span><span class="sxs-lookup"><span data-stu-id="0e84e-102">Changes to the System.Uri namespace in Version 2.0</span></span>
<span data-ttu-id="0e84e-103">Wprowadzono kilka zmian <xref:System.Uri?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="0e84e-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="0e84e-104">Te zmiany stałej niepoprawnego zachowania, rozszerzone użyteczność i zwiększonych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0e84e-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>  
  
## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="0e84e-105">Przestarzałe i przestarzałe elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0e84e-105">Obsolete and Deprecated Members</span></span>  
 <span data-ttu-id="0e84e-106">Konstruktory:</span><span class="sxs-lookup"><span data-stu-id="0e84e-106">Constructors:</span></span>  
  
-   <span data-ttu-id="0e84e-107">Wszystkie konstruktory, które mają `dontEscape` parametru.</span><span class="sxs-lookup"><span data-stu-id="0e84e-107">All constructors that have a `dontEscape` parameter.</span></span>  
  
 <span data-ttu-id="0e84e-108">Metody:</span><span class="sxs-lookup"><span data-stu-id="0e84e-108">Methods:</span></span>  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a><span data-ttu-id="0e84e-109">Zmiany</span><span class="sxs-lookup"><span data-stu-id="0e84e-109">Changes</span></span>  
  
-   <span data-ttu-id="0e84e-110">Dla schematy identyfikatorów URI, które nie mają części zapytania (pliku, ftp i inne) '?' znaków zawsze miały zmienione znaczenie i nie jest uważana za początku <xref:System.Uri.Query%2A> części.</span><span class="sxs-lookup"><span data-stu-id="0e84e-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>  
  
-   <span data-ttu-id="0e84e-111">Niejawne pliku identyfikatory URI (w postaci "c:\directory\file@name.txt"), fragment znak (#) zawsze została zmieniona, chyba że wymagane jest pełne unescaping lub <xref:System.Uri.LocalPath%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="0e84e-111">For implicit file URIs (of the form "c:\directory\file@name.txt"), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>  
  
-   <span data-ttu-id="0e84e-112">Została usunięta obsługa hostname UNC; przyjęto w specyfikacji IDN reprezentujący międzynarodowe nazwy hostów.</span><span class="sxs-lookup"><span data-stu-id="0e84e-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>  
  
-   <span data-ttu-id="0e84e-113"><xref:System.Uri.LocalPath%2A> zawsze zwraca wartość typu ciąg całkowicie niezmienionym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="0e84e-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>  
  
-   <span data-ttu-id="0e84e-114"><xref:System.Uri.ToString%2A> nie unescape zmienionym '%', '?', lub znaku "#".</span><span class="sxs-lookup"><span data-stu-id="0e84e-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>  
  
-   <span data-ttu-id="0e84e-115"><xref:System.Uri.Equals%2A> teraz obejmuje <xref:System.Uri.Query%2A> części w sprawdzania równości.</span><span class="sxs-lookup"><span data-stu-id="0e84e-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>  
  
-   <span data-ttu-id="0e84e-116">Operatory "=="i"! =" zastąpione i połączone z <xref:System.Uri.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0e84e-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>  
  
-   <span data-ttu-id="0e84e-117"><xref:System.Uri.IsLoopback%2A> teraz tworzy spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="0e84e-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>  
  
-   <span data-ttu-id="0e84e-118">Identyfikator URI "`file:///path`" jest już przetłumaczyć "file://path".</span><span class="sxs-lookup"><span data-stu-id="0e84e-118">The URI "`file:///path`" is no longer translated into "file://path".</span></span>  
  
-   <span data-ttu-id="0e84e-119">"#" teraz jest rozpoznawana jako terminatora nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="0e84e-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="0e84e-120">Oznacza to, że "http://consoto.com#fragment"teraz jest konwertowany na"http://contoso.com/#fragment".</span><span class="sxs-lookup"><span data-stu-id="0e84e-120">That is, "http://consoto.com#fragment" is now converted to "http://contoso.com/#fragment".</span></span>  
  
-   <span data-ttu-id="0e84e-121">Błąd podczas łączenia z fragmentem podstawowy identyfikator URI został rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="0e84e-121">A bug when combining a base URI with a fragment has been fixed.</span></span>  
  
-   <span data-ttu-id="0e84e-122">Błąd w <xref:System.Uri.HostNameType%2A> został rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="0e84e-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>  
  
-   <span data-ttu-id="0e84e-123">Błąd podczas analizowania NNTP jest stała.</span><span class="sxs-lookup"><span data-stu-id="0e84e-123">A bug in NNTP parsing is fixed.</span></span>  
  
-   <span data-ttu-id="0e84e-124">Identyfikator URI w postaci HTTP:contoso.com teraz zgłasza wyjątek podczas analizowania.</span><span class="sxs-lookup"><span data-stu-id="0e84e-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>  
  
-   <span data-ttu-id="0e84e-125">Platformę poprawnie obsługuje informacje o użytkowniku w identyfikatorze URI.</span><span class="sxs-lookup"><span data-stu-id="0e84e-125">The Framework correctly handles userinfo in a URI.</span></span>  
  
-   <span data-ttu-id="0e84e-126">Kompresja ścieżka identyfikatora URI jest ustalony tak, aby przerwane identyfikatora URI nie można przejść przez system plików główny.</span><span class="sxs-lookup"><span data-stu-id="0e84e-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e84e-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e84e-127">See Also</span></span>  
 <xref:System.Uri?displayProperty=nameWithType>
