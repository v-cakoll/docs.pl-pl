---
title: "Porady: sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy"
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
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, e-mail strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- e-mail [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
caps.latest.revision: "30"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03623cc4086981dc321aafe3020dcd571b74d9bc
ms.sourcegitcommit: 9c4b8d457ffb8d134c9d55c6d7682a0f22e2b9a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/20/2017
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="245f6-102">Porady: sprawdzanie, czy format poczty e-mail ciągów jest prawidłowy</span><span class="sxs-lookup"><span data-stu-id="245f6-102">How to: Verify that Strings Are in Valid Email Format</span></span>
<span data-ttu-id="245f6-103">W poniższym przykładzie użyto wyrażenia regularnego, aby sprawdzić, czy ciąg w formacie prawidłowy adres e-mail.</span><span class="sxs-lookup"><span data-stu-id="245f6-103">The following example uses a regular expression to verify that a string is in valid email format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="245f6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="245f6-104">Example</span></span>  
 <span data-ttu-id="245f6-105">W przykładzie zdefiniowano `IsValidEmail` metody, która zwraca `true` Jeśli ciąg zawiera prawidłowy adres e-mail i `false` Jeśli nie, ale nie podejmuje żadnych innych akcji.</span><span class="sxs-lookup"><span data-stu-id="245f6-105">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it does not, but takes no other action.</span></span>  
  
 <span data-ttu-id="245f6-106">Aby sprawdzić, czy adres e-mail jest prawidłowa, `IsValidEmail` wywołania metody <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> metody z `(@)(.+)$` wzorzec wyrażenia regularnego do Rozdziel nazwy domeny adresu e-mail.</span><span class="sxs-lookup"><span data-stu-id="245f6-106">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="245f6-107">Trzeci parametr jest <xref:System.Text.RegularExpressions.MatchEvaluator> delegata, który reprezentuje metodę, która przetwarza i zastępuje dopasowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="245f6-107">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="245f6-108">Wzorzec wyrażenia regularnego jest interpretowana w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="245f6-108">The regular expression pattern is interpreted as follows.</span></span>  
  
|<span data-ttu-id="245f6-109">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="245f6-109">Pattern</span></span>|<span data-ttu-id="245f6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="245f6-110">Description</span></span>|  
|-------------|-----------------|  
|`(@)`|<span data-ttu-id="245f6-111">Dopasowanie znaku @.</span><span class="sxs-lookup"><span data-stu-id="245f6-111">Match the @ character.</span></span> <span data-ttu-id="245f6-112">Jest to pierwsza grupa przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="245f6-112">This is the first capturing group.</span></span>|  
|`(.+)`|<span data-ttu-id="245f6-113">Odpowiada jedno lub więcej wystąpień dowolnego znaku.</span><span class="sxs-lookup"><span data-stu-id="245f6-113">Match one or more occurrences of any character.</span></span> <span data-ttu-id="245f6-114">Jest to druga grupa przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="245f6-114">This is the second capturing group.</span></span>|  
|`$`|<span data-ttu-id="245f6-115">Zakończenie dopasowuje koniec ciągu.</span><span class="sxs-lookup"><span data-stu-id="245f6-115">End the match at the end of the string.</span></span>|  
  
 <span data-ttu-id="245f6-116">Nazwa domeny wraz z programem znaku @ jest przekazywana do `DomainMapper` metodę, która używa <xref:System.Globalization.IdnMapping> klasy tłumaczenie znaków Unicode, które są poza zakresem znak US-ASCII na ciąg Punycode.</span><span class="sxs-lookup"><span data-stu-id="245f6-116">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="245f6-117">Ustawia również metoda `invalid` flaga `True` Jeśli <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> metody wykrywa nieprawidłowych znaków w nazwie domeny.</span><span class="sxs-lookup"><span data-stu-id="245f6-117">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="245f6-118">Metoda zwraca poprzedzona nazwą domeny Punycode @ symbol `IsValidEmail` metody.</span><span class="sxs-lookup"><span data-stu-id="245f6-118">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>  
  
 <span data-ttu-id="245f6-119">`IsValidEmail` Metoda wywołuje <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodę, aby zweryfikować, że adres jest zgodny ze wzorcem wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="245f6-119">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>  
  
 <span data-ttu-id="245f6-120">Należy pamiętać, że `IsValidEmail` — metoda nie przeprowadza uwierzytelniania Sprawdź poprawność adresu e-mail.</span><span class="sxs-lookup"><span data-stu-id="245f6-120">Note that the `IsValidEmail` method does not perform authentication to validate the email address.</span></span> <span data-ttu-id="245f6-121">Określa jedynie, czy jego format jest nieprawidłowy dla adresu e-mail.</span><span class="sxs-lookup"><span data-stu-id="245f6-121">It merely determines whether its format is valid for an email address.</span></span> <span data-ttu-id="245f6-122">Ponadto `IsValidEmail` — metoda sprawdza, czy nazwa domeny najwyższego poziomu nie jest prawidłową nazwę domeny wymienione na [bazy danych przez organizację IANA katalogu głównego strefy](https://www.iana.org/domains/root/db), które wymagałyby operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="245f6-122">In addition, the `IsValidEmail` method does not verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span> <span data-ttu-id="245f6-123">Zamiast tego wyrażenia regularnego jedynie sprawdza, czy nazwa domeny najwyższego poziomu składa się z od dwóch do 24 znaków ASCII, znaki alfanumeryczne imię i nazwisko i pozostałe znaki alfanumeryczne lub a łącznikiem (-).</span><span class="sxs-lookup"><span data-stu-id="245f6-123">Instead, the regular expression merely verifies that the top-level domain name consists of between two and twenty-four ASCII characters, with alphanumeric first and last characters and the remaining characters being either alphanumeric or a hyphen (-).</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 <span data-ttu-id="245f6-124">W tym przykładzie wzorzec wyrażenia regularnego ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`\` jest interpretowany, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="245f6-124">In this example, the regular expression pattern ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`\` is interpreted as shown in the following table.</span></span> <span data-ttu-id="245f6-125">Należy pamiętać, że wyrażenie regularne jest skompilowana przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flagi.</span><span class="sxs-lookup"><span data-stu-id="245f6-125">Note that the regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>  
  
|<span data-ttu-id="245f6-126">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="245f6-126">Pattern</span></span>|<span data-ttu-id="245f6-127">Opis</span><span class="sxs-lookup"><span data-stu-id="245f6-127">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="245f6-128">Rozpocznij dopasowania na początku ciąg.</span><span class="sxs-lookup"><span data-stu-id="245f6-128">Begin the match at the start of the string.</span></span>|  
|`(?(")`|<span data-ttu-id="245f6-129">Ustal, czy pierwszy znak jest znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="245f6-129">Determine whether the first character is a quotation mark.</span></span> <span data-ttu-id="245f6-130">`(?(")`jest początek konstrukcji wyrażenia warunkowe.</span><span class="sxs-lookup"><span data-stu-id="245f6-130">`(?(")` is the beginning of an alternation construct.</span></span>|  
|`(?("")("".+?(?<!\\)""@)`|<span data-ttu-id="245f6-131">Jeśli pierwszym znakiem jest znak cudzysłowu, zgodne cudzysłów początku następuje co najmniej jedno wystąpienie dowolny znak, następuje końcowy znak cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="245f6-131">If the first character is a quotation mark, match a beginning quotation mark followed by at least one occurrence of any character, followed by an ending quotation mark.</span></span> <span data-ttu-id="245f6-132">Końcowy znak cudzysłowu nie musi być poprzedzona znakiem ukośnika odwrotnego (\\).</span><span class="sxs-lookup"><span data-stu-id="245f6-132">The ending quotation mark must not be preceded by a backslash character (\\).</span></span> <span data-ttu-id="245f6-133">`(?<!`jest na początku potwierdzenia ujemne wybieganie wstecz zerowej szerokości.</span><span class="sxs-lookup"><span data-stu-id="245f6-133">`(?<!` is the beginning of a zero-width negative lookbehind assertion.</span></span> <span data-ttu-id="245f6-134">Ciąg powinien zawierać z znak @ (@).</span><span class="sxs-lookup"><span data-stu-id="245f6-134">The string should conclude with an at sign (@).</span></span>|  
|`&#124;(([0-9a-z]`|<span data-ttu-id="245f6-135">Jeśli pierwszy znak nie jest znak cudzysłowu, dopasowuje dowolny znak alfabetyczne, od do z i od A do Z (porównanie nie uwzględnia wielkości liter) lub dowolnego znaku numerycznego od 0 do 9.</span><span class="sxs-lookup"><span data-stu-id="245f6-135">If the first character is not a quotation mark, match any alphabetic character from a to z or A to Z (the comparison is case insensitive), or any numeric character from 0 to 9.</span></span>|  
|`(\.(?!\.))`|<span data-ttu-id="245f6-136">Jeśli następny znak jest okres, jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="245f6-136">If the next character is a period, match it.</span></span> <span data-ttu-id="245f6-137">Jeśli nie jest to okres, wyszukiwać na następny znak i kontynuować dopasowania.</span><span class="sxs-lookup"><span data-stu-id="245f6-137">If it is not a period, look ahead to the next character and continue the match.</span></span> <span data-ttu-id="245f6-138">`(?!\.)`to potwierdzenie wyprzedzenia ujemna zerowej szerokości, uniemożliwiający dwóch następujących po sobie kropek znajdujących się w lokalnym części adresu e-mail.</span><span class="sxs-lookup"><span data-stu-id="245f6-138">`(?!\.)` is a zero-width negative lookahead assertion that prevents two consecutive periods from appearing in the local part of an email address.</span></span>|  
|``&#124;[-!#\$%&'\*\+/=\?\^`{}\&#124;~\w]``|<span data-ttu-id="245f6-139">Jeśli następny znak nie jest okres, zgodne dowolny znak słowa lub jeden z następujących znaków:-! #$%'*+=?^'{} &#124; ~.</span><span class="sxs-lookup"><span data-stu-id="245f6-139">If the next character is not a period, match any word character or one of the following characters: -!#$%'*+=?^\`{}&#124;~.</span></span>|  
|``((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^`{}\&#124;~\w])*``|<span data-ttu-id="245f6-140">Jest zgodna z wzorcem wyrażenia warunkowe (okres następuje z systemem innym niż okres lub jeden z wielu znaków) zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="245f6-140">Match the alternation pattern (a period followed by a non-period, or one of a number of characters) zero or more times.</span></span>|  
|`@`|<span data-ttu-id="245f6-141">Dopasowanie znaku @.</span><span class="sxs-lookup"><span data-stu-id="245f6-141">Match the @ character.</span></span>|  
|`(?<=[0-9a-z])`|<span data-ttu-id="245f6-142">Kontynuować dopasowania, jeśli znak poprzedza znaku @ jest od A do Z, do z i od 0 do 9.</span><span class="sxs-lookup"><span data-stu-id="245f6-142">Continue the match if the character that precedes the @ character is A through Z, a through z, or 0 through 9.</span></span> <span data-ttu-id="245f6-143">`(?<=[0-9a-z])` Konstrukcja definiuje potwierdzenia dodatnie wybieganie wstecz zerowej szerokości.</span><span class="sxs-lookup"><span data-stu-id="245f6-143">The `(?<=[0-9a-z])` construct defines a zero-width positive lookbehind assertion.</span></span>|  
|`(?(\[)`|<span data-ttu-id="245f6-144">Sprawdź, czy znak znajdujący się @ nawiasem otwierającym.</span><span class="sxs-lookup"><span data-stu-id="245f6-144">Check whether the character that follows @ is an opening bracket.</span></span>|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|<span data-ttu-id="245f6-145">Jeśli jest otwierający nawias kwadratowy, odpowiadać następuje adres IP (cztery zestawy jednej do trzech cyfr, z każdego zestawu oddzielona kropką) i zamykający nawias kwadratowy otwierający nawias kwadratowy.</span><span class="sxs-lookup"><span data-stu-id="245f6-145">If it is an opening bracket, match the opening bracket followed by an IP address (four sets of one to three digits, with each set separated by a period) and a closing bracket.</span></span>|  
|`&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`|<span data-ttu-id="245f6-146">Jeśli znak znajdujący się @ nie jest otwierający nawias kwadratowy, jeden znak alfanumeryczny dopasowanie z wartością A-Z, a-z lub 0-9, a następnie zero lub więcej wystąpień łącznik, a następnie zero lub jeden znak alfanumeryczny o wartości A-Z, a-z lub 0-9 , a następnie kropki.</span><span class="sxs-lookup"><span data-stu-id="245f6-146">If the character that follows @ is not an opening bracket, match one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by zero or more occurrences of a hyphen, followed by zero or one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by a period.</span></span> <span data-ttu-id="245f6-147">Ten wzorzec można powtarzać jeden lub więcej razy, a musi następować nazwa domeny najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="245f6-147">This pattern can be repeated one or more times, and must be followed by the top-level domain name.</span></span>|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|<span data-ttu-id="245f6-148">Nazwa domeny najwyższego poziomu musi rozpoczynać i kończyć się znakiem alfanumerycznym (a – z, A-Z i 0 – 9).</span><span class="sxs-lookup"><span data-stu-id="245f6-148">The top-level domain name must begin and end with an alphanumeric character (a-z, A-Z, and 0-9).</span></span> <span data-ttu-id="245f6-149">Mogą również obejmować od 0 do 22 znaki ASCII, które są alfanumeryczne i łączniki.</span><span class="sxs-lookup"><span data-stu-id="245f6-149">It can also include from zero to 22 ASCII characters that are either alphanumeric or hyphens.</span></span>|  
|`$`|<span data-ttu-id="245f6-150">Zakończenie dopasowuje koniec ciągu.</span><span class="sxs-lookup"><span data-stu-id="245f6-150">End the match at the end of the string.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="245f6-151">Zamiast przy użyciu wyrażenia regularnego, aby zweryfikować adres e-mail, możesz użyć <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="245f6-151">Instead of using a regular expression to validate an email address, you can use the <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="245f6-152">Aby ustalić, czy adres e-mail jest nieprawidłowy, należy przekazać adres e-mail, aby <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="245f6-152">To determine whether an email address is valid, pass the email address to the <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType> class constructor.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="245f6-153">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="245f6-153">Compiling the Code</span></span>  
 <span data-ttu-id="245f6-154">`IsValidEmail` i `DomainMapper` metody mogą być zawarte w bibliotece metody narzędziowe wyrażenie regularne lub jako prywatny statyczny lub wystąpienie metody w klasie aplikacji mogą być uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="245f6-154">The `IsValidEmail` and `DomainMapper` methods can be included in a library of regular expression utility methods, or they can be included as private static or instance methods in the application class.</span></span>  
  
 <span data-ttu-id="245f6-155">Aby uwzględnić je w bibliotece wyrażenie regularne, albo i Wklej kod do projektu biblioteki klas w usłudze Visual Studio, lub skopiować i wkleić go do pliku tekstowego i skompiluj go z poziomu wiersza polecenia przy użyciu polecenia w następujący (przy założeniu, że nazwa kodu źródłowego  plik jest RegexUtilities.cs lub RegexUtilities.vb:</span><span class="sxs-lookup"><span data-stu-id="245f6-155">To include them in a regular expression library, either copy and paste the code into a Visual Studio Class Library project, or copy and paste it into a text file and compile it from the command line with a command like the following (assuming that the name of the source code file is RegexUtilities.cs or RegexUtilities.vb:</span></span>  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 <span data-ttu-id="245f6-156">Można również użyć <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metodę w celu uwzględnienia tej wyrażenie regularne w bibliotece wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="245f6-156">You can also use the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> method to include this regular expression in a regular expression library.</span></span>  
  
 <span data-ttu-id="245f6-157">Jeśli są używane w bibliotece wyrażenie regularne, należy wywołać je przy użyciu kodu, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="245f6-157">If they are used in a regular expression library, you can call them by using code such as the following:</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 <span data-ttu-id="245f6-158">Zakładając, że po utworzeniu biblioteki klas o nazwie RegexUtilities.dll zawierający wyrażenia regularnego sprawdzania poprawności poczty e-mail, będzie można kompilować w tym przykładzie w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="245f6-158">Assuming you've created a class library named RegexUtilities.dll that includes your email validation regular expression, you can compile this example in either of the following ways:</span></span>  
  
-   <span data-ttu-id="245f6-159">W programie Visual Studio, tworzenie aplikacji konsoli i dodać odwołanie do RegexUtilities.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="245f6-159">In Visual Studio, by creating a Console Application and adding a reference to RegexUtilities.dll to your project.</span></span>  
  
-   <span data-ttu-id="245f6-160">W wierszu polecenia, kopiowanie i wklejanie kodu źródłowego w pliku tekstowym i kompilowania go za pomocą polecenia podobnie do następującej (przy założeniu, że nazwa pliku źródła kodu jest Example.cs lub Example.vb:</span><span class="sxs-lookup"><span data-stu-id="245f6-160">From the command line, by copying and pasting the source code into a text file and compiling it with a command like the following (assuming that the name of the source code file is Example.cs or Example.vb:</span></span>  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="245f6-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="245f6-161">See Also</span></span>  
 [<span data-ttu-id="245f6-162">.NET framework — nieprawidłowe wyrażenia</span><span class="sxs-lookup"><span data-stu-id="245f6-162">.NET Framework Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
