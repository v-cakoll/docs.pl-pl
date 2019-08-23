---
title: Przykłady wyrażeń regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc62fffe3ca51acf0f2098d2975665b91b052992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930892"
---
# <a name="regular-expression-examples"></a><span data-ttu-id="d96a4-102">Przykłady wyrażeń regularnych</span><span class="sxs-lookup"><span data-stu-id="d96a4-102">Regular Expression Examples</span></span>
<span data-ttu-id="d96a4-103">Ta sekcja zawiera przykłady kodu, które ilustrują użycie wyrażeń regularnych we wspólnych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="d96a4-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d96a4-104"><xref:System.Web.RegularExpressions> Przestrzeń nazw zawiera wiele obiektów wyrażeń regularnych, które implementują wstępnie zdefiniowane wzorce wyrażeń regularnych na potrzeby analizowania ciągów z dokumentów HTML, XML i ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d96a4-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="d96a4-105">Na przykład <xref:System.Web.RegularExpressions.TagRegex> Klasa identyfikuje początkowe Tagi w ciągu <xref:System.Web.RegularExpressions.CommentRegex> , a Klasa identyfikuje Komentarze ASP.NET w ciągu.</span><span class="sxs-lookup"><span data-stu-id="d96a4-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d96a4-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d96a4-106">In This Section</span></span>  
 [<span data-ttu-id="d96a4-107">Przykład: Skanowanie w poszukiwaniu HREF</span><span class="sxs-lookup"><span data-stu-id="d96a4-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="d96a4-108">Zawiera przykład, który przeszukuje ciąg wejściowy i drukuje wszystkie odwołania href = "..." wartości i ich lokalizacje w ciągu.</span><span class="sxs-lookup"><span data-stu-id="d96a4-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="d96a4-109">Przykład: Zmienianie formatów daty</span><span class="sxs-lookup"><span data-stu-id="d96a4-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="d96a4-110">Zawiera przykład zastępujący daty w postaci mm/dd/rr z datami w postaci dd-mm-rr.</span><span class="sxs-lookup"><span data-stu-id="d96a4-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="d96a4-111">Instrukcje: Wyodrębnianie protokołu i numeru portu z adresu URL</span><span class="sxs-lookup"><span data-stu-id="d96a4-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="d96a4-112">Zawiera przykład wyodrębniający protokół i numer portu z ciągu, który zawiera adres URL.</span><span class="sxs-lookup"><span data-stu-id="d96a4-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="d96a4-113">Na przykład "http://www.contoso.com:8080/letters/readme.html" zwraca "http: 8080".</span><span class="sxs-lookup"><span data-stu-id="d96a4-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="d96a4-114">Instrukcje: Nieprawidłowe znaki w ciągu</span><span class="sxs-lookup"><span data-stu-id="d96a4-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="d96a4-115">Zapewnia przykład, że paski są nieprawidłowe znaki inne niż alfanumeryczne z ciągu.</span><span class="sxs-lookup"><span data-stu-id="d96a4-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="d96a4-116">Instrukcje: Sprawdź, czy ciągi są w prawidłowym formacie poczty E-mail</span><span class="sxs-lookup"><span data-stu-id="d96a4-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="d96a4-117">Zawiera przykład, który sprawdza, czy ciąg jest w prawidłowym formacie poczty e-mail.</span><span class="sxs-lookup"><span data-stu-id="d96a4-117">Provides an example that verifies that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d96a4-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d96a4-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="d96a4-119">Zawiera informacje dotyczące biblioteki klas dla przestrzeni nazw .NET **System. Text. RegularExpressions** .</span><span class="sxs-lookup"><span data-stu-id="d96a4-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d96a4-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d96a4-120">Related Sections</span></span>  
 [<span data-ttu-id="d96a4-121">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="d96a4-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="d96a4-122">Zawiera omówienie aspektu języka programowania wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="d96a4-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="d96a4-123">Model obiektów wyrażeń regularnych</span><span class="sxs-lookup"><span data-stu-id="d96a4-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="d96a4-124">Opisuje klasy wyrażeń regularnych zawarte w `System.Text.RegularExpression` przestrzeni nazw i zawiera przykłady ich użycia.</span><span class="sxs-lookup"><span data-stu-id="d96a4-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="d96a4-125">Szczegóły dotyczące zachowania wyrażeń regularnych</span><span class="sxs-lookup"><span data-stu-id="d96a4-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="d96a4-126">Zawiera informacje na temat możliwości i zachowania wyrażeń regularnych programu .NET.</span><span class="sxs-lookup"><span data-stu-id="d96a4-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="d96a4-127">Język wyrażeń regularnych — podręczny wykaz</span><span class="sxs-lookup"><span data-stu-id="d96a4-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="d96a4-128">Zawiera informacje dotyczące zestawu znaków, operatorów i konstrukcji, których można użyć do definiowania wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="d96a4-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
