---
title: Sprawdzanie poprawności złożoności haseł (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 829d6485acdca22fbf10160c734e5c7f931dd855
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824939"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="82787-102">Przewodnik: Sprawdzanie poprawności hasła złożoności (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82787-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="82787-103">Ta metoda sprawdza, czy niektóre cechy silnego hasła i aktualizuje jako parametr ciągu przy użyciu informacji o tym, które sprawdza, czy hasła nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="82787-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="82787-104">Hasła mogą być wykorzystywane w bezpieczny system do autoryzacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="82787-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="82787-105">Jednak musi być trudne dla nieautoryzowanych użytkowników w celu odgadnięcia hasła.</span><span class="sxs-lookup"><span data-stu-id="82787-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="82787-106">Osoby atakujące mogą wykorzystać *atak słownikowy* program, który wykonuje iterację przez wszystkie wyrazy w słowniku (lub słowniki wielu w różnych językach) i sprawdza, czy dowolny wyraz działać jako hasło tego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="82787-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="82787-107">Szybko można złamać słabe hasła, takie jak "Yankees" lub "Mustang".</span><span class="sxs-lookup"><span data-stu-id="82787-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="82787-108">Silniejszych haseł, takich jak "? Użytkownik "L1N3vaFiNdMeyeP@sSWerd!", są znacznie mniej prawdopodobne złamać.</span><span class="sxs-lookup"><span data-stu-id="82787-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="82787-109">System chronionych hasłem należy upewnić się, że użytkownicy wybierać silne hasła.</span><span class="sxs-lookup"><span data-stu-id="82787-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="82787-110">Silne hasło jest złożony (zawierającego kombinację wielkie litery, małe litery, cyfry i znaki specjalne) i nie jest wyrazem.</span><span class="sxs-lookup"><span data-stu-id="82787-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="82787-111">W tym przykładzie pokazano, jak sprawdzić, co do złożoności.</span><span class="sxs-lookup"><span data-stu-id="82787-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82787-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="82787-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="82787-113">Kod</span><span class="sxs-lookup"><span data-stu-id="82787-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="82787-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="82787-114">Compiling the Code</span></span>  
 <span data-ttu-id="82787-115">Wywołaj tę metodę, przekazując ciąg, który zawiera to hasło.</span><span class="sxs-lookup"><span data-stu-id="82787-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="82787-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="82787-116">This example requires:</span></span>  
  
-   <span data-ttu-id="82787-117">Dostęp do elementów członkowskich <xref:System.Text.RegularExpressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82787-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="82787-118">Dodaj `Imports` instrukcji, jeśli użytkownik są nie pełni kwalifikujących się nazwy elementów członkowskich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="82787-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="82787-119">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="82787-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="82787-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="82787-120">Security</span></span>  
 <span data-ttu-id="82787-121">Jeśli przenosisz hasła przez sieć, należy użyć metody bezpiecznego przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="82787-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="82787-122">Aby uzyskać więcej informacji, zobacz [zabezpieczenia aplikacji sieci Web platformy ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="82787-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="82787-123">Można zwiększyć dokładność `ValidatePassword` funkcja poprzez dodanie dodatkowej złożoności kontroli:</span><span class="sxs-lookup"><span data-stu-id="82787-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="82787-124">Porównaj hasło i jego podciągów przed nazwę użytkownika, identyfikator użytkownika i słownika zdefiniowanego przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="82787-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="82787-125">Ponadto należy traktować podobnych znaków jako równoważne podczas przeprowadzania porównania.</span><span class="sxs-lookup"><span data-stu-id="82787-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="82787-126">Na przykład zaliczenie litery "l" i "e" odpowiednikiem cyfry "1" i "3".</span><span class="sxs-lookup"><span data-stu-id="82787-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="82787-127">Jeśli ma tylko jedną wielką literę, upewnij się, że nie jest pierwszym znakiem hasła.</span><span class="sxs-lookup"><span data-stu-id="82787-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="82787-128">Upewnij się, że ostatnich dwóch znaków hasła są znaki.</span><span class="sxs-lookup"><span data-stu-id="82787-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="82787-129">Nie zezwalaj na hasła, w których wszystkie symbole są wprowadzane z klawiatury w górnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="82787-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82787-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82787-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="82787-131">[Zabezpieczenia aplikacji sieci Web platformy ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="82787-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
