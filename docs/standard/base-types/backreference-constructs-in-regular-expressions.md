---
title: "Konstrukcje dopasowań w wyrażeniach regularnych"
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
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ec92933bdf123412a3d489fc493d76c4a0dc0d0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a><span data-ttu-id="3ac97-102">Konstrukcje dopasowań w wyrażeniach regularnych</span><span class="sxs-lookup"><span data-stu-id="3ac97-102">Backreference Constructs in Regular Expressions</span></span>
<span data-ttu-id="3ac97-103">Odwołania wstecznego zapewnić wygodny sposób identyfikowania powtarzających się znaków lub podciąg ciągu.</span><span class="sxs-lookup"><span data-stu-id="3ac97-103">Backreferences provide a convenient way to identify a repeated character or substring within a string.</span></span> <span data-ttu-id="3ac97-104">Na przykład jeśli ciąg wejściowy zawiera wiele wystąpień dowolnego podciąg, można odpowiada pierwszego wystąpienia z grupą przechwytywanie, a następnie użyć dopasuje odpowiadające kolejne wystąpienia podciąg.</span><span class="sxs-lookup"><span data-stu-id="3ac97-104">For example, if the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ac97-105">Oddzielne składni jest użyta w odwołaniu do nazwane i numerem grupy w ciągów zamiennych przechwycone.</span><span class="sxs-lookup"><span data-stu-id="3ac97-105">A separate syntax is used to refer to named and numbered capturing groups in replacement strings.</span></span> <span data-ttu-id="3ac97-106">Aby uzyskać więcej informacji, zobacz [podstawienia](substitutions-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3ac97-106">For more information, see [Substitutions](substitutions-in-regular-expressions.md).</span></span>  
  
 <span data-ttu-id="3ac97-107">.NET definiuje elementy oddzielne języka Aby odwołać się do grup przechwytywania numerowane i nazwane.</span><span class="sxs-lookup"><span data-stu-id="3ac97-107">.NET defines separate language elements to refer to numbered and named capturing groups.</span></span> <span data-ttu-id="3ac97-108">Aby uzyskać więcej informacji na temat grup przechwytywania, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3ac97-108">For more information about capturing groups, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).</span></span>  
  
