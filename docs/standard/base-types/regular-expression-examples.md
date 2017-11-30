---
title: "Przykłady wyrażeń regularnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d7fa8fe2bade9f20f71f846c717d79d6b6ffb36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-examples"></a><span data-ttu-id="9e97d-102">Przykłady wyrażeń regularnych</span><span class="sxs-lookup"><span data-stu-id="9e97d-102">Regular Expression Examples</span></span>
<span data-ttu-id="9e97d-103">Ta sekcja zawiera przykłady kodu, ilustrujące używanie wyrażeń regularnych w typowych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="9e97d-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e97d-104"><xref:System.Web.RegularExpressions> Przestrzeń nazw zawiera wiele obiektów wyrażeń regularnych, implementujących wzorców wstępnie zdefiniowanych wyrażeń regularnych do analizowania ciągów z dokumentów HTML, XML i programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9e97d-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="9e97d-105">Na przykład <xref:System.Web.RegularExpressions.TagRegex> klasy identyfikuje początkowe tagi w ciągu i <xref:System.Web.RegularExpressions.CommentRegex> klasy identyfikuje komentarze ASP.NET w ciągu.</span><span class="sxs-lookup"><span data-stu-id="9e97d-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e97d-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9e97d-106">In This Section</span></span>  
 [<span data-ttu-id="9e97d-107">Przykład: Wyszukiwanie wartości href</span><span class="sxs-lookup"><span data-stu-id="9e97d-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="9e97d-108">Zawiera przykład, w którym wyszukuje ciąg wejściowy i drukowania wszystkich href = "..." wartości i ich lokalizacji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="9e97d-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="9e97d-109">Przykład: Zmienianie formatów daty</span><span class="sxs-lookup"><span data-stu-id="9e97d-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="9e97d-110">Przykład zastępujący daty w formacie mm/dd/rr z daty w formacie dd-mm rr.</span><span class="sxs-lookup"><span data-stu-id="9e97d-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="9e97d-111">Porady: wyodrębnianie protokółu i numeru portu z adresu URL</span><span class="sxs-lookup"><span data-stu-id="9e97d-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="9e97d-112">Przykład wyodrębniające protokołem i numerem portu z ciąg znaków zawierający adres URL.</span><span class="sxs-lookup"><span data-stu-id="9e97d-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="9e97d-113">Na przykład "http://www.contoso.com:8080/letters/readme.html" zwraca "http:8080".</span><span class="sxs-lookup"><span data-stu-id="9e97d-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="9e97d-114">Porady: usuwanie nieprawidłowych znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="9e97d-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="9e97d-115">Przykład wyodrębniania nieprawidłowe znaki inne niż alfanumeryczne z ciągu.</span><span class="sxs-lookup"><span data-stu-id="9e97d-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="9e97d-116">Porady: Sprawdź, czy Format ciągów jest prawidłowy adres E-mail</span><span class="sxs-lookup"><span data-stu-id="9e97d-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="9e97d-117">Zawiera przykład, w którym można użyć, aby sprawdzić, czy ciąg w formacie prawidłowy adres e-mail.</span><span class="sxs-lookup"><span data-stu-id="9e97d-117">Provides an example that you can use to verify that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9e97d-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="9e97d-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="9e97d-119">Zawiera informacje o odwołaniu biblioteki klas dla programu .NET **System.Text.RegularExpressions** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9e97d-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9e97d-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9e97d-120">Related Sections</span></span>  
 [<span data-ttu-id="9e97d-121">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="9e97d-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="9e97d-122">Omówienie programowania aspekt język wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="9e97d-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="9e97d-123">Model obiektów wyrażeń regularnych</span><span class="sxs-lookup"><span data-stu-id="9e97d-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="9e97d-124">W tym artykule opisano klasy wyrażeń regularnych zawarte w `System.Text.RegularExpression` przestrzeni nazw i przykłady ich użycia.</span><span class="sxs-lookup"><span data-stu-id="9e97d-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="9e97d-125">Szczegóły zachowania wyrażeń regularnych</span><span class="sxs-lookup"><span data-stu-id="9e97d-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="9e97d-126">Zawiera informacje dotyczące możliwości i zachowania wyrażeń regularnych programu .NET.</span><span class="sxs-lookup"><span data-stu-id="9e97d-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="9e97d-127">Język wyrażeń regularnych — podręczny wykaz</span><span class="sxs-lookup"><span data-stu-id="9e97d-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="9e97d-128">Zawiera informacje dotyczące zestawu znaków, Operatorzy i konstrukcji, których można użyć do zdefiniowania wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="9e97d-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
