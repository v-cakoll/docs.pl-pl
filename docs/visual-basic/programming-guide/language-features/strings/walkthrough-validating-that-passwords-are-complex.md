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
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Wskazówki: sprawdzanie poprawności złożoności haseł (Visual Basic)
Ta metoda sprawdza, czy niektóre cechy silnego hasła i aktualizuje informacje o tym, które sprawdza hasła nie powiedzie się. parametr typu string.  
  
 Hasła mogą być wykorzystywane w bezpieczny system do autoryzacji użytkownika. Jednak musi być trudne dla nieautoryzowanych użytkowników do odgadnięcia hasła. Osoby atakujące mogą wykorzystać *atak słownikowy* program, który iteruje po wszystkich wyrazów słownika (lub słowniki wielu w różnych językach) i sprawdza, czy dowolne wyrażenie działa jako hasło użytkownika. Słabe hasła, takie jak "Wydarzenia dotyczące Legii" lub "Mustang" można szybko złamać. Silniejszych haseł, takich jak "? Użytkownik "L1N3vaFiNdMeyeP@sSWerd!", jest znacznie mniej prawdopodobne złamać. System chroniony hasłem powinien upewnić się, że użytkownicy wybiorą hasła silne.  
  
 Silne hasła jest złożony, (zawierających mieszankę wielkie litery, małe litery, liczbowych i specjalne znaków) i nie jest ona słowem. W tym przykładzie przedstawiono sposób weryfikacji złożoności.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tę metodę można wywołać, przekazując ciąg, który zawiera hasło.  
  
 Ten przykład wymaga:  
  
-   Dostęp do elementów członkowskich <xref:System.Text.RegularExpressions> przestrzeni nazw. Dodaj `Imports` instrukcję, jeśli użytkownik jest całkowicie niekwalifikujących nazwy elementów członkowskich w kodzie. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Zabezpieczenia  
 Jeśli przenosisz hasła przez sieć, należy użyć bezpieczną metodę transferu danych. Aby uzyskać więcej informacji, zobacz [zabezpieczenia aplikacji sieci Web ASP.NET](https://msdn.microsoft.com/library/330a99hc).  
  
 Można zwiększyć dokładność `ValidatePassword` funkcja przez dodanie złożoności dodatkowe kontrole:  
  
-   Porównaj hasło i jego podciągów przed nazwę użytkownika, identyfikator użytkownika i słowniku zdefiniowanym przez aplikację. Ponadto należy traktować wizualnie podobne znaków jako równoważne podczas przeprowadzania porównania. Na przykład traktować litery "l" i "e" jako odpowiednik liczb, "1" i "3".  
  
-   W przypadku tylko jedną wielką literę, upewnij się, że nie jest to pierwszy znak hasła.  
  
-   Upewnij się, że ostatnich dwóch znaków hasła są znaki.  
  
-   Nie zezwalaj hasła, w których wszystkie symbole są wprowadzane z klawiatury w górnym wierszu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Text.RegularExpressions.Regex>  
 [Zabezpieczenia aplikacji sieci Web ASP.NET](https://msdn.microsoft.com/library/330a99hc)