## <a name="numbered-backreferences"></a><span data-ttu-id="3ac97-109">Numerowane odwołania wstecznego</span><span class="sxs-lookup"><span data-stu-id="3ac97-109">Numbered Backreferences</span></span>  
 <span data-ttu-id="3ac97-110">Numerowane dopasuje używa następującej składni:</span><span class="sxs-lookup"><span data-stu-id="3ac97-110">A numbered backreference uses the following syntax:</span></span>  
  
 <span data-ttu-id="3ac97-111">`\`*numer*</span><span class="sxs-lookup"><span data-stu-id="3ac97-111">`\` *number*</span></span>  
  
 <span data-ttu-id="3ac97-112">gdzie *numer* jest numerem porządkowym przechwytywania grupy w wyrażeniu regularnym.</span><span class="sxs-lookup"><span data-stu-id="3ac97-112">where *number* is the ordinal position of the capturing group in the regular expression.</span></span> <span data-ttu-id="3ac97-113">Na przykład `\4` odpowiada zawartość czwarty grupy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3ac97-113">For example, `\4` matches the contents of the fourth capturing group.</span></span> <span data-ttu-id="3ac97-114">Jeśli *numer* nie jest zdefiniowany w wzorzec wyrażenia regularnego, występuje błąd analizy i zgłasza wyjątek, aparat wyrażeń regularnych <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="3ac97-114">If *number* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="3ac97-115">Na przykład, wyrażenie regularne `\b(\w+)\s\1` jest nieprawidłowe, ponieważ `(\w+)` jest pierwszy i tylko Przechwytywanie grupy w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="3ac97-115">For example, the regular expression `\b(\w+)\s\1` is valid, because `(\w+)` is the first and only capturing group in the expression.</span></span> <span data-ttu-id="3ac97-116">Z drugiej strony `\b(\w+)\s\2` jest nieprawidłowy i zgłasza wyjątek argumentu, ponieważ nie istnieje żadna grupa przechwytywania numerowane `\2`.</span><span class="sxs-lookup"><span data-stu-id="3ac97-116">On the other hand, `\b(\w+)\s\2` is invalid and throws an argument exception, because there is no capturing group numbered `\2`.</span></span>  
  
 <span data-ttu-id="3ac97-117">Należy zwrócić uwagę niejednoznaczności między kody ósemkowe ESC (takich jak `\16`) i `\` *numer* odwołania wstecznego, które używają tego samego notacji.</span><span class="sxs-lookup"><span data-stu-id="3ac97-117">Note the ambiguity between octal escape codes (such as `\16`) and `\`*number* backreferences that use the same notation.</span></span> <span data-ttu-id="3ac97-118">Tę niejednoznaczność zostanie rozwiązany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3ac97-118">This ambiguity is resolved as follows:</span></span>  
  
-   <span data-ttu-id="3ac97-119">Wyrażenia `\1` za pośrednictwem `\9` zawsze będą interpretowane jako odwołania wstecznego, a nie jako ósemkowe kodów.</span><span class="sxs-lookup"><span data-stu-id="3ac97-119">The expressions `\1` through `\9` are always interpreted as backreferences, and not as octal codes.</span></span>  
  
-   <span data-ttu-id="3ac97-120">Jeśli cyfry multidigit wyrażenia jest 8, 9 (takich jak `\80` lub `\91`), wyrażenia, jak jest interpretowana jako literału.</span><span class="sxs-lookup"><span data-stu-id="3ac97-120">If the first digit of a multidigit expression is 8 or 9 (such as `\80` or `\91`), the expression as interpreted as a literal.</span></span>  
  
-   <span data-ttu-id="3ac97-121">Wyrażenia z `\10` i większa są traktowane jako odwołania wstecznego przypadku braku dopasowań, odpowiadającego do to numer, a w przeciwnym, są traktowane jako ósemkowe kodów.</span><span class="sxs-lookup"><span data-stu-id="3ac97-121">Expressions from `\10` and greater are considered backreferences if there is a backreference corresponding to that number; otherwise, they are interpreted as octal codes.</span></span>  
  
-   <span data-ttu-id="3ac97-122">Jeśli wyrażenie regularne zawiera dopasuje do niezdefiniowanego numeru grupy, występuje błąd analizy i zgłasza wyjątek, aparat wyrażeń regularnych <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="3ac97-122">If a regular expression contains a backreference to an undefined group number, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="3ac97-123">Jeśli niejednoznaczności problem, można użyć `\k<` *nazwa* `>` zapisu, który jest jednoznaczne i nie należy mylić jej z kodów ósemkowe znaków.</span><span class="sxs-lookup"><span data-stu-id="3ac97-123">If the ambiguity is a problem, you can use the `\k<`*name*`>` notation, which is unambiguous and cannot be confused with octal character codes.</span></span> <span data-ttu-id="3ac97-124">Podobnie, takich jak liczba szesnastkowa kodów `\xdd` są jednoznaczne i nie należy mylić jej z odwołania wstecznego.</span><span class="sxs-lookup"><span data-stu-id="3ac97-124">Similarly, hexadecimal codes such as `\xdd` are unambiguous and cannot be confused with backreferences.</span></span>  
  
 <span data-ttu-id="3ac97-125">Poniższy przykład umożliwia znalezienie podwójna word znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="3ac97-125">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="3ac97-126">Definiuje wyrażenie regularne `(\w)\1`, który składa się z następujących elementów.</span><span class="sxs-lookup"><span data-stu-id="3ac97-126">It defines a regular expression, `(\w)\1`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="3ac97-127">Element</span><span class="sxs-lookup"><span data-stu-id="3ac97-127">Element</span></span>|<span data-ttu-id="3ac97-128">Opis</span><span class="sxs-lookup"><span data-stu-id="3ac97-128">Description</span></span>|  
|-------------|-----------------|  
|`(\w)`|<span data-ttu-id="3ac97-129">Dopasowuje znak słowa i przypisz je do pierwszej grupy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3ac97-129">Match a word character and assign it to the first capturing group.</span></span>|  
|`\1`|<span data-ttu-id="3ac97-130">Zgodne następny znak, który jest taka sama jak wartość w pierwszej grupy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3ac97-130">Match the next character that is the same as the value of the first capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a><span data-ttu-id="3ac97-131">Nazwane odwołania wstecznego</span><span class="sxs-lookup"><span data-stu-id="3ac97-131">Named Backreferences</span></span>  
 <span data-ttu-id="3ac97-132">Nazwane dopasuje jest definiowana za pomocą następującej składni:</span><span class="sxs-lookup"><span data-stu-id="3ac97-132">A named backreference is defined by using the following syntax:</span></span>  
  
 <span data-ttu-id="3ac97-133">`\k<`*nazwa*`>`</span><span class="sxs-lookup"><span data-stu-id="3ac97-133">`\k<` *name* `>`</span></span>  
  
 <span data-ttu-id="3ac97-134">lub:</span><span class="sxs-lookup"><span data-stu-id="3ac97-134">or:</span></span>  
  
 <span data-ttu-id="3ac97-135">`\k'`*nazwa*`'`</span><span class="sxs-lookup"><span data-stu-id="3ac97-135">`\k'` *name* `'`</span></span>  
  
 <span data-ttu-id="3ac97-136">gdzie *nazwa* to nazwa grupy przechwytywania zdefiniowanej w wzorzec wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="3ac97-136">where *name* is the name of a capturing group defined in the regular expression pattern.</span></span> <span data-ttu-id="3ac97-137">Jeśli *nazwa* nie jest zdefiniowany w wzorzec wyrażenia regularnego, występuje błąd analizy i zgłasza wyjątek, aparat wyrażeń regularnych <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="3ac97-137">If *name* is not defined in the regular expression pattern, a parsing error occurs, and the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="3ac97-138">Poniższy przykład umożliwia znalezienie podwójna word znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="3ac97-138">The following example finds doubled word characters in a string.</span></span> <span data-ttu-id="3ac97-139">Definiuje wyrażenie regularne `(?<char>\w)\k<char>`, który składa się z następujących elementów.</span><span class="sxs-lookup"><span data-stu-id="3ac97-139">It defines a regular expression, `(?<char>\w)\k<char>`, which consists of the following elements.</span></span>  
  
|<span data-ttu-id="3ac97-140">Element</span><span class="sxs-lookup"><span data-stu-id="3ac97-140">Element</span></span>|<span data-ttu-id="3ac97-141">Opis</span><span class="sxs-lookup"><span data-stu-id="3ac97-141">Description</span></span>|  
|-------------|-----------------|  
|`(?<char>\w)`|<span data-ttu-id="3ac97-142">Dopasowuje znak słowa i przypisz je do przechwytywania grupę o nazwie `char`.</span><span class="sxs-lookup"><span data-stu-id="3ac97-142">Match a word character and assign it to a capturing group named `char`.</span></span>|  
|`\k<char>`|<span data-ttu-id="3ac97-143">Następny znak, który jest taka sama jak wartość odpowiada `char` Przechwytywanie grupy.</span><span class="sxs-lookup"><span data-stu-id="3ac97-143">Match the next character that is the same as the value of the `char` capturing group.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 <span data-ttu-id="3ac97-144">Należy pamiętać, że *nazwa* można także reprezentację liczby.</span><span class="sxs-lookup"><span data-stu-id="3ac97-144">Note that *name* can also be the string representation of a number.</span></span> <span data-ttu-id="3ac97-145">Na przykład w poniższym przykładzie użyto wyrażenia regularnego `(?<2>\w)\k<2>` można znaleźć w ciągu znaków podwójna słów.</span><span class="sxs-lookup"><span data-stu-id="3ac97-145">For example, the following example uses the regular expression `(?<2>\w)\k<2>` to find doubled word characters in a string.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## <a name="what-backreferences-match"></a><span data-ttu-id="3ac97-146">Jakie dopasowania odwołania wstecznego</span><span class="sxs-lookup"><span data-stu-id="3ac97-146">What Backreferences Match</span></span>  
 <span data-ttu-id="3ac97-147">Dopasuje odwołuje się do najnowszych definicji grupy (definicja najbardziej bezpośrednio po lewej, podczas dopasowywania od lewej do prawej).</span><span class="sxs-lookup"><span data-stu-id="3ac97-147">A backreference refers to the most recent definition of a group (the definition most immediately to the left, when matching left to right).</span></span> <span data-ttu-id="3ac97-148">Gdy ułatwia grupy, który przechwytuje wielu, dopasuje odwołuje się do najnowszych przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3ac97-148">When a group makes multiple captures, a backreference refers to the most recent capture.</span></span>  
  
 <span data-ttu-id="3ac97-149">Poniższy przykład zawiera wzorzec wyrażenia regularnego, `(?<1>a)(?<1>\1b)*`, które ponownie definiuje \1 o nazwie grupy.</span><span class="sxs-lookup"><span data-stu-id="3ac97-149">The following example includes a regular expression pattern, `(?<1>a)(?<1>\1b)*`, which redefines the \1 named group.</span></span> <span data-ttu-id="3ac97-150">W poniższej tabeli opisano każdy wzorzec wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="3ac97-150">The following table describes each pattern in the regular expression.</span></span>  
  
|<span data-ttu-id="3ac97-151">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="3ac97-151">Pattern</span></span>|<span data-ttu-id="3ac97-152">Opis</span><span class="sxs-lookup"><span data-stu-id="3ac97-152">Description</span></span>|  
|-------------|-----------------|  
|`(?<1>a)`|<span data-ttu-id="3ac97-153">Dopasowanie znaku "a" i przypisz wynik do przechwytywania grupy o nazwie `1`.</span><span class="sxs-lookup"><span data-stu-id="3ac97-153">Match the character "a" and assign the result to the capturing group named `1`.</span></span>|  
|`(?<1>\1b)*`|<span data-ttu-id="3ac97-154">Wystąpienie dopasowania 0 lub 1 grupę o nazwie `1` wraz z "b" i przypisz wynik do przechwytywania grupy o nazwie `1`.</span><span class="sxs-lookup"><span data-stu-id="3ac97-154">Match 0 or 1 occurrence of the group named `1` along with a "b", and assign the result to the capturing group named `1`.</span></span>|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 <span data-ttu-id="3ac97-155">W porównaniu z wyrażeniem regularnym z ciągu wejściowego ("aababb"), aparat wyrażeń regularnych wykonuje następujące operacje:</span><span class="sxs-lookup"><span data-stu-id="3ac97-155">In comparing the regular expression with the input string ("aababb"), the regular expression engine performs the following operations:</span></span>  
  
1.  <span data-ttu-id="3ac97-156">Rozpoczyna się od początku ciągu i pomyślnie zgodny "a" na wyrażenie `(?<1>a)`.</span><span class="sxs-lookup"><span data-stu-id="3ac97-156">It starts at the beginning of the string, and successfully matches "a" with the expression `(?<1>a)`.</span></span> <span data-ttu-id="3ac97-157">Wartość `1` grupy jest teraz "".</span><span class="sxs-lookup"><span data-stu-id="3ac97-157">The value of the `1` group is now "a".</span></span>  
  
2.  <span data-ttu-id="3ac97-158">Przechodzi do drugiego znaku i pomyślnie pasującej do ciągu "ab" za pomocą wyrażenia `\1b`, lub "ab".</span><span class="sxs-lookup"><span data-stu-id="3ac97-158">It advances to the second character, and successfully matches the string "ab" with the expression `\1b`, or "ab".</span></span> <span data-ttu-id="3ac97-159">Następnie przypisuje wynik "ab", aby `\1`.</span><span class="sxs-lookup"><span data-stu-id="3ac97-159">It then assigns the result, "ab" to `\1`.</span></span>  
  
3.  <span data-ttu-id="3ac97-160">Zmienia jego czwarty znak.</span><span class="sxs-lookup"><span data-stu-id="3ac97-160">It advances to the fourth character.</span></span> <span data-ttu-id="3ac97-161">Wyrażenie `(?<1>\1b)` jest być dopasowane zero lub więcej razy, aby go pomyślnie pasującej do ciągu "abb" za pomocą wyrażenia `\1b`.</span><span class="sxs-lookup"><span data-stu-id="3ac97-161">The expression `(?<1>\1b)` is to be matched zero or more times, so it successfully matches the string "abb" with the expression `\1b`.</span></span> <span data-ttu-id="3ac97-162">Przypisuje wynik "abb", przywracając `\1`.</span><span class="sxs-lookup"><span data-stu-id="3ac97-162">It assigns the result, "abb", back to `\1`.</span></span>  
  
 <span data-ttu-id="3ac97-163">W tym przykładzie `*` jest pętli kwantyfikatora — ocena wielokrotnie aż aparat wyrażeń regularnych nie jest zgodna z wzorcem definiuje.</span><span class="sxs-lookup"><span data-stu-id="3ac97-163">In this example, `*` is a looping quantifier -- it is evaluated repeatedly until the regular expression engine cannot match the pattern it defines.</span></span> <span data-ttu-id="3ac97-164">Kwantyfikatory pętli nie usuwaj definicje grup.</span><span class="sxs-lookup"><span data-stu-id="3ac97-164">Looping quantifiers do not clear group definitions.</span></span>  
  
 <span data-ttu-id="3ac97-165">Jeśli grupa nie ma przechwycone żadnych podciągów, dopasowań dla tej grupy nie jest zdefiniowana i nigdy nie jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="3ac97-165">If a group has not captured any substrings, a backreference to that group is undefined and never matches.</span></span> <span data-ttu-id="3ac97-166">Jest to zilustrowane wzorzec wyrażenia regularnego `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, która jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3ac97-166">This is illustrated by the regular expression pattern `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b`, which is defined as follows:</span></span>  
  
