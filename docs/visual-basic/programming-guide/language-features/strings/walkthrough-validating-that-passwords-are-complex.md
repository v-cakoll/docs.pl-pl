---
title: Walidacja złożoności haseł
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 6e8697379a6fbb5cc15b60291e5b822897c2c013
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348329"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="b8cb0-102">Wskazówki: sprawdzanie poprawności złożoności haseł (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8cb0-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="b8cb0-103">Ta metoda sprawdza pewne cechy silnego hasła i aktualizuje parametr ciągu z informacjami o tym, które sprawdzenia nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="b8cb0-104">Hasła mogą być używane w zabezpieczonym systemie w celu autoryzowania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="b8cb0-105">Jednak hasła muszą być trudne dla nieautoryzowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="b8cb0-106">Osoby atakujące mogą korzystać z programu *ataku słownikowego* , który wykonuje iterację we wszystkich słowach w słowniku (lub wielu słownikach w różnych językach) i sprawdza, czy którykolwiek z tych słów działa jako hasło użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="b8cb0-107">Słabe hasła, takie jak "Yankees" lub "Mustang", można szybko wypróbować.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="b8cb0-108">Silniejsze hasła, na przykład "? "L1N3vaFiNdMeyeP@sSWerd!", są znacznie mniej znaczące do odgadnięcia.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="b8cb0-109">System chroniony hasłem powinien mieć pewność, że użytkownicy wybierają silne hasła.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="b8cb0-110">Silne hasło jest złożone (zawierające kombinację wielkich, małych liter, cyfr i znaków specjalnych) i nie jest słowem.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="b8cb0-111">W tym przykładzie pokazano, jak sprawdzić złożoność.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8cb0-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8cb0-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="b8cb0-113">Kod</span><span class="sxs-lookup"><span data-stu-id="b8cb0-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8cb0-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b8cb0-114">Compiling the Code</span></span>  
 <span data-ttu-id="b8cb0-115">Wywołaj tę metodę, przekazując ciąg, który zawiera to hasło.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="b8cb0-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b8cb0-116">This example requires:</span></span>  
  
- <span data-ttu-id="b8cb0-117">Dostęp do elementów członkowskich <xref:System.Text.RegularExpressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="b8cb0-118">Dodaj instrukcję `Imports`, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="b8cb0-119">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="b8cb0-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="b8cb0-120">Bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="b8cb0-120">Security</span></span>  
 <span data-ttu-id="b8cb0-121">Jeśli przenosisz hasło za pośrednictwem sieci, musisz użyć bezpiecznej metody przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="b8cb0-122">Aby uzyskać więcej informacji, zobacz [ASP.NET zabezpieczenia aplikacji sieci Web](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b8cb0-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="b8cb0-123">Dokładność funkcji `ValidatePassword` można poprawić, dodając dodatkowe sprawdzenia złożoności:</span><span class="sxs-lookup"><span data-stu-id="b8cb0-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
- <span data-ttu-id="b8cb0-124">Porównaj hasło i jego podciągi w odniesieniu do nazwy użytkownika, identyfikatora użytkownika i słownika zdefiniowanego przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="b8cb0-125">Ponadto Traktuj podobne wizualnie znaki jako równoważne podczas przeprowadzania porównania.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="b8cb0-126">Na przykład Traktuj litery "l" i "e" jako równoważne cyfrom "1" i "3".</span><span class="sxs-lookup"><span data-stu-id="b8cb0-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
- <span data-ttu-id="b8cb0-127">Jeśli istnieje tylko jeden znak pisany wielkimi literami, upewnij się, że nie jest on pierwszym znakiem hasła.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
- <span data-ttu-id="b8cb0-128">Upewnij się, że ostatnie dwa znaki hasła są literami znaków.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
- <span data-ttu-id="b8cb0-129">Nie Zezwalaj na hasła, w których wszystkie symbole są wprowadzane z górnego wiersza klawiatury.</span><span class="sxs-lookup"><span data-stu-id="b8cb0-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8cb0-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8cb0-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="b8cb0-131">[Zabezpieczenia aplikacji sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b8cb0-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
