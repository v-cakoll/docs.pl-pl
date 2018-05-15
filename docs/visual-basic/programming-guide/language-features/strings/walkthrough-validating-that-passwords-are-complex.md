---
title: Sprawdzanie poprawności złożoności haseł (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: acfc8ab958c8671ed7f1afd245d24a43ca12be29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="77602-102">Wskazówki: sprawdzanie poprawności złożoności haseł (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77602-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="77602-103">Ta metoda sprawdza, czy niektóre cechy silnego hasła i aktualizuje informacje o tym, które sprawdza hasła nie powiedzie się. parametr typu string.</span><span class="sxs-lookup"><span data-stu-id="77602-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="77602-104">Hasła mogą być wykorzystywane w bezpieczny system do autoryzacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="77602-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="77602-105">Jednak musi być trudne dla nieautoryzowanych użytkowników do odgadnięcia hasła.</span><span class="sxs-lookup"><span data-stu-id="77602-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="77602-106">Osoby atakujące mogą wykorzystać *atak słownikowy* program, który iteruje po wszystkich wyrazów słownika (lub słowniki wielu w różnych językach) i sprawdza, czy dowolne wyrażenie działa jako hasło użytkownika.</span><span class="sxs-lookup"><span data-stu-id="77602-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="77602-107">Słabe hasła, takie jak "Wydarzenia dotyczące Legii" lub "Mustang" można szybko złamać.</span><span class="sxs-lookup"><span data-stu-id="77602-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="77602-108">Silniejszych haseł, takich jak "? Użytkownik "L1N3vaFiNdMeyeP@sSWerd!", jest znacznie mniej prawdopodobne złamać.</span><span class="sxs-lookup"><span data-stu-id="77602-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="77602-109">System chroniony hasłem powinien upewnić się, że użytkownicy wybiorą hasła silne.</span><span class="sxs-lookup"><span data-stu-id="77602-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="77602-110">Silne hasła jest złożony, (zawierających mieszankę wielkie litery, małe litery, liczbowych i specjalne znaków) i nie jest ona słowem.</span><span class="sxs-lookup"><span data-stu-id="77602-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="77602-111">W tym przykładzie przedstawiono sposób weryfikacji złożoności.</span><span class="sxs-lookup"><span data-stu-id="77602-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77602-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="77602-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="77602-113">Kod</span><span class="sxs-lookup"><span data-stu-id="77602-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77602-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="77602-114">Compiling the Code</span></span>  
 <span data-ttu-id="77602-115">Tę metodę można wywołać, przekazując ciąg, który zawiera hasło.</span><span class="sxs-lookup"><span data-stu-id="77602-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="77602-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="77602-116">This example requires:</span></span>  
  
-   <span data-ttu-id="77602-117">Dostęp do elementów członkowskich <xref:System.Text.RegularExpressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="77602-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="77602-118">Dodaj `Imports` instrukcję, jeśli użytkownik jest całkowicie niekwalifikujących nazwy elementów członkowskich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="77602-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="77602-119">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="77602-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="77602-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="77602-120">Security</span></span>  
 <span data-ttu-id="77602-121">Jeśli przenosisz hasła przez sieć, należy użyć bezpieczną metodę transferu danych.</span><span class="sxs-lookup"><span data-stu-id="77602-121">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="77602-122">Aby uzyskać więcej informacji, zobacz [zabezpieczenia aplikacji sieci Web ASP.NET](https://msdn.microsoft.com/library/330a99hc).</span><span class="sxs-lookup"><span data-stu-id="77602-122">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="77602-123">Można zwiększyć dokładność `ValidatePassword` funkcja przez dodanie złożoności dodatkowe kontrole:</span><span class="sxs-lookup"><span data-stu-id="77602-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="77602-124">Porównaj hasło i jego podciągów przed nazwę użytkownika, identyfikator użytkownika i słowniku zdefiniowanym przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="77602-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="77602-125">Ponadto należy traktować wizualnie podobne znaków jako równoważne podczas przeprowadzania porównania.</span><span class="sxs-lookup"><span data-stu-id="77602-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="77602-126">Na przykład traktować litery "l" i "e" jako odpowiednik liczb, "1" i "3".</span><span class="sxs-lookup"><span data-stu-id="77602-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="77602-127">W przypadku tylko jedną wielką literę, upewnij się, że nie jest to pierwszy znak hasła.</span><span class="sxs-lookup"><span data-stu-id="77602-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="77602-128">Upewnij się, że ostatnich dwóch znaków hasła są znaki.</span><span class="sxs-lookup"><span data-stu-id="77602-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="77602-129">Nie zezwalaj hasła, w których wszystkie symbole są wprowadzane z klawiatury w górnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="77602-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77602-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77602-130">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex>  
 [<span data-ttu-id="77602-131">Zabezpieczenia aplikacji sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="77602-131">ASP.NET Web Application Security</span></span>](https://msdn.microsoft.com/library/330a99hc)