|<span data-ttu-id="3ac97-167">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="3ac97-167">Pattern</span></span>|<span data-ttu-id="3ac97-168">Opis</span><span class="sxs-lookup"><span data-stu-id="3ac97-168">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="3ac97-169">Rozpocznij dopasowania na granicy programu word.</span><span class="sxs-lookup"><span data-stu-id="3ac97-169">Begin the match on a word boundary.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="3ac97-170">Zgodne dwie wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="3ac97-170">Match two uppercase letters.</span></span> <span data-ttu-id="3ac97-171">Jest to pierwsza grupa przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3ac97-171">This is the first capturing group.</span></span>|  
|`(\d{2})?`|<span data-ttu-id="3ac97-172">Zgodne wystąpienie zero lub jeden z dwóch cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="3ac97-172">Match zero or one occurrence of two decimal digits.</span></span> <span data-ttu-id="3ac97-173">Jest to druga grupa przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3ac97-173">This is the second capturing group.</span></span>|  
|`(\p{Lu}{2})`|<span data-ttu-id="3ac97-174">Zgodne dwie wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="3ac97-174">Match two uppercase letters.</span></span> <span data-ttu-id="3ac97-175">Jest to trzecia grupa przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3ac97-175">This is the third capturing group.</span></span>|  
|`\b`|<span data-ttu-id="3ac97-176">W celu dopasowania na granicy programu word.</span><span class="sxs-lookup"><span data-stu-id="3ac97-176">End the match on a word boundary.</span></span>|  
  
 <span data-ttu-id="3ac97-177">Ciąg wejściowy można dopasować tego wyrażenia regularnego, nawet jeśli nie występują dwa cyfr dziesiętnych, które są definiowane przez drugiej grupy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="3ac97-177">An input string can match this regular expression even if the two decimal digits that are defined by the second capturing group are not present.</span></span> <span data-ttu-id="3ac97-178">W poniższym przykładzie pokazano, czy mimo że dopasowanie jest pomyślne, pustej grupy przechwytywania znajduje się między dwie grupy przechwytywania powiodło się.</span><span class="sxs-lookup"><span data-stu-id="3ac97-178">The following example shows that even though the match is successful, an empty capturing group is found between two successful capturing groups.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3ac97-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ac97-179">See Also</span></span>  
 [<span data-ttu-id="3ac97-180">Język wyrażeń regularnych — podręczny wykaz</span><span class="sxs-lookup"><span data-stu-id="3ac97-180">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
