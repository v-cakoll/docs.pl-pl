---
title: "Przykład wyrażenia regularnego: wyszukiwanie wartości HREF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c6da140ea82fc3c6d3f5f3001f37711ffe861370
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="regular-expression-example-scanning-for-hrefs"></a><span data-ttu-id="ebb86-102">Przykład wyrażenia regularnego: wyszukiwanie wartości HREF</span><span class="sxs-lookup"><span data-stu-id="ebb86-102">Regular Expression Example: Scanning for HREFs</span></span>
<span data-ttu-id="ebb86-103">Poniższy przykład wyszukuje ciąg wejściowy i wyświetla wszystkie href = "..." wartości i ich lokalizacji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="ebb86-103">The following example searches an input string and displays all the href="…" values and their locations in the string.</span></span>  
  
## <a name="the-regex-object"></a><span data-ttu-id="ebb86-104">Obiekt Regex</span><span class="sxs-lookup"><span data-stu-id="ebb86-104">The Regex Object</span></span>  
 <span data-ttu-id="ebb86-105">Ponieważ `DumpHRefs` metoda może być wywołana wiele razy z kodu użytkownika, używa `static` (`Shared` w języku Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ebb86-105">Because the `DumpHRefs` method can be called multiple times from user code, it uses the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ebb86-106">To umożliwia aparat wyrażeń regularnych do pamięci podręcznej z wyrażeniem regularnym i pozwala uniknąć ponoszenia dodatkowych nakładów na uruchamianiu nową <xref:System.Text.RegularExpressions.Regex> obiektu zawsze ma zostać wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="ebb86-106">This enables the regular expression engine to cache the regular expression and avoids the overhead of instantiating a new <xref:System.Text.RegularExpressions.Regex> object each time the method is called.</span></span> <span data-ttu-id="ebb86-107">A <xref:System.Text.RegularExpressions.Match> obiekt jest następnie używany do iterowania po wszystkich dopasowań w ciągu.</span><span class="sxs-lookup"><span data-stu-id="ebb86-107">A <xref:System.Text.RegularExpressions.Match> object is then used to iterate through all matches in the string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 <span data-ttu-id="ebb86-108">Poniższy przykład przedstawia następnie wywołania `DumpHRefs` metody.</span><span class="sxs-lookup"><span data-stu-id="ebb86-108">The following example then illustrates a call to the `DumpHRefs` method.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 <span data-ttu-id="ebb86-109">Wzorzec wyrażenia regularnego `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` jest interpretowany, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ebb86-109">The regular expression pattern `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="ebb86-110">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="ebb86-110">Pattern</span></span>|<span data-ttu-id="ebb86-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ebb86-111">Description</span></span>|  
|-------------|-----------------|  
|`href`|<span data-ttu-id="ebb86-112">Zgodny z ciągiem literału "href".</span><span class="sxs-lookup"><span data-stu-id="ebb86-112">Match the literal string "href".</span></span> <span data-ttu-id="ebb86-113">Dopasowanie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="ebb86-113">The match is case-insensitive.</span></span>|  
|`\s*`|<span data-ttu-id="ebb86-114">Dopasowanie do zera lub większej liczby znaków odstępu.</span><span class="sxs-lookup"><span data-stu-id="ebb86-114">Match zero or more white-space characters.</span></span>|  
|`=`|<span data-ttu-id="ebb86-115">Zgodne znaku równości.</span><span class="sxs-lookup"><span data-stu-id="ebb86-115">Match the equals sign.</span></span>|  
|`\s*`|<span data-ttu-id="ebb86-116">Dopasowanie do zera lub większej liczby znaków odstępu.</span><span class="sxs-lookup"><span data-stu-id="ebb86-116">Match zero or more white-space characters.</span></span>|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|<span data-ttu-id="ebb86-117">Pasuje do jednej z następujących bez przypisywanie wynik do przechwyconej grupy:</span><span class="sxs-lookup"><span data-stu-id="ebb86-117">Match one of the following without assigning the result to a captured group:</span></span><br /><br /> <span data-ttu-id="ebb86-118">-Cudzysłów lub apostrof, następuje zero lub więcej wystąpień dowolnych znaków innych niż cudzysłów lub apostrof następuje znak cudzysłowu lub apostrof.</span><span class="sxs-lookup"><span data-stu-id="ebb86-118">-   A quotation mark or apostrophe, followed by zero or more occurrences of any character other than a quotation mark or apostrophe, followed by a quotation mark or apostrophe.</span></span> <span data-ttu-id="ebb86-119">Grupa o nazwie `1` znajduje się w tym wzorcu.</span><span class="sxs-lookup"><span data-stu-id="ebb86-119">The group named `1` is included in this pattern.</span></span><br /><span data-ttu-id="ebb86-120">-Co najmniej jeden z systemem innym niż białe znaki.</span><span class="sxs-lookup"><span data-stu-id="ebb86-120">-   One or more non-white-space characters.</span></span> <span data-ttu-id="ebb86-121">Grupa o nazwie `1` znajduje się w tym wzorcu.</span><span class="sxs-lookup"><span data-stu-id="ebb86-121">The group named `1` is included in this pattern.</span></span>|  
|`(?<1>[^"']*)`|<span data-ttu-id="ebb86-122">Przypisz zero lub więcej wystąpień dowolnych znaków innych niż cudzysłów lub apostrof do przechwytywania grupy o nazwie `1`.</span><span class="sxs-lookup"><span data-stu-id="ebb86-122">Assign zero or more occurrences of any character other than a quotation mark or apostrophe to the capturing group named `1`.</span></span>|  
|`"(?<1>\S+)`|<span data-ttu-id="ebb86-123">Przypisz co najmniej jeden z systemem innym niż biały znak do przechwytywania grupy o nazwie `1`.</span><span class="sxs-lookup"><span data-stu-id="ebb86-123">Assign one or more non-white-space characters to the capturing group named `1`.</span></span>|  
  
## <a name="match-result-class"></a><span data-ttu-id="ebb86-124">Dopasuj wynik klasy</span><span class="sxs-lookup"><span data-stu-id="ebb86-124">Match Result Class</span></span>  
 <span data-ttu-id="ebb86-125">Wyniki wyszukiwania są przechowywane w <xref:System.Text.RegularExpressions.Match> klasy, która zapewnia dostęp do wszystkich podciągów wyodrębnione podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ebb86-125">The results of a search are stored in the <xref:System.Text.RegularExpressions.Match> class, which provides access to all the substrings extracted by the search.</span></span> <span data-ttu-id="ebb86-126">On również pamięta przeszukiwany ciąg i wyrażenie regularne używane, dlatego może wywołać <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodę w celu których ostatnio zakończone innego początkowy wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ebb86-126">It also remembers the string being searched and the regular expression being used, so it can call the <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> method to perform another search starting where the last one ended.</span></span>  
  
## <a name="explicitly-named-captures"></a><span data-ttu-id="ebb86-127">Przechwytuje wyraźnie nazwane</span><span class="sxs-lookup"><span data-stu-id="ebb86-127">Explicitly Named Captures</span></span>  
 <span data-ttu-id="ebb86-128">W tradycyjnym wyrażeń regularnych nawiasów przechwytywania automatycznie numerowane kolejno.</span><span class="sxs-lookup"><span data-stu-id="ebb86-128">In traditional regular expressions, capturing parentheses are automatically numbered sequentially.</span></span> <span data-ttu-id="ebb86-129">Prowadzi to do dwóch problemów.</span><span class="sxs-lookup"><span data-stu-id="ebb86-129">This leads to two problems.</span></span> <span data-ttu-id="ebb86-130">Najpierw Jeśli wyrażenie regularne jest modyfikowany przez wstawiania lub usuwania zestawu nawiasów, żadnego kodu, który odwołuje się do przechwytywania numerowane należy ponownie zapisać celu odzwierciedlenia nowych numerów.</span><span class="sxs-lookup"><span data-stu-id="ebb86-130">First, if a regular expression is modified by inserting or removing a set of parentheses, all code that refers to the numbered captures must be rewritten to reflect the new numbering.</span></span> <span data-ttu-id="ebb86-131">Po drugie ponieważ często różne zestawy nawiasów służą do zapewniania dwóch wyrażeń alternatywne dopasowania dopuszczalne, może być trudne do ustalenia, które z dwóch wyrażeń faktycznie zwrócił wynik.</span><span class="sxs-lookup"><span data-stu-id="ebb86-131">Second, because different sets of parentheses often are used to provide two alternative expressions for an acceptable match, it might be difficult to determine which of the two expressions actually returned a result.</span></span>  
  
 <span data-ttu-id="ebb86-132">Aby rozwiązać te problemy, <xref:System.Text.RegularExpressions.Regex> klasa obsługuje składnię `(?<name>…)` przechwytywania dopasowania do określonego miejsca (gniazdo może nosić przy użyciu ciąg lub liczba całkowita; liczby całkowite można odwołać szybciej).</span><span class="sxs-lookup"><span data-stu-id="ebb86-132">To address these problems, the <xref:System.Text.RegularExpressions.Regex> class supports the syntax `(?<name>…)` for capturing a match into a specified slot (the slot can be named using a string or an integer; integers can be recalled more quickly).</span></span> <span data-ttu-id="ebb86-133">W związku z tym alternatywne dopasowania dla tych samych parametrach, którego wszystkie może zostać skierowany do tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="ebb86-133">Thus, alternative matches for the same string all can be directed to the same place.</span></span> <span data-ttu-id="ebb86-134">W przypadku konfliktu ostatni dopasowania upuścić na gnieździe jest pomyślne dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="ebb86-134">In case of a conflict, the last match dropped into a slot is the successful match.</span></span> <span data-ttu-id="ebb86-135">(Jednak pełną listę wiele elementów zgodnych z jednego miejsca jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="ebb86-135">(However, a complete list of multiple matches for a single slot is available.</span></span> <span data-ttu-id="ebb86-136">Zobacz <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekcji, aby uzyskać więcej informacji.)</span><span class="sxs-lookup"><span data-stu-id="ebb86-136">See the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection for details.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb86-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebb86-137">See Also</span></span>  
 [<span data-ttu-id="ebb86-138">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="ebb86-138">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
